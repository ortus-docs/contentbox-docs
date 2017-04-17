# Existing ColdBox Application

If you already have a ColdBox application and you wish to install ContentBox into it, you most definitely can. 

## System Requirements
Please note that ContentBox requires ColdBox 4.3+.

## Step 1 : Dependencies

Since version 3.5.0, you can now simply issue a command in CommandBox to install the ContentBox module into an existing ColdBox application.  Just open a `box` shell in the root of your ColdBox application and use the following command:

```
install contentbox production=true
```

This will install the ContentBox module with all of its dependencies under the `/modules/contentbox` folder and update your `box.json` with the appropriate dependency.  That's it, next step!


## Step 2 : Copy Over Installer (Optional)
If you need to execute the ContentBox installer for the first time, you will have to download the installer package from our [download page](https://www.ortussolutions.com/products/contentbox#downloads).  Extract the zip and copy over the `modules/contentbox-installer` folder into your `modules` folder.

> **Note** We will create another installer approach in the future for this portion.


## Step 3 : `Application.cfc` Updates
Now open your `Application.cfc` and you will add the following updates:

### Mappings
```js
// LOCATION MAPPINGS
this.mappings[ "/contentbox" ] = COLDBOX_APP_ROOT_PATH & "modules/contentbox";
// THE LOCATION OF THE ORM MODULE
this.mappings[ "/cborm" ] = this.mappings[ "/contentbox" ] & "/modules/contentbox-deps/modules/cborm";
```

### ORM Settings

```js
// ORM SETTINGS
this.ormEnabled = true;
this.ormSettings = {
    // ENTITY LOCATIONS, ADD MORE LOCATIONS AS YOU SEE FIT
    cfclocation=[ "models", "modules", "modules_app" ],
    // DO NOT REMOVE THE FOLLOWING LINE OR AUTO-UPDATES MIGHT FAIL.
    dbcreate = "update",
    // FILL OUT: IF YOU WANT CHANGE SECONDARY CACHE, PLEASE UPDATE HERE
    secondarycacheenabled      = false,
    cacheprovider		= "ehCache",
    // ORM SESSION MANAGEMENT SETTINGS, DO NOT CHANGE
    logSQL 			= false,
    flushAtRequestEnd 	        = false,
    autoManageSession	        = false,
    // ORM EVENTS MUST BE TURNED ON FOR CONTENTBOX TO WORK
    eventHandling 		= true,
    eventHandler		= "cborm.models.EventHandler",
    // THIS IS ADDED SO OTHER CFML ENGINES CAN WORK WITH CONTENTBOX
    skipCFCWithError	= true
};
```

### Step 4 : `ColdBox.cfc` Settings

We now move to the last step, open your application's `ColdBox.cfc` and you will add the following settings:

```js
// ORM Module Configuration
orm = {
    // Enable Injection
    injection = {
        enabled = true
    }
};
```

That's it!  Once all those settings, mappings and module installations are done you can now visit the installer module to continue with the installation process: `http://localhost/index.cfm/cbinstaller`

> **Danger** Make sure you have the datasource created in your ColdFusion administrator or inline in your `Application.cfc`


### Step 5 (Optional) : UI Route
By default ContentBox is in **take over** mode. Meaning that the UI module will intercept all calls made to the application and process them as pages or blog entries.  If you DO NOT want this to happen, then you can segregate the UI module into a single entry point URL like `blog` or `site` or `pages`.  You can do this by opening the following file: `modules/contentbox-ui/ModuleConfig.cfc` and looking for the following code:

```
// YOUR SES URL ENTRY POINT FOR CONTENTBOX, IF EMPTY IT WILL TAKE OVER THE ENTIRE APPLICATION
// IF YOU WANT TO SECTION OFF CONTENTBOX THEN FILL OUT AN SES ENTRY POINT LIKE /site OR /content
// BY DEFAULT IT TAKES OVER THE ENTIRE APPLICATION
this.entryPoint	= "";
```

Now update the `this.entryPoint` to whatever you like the entry point URL to be.  Restart the application and voila!
