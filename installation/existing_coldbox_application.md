# Existing ColdBox Application

If you already have a ColdBox application and you wish to install ContentBox into it, you most definitely can.  There are a few more steps involved than our simple `box install contentbox` procedure as we will be integrating into an existing application.

## System Requirements
Please note that ContentBox 3 requires ColdBox 4.2+.

## Step 1 : Dependencies
Before we go and install the ContentBox modules we must make sure our  application has the right dependencies for ContentBox to work.  Please make sure you download and install [CommandBox](https://www.ortussolutions.com/products/commandbox) as we will use it for dependency management.  Open a CommandBox shell in the root of your ColdBox application by typing `box` or opening the `box` binary in that directory.  Once in the shell you will install the following dependencies:

* cborm
* cbjavaloader
* cbmailservices
* cbsecurity
* cbstorages
* cbfeeds
* cbmessagebox
* cbantisamy
* bcrypt
* cbmarkdown

You can either do a `install {list here}` and list out all the dependencies or just copy paste the following snippet below and add it to your `dependencies` structure of your `box.json` file and then type `install`

```js
"cborm":"1.2.1+00004",
"cbjavaloader":"1.1.0+00002",
"cbmailservices":"1.2.0+00028",
"cbsecurity":"1.3.0+00003",
"cbstorages":"1.1.0+00002",
"cbfeeds":"1.0.1",
"cbmessagebox":"2.1.0+00027",
"cbantisamy":"1.3.0+00033",
"bcrypt":"https://github.com/coldbox-modules/cbox-bcrypt/archive/v2.1.0.zip",
"cbmarkdown":"2.0.0+00007"
```

> **Hint** You can find the latest dependency listing inside of the ConntentBox download in the root as `box.json`

## Step 2 : Copy over ContentBox Modules
Now that the dependencies are installed, copy over all of the ContentBox modules from our regular download:

* contentbox
* contentbox-admin
* contentbox-installer
* contentbox-ui


## Step 3 : `Application.cfc` Updates
Now open your `Application.cfc` and you will add the following updates:

### Mappings
```js
// LOCATION MAPPINGS
this.mappings[ "/contentbox" ] 	= COLDBOX_APP_ROOT_PATH & "modules/contentbox";
// THE LOCATION OF THE ORM MODULE
this.mappings[ "/cborm" ] = COLDBOX_APP_ROOT_PATH & "/modules/cborm";
```

### ORM Settings

```js
// ORM SETTINGS
this.ormEnabled = true;
this.ormSettings = {
    // ENTITY LOCATIONS, ADD MORE LOCATIONS AS YOU SEE FIT
    cfclocation=[ "models", "modules" ],
    // DO NOT REMOVE THE FOLLOWING LINE OR AUTO-UPDATES MIGHT FAIL.
    dbcreate = "update",
    // FILL OUT: IF YOU WANT CHANGE SECONDARY CACHE, PLEASE UPDATE HERE
    secondarycacheenabled = false,
    cacheprovider		= "ehCache",
    // ORM SESSION MANAGEMENT SETTINGS, DO NOT CHANGE
    logSQL 				= false,
    flushAtRequestEnd 	= false,
    autoManageSession	= false,
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
// Configure the admin messagebox
messagebox = {
    styleOverride 	= true,
    template 		= "/contentbox/models/ui/templates/messagebox.cfm"
};

// ORM Module Configuration
orm = {
    // Enable Injection
    injection = {
        enabled = true
    }
};
```

That's it!  Once all those settings, mappings and module installations are done you can now visit the installer module to continue with the installation process: `http://localhost/index.cfm/cbinstaller`

> **Danger** Make sure you have the datasource created in your ColdFusion administrator.


