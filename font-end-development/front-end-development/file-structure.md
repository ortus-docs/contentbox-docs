# File Structure

ContentBox itself is a ColdBox application, with 3 special modules that do all of the hard work. Below you will see the shell of the ColdBox app, with the key folders expanded and bolded.

Although ContentBox has a large number of folders and files, most customization activities will be done in a few key locations. This should make navigating the ContentBox source files easier.

We recommend using modules for extending ContentBox. Modules are easy to install, and can be managed through the ContentBox admin, activating and deactivating as needed. Modules can contain widgets, interceptors, admin or front end menu items, including handlers and views.

Themes are self contained folders, within ContentBox's themes folder. Themes themselves are module like, with a few added features, which means you can include modules in your themes for truly deep and powerful themes.

Traditional ColdBox Modules can be installed outside of ContentBox's control and life-cycle with ColdBox's normal conventions.

 Initial ContentBox Website Install

*  coldbox \( The ColdBox core, including system and ColdBox dependencies \)
*  config \( The ColdBox app config folder \)
*  handlers \( The ColdBox app handlers folder \)
*  layouts \( The ColdBox app layouts folder \)
*  models \( The ColdBox app layouts folder \)
*  **modules** \( The ColdBox app layouts folder \)
  *  **contentbox**
    *  content \( default location for the media manager - customizable through Admin settings \)
    *  email\_templates \( Email templates for adding authors, comments, pages, blog posts and many more \)
    *  i18n \( i18N properties files for DE, US, SV, IT, BR currently \)
    *  models \( Core ContentBox Models and Services \)
    *  modules \( Modules here are always loaded no matter what. These are core sub-modules of the ContentBox core module \)
    *  **modules\_user** \( ContentBox life-cycle controlled modules. Manually installed or downloaded from Forgebox. These Modules can be activated and deactivated through the admin \)
      *  **Hello** \( Hello World Sample Module \)
    *  **themes** \( ContentBox Themes, manually installed or downloaded from Forgebox \)
      *  **default** \( Default ContentBox Theme \)
    *  tmp
    *  updates \( Location for downloaded and manually installed patches \)
    *  **widgets** \( Default ContentBox Widgets - Override-able \)
    *  Application.cfc
    *  ModuleConfig.cfc
  *  **contentbox-admin** \( ContentBox Admin - removable for security reasons \)
  *  **contentbox-ui** \( Contentbox UI Module \)
*  **modules\_app** \( Home for all of your custom ColdBox modules, outside of ContentBox's lifecycle \)
*  views \( The ColdBox app layouts folder \)
*  .htaccess
*  Application.cfc \( The main ColdBox Application.cfc \)
*  box.json
*  favicon.ico
*  index.cfm
*  license.txt
*  readme.md
*  robots.txt
*  server.json

