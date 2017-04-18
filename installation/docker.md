<
p class="text-align:center">
<img src="https://www.ortussolutions.com/__media/cbox-plus-docker.jpg" alt="ContentBox + Docker" class="img-responsive"/>
</p>

<br><br>

ContentBox sports its very own [ContentBox Docker image](https://hub.docker.com/r/ortussolutions/contentbox/). As with the [CommandBox image](https://hub.docker.com/r/ortussolutions/commandbox/), the `[major].[minor].[patch]` versioning mirrors the upstream product version, so it's easy to pull deploy a specific version, should your application require it.

## Playing around

The image is packaged with a self-contained **express** version, which uses an in-memory [H2](//www.h2database.com/html/main.html) database. To stand up an image for testing purposes, using an unconfigured express edition, simply run:

```bash
docker pull ortussolutions/contentbox &&
docker run -p 8080:8080 \
-e express=true \
-e install=true \
ortussolutions/contentbox
```

A new container will be spun up from the image and, upon opening your browser to `http://[docker machine ip]:8080`, you will be directed to configure your [ContentBox](https://www.ortussolutions.com/products/contentbox) installation using the ContentBox Installer.

## Persisting Data Between Restarts

The above `run` command produces an image which is self-contained, and would be destroyed when the container is stopped. If we wanted to run a version in production, we would need to persist, at the very minimum, the database and user-uploaded assets. In order to do this we need to mount those resources in to the Docker host file system.

By convention, the `express` H2 database is stored at `/data/contentbox/db` inside the container. In addition, the default storage location for the CMS user media assets is set to `/app/includes/shared/media`. Let's mount both of those volume points, so that our database and user-uploaded assets persists between restarts:

```bash
docker run -p 8080:8080 \
-e express=true \
-e install=true \
-v `pwd`/contentbox-db:/data/contentbox/db \
-v `pwd`/contentbox-media:/app/includes/shared/media \
ortussolutions/contentbox
```


Now, once our image is up, we can walk through the initial configuration. Once configuration is complete, simply stop the container and then start it without the environment variable `install` in place. The H2 database and uploads will be persisted and the installer will be removed automatically on container start.

```bash
docker run -p 8080:8080 \
-e express=true \
-v `pwd`/contentbox-db:/data/contentbox/db \
-v `pwd`/contentbox-media:/app/includes/shared/media \
ortussolutions/contentbox
```

## Custom Database Configuration

Because the `express` flag produces a ContentBox installation which runs on a file-based, in-memory H2 database, it's really suitable only for testing or low-traffic containers. For scalability, we would want to connect to an database server, which would allow us to connect from multiple containers in a distributed fasion (MySQL, Oracle, MSSQL, etc)

The image is configured to allow all ORM-supported JDBC drivers to be configured by specifying the environment variables to connect. Alternately, you may specify a [`CFCONFIG`](https://www.forgebox.io/view/commandbox-cfconfig) environment variable which points to file containing your engine configuration, including datasources.

By convention, the datasource name expected is simply named `contentbox`.

To programatically configure the database on container start, environment variables which represent your datasource configuration should be provided. There are two patterns supported:

1. `DB_DRIVER` configuration - which may be used for Adobe Coldfusion servers
2. `DB_CLASS` configuration - which configures a datasource by JDBC driver and connection string (Both Adobe and Lucee)

An example container `run` command, configuring a MySQL database would be executed like so:

```bash
docker run -p 8080:8080 \
-e 'installer=true' \
-e 'cfconfig_adminPassword=myS3cur3P455' \
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
-e 'installer=true' \
-e 'cfconfig_adminPassword=myS3cur3P455' \
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

A number of environment variables, specific to the ContentBox image, are availabe for use. They include:

* `express=true` - Uses an H2, in-memory database. Useful for very small sites or for testing the image. See http://www.h2database.com/html/main.html
* `install=true` (alias: `installer`) - Adds the installer module at runtime, to assit in configuring your installation. You would omit this from your `run` command, once your database has been configured
* `$HEALTHCHECK_URI` - Specifies the URI endpoint for container health checks.  By default, this is set `http://127.0.0.1:${PORT}/` at 1 minute intervals with 5 retries and a timeout of 30s
* `FWREINIT_PW` - Allows you to specify the reinit password for the ColdBox framework
* `SESSION_STORAGE` - Allows the customization of session storage. Allows any valid `this.sessionStorage` value, available in [Application.cfc](http://docs.lucee.org/reference/tags/application.html). By default it will use the JDBC connection to store your sessions in your database of choice.
* `DISTRIBUTED_CACHE` - Allows you to specify a CacheBox cache region for distributing ContentBox content, flash messages, cache storage, RSS feeds, sitemaps and settings. There are only three cache regions defined in this image: `default`, `template` and `jdbc`. `jdbc` is the default cache that will distribute your data, `default` and `template` are in-memory caches. Please see the distributed caching section below to see how to register more caches.
* `H2_DIR` - Allows you to specify a custom directory path for your H2 database. By convention, this is set to `/data/contentbox/db` within the container
* `contentbox_*` - All [Contentbox](https://www.ortussolutions.com/products/contentbox) "[Geek Settings](https://contentbox.ortusbooks.com/content/using/system/settings.html)" may be provided as environment variables, allowing granular control of your ContentBox settings.
* `ORM_SECONDARY_CACHE` - If `true` it will activate the ORM secondary cash to the `ehcache` provider. By default it is turned off.
* `ORM_DIALECT` - You can choose the specific ORM dialect if needed, if not we will try to auto-detect it for you.

In addition, the [CommandBox docker image](https://hub.docker.com/r/ortussolutions/commandbox/) environment variables are also available to use in your container. For additional information on using the CommandBox docker image, see [the initial release blog entry](https://www.ortussolutions.com/blog/commandbox-docker-image-360-released).

## Automatic Session Distribution

By default, the ContentBox image will use the Lucee Open Source CFML engine for running the application. It will also configure the datasource to store user sessions so you can easily scale the image or send it to Docker Swarm, Kubernetes, etc for scalability. You can also use the `SESSION_STORAGE` environment variable to switch the connection to any backend you like.

## Distributed Caching

By default, our image configures a `jdbc` CacheBox cache region that will be used to distribute settings, flash data, content, RSS feeds, sitemaps, etc. This means that out-of-the-box, your ContentBox containers can use the database to distribute its content within a swarm or set of services. However, if you would like to use your own CacheBox providers or a more sophisticated distributed cache like Redis or Couchbase, you can.

We have also prepared a docker compose and distribution example using Redis (more caches to come) and the ContentBox image. This example will allow you to have a stack that can easily distribute your sessions and content via Redis. You can find the repository here: [https://github.com/Ortus-Solutions/docker-contentbox-distributed](https://github.com/Ortus-Solutions/docker-contentbox-distributed)

## Healthchecks

The image contains built-in capabilities for healthchecks for the running application.  You can customize the URL entry point by using the `$HEALTHCHECK_URI` environment variable. By default, this is set `http://127.0.0.1:${PORT}/` at 1 minute intervals with 5 retries and a timeout of 30s.

## In The Real World

Playing around with the image is great, but what does this mean for you as a developer? Effectively it means that you can develop and deploy customized CMS applications with only a single theme directory (and, possibly, a customized `config/Coldbox.cfc` file).

The image location for the themes directory in ContentBox is `/app/modules/contentbox/themes`. Any theme mounted in to this directory can be configured in the run of the container, which means you no longer have to commit an entire ContentBox installation to your repository. You can mount only those files and folders ( e.g. - custom modules ) necessary for your application to do its thing. In addition, you also have power to reconfigure ContentBox settings on-the-fly using environment variables prefixed with `contentbox_{site}_{setting}={value}`.

Let's start an image with a custom theme, and a ColdBox module, persisting our assets, while using a MySQL database with the installer:

```bash
docker run -p 8080:8080 \
-e 'installer=true' \
-e 'cfconfig_adminPassword=myS3cur3P455' \
-e "DB_CONNECTION_STRING=jdbc:mysql://mysqlhost:3306/contentbox_docker?useUnicode=true&characterEncoding=UTF-8&useLegacyDatetimeCode=true" \
-e 'DB_CLASS=org.gjt.mm.mysql.Driver' \
-e 'DB_USER=contentbox_user' \
-e 'DB_PASSWORD=myS3cur3P455' \
-v `pwd`/contentbox-media:/app/includes/shared/media \
ortussolutions/contentbox
-e 'contentbox_cb_site_theme=myCustomTheme' \
-v `pwd`/myCustomTheme:/app/modules/contentbox/themes/myCustomTheme \
ortussolutions/contentbox
-v `pwd`/myAwesomeModule:/app/modules/myAwesomeModule \
ortussolutions/contentbox
```

### Customizable Volume Paths
Please note the following customizable paths for custom assets.

* `/app/includes/shared/media` - ContentBox Media Manager
* `/app/modules` - CommandBox managed modules
* `/app/modules_app` - Custom ColdBox modules
* `/app/modules/contentbox/themes` - Custom ContentBox Themes
* `/app/modules/contentbox/widgets` - Custom ContentBox Widgets
* `/app/modules/contentbox/modules_user` - Custom ContentBox Modules

There are more geek settings and paths that we have time to go in to in this post but, suffice it to say, you will be able to control nearly every aspect of your site settings on the startup of your Docker container.

For a list open source themes, readily available for your customization, [visit Forgebox](https://www.forgebox.io/type/contentbox-themes).


> **Note** that the `Application.cfc` and the `config` directory of the ContentBox Docker image have some customizations specific to their purpose. If you wish to customize those, please see [the Docker build repository files](https://github.com/Ortus-Solutions/docker-commandbox/tree/master/resources/contentbox) to ensure those customizations are present in yours.


## In Short

The ContentBox image for Docker re-vamps the entire Modular CMS game by de-coupling your customizations and user assets from the underlying framework. It can makes your source code lighter-weight, as well as providing you with a standardized development environment, which matches your production container strategy.





