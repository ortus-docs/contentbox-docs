# Upgrading From v4.x

ContentBox v5.x is a **major** version update and will require the following instructions to update your v4.x installations. Please follow this guide or contact us at [info@ortussolutions.com](mailto:info@ortussolutions.com) so we can assist you during your upgrade process.

{% hint style="danger" %}
If you are in version 3.x then you will need to upgrade to version 4.x before upgrading to the 5.x series [https://contentbox.ortusbooks.com/v/v4.x/intro/introduction/upgrading-from-v3.x](https://contentbox.ortusbooks.com/v/v4.x/intro/introduction/upgrading-from-v3.x)
{% endhint %}

## 1. Requirements

All Upgrades to ContentBox should be done with the assistance of [CommandBox CLI.](https://www.ortussolutions.com/products/commandbox) So make sure you have CommandBox installed in the server/machine you will be upgrading.

### Install CommandBox Dependencies

Once you have CommandBox installed, let's make sure we have some global dependencies installed so CommandBox can work with ContentBox automated upgrades:

```bash
# install env controls and db migrations
box install commandbox-dotenv,commandbox-migrations
```

This will install the [environment](https://forgebox.io/view/commandbox-dotenv) module and the [database migrations](https://forgebox.io/view/commandbox-migrations) module that will be used to provide upgrades in the future.  This is only done once. ContentBox 5 already ships with these dependencies once you install it.

### Environment \(`.env`\)

The upgrade process and the database migrations rely on environment variables/secrets in order to connect to your database and migrate it.  Create an `.env` file in the root of the ContentBox installation and add in your migrations database credentials below and/or the CommandBox server database credentials as well.

```text
#################################################################
# App Name and Environment
#################################################################
APPNAME=ContentBox Modular CMS
# This can be development, staging, production or custom.
ENVIRONMENT=development

#################################################################
# ContentBox Migrations Variables
# --------------------------------
# This is used for the automated CLI migrationts to
# upgrade your ContentBox database. Uncomment the RDBMS connection
# of your choice.
#################################################################
MIGRATIONS_DATABASE=contentbox
MIGRATIONS_USER=root
MIGRATIONS_PASSWORD=
# MySQL
MIGRATIONS_CONNECTIONSTRING=jdbc:mysql://127.0.0.1:3306/contentbox?useSSL=false&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC&useLegacyDatetimeCode=true
MIGRATIONS_CLASS=com.mysql.cj.jdbc.Driver
MIGRATIONS_BUNDLENAME=com.mysql.cj
MIGRATIONS_BUNDLEVERSION=8.0.19
# PostgreSQL
#MIGRATIONS_CONNECTIONSTRING=jdbc:postgresql://localhost:5432/contentbox
#MIGRATIONS_CLASS=org.postgresql.Driver
#MIGRATIONS_BUNDLENAME=org.postgresql.jdbc42
#MIGRATIONS_BUNDLEVERSION=9.4.1212
# Microsoft SQL
#MIGRATIONS_CONNECTIONSTRING=jdbc:sqlserver://localhost:1433;DATABASENAME=contentbox;sendStringParametersAsUnicode=true;SelectMethod=direct
#MIGRATIONS_CLASS=com.microsoft.sqlserver.jdbc.SQLServerDriver
#MIGRATIONS_BUNDLENAME=mssqljdbc4
#MIGRATIONS_BUNDLEVERSION=4.0.2206.100

#################################################################
# ContentBox Datasource Connection
# --------------------------------
# This is used for a CommandBox application server to configure
# your database connection using the .cfconfig.json file in the
# root of your installation.
# Uncomment the RDBMS of your choice
#################################################################

######################################################
# MySQL 5.7 DB Driver
######################################################
DB_CLASS=com.mysql.cj.jdbc.Driver
DB_DRIVER=MySQL
# Lucee Bundle Info: 5.1.40 IS THE ONLY ONE THAT WORKS FOR HIBERNATE
DB_BUNDLEVERSION=5.1.40
DB_BUNDLENAME=com.mysql.cj
# DB Location
DB_HOST=127.0.0.1
DB_PORT=3306
DB_CONNECTIONSTRING=jdbc:mysql://127.0.0.1:3306/contentbox?useSSL=false&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC&useLegacyDatetimeCode=true
# DB Credentials
DB_DATABASE=contentbox
DB_USER=root
DB_PASSWORD=mysql

######################################################
# MySQL 8 DB Driver
######################################################
#DB_CLASS=com.mysql.cj.jdbc.Driver
#DB_DRIVER=MySQL
#DB_BUNDLEVERSION=8.0.19
#DB_BUNDLENAME=com.mysql.cj
## DB Location
#DB_HOST=127.0.0.1
#DB_PORT=3306
#DB_CONNECTIONSTRING=jdbc:mysql://127.0.0.1:3306/contentbox?useSSL=false&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC&useLegacyDatetimeCode=true
## DB Credentials
#DB_DATABASE=contentbox
#DB_USER=root
#DB_PASSWORD=mysql

######################################################
# PostgreSQL DB Driver #
######################################################
#DB_CLASS=org.postgresql.Driver
#DB_DRIVER=PostgreSQL
#DB_BUNDLEVERSION=9.4.1212
#DB_BUNDLENAME=org.postgresql.jdbc42
## DB Location
#DB_HOST=127.0.0.1
#DB_PORT=5432
#DB_CONNECTIONSTRING=jdbc:postgresql://localhost:5432/contentbox
## DB Credentials
#DB_DATABASE=contentbox
#DB_USER=contentbox
#DB_PASSWORD=contentbox

######################################################
# Microsoft SQL DB Driver #
######################################################
#DB_CLASS=com.microsoft.sqlserver.jdbc.SQLServerDriver
#DB_DRIVER=mssql
#DB_BUNDLEVERSION=4.0.2206.100
#DB_BUNDLENAME=mssqljdbc4
## DB Location
#DB_HOST=127.0.0.1
#DB_PORT=1433
#DB_CONNECTIONSTRING=jdbc:sqlserver://localhost:1433;DATABASENAME=contentbox;sendStringParametersAsUnicode=true;SelectMethod=direct
## DB Credentials
#DB_DATABASE=contentbox
#DB_USER=contentbox
#DB_PASSWORD=contentbox

#################################################################
# JWT Information
# --------------------------------
# You can seed the JWT secret below or you can also leave it empty
# and ContentBox will auto-generate one for you that rotates
# everytime the application restarts or expires
#################################################################
JWT_SECRET=

#################################################################
# AWS S3 or Digital Ocean Spaces
# --------------------------------
# If you are using any of our S3/Spaces compatible storages, you
# will have to seed your credentials and information below
#################################################################
S3_ACCESS_KEY=
S3_SECRET_KEY=
S3_REGION=us-east-1
S3_DOMAIN=amazonaws.com
S3_BUCKET=
```

{% hint style="success" %}
Please note that once you are on ContentBox 5 none of these steps will be necessary anymore. Since it is part of the default installation.
{% endhint %}

{% hint style="danger" %}
Please note that this `.env` file should **NEVER** be in source control and **NEVER** be web accessible
{% endhint %}

Once your environment file is seeded open the `box.json` of the ContentBox 4 installation and add the following `cfmigrations` as another root element:

```javascript
...

"cfmigrations":{
    "schema":"${MIGRATIONS_DATABASE}",
    "connectionInfo":{
        "password":"${MIGRATIONS_PASSWORD}",
        "connectionString":"${MIGRATIONS_CONNECTIONSTRING}",
        "class":"${MIGRATIONS_CLASS}",
        "username":"${MIGRATIONS_USER}",
        "bundleName":"${MIGRATIONS_BUNDLENAME}",
        "bundleVersion":"${MIGRATIONS_BUNDLEVERSION}"
    },
    "defaultGrammar":"AutoDiscover@qb"
}

...
```

This will tell CommandBox migrations how to connect to your database in preparation for upgrades. Once this is done we can reload the CommandBox shell with the command `reload` and it's time to make sure migrations can connect to your database with the variables and connection information:

```bash
# Run the migration table installation
$ migrate install
 Migration table installed!
```

If this command succeeds, then we are ready to go to the next step.  If it fails, then check your credentials, connection information and that you can actually connect to the database. If not, ask away in our community forum: [https://community.ortussolutions.com/c/communities/contentbox/15](https://community.ortussolutions.com/c/communities/contentbox/15)

## 2. Backups

Please make sure you backup your source code and your database. We are not liable for broken installations.

## 3. Run the Updater

We have prepared a CommandBox recipe that will upgrade your installation in one easy execution.

### \*nix/Mac

If you are in a Linux or Mac environment you can execute the recipe using the following shell commands from the root directory of your application.

```bash
# Execute our recipe
curl -o updater.boxr https://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/5.0.0/updater.boxr | box recipe updater.boxr
# Clean it upt
rm updater.boxr
```

### Windows

If you are in windows, download the following recipe:

[http://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/5.0.0/updater.boxr](http://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/5.0.0/updater.boxr)

and place it in the root of your project. Then issue the following CommandBox shell command to execute it.

```bash
box recipe updater.boxr
```

Once it runs, remove the file and you are done! You can start up your new engine!



