---
description: September 23, 2021
---

# What's new With 5.0.0

ContentBox 5 is a major update for this CMS and it includes a major architectural change to move the CMS forward for the next 10-15 years. We have introduced multi-tenancy and a complete headless approach to ContentBox. It has become one of our biggest releases since our initial release since 2011.

You can find our release notes here and we will discuss our major areas of improvement for this release.  If you need to upgrade your previous versions of ContentBox, please see our [upgrade guide](upgrading-from-v4.x.md).

## ContentBox CLI

We have used the power of [CommandBox](https://www.ortussolutions.com/products/commandbox#download), to build a ContentBox CLI (`contentbox-cli`) module that will assist you with installations, upgrades, maintenance and much more.  Once CommandBox is installed you can run the following to install our cli:

```bash
box install contentbox-cli
```

That's it. This will install the `contentbox` namespace which will assist you in your ContentBox adventures.  Please see the [installation](../../getting-started/installation/) guide on usage.

## ColdBox 6 Core

![](<../../.gitbook/assets/image (2).png>)

We have upgraded our core to ColdBox 6 and we have received a tremendous amounts of benefits ([https://coldbox.ortusbooks.com/intro/release-history/whats-new-with-6.0.0](https://coldbox.ortusbooks.com/intro/release-history/whats-new-with-6.0.0)). Here are some of the features we get with this upgrade:

* Performance, performance, performance.  ColdBox 6 has been finely tuned to make your applications much more performant and stable under high load.
* Better new CFML engine support
* Asynchronous programming.  We have introduced the concepts of the **`async`** package to the core and ContentBox will leverage more of these features for background job processing, automation and much more.
* New logging facilities and enhancements
* Better exception handling for developers
* REST Handlers and highly performant REST Routing
* Singleton View Rendering. You will find that all renderings are way faster than before.
* Much more!

## CBSecurity 2

![](<../../.gitbook/assets/image (1).png>)

We have migrated our `cbsecurity` module to the latest version to give you a wealth of features ([https://coldbox-security.ortusbooks.com/intro/release-history/whats-new-with-2.0.0](https://coldbox-security.ortusbooks.com/intro/release-history/whats-new-with-2.0.0)) such as:

* Fortified rule engine
* Annotation based security engine
* JWT support
* Security Services
* Cross site request forgery support

## Multi Site Support

![](<../../.gitbook/assets/image (3).png>)

Although multi-tenancy been one of ContentBox's most requested features, we were hesitant for many years to comply due to the size of the needed refactoring. However, we have finally created a great base for making ContentBox multi-tenant. You can now configure 1 or 10000 sites under the same ContentBox umbrella. The new installer actually creates two sites for you: a development/staging site and a production site. That means that you can manage different content environments all under the same deployment.



![Multi-Site Manager](../../.gitbook/assets/multi-site-overview.png)

Here are some of the features you get with multi-site ContentBox:

* Ability to register an infinite number of sites
* Site detection by regular expressions or patterns on incoming URIs
* Site detection by header identifier if using the headless CMS or reverse proxies
* Each site can contain its own
  * Categories
  * Blog
  * Pages
  * Content Store
  * Menus
  * Commenting System
  * Themes
* Admin site switcher
* Admin site control bar
* Clone content or entire content hierarchies from one site to the other
* Publish content directly to different sites
* Move content between sites
* Much more coming soon.

![Multi-Site Switcher](../../.gitbook/assets/multi-site-switcher.png)

![Multi-Site Cloning](../../.gitbook/assets/multi-site-cloning.png)

![Multi-Site Publishing](../../.gitbook/assets/multi-site-publishing.png)

## Admin UI Revamp

![New Admin UI](../../.gitbook/assets/contentbox-5-admin.png)

The entire admin UI has been revamped and streamlined. You will find it much more breathable and easier to work with, especially from mobile devices and smaller screens. We are also starting to prepare a major theme change and customization that might be introduced in the final release or scheduled for a minor update.

![](<../../.gitbook/assets/image (6).png>)

![](<../../.gitbook/assets/image (5).png>)

We have also started our migrations to [Alpine.js](https://alpinejs.dev/) and [Tailwind](https://tailwindcss.com/) for the reactivity and overall look and feel of the admin module.

![Tablet Version](../../.gitbook/assets/contentbox-5-admin-ipad.png)

## PostgreSQL Support

![](<../../.gitbook/assets/image (4).png>)

We have completely changed our ORM structures and custom queries so it can be friendlier to other RDBMS. In this release we focus on portability of the host database and finally have core PostgreSQL support.

## Performance

We have analyzed the entire ORM structures, queries and CFML code in this release thanks to [FusionReactor](https://www.fusion-reactor.com/)'s Profiler. We have streamlined the way the CMS loads and the results are impressive. In ContentBox 5, first loads are about 70% faster and page executions are around 30-40% faster than ContentBox 4.

## No More Admin Auto Updates

This is such a controversial feature to be able to deliver patches via the admin. We have completely _dropped_ the capability to patch the CMS from within the CMS. It caused more issues than it solved and in Windows it was pretty much impossible.

We have moved to a CommandBox + Migrations approach and the results are amazing. No more broken installs, half done db updates and more. Now you can simply run two CLI commands and be done with it. Here is a typical flow for updating your system:

```bash
# stop the server
stop
# Update ColdBox and ContentBox
update coldbox,contentbox
# Run Migrations
migrate up
# start it up again
start
```

## Release Notes

### Bugs Squashed!

* \[[CONTENTBOX-1085](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1085)] - **Preflight** check has a race condition where duplicate settings can be inserted and stop app from starting
* \[[CONTENTBOX-1106](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1106)] - ColdBox modules directory renamed to modules\_bak during upgrade to ContentBox 4.2
* \[[CONTENTBOX-1107](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1107)] - Custom Module Dependencies are not respected by ContentBox ModuleService
* \[[CONTENTBOX-1111](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1111)] - When deactivating modules, module widgets still remained registered
* \[[CONTENTBOX-1115](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1115)] - Regression `cachelayout` setting missing from UI on pages and blog entries
* \[[CONTENTBOX-1118](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1118)] - media service had a `hardlink` to the UI module which threw an exception when the UI module was removed
* \[[CONTENTBOX-1126](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1126)] - `BaseContent` has `expireDate` as required via validation but not in the model
* \[[CONTENTBOX-1127](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1127)] - Problem with multiple select options in `RecentPages` widget
* \[[CONTENTBOX-1128](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1128)] - Problem in `RecentPages` widget on filter by category
* \[[CONTENTBOX-1132](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1132)] - Fix CB admin bar image alignment on tailwind sites
* \[[CONTENTBOX-1133](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1133)] - Fix ContentBox "**latestversion**" updater error #445
* \[[CONTENTBOX-1134](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1134)] - Fix content sidebar toggle label #444
* \[[CONTENTBOX-1143](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1143)] - multi domain bug when using cgi.http\_host just like ColdBox, move to cgi.server\_name instead affects all caching cleanups
* \[[CONTENTBOX-1151](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1151)] - Bug in Widget View clearing out cached widget query
* \[[CONTENTBOX-1152](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1152)] - ACF incompats with `relocate`() after `applicationStop`() due to ungraceful app metadata wiping by ACF
* \[[CONTENTBOX-1155](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1155)] - Admin Views Accessible even if logged out: cbsecurity not firing.
* \[[CONTENTBOX-1157](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1157)] - CB 5, Context menu Sitemap not visible, see screenshot
* \[[CONTENTBOX-1158](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1158)] - ms sql server doesn't support `sqltype` boolean
* \[[CONTENTBOX-1196](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1196)] - When cloning and marking to publish, not publishing due to missing publish date
* \[[CONTENTBOX-1198](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1198)] - Site settings for comments are not being transferred
* \[[CONTENTBOX-1182](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1182)] - "\\" doesn't go to global search
* [CONTENTBOX-1331](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1331) zipSlip fix for zip extractions
* [CONTENTBOX-1330](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1330) Error in Menu Sandbox
* [CONTENTBOX-1329](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1329) Listing Options do not work in Media Manager
* [CONTENTBOX-1327](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1327) Content Store, Entries and Pages Clone Error
* [CONTENTBOX-1318](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1318) If Page and ContentStore Item Have the Same Slug an Error is Thrown
* [CONTENTBOX-1317](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1317) Deleting a ContentStore Item from the Options Menu Throws an Error
* [CONTENTBOX-1316](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1316) Text Filter on Widget Insert is Broken
* [CONTENTBOX-1311](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1311) Truncate Auth Logs Function Throws SQL Error on SQL Server
* [CONTENTBOX-1307](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1307) ContentBox Menus and Submenus Default Order to Publish Date, not the Order
* [CONTENTBOX-1306](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1306) "Create Page" button in Admin throws Error
* [CONTENTBOX-1304](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1304) No Longer Able to Drill Down in Site Map
* [CONTENTBOX-1302](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1302) Theme is reset to default when saving a site
* [CONTENTBOX-1298](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1298) Prevent Re-Slugification of ContentStore Slugs on Every Save
* [CONTENTBOX-1290](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1290) Add Backward Compatibility Alias for @cb for ContentBox Models
* [CONTENTBOX-1284](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1284) Saving content on one site, if your site selection clears, will result in the
* assignment of page to default
* [CONTENTBOX-1277](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1277) The model namespace of cb was always wrong. It should have been `contentbox` if not, no module settings woud have ever been set.
* [CONTENTBOX-1276](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1276) RenderView Widget Attempts to Render Before View has Been Set
* [CONTENTBOX-1268](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1268) Regression - `menu()` in the cbHelper does not return the menu children in `data` mode
* [CONTENTBOX-1266](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1266) Data Snapshots in Admin are not Site Aware
* [CONTENTBOX-1256](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1256) DIFF Screen forces everything onto a single line and is unusable in a modal
* [CONTENTBOX-1251](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1251) Change tray icons to relative paths so CommandBox can open them correctly
* [CONTENTBOX-1245](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1245) contentstore saving did not account for original slug in order to change downstream hiearchies
* [CONTENTBOX-1240](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1240) Ordering pages on the sitemap breaks the javascript
* [CONTENTBOX-1231](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1231) exception when visiting newly created sites due to theme not being activated
* [CONTENTBOX-1224](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1224) Site Data Does not Export
* [CONTENTBOX-1220](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1220) Cache cleanups interceptor missing events for entry and content store removals
* [CONTENTBOX-1214](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1214) Font issues when loading admin
* [CONTENTBOX-1206](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1206) Respect carriage returns on comments

### New Feature

* \[[CONTENTBOX-1121](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1121)] - Upgrade `javaloader` to v2.0
* \[[CONTENTBOX-1123](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1123)] - Upgrade to `cborm` 3 and get all of it's goodness
* \[[CONTENTBOX-1135](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1135)] - Upgrade to ColdBox 6
* \[[CONTENTBOX-1136](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1136)] - Upgrade to `CBSecurity` 2
* \[[CONTENTBOX-1139](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1139)] - New configuration for site is using `cfconfig` with environment variables
* \[[CONTENTBOX-1140](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1140)] - Upgrade the usage of \`bit\` sql type to \`boolean\` sql type to avoid issues with major DB vendors and also to support PostgreSQL natively
* \[[CONTENTBOX-1141](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1141)] - Multi-site capabilities for all content and installations
* \[[CONTENTBOX-1142](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1142)] - All administrator js/css libraries updated to latest versions
* \[[CONTENTBOX-1149](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1149)] - Installer can now create a production and development site for you thanks to multi-site support
* \[[CONTENTBOX-1153](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1153)] - update security rules to match cbsecurity 2.0
* \[[CONTENTBOX-1179](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1179)] - Upgrade to cborm 3
* \[[CONTENTBOX-1192](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1192)] - Use Docbox 3 to generate the docs instead of the old approach
* [CONTENTBOX-1308](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1308) Refresh tokens support
* [CONTENTBOX-1301](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1301) Remove all $(document).ready() and move to DOMContentLoaded events to avoid relying on jquery and allow for deferred js
* [CONTENTBOX-1300](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1300) Load all js assets with defer to allow for modern JS libraries and for non blocking to DOM loading
* [CONTENTBOX-1291](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1291) Add ability for all search based content type services to have a array of property list return
* [CONTENTBOX-1275](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1275) Consolidate the editors (pages,contentstore,entries) to a single content editor
* [CONTENTBOX-1274](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1274) content version Diff ignore whitespace by default
* [CONTENTBOX-1269](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1269) Content Object Helpers
* [CONTENTBOX-1264](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1264) Enable Setters on Primary Keys to allow for migration of uuids to be consistent
* [CONTENTBOX-1257](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1257) Add export all and export selected to bulk actions
* [CONTENTBOX-1254](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1254) Add ability to load .env files on demand for NON commandbox installations
* [CONTENTBOX-1253](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1253) Ability to configure all orm settings via env variables.
* [CONTENTBOX-1252](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1252) Add filtering to geek settings by site
* [CONTENTBOX-1249](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1249) Remove the dsn creator in preference to our cli based approach
* [CONTENTBOX-1248](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1248) DSN Creator should update the dialect once the process starts
* [CONTENTBOX-1246](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1246) Allow json as native markup for content storaage
* [CONTENTBOX-1244](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1244) Ability to have unique slugs on a per content type basis instead of before which was unique across content types
* [CONTENTBOX-1242](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1242) Use the browser's timezone to display all date times to users
* [CONTENTBOX-1241](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1241) Add cbswagger documentation to resources and api module
* [CONTENTBOX-1238](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1238) tailwind polyfills
* [CONTENTBOX-1234](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1234) ContentBox core now registers a `contentbox-tasks` schedule executor that can be used for scheduled tasks
* [CONTENTBOX-1232](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1232) Add an option to open a site from the site manager
* [CONTENTBOX-1225](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1225) Add a clear entire template cache from the admin
* [CONTENTBOX-1222](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1222) new buildContentCacheCleanupKey() on content objects so we can clean multiple permutations of the same content
* [CONTENTBOX-1219](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1219) Introduce category count caching to speed up renderings
* [CONTENTBOX-1217](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1217) Rearchitecture of the active content to NOT be a relationship but using the versions relationship
* [CONTENTBOX-1213](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1213) New Updater task and start of tasks that can ship with ContentBox
* [CONTENTBOX-1205](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1205) Add support for markdown comments from the ui
* [CONTENTBOX-1168](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1168) Responsive UI Verifications
* [CONTENTBOX-1153](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1153) Upgrade to cbSecurity 2

### Task

* \[[CONTENTBOX-1110](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1110)] - Drop lucee 4.5 support
* \[[CONTENTBOX-1138](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1138)] - Drop support for \`runtime.properties.cfm\` in favor of cfconfig datasource additions
* \[[CONTENTBOX-1144](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1144)] - Remove autoupdates capabilities in order to rely on CommandBox for patches and updates
* \[[CONTENTBOX-1166](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1166)] - Upgrade v4 migration to only run on v4 systems
* \[[CONTENTBOX-1177](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1177)] - Removal of full screen button as all browsers support this now
* \[[CONTENTBOX-1181](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1181)] - Remove the textarea editor, it's useless

### Improvements

* \[[CONTENTBOX-1108](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1108)] - Add restrictions on orm cfc locations for faster startups on Application.cfc
* \[[CONTENTBOX-1109](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1109)] - Remove directory browsing for production installations
* \[[CONTENTBOX-1116](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1116)] - Change the order of the logout function, to the announcement has the oCurrentAuthor still, for logging purposes.
* \[[CONTENTBOX-1117](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1117)] - Update dsn creator to support lucee 5.3 mysql jdbc path
* \[[CONTENTBOX-1120](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1120)] - Intercept installer relocation to check if the installer module is even installed else present a nice message
* \[[CONTENTBOX-1125](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1125)] - Add a setting for the timeout in the forgot password workflow
* \[[CONTENTBOX-1131](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1131)] - Encode theme settings in active theme page
* \[[CONTENTBOX-1150](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1150)] - CSS Updates to match new admin theme
* \[[CONTENTBOX-1156](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1156)] - CB5 - Multi site - feature to allow URL Path
* \[[CONTENTBOX-1161](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1161)] - DSN Module Update to latest CFML engine settings
* \[[CONTENTBOX-1197](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1197)] - Refactor formulas to methods so they can give a performance boost and increase encapsulation
* \[[CONTENTBOX-1193](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1193)] - update express to latest stable lucee
* \[[CONTENTBOX-1194](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1194)] - update express to latest tomcat 9
* \[[CONTENTBOX-1195](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1195)] - update tuckey rewrites to latest based on commandbox
* [CONTENTBOX-1328](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1328) Inconsistent spacing between panels under Details
* [CONTENTBOX-1324](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1324) Create Setting - Core Checkbox With Global Option Seems Redundant
* [CONTENTBOX-1319](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1319) SSL Options on Relocation Widget Should Default to Current Protocol
* [CONTENTBOX-1315](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1315) Settings Area is Extremely Slow to Load on Large Site
* [CONTENTBOX-1314](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1314) Stats for Subscribers Should be Placed under Comments Menu
* [CONTENTBOX-1313](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1313) Site Selection Cookie Should Either Not Expire or Expiry Forwarded on Request
* [CONTENTBOX-1310](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1310) Drag and Drop Ordering on Large Site Tree is Very Slow
* [CONTENTBOX-1305](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1305) Issue a warning when you will save content that is published and into draft mode.
* [CONTENTBOX-1299](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1299) Finalize migration to ColdBox 6 REST instead of REST Template assets
* [CONTENTBOX-1297](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1297) Increase Column Size of Content slugs, title, featuredImage, featuredImageURL
* [CONTENTBOX-1294](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1294) CKEditor Allow access to ContentBox Plugins Insert Buttons in Source Edit Mode
* [CONTENTBOX-1293](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1293) SubPage Menu Widget should Default to Current Page
* [CONTENTBOX-1289](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1289) Dashboard Should Be a Single Link in Admin and "About" should be in "System"
* [CONTENTBOX-1288](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1288) Clicking in to a Content Objects Children should Reset Page Scroll
* [CONTENTBOX-1287](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1287) Allow transactional argument to SiteService@save
* [CONTENTBOX-1283](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1283) Allow Categories to be Internal/UnPublished
* [CONTENTBOX-1282](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1282) Migrate post to pre js for assets to save on minimization and inline js that is used.
* [CONTENTBOX-1281](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1281) Admin current working site id should be set in a cookie instead of cache to provide longevity.
* [CONTENTBOX-1279](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1279) Loading Site Config Page on Large Site is Extremely Slow
* [CONTENTBOX-1273](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1273) rework all settings tabs to have their own form and validation to avoid validation issues in different tabs you don't get notified with
* [CONTENTBOX-1272](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1272) ACF increase post parameter list for mass setting updates
* [CONTENTBOX-1255](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1255) Add JSON Diffing support for ContentStore items in the history panel
* [CONTENTBOX-1250](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1250) Add quoted table names, join columns and columns to preserve case on all RDBMS systems
* [CONTENTBOX-1239](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1239) Also the DSN name is now hard-coded in the cfconfig file so you can have a database named something other than "contentbox"
* [CONTENTBOX-1223](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1223) Update the clear page wrappers call to include multi-site regex expression to clear stale data
* [CONTENTBOX-1218](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1218) Add an isPreview to the addContentVersion() so the max content checks are not executed on previews
* [CONTENTBOX-1216](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1216) registering info for contentbox logging as the default.
* [CONTENTBOX-1215](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1215) If a post has been written in a certain markup, make sure the editor adheres to it
* [CONTENTBOX-1211](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1211) Granular performance optimizations for content object iteration and rendering
* [CONTENTBOX-1210](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1210) Optimize avatar image creation by using a request cache
* [CONTENTBOX-1209](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1209) Optimize the way site() does discovery and site usage by adding a request cache
