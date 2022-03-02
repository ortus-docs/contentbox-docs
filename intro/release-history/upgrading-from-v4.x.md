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

### Environment (`.env`)

The upgrade process and the database migrations rely on environment variables/secrets in order to connect to your database and migrate it.  Create an `.env` file in the root of the ContentBox installation and add in the configuration according to your database and configuration preferences.

{% hint style="success" %}
To generate a JWT secret key you can use CommandBox and run the following in the command prompt: `#generatesecretkey "blowfish" 256`
{% endhint %}

```bash
#################################################################
# App Name and Environment
#################################################################
APPNAME=ContentBox Modular CMS
# This can be development, staging, production or custom.
ENVIRONMENT=development
# The password for the CFML Engine Administrator
CFCONFIG_ADMINPASSWORD=contentbox
# The ColdBox Reinit password
COLDBOX_REINITPASSWORD=
# How long do admin sessions last (In Minutes)
COLDBOX_SESSION_TIMEOUT=60
# Development CBDebugger
CBDEBUGGER_ENABLED=false

#################################################################
# ContentBox ORM Settings
# --------------------------------
# This is used to configure the ORM via env settings usually for
# different RDBMS settings or options
#################################################################
# Dialect choices:
# 	MySQL, Hypersonic 	=> org.hibernate.dialect.MySQL5InnoDBDialect,
# 	PostgreSQL 			=> PostgreSQL
# 	Microsoft SQL 		=> org.hibernate.dialect.SQLServer2008Dialect
# 	Oracle 				=> Oracle10g
# 	Derby 				=> Derby
ORM_DIALECT=org.hibernate.dialect.MySQL5InnoDBDialect
# Log sql to the console or not
ORM_LOGSQL=true
# Sql Script to execute after ORM is initialized
ORM_SQL_SCRIPT=
# Activate secondary cache or disable it
ORM_SECONDARY_CACHE=false
ORM_SECONDARY_CACHE_PROVIDER=ehcache

#################################################################
# ContentBox Datsource and Migrations Variables
# ----------------------------------------------------------------
# These settings configure the datasource connection to your database
# Please make sure you read the comments as there are differences
# between Adobe and Lucee. Uncomment your rdbms of choice, the options are:
# - MySQL 5.7
# - MySQL 5.8
# - PostgreSQL
# - Microsoft SQL
# - Custom Database
#################################################################

######################################################
# MySQL 5.7 DB Driver
######################################################
DB_DRIVER=MySQL
# Lucee Class
DB_CLASS=com.mysql.jdbc.Driver
# Adobe Class
#DB_CLASS=com.mysql.cj.jdbc.Driver
# Lucee Bundle Info: 5.1.40 IS THE ONLY ONE THAT WORKS FOR HIBERNATE + MySQL 5.7
DB_BUNDLEVERSION=5.1.40
DB_BUNDLENAME=com.mysql.jdbc
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
#DB_PORT=4306
#DB_CONNECTIONSTRING=jdbc:mysql://127.0.0.1:4306/contentbox?allowPublicKeyRetrieval=true&useSSL=false&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC&useLegacyDatetimeCode=true
## DB Credentials
#DB_DATABASE=contentbox
#DB_USER=root
#DB_PASSWORD=contentbox

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
#DB_DRIVER=mssql
#DB_CLASS=com.microsoft.sqlserver.jdbc.SQLServerDriver
#DB_BUNDLEVERSION=7.2.2.jre8
#DB_BUNDLENAME=org.lucee.mssql
## DB Location
#DB_HOST=127.0.0.1
#DB_PORT=1433
#DB_CONNECTIONSTRING=jdbc:sqlserver://localhost:1433;DATABASENAME=contentbox;sendStringParametersAsUnicode=true;SelectMethod=direct
## DB Credentials
#DB_DATABASE=contentbox
#DB_USER=sa
#DB_PASSWORD=ContentB0x!

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

If you are running CommandBox as your server of choice, then you can update your `.cfconfig.json` in the root of your application to the following:

{% code title=".cfconfig.json" %}
```javascript
{
	"systemErr":"System",
	"systemOut":"System",
	"thistimezone":"UTC",
	"whitespaceManagement":"white-space-pref",
	"postParametersLimit" : 200,
	"cacheDefaultObject":"contentbox",
        "caches":{
          "contentbox":{
            "storage":"true",
            "type":"RAM",
            "custom":{
                "timeToIdleSeconds":"1800",
                "timeToLiveSeconds":"3600"
            },
            "class":"lucee.runtime.cache.ram.RamCache",
            "readOnly":"false"
		}
        },
	"datasources" : {
		"contentbox":{
            "allowAlter":true,
            "allowCreate":true,
            "allowDelete":true,
            "allowDrop":true,
            "allowGrant":true,
            "allowInsert":true,
            "allowRevoke":true,
            "allowSelect":true,
            "allowUpdate":true,
            "blob":"true",
			      "bundleName": "${DB_BUNDLENAME}",
			      "bundleVersion": "${DB_BUNDLEVERSION}",
            "class":"${DB_CLASS}",
            "clob":"true",
            "connectionLimit":"100",
            "connectionTimeout":"1",
            "custom":"useUnicode=true&characterEncoding=UTF8&serverTimezone=UTC&useLegacyDatetimeCode=true&autoReconnect=true&useSSL=false&allowPublicKeyRetrieval=true",
            "database":"${DB_DATABASE:contentbox}",
            "dbdriver":"${DB_DRIVER}",
            "host":"${DB_HOST:127.0.0.1}",
            "metaCacheTimeout":"60000",
            "password":"${DB_PASSWORD}",
            "port":"${DB_PORT:3306}",
            "storage":"false",
            "username":"${DB_USER}",
			"validate":"false"
		}
	}
}
```
{% endcode %}

Once your environment file is seeded open the `box.json` of the ContentBox 4 and add the following configuration.&#x20;

{% hint style="danger" %}
Most likely you will already have a `scripts` key in the `box.json` so just add the listed scripts below:
{% endhint %}

```javascript
...

"scripts" : {
   "contentbox:migrate":"migrate up migrationsDirectory=modules/contentbox/migrations",
   "contentbox:migrate:up":"run-script contentbox:migrate",
   "contentbox:migrate:down":"migrate down migrationsDirectory=modules/contentbox/migrations"
},

"cfmigrations":{
    "schema":"${DB_DATABASE}",
    "connectionInfo":{
        "bundleName":"${DB_BUNDLENAME}",
        "bundleVersion":"${DB_BUNDLEVERSION}",
        "class":"${DB_CLASS}",
        "connectionString":"${DB_CONNECTIONSTRING}",
        "password":"${DB_PASSWORD}",
        "username":"${DB_USER}"
    },
    "defaultGrammar":"AutoDiscover@qb"
}

...
```

{% hint style="danger" %}
PLEASE MAKE SURE TO SAVE THE FILE!
{% endhint %}

This will tell CommandBox migrations how to connect to your database in preparation for upgrades.  Please note that the `contentbox:migrate` scripts are to execute migrations for ContentBox. You can have app migrations as well, following the normal [migrations approach](https://forgebox.io/view/commandbox-migrations).

Once this is done we can reload the CommandBox shell with the command `reload` and it's time to make sure migrations can connect to your database with the variables and connection information:

```bash
# Run the migration table installation
$ migrate install
 Migration table installed!
```

If this command succeeds, then we are ready to go to the next step.  If it fails, then check your credentials, connection information and that you can actually connect to the database. If not, ask away in our community forum: [https://community.ortussolutions.com/c/communities/contentbox/15](https://community.ortussolutions.com/c/communities/contentbox/15)

## 2. Backups

Please make sure you backup your source code and your database. We are not liable for broken installations.

{% hint style="danger" %}
Make sure the database, the tables and columns are using `utf8mb4` if you are using MySQLx
{% endhint %}

## 3. Run the Updater

We have prepared a CommandBox task that will upgrade your installation in one easy execution.

### \*nix/Mac

If you are in a Linux or Mac environment you can execute the task using the following shell commands from the root directory of your application.

```bash
# Download the updater
curl -o Updater.cfc https://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/5.0.0/Updater.cfc
# Execute the task
box task run Updater.cfc
# Clean it up
rm Updater.cfc
```

### Windows

If you are in windows, download the following task:

[http://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/5.0.0/Updater.cfc](http://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/5.0.0/Updater.cfc)

and place it in the root of your project. Then issue the following CommandBox shell command to execute it.

```bash
# Run the task
box task run Updater.cfc
# Clean it up
rm Updater.cfc
```

## 4. Final Steps

The updater will update your installation and run the migration scripts. However, it will also override the following files:

```
.cfconfig.json
server.json
Application.cfc
robots.txt
readme.md
config/CacheBox.cfc
config/Coldbox.cfc
```

It will create `.bak` files for the originals so you can manually merge in any changes you had before.  Once you do, go ahead and startup the engines! You are upgraded!



