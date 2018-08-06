# Existing ColdBox Application

If you already have a ColdBox application and you wish to install ContentBox into it, you most definitely can.

## System Requirements

Please note that ContentBox 4.x requires ColdBox 5.x

## Step 1 : Dependencies

Since version 3.5.0, you can now simply issue a command in CommandBox to install the ContentBox module into an existing ColdBox application. Just open a `box` shell in the root of your ColdBox application and use the following command:

```text
install contentbox,contentbox-installer-module
```

This will install the ContentBox module with all of its dependencies under the `/modules/contentbox` and the ContentBox installer module under `/modules/contentbox-installer`. 

## Step 2 : `Application.cfc` Updates

Now open your `Application.cfc` and you will add the following updates:

### Mappings

```javascript
// LOCATION MAPPINGS
this.mappings[ "/contentbox" ] = COLDBOX_APP_ROOT_PATH & "modules/contentbox";
// THE LOCATION OF THE ORM MODULE
this.mappings[ "/cborm" ] = this.mappings[ "/contentbox" ] & "/modules/contentbox-deps/modules/cborm";
```

### ORM Settings

```javascript
// ORM SETTINGS
this.ormEnabled = true;
this.ormSettings = {
    // ENTITY LOCATIONS, ADD MORE LOCATIONS AS YOU SEE FIT
    cfclocation=[ "models", "modules", "modules_app" ],
    // DO NOT REMOVE THE FOLLOWING LINE OR AUTO-UPDATES MIGHT FAIL.
    dbcreate = "update",
    // FILL OUT: IF YOU WANT CHANGE SECONDARY CACHE, PLEASE UPDATE HERE
    secondarycacheenabled      = false,
    cacheprovider        = "ehCache",
    // ORM SESSION MANAGEMENT SETTINGS, DO NOT CHANGE
    logSQL             = false,
    flushAtRequestEnd             = false,
    autoManageSession            = false,
    // ORM EVENTS MUST BE TURNED ON FOR CONTENTBOX TO WORK
    eventHandling         = true,
    eventHandler        = "cborm.models.EventHandler",
    // THIS IS ADDED SO OTHER CFML ENGINES CAN WORK WITH CONTENTBOX
    skipCFCWithError    = true
};
```

## Step 3 : `ColdBox.cfc` Settings

Open your application's `ColdBox.cfc` and you will add the following settings:

```javascript
// ORM Module Configuration
orm = {
    // Enable Injection
    injection = {
        enabled = true
    }
};
```

That's it! Once all those settings, mappings and module installations are done you can now visit the installer module to continue with the installation process: `http://localhost/index.cfm/cbinstaller`

{% hint style="danger" %}
**Danger** Make sure you have the datasource created in your ColdFusion administrator or inline in your `Application.cfc`
{% endhint %}

## Step 4: `CacheBox.cfc` Settings

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

## Step 5 \(Optional\) : UI Route

By default ContentBox is in **take over** mode. Meaning that the UI module will intercept all calls made to the application and process them as pages or blog entries. If you DO NOT want this to happen, then you can segregate the UI module into a single entry point URL like `blog` or `site` or `pages`. You can do this by opening the following file: `modules/contentbox-ui/ModuleConfig.cfc` and looking for the following code:

```text
// YOUR SES URL ENTRY POINT FOR CONTENTBOX, IF EMPTY IT WILL TAKE OVER THE ENTIRE APPLICATION
// IF YOU WANT TO SECTION OFF CONTENTBOX THEN FILL OUT AN SES ENTRY POINT LIKE /site OR /content
// BY DEFAULT IT TAKES OVER THE ENTIRE APPLICATION
this.entryPoint    = "";
```

Now update the `this.entryPoint` to whatever you like the entry point URL to be. Restart the application and voila!

