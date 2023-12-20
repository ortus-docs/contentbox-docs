---
description: Deploy ContentBox on an existing ColdBox application.
---

# Existing ColdBox Application

If you already have a ColdBox application and wish to install ContentBox, you most definitely can.

## System Requirements

Please note that ContentBox requires ColdBox 7.x

## Step 1: Dependencies

Since version 3.5.0, you can now issue a command in CommandBox to install the ContentBox module into an existing ColdBox application. Just open a `box` shell in the root of your ColdBox application and use the following command:

```
install contentbox,contentbox-installer-module
```

This will install the ContentBox module with all of its dependencies under the `/modules/contentbox` and the ContentBox installer module under `/modules/contentbox-installer`.&#x20;

### Lucee ORM Extension

If you are using Lucee, then you need to use the Ortus ORM Extension [https://orm-extension.ortusbooks.com/getting-started/installation](https://orm-extension.ortusbooks.com/getting-started/installation)

```
box install D062D72F-F8A2-46F0-8CBC91325B2F067B@6.4.0
```

{% embed url="https://forgebox.io/view/D062D72F-F8A2-46F0-8CBC91325B2F067B" %}

## Step 2: `Application.cfc` Updates

Now open your `Application.cfc` and you will add the following updates:

### Mappings

```javascript
// UTC timezone
this.timezone          = "UTC";


// LOCATION MAPPINGS
this.mappings[ "/contentbox" ] = COLDBOX_APP_ROOT_PATH & "modules/contentbox";
// THE LOCATION OF THE ORM MODULE
this.mappings[ "/cborm" ] = this.mappings[ "/contentbox" ] & "/modules/contentbox-deps/modules/cborm";
```

### ORM Settings

```javascript
/**
 * --------------------------------------------------------------------------
 * ORM + Datasource Settings
 * --------------------------------------------------------------------------
 * - Please update the cfcLocation as needed to locate more ORM entities for your app
 * - Dialect is incredibly important! Do not let Hibernate auto configur it, you can get nasty errors.
 * So Make sure you select one.
 */
request.cbSystemHelper = new coldbox.system.core.delegates.Env();
// THE CONTENTBOX DATASOURCE NAME
this.datasource        = "contentbox";
// ORM SETTINGS
this.ormEnabled        = true;
// cfformat-ignore-start
this.ormSettings       = {
	// ENTITY LOCATIONS, ADD MORE LOCATIONS AS YOU SEE FIT
	cfclocation           : [
		// If you create your own app entities
		"models",
		// The ContentBox Core Entities
		"modules/contentbox/models",
		// Custom Module Entities
		"modules_app",
		// Custom Module User Entities
		"modules/contentbox/modules_user"
	],
	// THE DIALECT OF YOUR DATABASE OR LET HIBERNATE FIGURE IT OUT, UP TO YOU TO CONFIGURE.
	dialect              : request.cbSystemHelper.getSystemSetting( "ORM_DIALECT", "" ),
	dbcreate             : "none",
	secondarycacheenabled: request.cbSystemHelper.getSystemSetting( "ORM_SECONDARY_CACHE", false ),
	cacheprovider        : request.cbSystemHelper.getSystemSetting( "ORM_SECONDARY_CACHE", "ehCache" ),
	logSQL               : request.cbSystemHelper.getSystemSetting( "ORM_LOGSQL", false ),
	sqlScript            : request.cbSystemHelper.getSystemSetting( "ORM_SQL_SCRIPT", "" ),
	// ORM SESSION MANAGEMENT SETTINGS, DO NOT CHANGE
	flushAtRequestEnd    : false,
	autoManageSession    : false,
	// ORM EVENTS MUST BE TURNED ON FOR CONTENTBOX TO WORK DO NOT CHANGE
	eventHandling        : true,
	eventHandler         : "cborm.models.EventHandler",
	// THIS IS ADDED SO OTHER CFML ENGINES CAN WORK WITH CONTENTBOX
	skipCFCWithError     : true,
	// TURN ON FOR Debugging if ORM mappings are not working.
	savemapping          : false
};
// cfformat-ignore-end
```

## Step 3: `.env` Settings

Below are the env settings for ContentBox to run, spice up as needed

```bash
#################################################################
# App Name and Environment
#################################################################
APPNAME=ContentBox Dev
# This can be development, staging, production or custom.
ENVIRONMENT=development
# The password for the CFML Engine Administrator
CFCONFIG_ADMINPASSWORD=contentbox
# The ColdBox Reinit password
COLDBOX_REINITPASSWORD=contentbox
# How long do admin sessions last (In Minutes)
COLDBOX_SESSION_TIMEOUT=60
# Development CBDebugger
CBDEBUGGER_ENABLED=true

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
ORM_LOGSQL=false
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
# Database Datasource Connection
######################################################
DB_DRIVER=MySQL
DB_CLASS=com.mysql.cj.jdbc.Driver
DB_BUNDLEVERSION=8.0.24
DB_BUNDLENAME=com.mysql.cj
# DB Location
DB_HOST=localhost
DB_PORT=3306
DB_CONNECTIONSTRING=jdbc:mysql://localhost:3306/contentbox?allowPublicKeyRetrieval=true&useSSL=false&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC&useLegacyDatetimeCode=true
# DB Credentials
DB_DATABASE=contentbox
DB_USER=root
DB_PASSWORD=ortussolutions


#################################################################
# JWT Information
# --------------------------------
# You can seed the JWT secret below or you can also leave it empty
# and ContentBox will auto-generate one for you that rotates
# everytime the application restarts or expires
#################################################################
JWT_SECRET=YQSUGww+IQQUhOfZxVhFnDMNtN0fV1uH8hEvMTt+Nao=

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

## Step 4: Module Settings

Here is the collection of the latest module settings for ContentBox. Make sure you copy/merge the settings found here: [https://github.com/Ortus-Solutions/ContentBox/tree/development/config/modules](https://github.com/Ortus-Solutions/ContentBox/tree/development/config/modules)

## Step 5: `CacheBox.cfc` Settings

Open your CacheBox configuration file: config/CacheBox.cfc and add the following cache declarations:

```javascript
// Register all the custom named caches you like here
caches = {
    // Named cache for all coldbox event and view template caching
    template = {
        provider = "coldbox.system.cache.providers.CacheBoxColdBoxProvider",
        properties = {
            objectDefaultTimeout = 120,
            objectDefaultLastAccessTimeout = 30,
            useLastAccessTimeouts = true,
            freeMemoryPercentageThreshold = 0,
            reapFrequency = 2,
            evictionPolicy = "LRU",
            evictCount = 5,
            maxObjects = 5000,
            objectStore = "ConcurrentSoftReferenceStore" //memory sensitive
        }
    },
    // ContentBox Sessions
    sessions = 	{
        provider = "coldbox.system.cache.providers.CacheBoxColdBoxProvider",
        properties = {
            objectDefaultTimeout = 60,
            objectDefaultLastAccessTimeout = 0,
            useLastAccessTimeouts = false,
            freeMemoryPercentageThreshold = 0,
            reapFrequency = 2,
            evictionPolicy = "LRU",
            evictCount = 5,
            maxObjects = 1000, // Can support up to 1000 user sessions concurrently.  Modify if needed. 0 = unlimited
            objectStore = "ConcurrentStore"
        }
    }
}
```

Once these updates are done, then you can start up the server and visit the installer URL: `http://localhost:port/cbInstaller`

## Step 6 (Optional) : UI Route

By default ContentBox is in **take over** mode. Meaning that the UI module will intercept all calls made to the application and process them as pages or blog entries. If you DO NOT want this to happen, then you can segregate the UI module into a single entry point URL like `blog` or `site` or `pages`. You can do this by opening the following file: `modules/contentbox-ui/ModuleConfig.cfc` and looking for the following code:

```
// YOUR SES URL ENTRY POINT FOR CONTENTBOX, IF EMPTY IT WILL TAKE OVER THE ENTIRE APPLICATION
// IF YOU WANT TO SECTION OFF CONTENTBOX THEN FILL OUT AN SES ENTRY POINT LIKE /site OR /content
// BY DEFAULT IT TAKES OVER THE ENTIRE APPLICATION
this.entryPoint    = "";
```

Now update the `this.entryPoint` to whatever you like the entry point URL to be. Restart the application and voila!
