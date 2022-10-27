# Adding Admin Menus to your Module

To add Menu Items for your Admin Modules into the Admin Interface, you need to update the `onLoad` and `onUnload` functions of your `ModuleConfig.cfc` file.

In this example, you'll start by adding the Menu Item by updating `onLoad`:

```text
* Fired when the module is registered and activated.
*/
function onLoad(){
    // Let's add ourselves to the main menu in the Modules section
    var menuService = controller.getWireBox().getInstance( "AdminMenuService@contentbox" );
    // Add Menu Contribution
    menuService.addSubMenu(topMenu=menuService.MODULES,name="mySecrets",label="my Secrets",href="#menuService.buildModuleLink('mySecrets','home')#" );
}
```

Next, you'll update the `onUnload` function to remove the Menu Item when deactivating our Admin Module:

```text
* Fired when the module is unregistered and unloaded
*/
function onUnload(){
    // Let's remove ourselves to the main menu in the Modules section
    var menuService = controller.getWireBox().getInstance( "AdminMenuService@contentbox" );
    // Remove Menu Contribution
    menuService.removeSubMenu(topMenu=menuService.MODULES,name="mySecrets" );
}
```

Now reload the app \(`?fwreinit=1`\). If you activate the `mySecrets` Admin Module, you should see `mySecrets` appear in the `Modules` sub menu items.

Now that your module menu button is working in the admin, you need to add some metadata to your module.

