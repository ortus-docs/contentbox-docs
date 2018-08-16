# What's New With 4.1.0

## Intro

ContentBox v4.1.0 is a minor release sporting a focus on stability from our 4.0.0 release and some great new improvements.  Let's explore this release:

### Upgrading

This is a minor release, so a simple `box update contentbox` will get you upgraded to this release.

### ColdBox Upgrade

ContentBox has been upgraded to work with ColdBox 5.1.x

### New Editor Interceptors

All content editors have the following new events being announced:

* **Editor Navigation Tab Area**
  * These events fire after the final tab in a content editor, usually so you can add your own tabs
    * `cbadmin_pageEditorInBody`
    * `cbadmin_ContentStoreEditorNav`
    * `cbadmin_entryEditorNav`
* **Editor Navigation Body Area**
  * These events fire after the final tab content panel, usually so you can add your own tab panels
    * `cbadmin_pageEditorNavContent`
    * `cbadmin_contentStoreEditorNavContent`
    * `cbadmin_entryEditorNavContent`

### Admin Menu Services

If you are building custom ContentBox modules that attach menus to the admin menu, then this update is for you.  All remove and add methods for menus now will not throw up if you reference a non-existent menu or sub menu.  Cleanup is now easier since you can remove at your heart's content without worrying of getting an exception.

### API Service Updates

The service layer for content objects has been updated with many new arguments and methods. As always, check out the [API Docs](https://apidocs.ortussolutions.com/contentbox/4.1.0/index.html) \([https://apidocs.ortussolutions.com/contentbox/4.1.0/index.html](https://apidocs.ortussolutions.com/contentbox/4.1.0/index.html)\) for further insight.  

* **ContentStoreService@cb**
  * `findPublishedContent()`
    * Added a `sortOrder` argument 
  * `search()`
    * `parent` argument can now be an entity or an entity ID
    * New `slugPrefix` argument which you can use to root a search on a specific content hierarchy. Ex: `slugPrefix = "products"` will search for all content under `products/*`
* **ContentService@cb**
  * `findPublishedContent()`
    * `parent` argument can now be an entity or an entity ID
    * New `slugPrefix` argument which you can use to root a search on a specific content hierarchy. Ex: `slugPrefix = "products"` will search for all content under `products/*`
* **CommentService@cb**
  * `search()`
  * Added a `sortOrder` argument

## Release Notes

### Bug

* \[[CONTENTBOX-1011](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1011)\] - Error while Insert Menu widget
* \[[CONTENTBOX-1012](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1012)\] - Translation Error on Installation for Email Setup
* \[[CONTENTBOX-1014](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1014)\] - Verification of custom widget missing a / on ModuleConfig creation
* \[[CONTENTBOX-1015](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1015)\] - cbhelper still had setnextevent instead of relocate
* \[[CONTENTBOX-1016](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1016)\] - Content displaying issues on Widget List & Media manager
* \[[CONTENTBOX-1017](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1017)\] - meta description not rendering content
* \[[CONTENTBOX-1019](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1019)\] - bug when creating new content, it fired a publishd nagging when saving and not publishing
* \[[CONTENTBOX-1020](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1020)\] - Permission Groups / Permissions relationship doesn't cascade and errors when removing permissions or authors
* \[[CONTENTBOX-1022](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1022)\] - Not able to delete a custom theme
* \[[CONTENTBOX-1024](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1024)\] - Don't display alert as "Your content is published already" for non published pages.
* \[[CONTENTBOX-1025](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1025)\] - Insert Widgets options are not enabled even the widgets having content.
* \[[CONTENTBOX-1029](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1029)\] - Invalid construct. A script statement must end with ";". in CF11.
* \[[CONTENTBOX-1030](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1030)\] - Don't show fbPreferences.listFolder is undefined in PRC error while using media manager
* \[[CONTENTBOX-1033](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1033)\] - Key \[MESSAGE\] doesn't exist when using bulk remove in Comments
* \[[CONTENTBOX-1038](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1038)\] - checks for ip and username banning so login does not break with multiple entries
* \[[CONTENTBOX-1040](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1040)\] - Can't cast Object type \[Struct\] to a value of type \[boolean\] when deleting admin modules
* \[[CONTENTBOX-1044](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1044)\] - Error on media manager due to HTML Helper update
* \[[CONTENTBOX-1045](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1045)\] - error opening import settings in the geek panel missing js
* \[[CONTENTBOX-1046](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1046)\] - Admin Layout does not include cbadmin\_beforeBodyEnd
* \[[CONTENTBOX-1050](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1050)\] - Category names should be unique, validation was missing
* \[[CONTENTBOX-1052](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1052)\] - bulk update of comment status breaks
* \[[CONTENTBOX-1053](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1053)\] - can't edit raw settings due to JS/CF boolean conversions
* \[[CONTENTBOX-1054](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1054)\] - security rules filter and ordering not working
* \[[CONTENTBOX-1058](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1058)\] - Throwing error while adding the existing name in Permission, Permission Group, Categories and Roles
* \[[CONTENTBOX-1059](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1059)\] - Need to change the Icon while assigning permissions for Roles and Permission Groups
* \[[CONTENTBOX-1060](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1060)\] - event caching cleanup was not working correctly for wrappers
* \[[CONTENTBOX-1061](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1061)\] - Lots of buttons missing the \`default\` class tag
* \[[CONTENTBOX-1063](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1063)\] - Some submenu items where not activated when used
* \[[CONTENTBOX-1064](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1064)\] - CommentForm widget previews not working and no way to default it to the currently executing page.
* \[[CONTENTBOX-1065](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1065)\] - Can't delete raw settings due to JS error
* \[[CONTENTBOX-1066](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1066)\] - Case issues for views on case sensitive OS's
* \[[CONTENTBOX-1067](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1067)\] - error on async interception points loading hibernate sessions

### New Feature

* \[[CONTENTBOX-746](https://ortussolutions.atlassian.net/browse/CONTENTBOX-746)\] - Multi-select in Media Manager for deletes and downloads
* \[[CONTENTBOX-1027](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1027)\] - Add sortOrder as an option for getting published contents
* \[[CONTENTBOX-1041](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1041)\] - New editor nav interceptors: cbadmin\_pageEditorInBody, cbadmin\_ContentStoreEditorNav,cbadmin\_entryEditorNav
* \[[CONTENTBOX-1042](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1042)\] - Update to ColdBox 5.1
* \[[CONTENTBOX-1051](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1051)\] - New Editor Content Interceptors: cbadmin\_pageEditorNavContent, cbadmin\_contentStoreEditorNavContent, cbadmin\_entryEditorNavContent
* \[[CONTENTBOX-1055](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1055)\] - Content Services search parent argument can now be the parent entity as well
* \[[CONTENTBOX-1056](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1056)\] - Content Services hiearchical search via the slugPrefix argument on all search methods

### Improvement

* \[[CONTENTBOX-831](https://ortussolutions.atlassian.net/browse/CONTENTBOX-831)\] - FileBrowser - Filter to only show directories for Asset Chooser
* \[[CONTENTBOX-981](https://ortussolutions.atlassian.net/browse/CONTENTBOX-981)\] - Remove upload capabilities for widgets, modules and themes due to high security risks
* \[[CONTENTBOX-995](https://ortussolutions.atlassian.net/browse/CONTENTBOX-995)\] - AdminMenuService could help Modules add and clean up after themselves
* \[[CONTENTBOX-1018](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1018)\] - improve reusability of date/time formats in content objects
* \[[CONTENTBOX-1028](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1028)\] - Don't show non-stop loading while upload files
* \[[CONTENTBOX-1032](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1032)\] - Missing alert message on media manager when trying to download a file but none selected
* \[[CONTENTBOX-1034](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1034)\] - container fluid on login screen left over in security login.cfm
* \[[CONTENTBOX-1049](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1049)\] - Update the UI module to use the content service when displaying pages to allow for custom page types
* \[[CONTENTBOX-1062](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1062)\] - Updated circle indicator to a filled circle for visual impact
* \[[CONTENTBOX-1068](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1068)\] - Updated environments for container heartbeats

