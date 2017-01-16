# What's New With 3.1.0

ContentBox 3.1.0 is a minor release with over 40 issues, improvements and new features addressed.  Below you will find the detailed release notes about this release but also the major areas of improvement and new features introduced. Enjoy!

## Upgrading to 3.1.0

The easiest way to upgrade your ContentBox installation is to use the auto updater located in the **system > updates** panel. Just make sure you please backup your database and source code as this release includes a major framework update and you will **most likely need to reboot your engine or server**.

## Travis Integration
Travis is now building and publishing ContentBox to ForgeBox.io.  We will also be able to accept pull requests with satisfaction that they do not break the builds.  So pull away my friends!

## Updated JDK/JRE + Lucee Engines
All express versions have been updated with the latest JRE/JDKs and Lucee CFML engines.

## Easily Render Captcha Images
ContentBox supports native captcha support and now your themes can render out a nice captcha image by using the new ContentBox helper method: `cb.renderCaptcha()` method.

## SEO Enhancements 

We have also devoted time to enhance the SEO capabilities of ContentBox not only in the ContentBox helper object but in the updated default theme.  The new helper methods are:

* `getContentTitle()` : Retrieve the assigned title for a rendered page
* `getContentDescription()` : Retrieve the assigned description for a rendered page
* `getContentKeywords()` : Retrieve the assigned keywords for a rendered page

### Title Discovery
Please note that the **title** for a page now comes in the following discovery hiearchy:

1. Override set by custom modules
2. SEO Panel title
2. Page name


### Description Discovery
Please note that the **description** for a page now comes in the following discovery hiearchy:

1. Override set by custom modules
2. SEO Panel description
3. Excerpt
4. Dynamic Excerpt (160 characters) from content

### Keywords Discovery
Please note that the **keywords** for a page now comes in the following discovery hiearchy:

1. Override set by custom modules
2. SEO Panel keywords
3. Global Site Keywords


### SEO Module Overrides

If you are building custom modules with views that render in a site's theme, you can now also set SEO content for title, description and keywords by leveraging the following methods in the ContentBox Helper:

* `setMetaTitle()`
* `setMetaDescription()`
* `setMetaKeywords()`

## Static Site Generator

![](/images/static_site_generator.png)

ContentBox 3.1 now supports the generation of static sites from your content and even your blog. This is a great addition to ContentBox as now you can produce static versions and workflows, deploy to CDN networks, secure your content and much more.  Once you click on the **Start Generation** button, ContentBox will go over your entire site and produce a static archive for you in the associated theme.  It will also announce two interception points for you during the process:

* `cbadmin_preStaticSiteExport` : Receives all the export `options` in the intercept data so you can alter the export behavior.
* `cbadmin_postStaticSiteExport` : Receives all the export `options` and also a `results` structure with the following keys: `exportLog:builder, exportDirectory, exportArchive`.  This is a great way to listen for the export and send to S3 for archiving, etc.

> **Warning** Dynamic elements like commenting, searching, etc must require a JavaScript implementation.  So make sure you have a static export strategy in place.

## Module Enhancements

This release sports many enhancements to support module development authors in order for them to seamlessly build high impact applications using ContentBox.

### Author Object Availability

The logged in (or not) author/user of ContentBox is now globally available in the ColdBox private request collection as `prc.oCurrentAuthor`.  This will allow module developers to have easy access to the current object that would represent a logged in Author or User of the ContentBox instance.




----

## Release Notes
            
### Bug

- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-762'>CONTENTBOX-762</a>] -         If admin is in SSL mode, then previews should trigger ssl as well 
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-766'>CONTENTBOX-766</a>] -         BaseWidget not providing a default logging class &#39;log&#39; as it did in ContentBox 2
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-767'>CONTENTBOX-767</a>] -         Admin Layout - loop through jsFullAppendList uses the wrong src base
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-771'>CONTENTBOX-771</a>] -         background color indicators for drafts, published future and expired content is not showing up
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-776'>CONTENTBOX-776</a>] -         PermissionService, RoleService missing date util injection
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-777'>CONTENTBOX-777</a>] -         exclude pages,entries on author mementos, they are not treated for export/import
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-778'>CONTENTBOX-778</a>] -         Importer not importing correct custom modules if coming from windows
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-780'>CONTENTBOX-780</a>] -         Blog excerpt not rendering ContentStore objects
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-800'>CONTENTBOX-800</a>] -         Adobe Compilation error due to ColdBox 4.3 updates
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-803'>CONTENTBOX-803</a>] -         Cascading issue on deletion of one-to-one relationship between base content and its stats
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-808'>CONTENTBOX-808</a>] -         Incorrect title on snapshots data table
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-809'>CONTENTBOX-809</a>] -         i18n properties out of sync with the US file
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-815'>CONTENTBOX-815</a>] -         Installer doesn&#39;t work without rewrites
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-816'>CONTENTBOX-816</a>] -         Blog Paging in front end works correctly but display is incorrect
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-817'>CONTENTBOX-817</a>] -         Blog Paging uses Javascript:null which errors in Firefox
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-818'>CONTENTBOX-818</a>] -         Blog Pagination - If you hit a page over total it shows up blank
            
### New Feature

- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-514'>CONTENTBOX-514</a>] -         Content Subscriptions
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-760'>CONTENTBOX-760</a>] -         Update express editions to use latest JDK
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-761'>CONTENTBOX-761</a>] -         Update lucee to latest stable in 4.5 series for Express/War Editions
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-765'>CONTENTBOX-765</a>] -         New CBHelper method: renderCaptcha() to easily render the img tag
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-783'>CONTENTBOX-783</a>] -         Static Site Generator
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-796'>CONTENTBOX-796</a>] -         prc.oCurrentAuthor is now set and available globally by the UI prepare request interceptor
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-801'>CONTENTBOX-801</a>] -         Travis integration
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-802'>CONTENTBOX-802</a>] -         edge case exception when a content object has no active content versions on ACF
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-805'>CONTENTBOX-805</a>] -         new cbhelper seo method: getContentTitle() that retrieves the content title according to discovery rules
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-806'>CONTENTBOX-806</a>] -         new cbhelper seo method: getContentDescription() that retrieves the metadata according to discover rules
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-807'>CONTENTBOX-807</a>] -         new cbhelper seo method: getContentKeywords() that retrieves the metadata according to discover rules

### Improvement

- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-573'>CONTENTBOX-573</a>] -         Auto-fill Name/E-mail and skip captcha on comments if logged in
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-641'>CONTENTBOX-641</a>] -         Add image resizing/cropping to filebrowser
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-740'>CONTENTBOX-740</a>] -         Update site maintenance feature to have admin still view site but it&#39;s down for everyone else
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-756'>CONTENTBOX-756</a>] -         SEO Convention for passing title, keywords, description to theme from modules
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-759'>CONTENTBOX-759</a>] -         Convention for Module Based Security Rules
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-768'>CONTENTBOX-768</a>] -         Admin Layout - loop through jsFullAppendList and cssFullAppendList expects no extension
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-779'>CONTENTBOX-779</a>] -         CBHelper now accounts for ssl via request context on all link building operations
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-785'>CONTENTBOX-785</a>] -         cbhelper isprintFormat not accounting for html formats
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-797'>CONTENTBOX-797</a>] -         CommentForm widget standardizes to default bootstrap themes
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-798'>CONTENTBOX-798</a>] -         Search Form Widget standardized to bootstrap
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-799'>CONTENTBOX-799</a>] -         Updated all box dependencies to latest releases
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-804'>CONTENTBOX-804</a>] -         Update mobile detector to latest incoming script
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-811'>CONTENTBOX-811</a>] -         Add more documentation options for theme elements and groups
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-819'>CONTENTBOX-819</a>] -         Filebrowser - Download a folder gives confusing error message
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-820'>CONTENTBOX-820</a>] -         FileBrowser - Right click doesn&#39;t select object when showing Context Menu
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-821'>CONTENTBOX-821</a>] -         FileBrowser - Format the timestamp in the status bar to be more user friendly
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-822'>CONTENTBOX-822</a>] -         FileBrowser - Make Location Breadcrumbs clickable
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-823'>CONTENTBOX-823</a>] -         FileBrowser - Excluded Items not removed from Item count in Status Bar
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-824'>CONTENTBOX-824</a>] -         FileBrowser - In grid view - the selection area isn&#39;t the full thumb square
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-825'>CONTENTBOX-825</a>] -         FileBrowser - Update Message to include Settings
- [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-828'>CONTENTBOX-828</a>] -         Widgets - Widgets loaded from Themes are still marked as Layouts
                                        