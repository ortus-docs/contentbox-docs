# What's New With 3.0.0

ContentBox 3.0.0 is a major release and with a completely rewritten administration module.  If you are upgrading from a previous release, please make sure you read the [Upgrading Guide](upgrading.md).  You can find the full release notes here: [Release Notes](https://ortussolutions.atlassian.net/secure/ReleaseNote.jspa?projectId=10008&version=12908)

ContentBox 3 is a collection of more than 150 tickets resolved.  It has been a massive undertaking with some great resoluts.  Below we go through the major updates and feature improvements.

## System Architecture Updates

The following are major system architecture updates we have done in ContentBox 3.

### ColdBox 4 
We have updated the entire core to leverage ColdBox 4 and modularity.  We have completely re-architected all modules to adhere to ColdBox 4 standards and rely on CommandBox CLI for package management and resolutions.  This update in itself is worth noting as it not only modularized even more ContentBox, but gave it a source code reduction and performance boosts.


### Oracle + PostgreSQL Support
Oracle and PostgreSQL are now fully supported.


### BCrypt Support
The default algorithm for passwords is now BCrypt with work factors for better security and entropy.


### Password Policy
A new password policy is now in place for ContentBox for new and current users.  


### Core Settings
Introduction of core and user based system settings. This allows for the distinguishing of what are ContentBox core settings and custom user or module settings.


### Settings Cluster Storage
You can now decide in which caching engine to store global ContentBox settings. This provides the way to fully scale ContentBox in any cloud provider.


### SSL Support + 
SSL support can now be found everywhere in ContentBox for both the UI and admin modules.  Users can even select specific pages for users to transition into or out of SSL for richer eCommerce or secure experiences.


### Internationalization
The majority of all modules have been now translated into English, Spanish, Italian, German and French.  There is still work to do to localize the entire source, but it is coming.


### ContentBox Express with JRE
Our entire build process has been revamped and now we can produce ContentBox Express editions with included Java runtimes for Linux, Mac OS X and Windows.


### Automated Asset Pipeline
We have completely re-architected our asset pipeline and ContentBox now comes with an integrated development pipeline for front-end development.  All assets are now tracked via bower and npm.  We have created a developer guide for anybody working with the admin assets and collaborating.


### CommandBox Integration
All development is now done with CommandBox and all dependencies are tracked via CommandBox.  This provides a smoother update processes for users and also a great workflow for collaboration.

### DocBox API Docs
DocBox now generates all API docs with much better documentation and readability.


----

## Admin Updates

Below is a listing of all the major updates in the administration modules.

### Admin UI
The administration module sports a completely re-designed responsive UI.  Our goal was to think mobile first and build from there.  So you will see tons of great additions for working on mobile devices, new editors, new fullscreen mdoes and much much more.


### Markdown Native Support
ContentBox now sports native Markdown support for all content objects.


### New Code Editor
We have included a new code editor that supports HTML and Markdown natively.  This will allow developers or editors to write in native markup and have all the integrations into ContentBox.  It also sports realtime previews and side-by-side editing in full screen.  Your editing experience is about to get a whole lot better now.


### Editor Auto Save
We have introduced local storage auto saving capabilities for all editors in ContentBox.  No matter the implementation, we will provide auto-save capabilities.  This is a great way to know that silently your work is secure.

### Editor Escaping Markup Translations
You can now use the `<escape></escape>` syntax in any content editor to escape ContentBox translations for settings, markdown, etc.


### Editor Responsive Previews
All live previews are now responsive.  Meaning you can choose from the responsive previewer the type of device and get immediate feedback of the content result in real-time.


### Editor UI Updates
The content editors have completely been re-designed for mobile first paradigm.  They sport new tabbed interfaces for history, comments, custom fields and editing.  You also have much more real estate when editing and even full screen editing support. 


### New Dashboard
The dashboard now supports a cleaner interface for visualizing the latest content edits, drafts, comments and news.


### Media Manager Updates
Improved UI to match the new admin UI with responsive updates.  It also has a smoother uploading and drag and drop uploading capabilities.

### Admin Fullscreen Mode
We have added HTML5 fullscreen mode capabilities for the admin UI.  This will allow you to go full screen to edit, create and manage in a gorgeous huge display.


### Configurable RSS
RSS feed creation can now be customized via settings.


### Content Featured Images
All content objects now have the ability to set natively a featured image alongside the content.

### Author Edit Panels
The author details now sports two new panels to showcase their latest edits and latest drafts.  It will make it much easier for authors or administrators to discover what they are working on.


### CBHelper Updates
The CBHelper sports some new methods:
* `getPrivateRequestCollection()` - Get the ColdBox private request collection
* `isHomePage()` - Verify if the current rendered page is the home page
* `prepareUIRequest()` - Use in any ColdBox module to prepare rendering under the ContentBox theme

### New Admin Interception Points
Here is a collection of all the new admin interception points:

* `onGlobalSearchRequest` - When a global search is made
* `onGlobalSearchDisplay` - When the global search is displayed
* `cbadmin_beforeLoginForm` - Before the login form renders
* `cbadmin_afterLoginForm` - After the login form renders
* `cbadmin_preThemeSettingsSave` - Before saving theme settings
* `cbadmin_postThemeSettingsSave` - After saving theme settings
* `cbadmin_onThemeSettings` - When displaying theme settings in the admin UI
* `cbadmin_onThemeInfo` - When displaying theme information on the admin UI

----

## Theme Updates

We have also updated the theming engine in ContentBox with ColdBox 4 goodness and extreme modularity.  Here you can find the major updates for the theming engine.

### Themes not Layouts
Themes is our new mantra.  We have transitioned layouts to what we now call ContentBox Themes.  They have been revamped to support ColdBox 4.

### New Theme.cfc
The theme descriptor CFC is now named `Theme.cfc`.  Backwards compatibility still remains, but now the new descriptor will provide a nice way for editors and tools to target.

### Theme Setting Groups
You can now create theme setting groups in the theme descriptor `Theme.cfc` and the new admin UI will present them in a categorized and ordered format.  This is a great way to visualize theme settings.

### Theme Modules
Themes can now include ContentBox modules in a new folder convention called `modules`. This allows you to ship your theme with 1 or a billion modules.

### New Theme Events
The theme life-cycle now presents several new events:

* `cbadmin_preThemeSettingsSave` - Before saving theme settings
* `cbadmin_postThemeSettingsSave` - After saving theme settings
* `cbadmin_onThemeSettings` - When displaying theme settings in the admin UI
* `cbadmin_onThemeInfo` - When displaying theme information on the admin UI



----

## Major Front End Updates


### New ContentBox Theme
We have a new official UI theme that you will come to love.  It has over 10 different skins and configurations that will give you a plethora of configuration patterns for your site.  It is based on bower and grunt assets, so you can easily fork and customize.


### RESTFul Response Formats
The UI module now allows you to be able to export your pages, or blog entries in many response formats:

* json
* XML
* PDF
* word

The JSON and XML support means you can now build alternative UI modules based on modern JavaScript or other language frameworks.  This is a game changer for ContentBox as it will provide you with the ability to export any piece of content or blog in a tranportable RESTFul format.

### New Rendering Cache Headers
A new header will be sent to the browser if a content page is cached: `x-contentbox-cached-content`. This can provide proxies or cache engines the ability to tell when a page is cached by ContentBox.