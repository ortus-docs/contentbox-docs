# What's New With 3.6.0

This release was all about improvements to the core, localization and internationalization for sites, many bug fixes, UI improvements and updates to our containerization strategy. Please see below the major areas of improvement and our full release notes.

## New Installer Module

The installer module is now available as a standalone module using the slug `contentbox-installer-module`. This will improve our container and your container strategy as now you can bring in the installer on demand via CommandBox.

```bash
install contentbox-installer-module
```

## Ability to contribute CSS to CKEditor

Thanks to the Computer Know How guys you can contribute your own CSS files to the CKEditor instance so the content has your theme's look and feel. Please note, this is mostly usable for theme developers and module developers.

The event is called `cbadmin_ckeditorContentsCss` and it will receive a struct with one key called `contentsCss` which is an array. You can then append CSS style sheets to that array that CKEditor will showcase.

```javascript
function cbadmin_ckeditorContentsCss( event, interceptData ){
  // Add css
  interceptData.contentsCss.append( "/path/theme.css" );
}
```

## Site Localization Updates

Thanks to the Computer Know How guys, this release sports many i18n improvements.

### Changing Site Locales

A ContentBox application depends on the ColdBox i18n module which gives you the ability to serve any content in any language, use resource bundles and use the resource utilities. However, we have now exposed the ability natively for users to change locales via the UI module using our URL of: `http://site.com/__changelang/en_US`. The route expects an ISO valid language code in the format of `code_variant`.

> **Note** By default, visitor locale's are stored in the `cookie` scope. You can change this via the `config/Coldbox.cfc` configuration CFC.

### Generating Locale Links

The `CBHelper` object can now produce these links for you in your layouts, themes and views by leveraging the following method:

```javascript
/**
 * Link to the __changeLang route, this is where the fwLocale is changed
 * @lang The iso language code
 */
function linkLanguageChange( string lang = "en_US" ) {
    return getRequestContext().buildLink( '__changeLang/' & arguments.lang );
}
```

### Locale Content Caching

All caching strategies have now been updated to allow for locale to determine its key. This way, every visitor's language will be cacheable and performant.

## Release Notes

### Bugs

* \[[CONTENTBOX-442](https://ortussolutions.atlassian.net/browse/CONTENTBOX-442)\] - Emails sent out to be approved or point back to the dashboard are not adhering to SSL rules of the site
* \[[CONTENTBOX-814](https://ortussolutions.atlassian.net/browse/CONTENTBOX-814)\] - Blog counts in category list include non-published entries.
* \[[CONTENTBOX-880](https://ortussolutions.atlassian.net/browse/CONTENTBOX-880)\] - Admin actions are note multi-tenant, regression
* \[[CONTENTBOX-896](https://ortussolutions.atlassian.net/browse/CONTENTBOX-896)\] - markdown converter not accounting for null markups from upgrades
* \[[CONTENTBOX-897](https://ortussolutions.atlassian.net/browse/CONTENTBOX-897)\] - Importer does not import cbox package
* \[[CONTENTBOX-898](https://ortussolutions.atlassian.net/browse/CONTENTBOX-898)\] - Error on update patch for additonal non-existen argument on log.append\(\)
* \[[CONTENTBOX-899](https://ortussolutions.atlassian.net/browse/CONTENTBOX-899)\] - missing variable exception on module config for environment variables and setting service
* \[[CONTENTBOX-901](https://ortussolutions.atlassian.net/browse/CONTENTBOX-901)\] - On HTTPS reload link are not ssl enabled
* \[[CONTENTBOX-909](https://ortussolutions.atlassian.net/browse/CONTENTBOX-909)\] - Adobe ORM Incompatibilities
* \[[CONTENTBOX-910](https://ortussolutions.atlassian.net/browse/CONTENTBOX-910)\] - bug on maintenance mode when user not logged in, null exception

### New Features

* \[[CONTENTBOX-878](https://ortussolutions.atlassian.net/browse/CONTENTBOX-878)\] - Admin &gt; Settings On/Off toggle
* \[[CONTENTBOX-881](https://ortussolutions.atlassian.net/browse/CONTENTBOX-881)\] - Create new installer slug: contentbox-installer-module
* \[[CONTENTBOX-905](https://ortussolutions.atlassian.net/browse/CONTENTBOX-905)\] - New \_\_changeLang/:lang UI route to allow for User locale changes
* \[[CONTENTBOX-906](https://ortussolutions.atlassian.net/browse/CONTENTBOX-906)\] - New CBHelper method for creating links to change UI locale languages linkLanguageChange\(\)
* \[[CONTENTBOX-911](https://ortussolutions.atlassian.net/browse/CONTENTBOX-911)\] - New ContentsCss interceptor for CKEditor module in order to allow for custom css to be loaded
* \[[CONTENTBOX-912](https://ortussolutions.atlassian.net/browse/CONTENTBOX-912)\] - Add getNumberOfContentStore and PublishedContentStore formulas to categories

### Improvements

* \[[CONTENTBOX-747](https://ortussolutions.atlassian.net/browse/CONTENTBOX-747)\] - Menu builder cannot render SSL links
* \[[CONTENTBOX-812](https://ortussolutions.atlassian.net/browse/CONTENTBOX-812)\] - File Uploader - Select File Change text not obvious a button
* \[[CONTENTBOX-813](https://ortussolutions.atlassian.net/browse/CONTENTBOX-813)\] - Filebrowser Root Path Setting failure doesn't throw error
* \[[CONTENTBOX-883](https://ortussolutions.atlassian.net/browse/CONTENTBOX-883)\] - Tools Importer Function often times out
* \[[CONTENTBOX-884](https://ortussolutions.atlassian.net/browse/CONTENTBOX-884)\] - Tools - Import button needs to be clicked twice?
* \[[CONTENTBOX-885](https://ortussolutions.atlassian.net/browse/CONTENTBOX-885)\] - Importer - BlogCFC Importer fails if Pages aren't in current version
* \[[CONTENTBOX-886](https://ortussolutions.atlassian.net/browse/CONTENTBOX-886)\] - Importer - BlogCFC Importer doesn't import blog hits correctly
* \[[CONTENTBOX-894](https://ortussolutions.atlassian.net/browse/CONTENTBOX-894)\] - Related content entries not showing in chronological order
* \[[CONTENTBOX-900](https://ortussolutions.atlassian.net/browse/CONTENTBOX-900)\] - strip whitespace for metadata content
* \[[CONTENTBOX-902](https://ortussolutions.atlassian.net/browse/CONTENTBOX-902)\] - cbhelper links now link correctly to homepage
* \[[CONTENTBOX-903](https://ortussolutions.atlassian.net/browse/CONTENTBOX-903)\] - Admin bar UI fixes
* \[[CONTENTBOX-904](https://ortussolutions.atlassian.net/browse/CONTENTBOX-904)\] - Add i18n locale to content cache keys
* \[[CONTENTBOX-908](https://ortussolutions.atlassian.net/browse/CONTENTBOX-908)\] - Security updates on pathing and forgebox modules

