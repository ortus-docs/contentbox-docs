ContentBox 3.1.0 is a minor release with over 40 issues, improvements and new features addressed. 


## Release Notes - ContentBox Modular CMS - Version 3.1.0
            
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
                                        