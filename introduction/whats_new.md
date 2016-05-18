# What's New With 3.0.0

ContentBox 3.0.0 is a major release and with a completely rewritten administration module.  If you are upgrading from a previous release, please make sure you read the [Upgrading Guide](upgrading.md).  You can find the full release notes here: [Release Notes](https://ortussolutions.atlassian.net/secure/ReleaseNote.jspa?projectId=10008&version=12908)

ContentBox 3 is a collection of more than 150 tickets resolved.  It has been a massive undertaking with some great resoluts.  Below we go through the major updates and feature improvements.




----

## Admin Updates



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