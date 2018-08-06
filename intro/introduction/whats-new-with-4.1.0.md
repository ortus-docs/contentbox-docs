# What's New With 4.1.0

## Intro

ContentBox v4.1.0 is a minor release sporting a focus on stability from our 4.0.0 release and some great new improvements.

## Release Notes

### Bugs

* \[[CONTENTBOX-1011](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1011)\] - Error while Insert Menu widget
* \[[CONTENTBOX-1012](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1012)\] - Translation Error on Installation for Email Setup
* \[[CONTENTBOX-1014](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1014)\] - Verification of custom widget missing a / on ModuleConfig creation
* \[[CONTENTBOX-1015](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1015)\] - cbhelper still had setnextevent instead of relocate
* \[[CONTENTBOX-1016](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1016)\] - Content displaying issues on Widget List & Media manager
* \[[CONTENTBOX-1017](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1017)\] - meta description not rendering content
* \[[CONTENTBOX-1019](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1019)\] - bug when creating new content, it fired a publishd nagging when saving and not publishing
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

### New Features

* \[[CONTENTBOX-746](https://ortussolutions.atlassian.net/browse/CONTENTBOX-746)\] - Multi-select in Media Manager for deletes and downloads
* \[[CONTENTBOX-1027](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1027)\] - Add sortOrder as an option for getting published contents
* \[[CONTENTBOX-1041](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1041)\] - New editor nav interceptors: cbadmin\_pageEditorInBody, cbadmin\_ContentStoreEditorNav,cbadmin\_entryEditorNav
* \[[CONTENTBOX-1042](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1042)\] - Update to ColdBox 5.1
* \[[CONTENTBOX-1051](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1051)\] - New Editor Content Interceptors: cbadmin\_pageEditorNavContent, cbadmin\_contentStoreEditorNavContent, cbadmin\_entryEditorNavContent

### Improvements

* \[[CONTENTBOX-831](https://ortussolutions.atlassian.net/browse/CONTENTBOX-831)\] - FileBrowser - Filter to only show directories for Asset Chooser
* \[[CONTENTBOX-981](https://ortussolutions.atlassian.net/browse/CONTENTBOX-981)\] - Remove upload capabilities for widgets, modules and themes due to high security risks
* \[[CONTENTBOX-995](https://ortussolutions.atlassian.net/browse/CONTENTBOX-995)\] - AdminMenuService could help Modules add and clean up after themselves
* \[[CONTENTBOX-1018](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1018)\] - improve reusability of date/time formats in content objects
* \[[CONTENTBOX-1028](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1028)\] - Don't show non-stop loading while upload files
* \[[CONTENTBOX-1032](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1032)\] - Missing alert message on media manager when trying to download a file but none selected
* \[[CONTENTBOX-1034](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1034)\] - container fluid on login screen left over in security login.cfm
* \[[CONTENTBOX-1049](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1049)\] - Update the UI module to use the content service when displaying pages to allow for custom page types

