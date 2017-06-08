# What's New in 3.6.0

This release was all about improvements to the core, localization and internationalization for sites, many bug fixes, UI improvements and updates to our containerization strategy.  Please see below the major areas of improvement and our full release notes.

## New Installer Module

The installer module is now available as a standalone module using the slug `contentbox-installer-module`.  This will improve our container and your container strategy as now you can bring in the installer on demand via CommandBox.

```bash
install contentbox-installer-module
```

## Ability to contribute CSS to CKEditor

Thanks to the Computer Know How guys you can contribute your own CSS files to the CKEditor instance so the content has your theme's look and feel.  Please note, this is mostly usable for theme developers and module developers.

The event is called `cbadmin_ckeditorContentsCss` and it will receive a struct with one key called `contentsCss` which is an array.  You can then append CSS style sheets to that array that CKEditor will showcase.


```js
function cbadmin_ckeditorContentsCss( event, interceptData ){
  // Add css
  interceptData.contentsCss.append( "/path/theme.css" );
}
```

## Site Localization Updates

Thanks to the Computer Know How guys, this release sports many i18n improvements.

### Changing Site Locales

A ContentBox application depends on the ColdBox i18n module which gives you the ability to serve any content in any language, use resource bundles and use the resource utilities.  However, we have now exposed the ability natively for users to change locales via the UI module using our URL of: `http://site.com/__changelang/en_US`.  The route expects an ISO valid language code in the format of `code_variant`.  

> **Note** By default, visitor locale's are stored in the `cookie` scope. You can change this via the `config/Coldbox.cfc` configuration CFC.


### Generating Locale Links

The `CBHelper` object can now produce these links for you in your layouts, themes and views by leveraging the following method:

```js
/**
 * Link to the __changeLang route, this is where the fwLocale is changed
 * @lang The iso language code
 */
function linkLanguageChange( string lang = "en_US" ) {
	return getRequestContext().buildLink( '__changeLang/' & arguments.lang );
}
```

### Locale Content Caching

All caching strategies have now been updated to allow for locale to determine its key.  This way, every visitor's language will be cacheable and performant.

## Release Notes            

### Bugs
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-442'>CONTENTBOX-442</a>] - Emails sent out to be approved or point back to the dashboard are not adhering to SSL rules of the site
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-814'>CONTENTBOX-814</a>] - Blog counts in category list include non-published entries.
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-880'>CONTENTBOX-880</a>] - Admin actions are note multi-tenant, regression
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-896'>CONTENTBOX-896</a>] - markdown converter not accounting for null markups from upgrades
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-897'>CONTENTBOX-897</a>] - Importer does not import cbox package
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-898'>CONTENTBOX-898</a>] - Error on update patch for additonal non-existen argument on log.append()
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-899'>CONTENTBOX-899</a>] - missing variable exception on module config for environment variables and setting service
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-901'>CONTENTBOX-901</a>] - On HTTPS reload link are not ssl enabled
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-909'>CONTENTBOX-909</a>] - Adobe ORM Incompatibilities
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-910'>CONTENTBOX-910</a>] - bug on maintenance mode when user not logged in, null exception
            
### New Features
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-878'>CONTENTBOX-878</a>] - Admin &gt; Settings On/Off toggle
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-881'>CONTENTBOX-881</a>] - Create new installer slug: contentbox-installer-module
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-905'>CONTENTBOX-905</a>] - New __changeLang/:lang UI route to allow for User locale changes
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-906'>CONTENTBOX-906</a>] - New CBHelper method for creating links to change UI locale languages linkLanguageChange()
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-911'>CONTENTBOX-911</a>] - New ContentsCss interceptor for CKEditor module in order to allow for custom css to be loaded
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-912'>CONTENTBOX-912</a>] - Add getNumberOfContentStore and PublishedContentStore formulas to categories
        
### Improvements
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-747'>CONTENTBOX-747</a>] - Menu builder cannot render SSL links
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-812'>CONTENTBOX-812</a>] - File Uploader - Select File Change text not obvious a button
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-813'>CONTENTBOX-813</a>] - Filebrowser Root Path Setting failure doesn&#39;t throw error
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-883'>CONTENTBOX-883</a>] - Tools Importer Function often times out
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-884'>CONTENTBOX-884</a>] - Tools - Import button needs to be clicked twice?
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-885'>CONTENTBOX-885</a>] - Importer - BlogCFC Importer fails if Pages aren&#39;t in current version
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-886'>CONTENTBOX-886</a>] - Importer - BlogCFC Importer doesn&#39;t import blog hits correctly
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-894'>CONTENTBOX-894</a>] - Related content entries not showing in chronological order
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-900'>CONTENTBOX-900</a>] - strip whitespace for metadata content
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-902'>CONTENTBOX-902</a>] - cbhelper links now link correctly to homepage
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-903'>CONTENTBOX-903</a>] - Admin bar UI fixes
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-904'>CONTENTBOX-904</a>] - Add i18n locale to content cache keys
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-908'>CONTENTBOX-908</a>] - Security updates on pathing and forgebox modules
                                        