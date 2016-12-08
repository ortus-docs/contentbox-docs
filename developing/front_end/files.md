# File Structure

ContentBox itself is a ColdBox application, with 3 special modules that do all of the hard work. Below you will see the shell of the ColdBox app, with the key folders expanded and bolded.

Although ContentBox has a large number of folders and files, most customization activities will be done in a few key locations. This should make navigating the ContentBox source files easier.

We recommend using modules for extending ContentBox. Modules are easy to install, and can be managed through the ContentBox admin, activating and deactivating as needed. Modules can contain widgets, interceptors, admin or front end menu items, including handlers and views. 

Themes are self contained folders, within ContentBox's themes folder. Themes themselves are module like, with a few added features, which means you can include modules in your themes for truly deep and powerful themes.

Traditional ColdBox Modules can be installed outside of ContentBox's control and life-cycle with ColdBox's normal conventions.

<i class="fa fa-folder-open"></i> Initial ContentBox Website Install
 
 - <i class="fa fa-folder"></i> coldbox ( The ColdBox core, including system and ColdBox dependencies )
 - <i class="fa fa-folder"></i> config ( The ColdBox app config folder )
 - <i class="fa fa-folder"></i> handlers ( The ColdBox app handlers folder )
 - <i class="fa fa-folder"></i> layouts ( The ColdBox app layouts folder )
 - <i class="fa fa-folder"></i> models ( The ColdBox app layouts folder )
 - <i class="fa fa-folder-open"></i> **modules** ( The ColdBox app layouts folder )
   - <i class="fa fa-folder-open"></i> **contentbox**
     - <i class="fa fa-folder"></i> content ( default location for the media manager - customizable through Admin settings )
     - <i class="fa fa-folder"></i> email_templates ( Email templates for adding authors, comments, pages, blog posts and many more )
     - <i class="fa fa-folder"></i> i18n ( i18N properties files for DE, US, SV, IT, BR currently )
     - <i class="fa fa-folder"></i> models ( Core ContentBox Models and Services )
     - <i class="fa fa-folder"></i> modules ( Modules here are always loaded no matter what. These are core sub-modules of the ContentBox core module )
     - <i class="fa fa-folder-open"></i> **modules_user** ( ContentBox life-cycle controlled modules. Manually installed or downloaded from Forgebox. These Modules can be activated and deactivated through the admin )
       - <i class="fa fa-folder-open"></i> **Hello** ( Hello World Sample Module )
     - <i class="fa fa-folder-open"></i> **themes** ( ContentBox Themes, manually installed or downloaded from Forgebox )
       - <i class="fa fa-folder-open"></i> **default** ( Default ContentBox Theme )
     - <i class="fa fa-folder-open"></i> tmp
     - <i class="fa fa-folder-open"></i> updates ( Location for downloaded and manually installed patches )
     - <i class="fa fa-folder-open"></i> **widgets** ( Default ContentBox Widgets - Override-able )
     - <i class="fa fa-file"> </i> Application.cfc
     - <i class="fa fa-file"> </i> ModuleConfig.cfc
   - <i class="fa fa-folder-open"></i> **contentbox-admin** ( ContentBox Admin - removable for security reasons )
   - <i class="fa fa-folder-open"></i> **contentbox-ui** ( Contentbox UI Module )
 - <i class="fa fa-folder-open"></i> **modules_app** ( Home for all of your custom ColdBox modules, outside of ContentBox's lifecycle )
 - <i class="fa fa-folder"></i> views ( The ColdBox app layouts folder )
 - <i class="fa fa-file"></i> .htaccess
 - <i class="fa fa-file"> </i> Application.cfc ( The main ColdBox Application.cfc )
 - <i class="fa fa-file"></i> box.json
 - <i class="fa fa-file"></i> favicon.ico
 - <i class="fa fa-file"></i> index.cfm
 - <i class="fa fa-file"></i> license.txt
 - <i class="fa fa-file"></i> readme.md
 - <i class="fa fa-file"></i> robots.txt
 - <i class="fa fa-file"></i> server.json
