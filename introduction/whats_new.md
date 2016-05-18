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


