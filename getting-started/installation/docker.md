# Docker

![ContentBox + Docker](https://www.ortussolutions.com/\_\_media/cbox-plus-docker.jpg)

ContentBox sports its very own [ContentBox Docker image](https://hub.docker.com/r/ortussolutions/contentbox/). As with the [CommandBox image](https://hub.docker.com/r/ortussolutions/commandbox/), the `[major].[minor].[patch]` versioning mirrors the upstream product version, so it's easy to pull deploy a specific version, should your application require it.

## Playing around

The image is packaged with a self-contained **express** version, which uses an in-memory [H2](https://github.com/ortus/contentbox-modular-cms/tree/76cb63aa894e4f019c2d324f6bfb86f8d0142a92/www.h2database.com/html/main.html) database. To stand up an image using an un-configured express edition, simply run:

```bash
docker pull ortussolutions/contentbox &&
docker run -p 8080:8080 \
-e EXPRESS=true \
-e INSTALL=true \
ortussolutions/contentbox
```

{% hint style="info" %}
The command above is using `&&` to concatenate the two commands which will work under \*unix. If you are in windows, replace `&&` with `;` in Powershell, replace `&&` with `&` in Cmd, or run the two commands separately
{% endhint %}

A new container will be spun up from the image and, upon opening your browser to `http://[docker machine ip]:8080`, you will be directed to configure your [ContentBox](https://www.ortussolutions.com/products/contentbox) installation using the ContentBox Installer. That easy! Boom!

## CommandBox Image Features

The ContentBox image is based on the [CommandBox Image,](https://hub.docker.com/r/ortussolutions/commandbox/) so all features and environment variables are applicable. Please refer to that documentation as well: [https://hub.docker.com/r/ortussolutions/commandbox/](https://hub.docker.com/r/ortussolutions/commandbox/)

## Persisting Data Between Restarts

The above `run` command produces an image which is self-contained, and would be destroyed when the container is stopped. If we wanted to run a version in production, we would need to **persist**, at the very minimum, the database and your custom assets (widgets, modules, themes, and media library). In order to do this, we need to mount those resources into the Docker host file system.

By convention, the `express` H2 database is stored at `/data/contentbox/db` inside the container. In addition, the custom content module which contains your custom themes, widgets, modules, and media library are stored under `/app/modules_app/contentbox-custom`.

{% hint style="warning" %}
In 3.x versions the default storage location for the CMS user media assets was set to `/app/includes/shared/media` and the contentbox-custom module did not exist.
{% endhint %}

### Mountable Points

| Mount Point                          | Description                                                               |
| ------------------------------------ | ------------------------------------------------------------------------- |
| `/data/contentbox/db`                | The express H2 database                                                   |
| `/app/modules_app/contentbox-custom` | The custom code module                                                    |
| `/app/includes/shared/media`         | _\*\*The legacy media location, use the custom modules location instead._ |

Let's mount both of those volume points so that our database and user assets persists between restarts:

```bash
docker run -p 8080:8080 \
-e EXPRESS=true \
-e INSTALL=true \
-v `pwd`/contentbox-db:/data/contentbox/db \
-v `pwd`/contentbox-custom:/app/modules_app/contentbox-custom \
ortussolutions/contentbox
```

Now, once our image is up, we can walk through the initial configuration. Once the configuration is complete, simply **stop** the container and then **start** it without the environment variable `INSTALL` in place. The H2 database and uploads will be persisted and the installer will be removed automatically on container start.

```bash
docker run -p 8080:8080 \
-e EXPRESS=true \
-v `pwd`/contentbox-db:/data/contentbox/db \
-v `pwd`/contentbox-media:/app/includes/shared/media \
ortussolutions/contentbox
```

### `INSTALL` Setting Caveats

Please remember that the INSTALL environment variable is ONLY used to go through the ContentBox installer wizard. Once the database is seeded with the installation process, you will no longer use it unless you want to reconfigure the installation.

## Custom Database Configuration

If you would like to connect your container to an external database system, you can very easily do so, which would allow us to connect from multiple containers in a distributed fashion (MySQL, Oracle, MSSQL, etc). If not, you run the risk of file locks if multiple container replicas are sharing the same H2 database.

{% hint style="success" %}
**Tip:** We would suggest you use the H2 database or EXPRESS edition when using only 1 replica.
{% endhint %}

The image is configured to allow all ORM-supported JDBC drivers to be configured by specifying the environment variables to connect. Alternately, you may specify a [`CFCONFIG`](https://www.forgebox.io/view/commandbox-cfconfig) environment variable which points to a file containing your engine configuration, including data sources.

{% hint style="info" %}
By convention, the **datasource name** expected is simply named `contentbox`.
{% endhint %}

To programmatically configure the database on container start, environment variables that represent your datasource configuration should be provided. There are two patterns supported:

1. `DB_DRIVER` configuration - which may be used for **Adobe Coldfusion** servers
2. `DB_CLASS` configuration - which configures a datasource by JDBC driver and connection string (Both Adobe and Lucee)

An example container `run` command, configuring a MySQL database would be executed like so:

```bash
docker run -p 8080:8080 \
-e 'INSTALL=true' \
-e 'CFCONFIG_ADMINPASSWORD=myS3cur3P455' \
-e "DB_CONNECTION_STRING=jdbc:mysql://mysqlhost:3306/contentbox_docker?useUnicode=true&characterEncoding=UTF-8&useLegacyDatetimeCode=true" \
-e 'DB_CLASS=org.gjt.mm.mysql.Driver' \
-e 'DB_USER=contentbox_user' \
-e 'DB_PASSWORD=myS3cur3P455' \
-v `pwd`/contentbox-media:/app/includes/shared/media \
ortussolutions/contentbox
```

To use the `DB_DRIVER` syntax for Adobe Coldfusion, an example `run` command would be:

```bash
docker run -p 8080:8080 \
-e 'CFENGINE=adobe@11' \
-e 'INSTALL=true' \
-e 'CFCONFIG_ADMINPASSWORD=myS3cur3P455' \
-e 'DB_DRIVER=MSSQLServer' \
-e 'DB_HOST=sqlserver_host' \
-e 'DB_PORT=1433' \
-e 'DB_NAME=contentbox_docker' \
-e 'DB_USER=sa' \
-e 'DB_PASSWORD=myS3cur3P455' \
-v `pwd`/contentbox-media:/app/includes/shared/media \
ortussolutions/contentbox
```

As you can see, these commands can become quite long. As such, using [Docker Compose](https://docs.docker.com/compose/) or [CFConfig](https://www.gitbook.com/book/ortus/cfconfig-documentation/details) may provide a more manageable alternative.

## Granular Environmental Control

A number of environment variables, specific to the ContentBox image, are available for use. They include:

* `EXPRESS=true` - Uses an H2, in-memory database. Useful for very small sites or for testing the image. See [http://www.h2database.com/html/main.html](http://www.h2database.com/html/main.html)
* `INSTALL=true` (alias: `INSTALLER`) - Adds the installer module at runtime, to assist in configuring your installation. You would omit this from your `run` command, once your database has been configured
* `BE=true` - Uses the **bleeding edge** snapshot of the ContentBox CMS, else we will defer to the **latest stable** version of ContentBox.
* `HEALTHCHECK_URI` - Specifies the URI endpoint for container health checks.  By default, this is set `http://127.0.0.1:${PORT}/` at 30s  intervals with 5 retries and a timeout of 60s
* `FWREINIT_PW` - Allows you to specify the reinit password for the ColdBox framework
* `SESSION_STORAGE` - Allows the customization of session storage. Allows any valid `this.sessionStorage` value, available in [Application.cfc](http://docs.lucee.org/reference/tags/application.html). By default, it will use the JDBC connection to store your sessions in your database of choice.
* `DISTRIBUTED_CACHE` - Allows you to specify a CacheBox cache region for distributing ContentBox content, flash messages, cache storage, RSS feeds, sitemaps, and settings. There are only three cache regions defined in this image: `default`, `template` and `jdbc`. `jdbc` is the default cache that will distribute your data, `default` and `template` are in-memory caches. Please see the distributed caching section below to see how to register more caches.
* `H2_DIR` - Allows you to specify a custom directory path for your H2 database. By convention, this is set to `/data/contentbox/db` within the container
* `contentbox_default_*` - All [Contentbox](https://www.ortussolutions.com/products/contentbox) "[Geek Settings](https://contentbox.ortusbooks.com/content/using/system/settings.html)" may be provided as environment variables, allowing granular control of your ContentBox settings.
* `ORM_SECONDARY_CACHE` - If `true` it will activate the ORM secondary cash to the `ehcache` provider. By default, it is turned off.
* `ORM_DIALECT` - You can choose the specific ORM dialect if needed, if not we will try to auto-detect it for you.
* `HEADLESS=false` - If `true` then this image will not publish an Admin module, just the core, REST and UI modules.

In addition, the [CommandBox docker image](https://hub.docker.com/r/ortussolutions/commandbox/) environment variables are also available to use in your container. For additional information on using the CommandBox docker image, see [the initial release blog entry](https://www.ortussolutions.com/blog/commandbox-docker-image-360-released).

## Automatic Session Distribution

By default, the ContentBox image will use the Lucee Open Source CFML engine for running the application. It will also configure the **datasource** to store **user sessions** so you can easily scale the image or send it to Docker Swarm, Kubernetes, etc for scalability.

You can also use the `SESSION_STORAGE` environment variable to switch the connection to any backend you like.

## Distributed Caching

By default, our image configures a `jdbc` CacheBox cache region that will be used to distribute settings, sessions, flash data, content, RSS feeds, sitemaps, etc. This means that out-of-the-box, your ContentBox containers can use the database to distribute its content within a swarm or set of services. However, if you would like to use your own CacheBox providers or a more sophisticated distributed cache like Redis or Couchbase, you can.

We have also prepared a docker-compose and distribution example using Redis (more caches to come) and the ContentBox image. This example will allow you to have a stack that can easily distribute your sessions and content via Redis. You can find the repository here: [https://github.com/Ortus-Solutions/docker-contentbox-distributed](https://github.com/Ortus-Solutions/docker-contentbox-distributed)

{% hint style="warning" %}
Please check the Database for CF Sessions, to ensure this table is purging older expired values. If this table grows in size, you will notice performance hits and may need to schedule a purge or truncation manually.
{% endhint %}

## Healthchecks

The image contains built-in capabilities for health checks for the running application. You can customize the URL entry point by using the `HEALTHCHECK_URI` environment variable. By default, this is set `http://127.0.0.1:${PORT}/` at 30s intervals with 5 retries and a timeout of 60s.

## In Short

The ContentBox image for Docker re-vamps the entire Modular CMS game by de-coupling your customizations and user assets from the underlying framework. It can make your source code lighter-weight, as well as providing you with a standardized development environment, which matches your production container strategy.
