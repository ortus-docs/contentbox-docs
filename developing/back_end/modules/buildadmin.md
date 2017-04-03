# Build an Admin Module

ContentBox makes it easy to create your own Admin Modules, add Menu Items into the Admin Interface, use ContentBox Admin Users and Permissions instead of building your own security by extending ContentBox.

At it's core, ContentBox is an Application running on top of ColdBox as a framework, but with all of the great features ContentBox has, ORM, Pages, Blog Posts, Categories, Comments, Subscriptions, Admin User Interface, Permissions, Modules, and much more, you can treat ContentBox like an Application Framework, and just extend it, with Modules. With almost every real Application, you will need to add front end modules, and then admin modules.

When you are building admin modules, you need to build / install those modules into the `modules/contentbox/modules_user` folder or `modules/contentbox/modules` folder. Read Module Conventions to know when to use what folder... depending if the module will be custom, vs a shared forgebox module, you should put them in different locations.

One big benefits with ContentBox, is how easy it is to use the base admin, and extend it to make it your own admin. Why build a normal website the hard way, when ContentBox already has all the login, password reset, security roles and permissions build for you. Can you simply use the admin, and add more buttons for your admin modules. 

This page walks through building a simple module in the ContentBox admin. We're going to make a custom module, that will only live with this application, and will not be shared with forgebox, so we want this to be included in our source code. So we will build this module in this folder:

`/modules/contentbox/modules_user/`

The full path of our module, which will be called mySecrets would be

`/modules/contentbox/modules_user/mySecrets`

Now, if we go to the Module Manager in the backend, and rescan for modules, you will see it doesn't show up yet.

![ContentBox Module Rescan 1](modulesRescan1.jpg)

First, we need to create a module config. This is similar to a normal ColdBox module, with a few extra splashes of flavor for ContentBox. 
Since it is a CFC, we can use the pseudo contructor to set the module properties. For mySecrets, it looks something like this.

```
// Module Properties
this.title                       = "MySecrets";
this.author                = "Ortus Solutions, Corp";
this.webURL                = "http://www.ortussolutions.com";
this.description           = "This is a secrets module";
this.version               = "1.0";
 
// If true, looks for views in the parent first, if not found, then in the module. Else vice-versa
this.viewParentLookup      = true;
 
// If true, looks for layouts in the parent first, if not found, then in module. Else vice-versa
this.layoutParentLookup = true;
 
// Module Entry Point
this.entryPoint                  = "mysecrets";
```

The only required function for the ModuleConfig.cfc is the configure() function. This is where you can set ( or inherit ) settings, parent settings, layout settings, datasources, webservices, routes, interceptorSettings, custom Interceptors and Interception Points, model bindings ( mappings ). A shell of your configure method might look like this.
```
function configure(){
      // parent settings
      parentSettings = {
      };
      // module settings - stored in modules.name.settings
      settings = {
      };
      // Layout Settings
      layoutSettings = {
             defaultLayout = ""
      };
      // datasources
      datasources = {
      };
      // web services
      webservices = {
      };
      // SES Routes
      routes = [
             // Module Entry Point
             {pattern="/", handler="home",action="index"},
             // Convention Route
             {pattern="/:handler/:action?"}
      ];
      // Custom Declared Points
      interceptorSettings = {
             customInterceptionPoints = ""
      };
      // Custom Declared Interceptors
      interceptors = [
      ];
      // Binder Mappings
      // binder.map( "Alias" ).to( "#moduleMapping#.model.MyService" );
}
```

This is the minimum you need for the module to show up in the Manage Modules screen. If we rescan now, you'll see it detects our Module.

![ContentBox Module Rescan 2](modulesRescan2.jpg)

When you click the Thumb Up icon to activate, it activates the module.

![ContentBox Module Activated](modulesActivated.jpg)

Since these modules are inside of ContentBox, Contentbox manages loading and unloading the module, as well as activating and deactivating the modules, so you need those functions to listen for those events. ModuleConfig.cfc is one big interceptor, so you can catch all sorts of interception points, but these are the four needed for a ContentBox Module to function to its fullest.

```	
/**
* Fired when the module is registered and activated.
*/
function onLoad(){
}
 
/**
* Fired when the module is activated by ContentBox
*/
function onActivate(){
}
 
/**
* Fired when the module is unregistered and unloaded
*/
function onUnload(){
}
 
/**
* Fired when the module is deactivated by ContentBox
*/
function onDeactivate(){
}
```

This is a bare bones template for a module controlled by ContentBox, but right now it doesn't really do anything... in fact if you tried to hit the module, the default route for / would look for home hander with index action/view but we haven't created those yet. None of the functions above do anything, so all the activation and deactivation does, is make the module available or not. If you try and access /mysecrets ( the entry point ) with the module deactivated you see this

![ContentBox Module Deactivated](modulesEntryPointDeactivated.jpg)

When the module is activated, and you hit the entry point, you will get the error that the event is not a valid registered event

![ContentBox Module Entry Point Activated](modulesEntryPointActivated.jpg)

Here is the gist of step 1.
ModuleConfig.CFC for Step 1 - https://gist.github.com/gpickin/545242a3da6c2805efb4e6cac82ce1ad

As you can see, we have our own routes setup for the module in the ModuleConfig.cfc. The default action is handler=home and action=index. We'll need to create this event, or update our module route to point to the new one. Let's keep it simple, and we'll make a home.index event.

### First step - we need to make a views folder for all of our views.

ColdBox and therefore ContentBox calls the views folder 'views'. Since our action is home.index, we need a folder inside of 'views' called home, and an index.cfm file inside of that.

```
- mySecrets
--- views
------ home
--------- index.cfm
--- ModuleConfig.cfc
```

### Next Step - Add some code to our view Index.cfm

Inside the index.cfm, just put some simple html, like &lt;h1&gt;my Secrets&lt;/h1&gt;

### Next Step - Reload our Application and Test the Entrypoint

Lets reload our application with `/?fwreinit=1` or Reload Application from the admin cog dropdown menu.
Now lets try hitting out entrypoint `/mysecrets` and you'll see something like this.

![ContentBox View 1](view1.jpg)

Wait, why did that work? ColdBox uses conventions to find the view, even without the handler. For legacy conversion or simple views, you don't even need the handler. 
Wait, I wasn't logged into the admin, how did that not ask me to login?

If you look at the url, i was using `/mysecrets` which is actually the front end url... so that worked.

What is the admin entrypoint for this module?: `/cbadmin/modules/mysecrets/`
Now what happens when we hit that url

![ContentBox View Login](viewLogin.jpg)

It bounces me to the login page, like it should. Ok, so when I login, then what happens?

![ContentBox View Handler](viewHandlerError.JPG)

In the admin, its throwing an error, telling me the handler doesn't exist. Strange that it worked in the front end right? The admin has a little more security, so it requires a handler. One of the pitfalls of not using handlers is that the ColdBox Lifecycle special actions like pre and post handlers etc cannot run, because it bypasses a lot of the lifecycle and just spits out the view. Keep that in mind when you are having issues with anything out of the ordinary and you don't have a handler, or have a handler without a handler event for the event you're executing.

### Lets add a handler

We need to follow conventions ( unless you want to complicate things and override the conventions ) and make a folder called 'handlers' for our handler. We can just add the Home.cfc directly into the 'handlers' folder, and now your folder tree structure will look like this

![ContentBox Handler Folder Tree](handlerFolderTree.jpg)

We'll keep our handler very simple, just a shell, so we'll add this to our Home.cfc

```
component{
        function index( event, rc, prc ){
             event.setView( "home/index" );
       }
}
```

Now we have added the handler, lets reinit the application and see what it looks like now.

Another note: If you hit http://127.0.0.1:61805/cbadmin/module/mysecrets/ you will get a strange handler error... because it thinks the module isn't a module, but its an action of a parent module... so make sure you use the full url, like below.

`http://127.0.0.1:61805/cbadmin/module/mysecrets/home/index`

Now, you will see the following

![ContentBox Admin Handler View](handlerAdminView.jpg)

Now our module is working, in the admin, we need to add some menu buttons so users can access your module.
