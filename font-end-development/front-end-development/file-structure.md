# File Structure

ContentBox itself is a ColdBox application, with 3 special modules that do all of the hard work. Below you will see the shell of the ColdBox app, with the key folders expanded and bolded.

Although ContentBox has a large number of folders and files, most customization activities will be done in a few key locations. This should make navigating the ContentBox source files easier.

We recommend using modules for extending ContentBox. Modules are easy to install, and can be managed through the ContentBox admin, activating and deactivating as needed. Modules can contain widgets, interceptors, admin or front end menu items, including handlers and views.

Themes are self contained folders, within ContentBox's themes folder. Themes themselves are module like, with a few added features, which means you can include modules in your themes for truly deep and powerful themes.

Traditional ColdBox Modules can be installed outside of ContentBox's control and life-cycle with ColdBox's normal conventions.

&#x20;Initial ContentBox Website Install

* &#x20;coldbox ( The ColdBox core, including system and ColdBox dependencies )
* &#x20;config ( The ColdBox app config folder )
* &#x20;handlers ( The ColdBox app handlers folder )
* &#x20;layouts ( The ColdBox app layouts folder )
* &#x20;models ( The ColdBox app layouts folder )
* &#x20;**modules** ( The ColdBox app layouts folder )
  * &#x20;**contentbox**
    * &#x20;content ( default location for the media manager - customizable through Admin settings )
    * &#x20;email\_templates ( Email templates for adding authors, comments, pages, blog posts and many more )
    * &#x20;i18n ( i18N properties files for DE, US, SV, IT, BR currently )
    * &#x20;models ( Core ContentBox Models and Services )
    * &#x20;modules ( Modules here are always loaded no matter what. These are core sub-modules of the ContentBox core module )
    * &#x20;**modules\_user** ( ContentBox life-cycle controlled modules. Manually installed or downloaded from Forgebox. These Modules can be activated and deactivated through the admin )
      * &#x20;**Hello** ( Hello World Sample Module )
    * &#x20;**themes** ( ContentBox Themes, manually installed or downloaded from Forgebox )
      * &#x20;**default** ( Default ContentBox Theme )
    * &#x20;tmp
    * &#x20;updates ( Location for downloaded and manually installed patches )
    * &#x20;**widgets** ( Default ContentBox Widgets - Override-able )
    * &#x20;Application.cfc
    * &#x20;ModuleConfig.cfc
  * &#x20;**contentbox-admin** ( ContentBox Admin - removable for security reasons )
  * &#x20;**contentbox-ui** ( Contentbox UI Module )
* &#x20;**modules\_app** ( Home for all of your custom ColdBox modules, outside of ContentBox's lifecycle )
* &#x20;views ( The ColdBox app layouts folder )
* &#x20;.htaccess
* &#x20;Application.cfc ( The main ColdBox Application.cfc )
* &#x20;box.json
* &#x20;favicon.ico
* &#x20;index.cfm
* &#x20;license.txt
* &#x20;readme.md
* &#x20;robots.txt
* &#x20;server.json
