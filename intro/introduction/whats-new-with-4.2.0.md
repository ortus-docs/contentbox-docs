# What's New With 4.2.0

## Intro

ContentBox v4.2.0 is a minor release sporting a focus on performance, security and stability from our 4.x release and some great new improvements.  Let's explore this release:

### Upgrading

This is a minor release, so a simple `box update contentbox` will get you upgraded to this release.

### ColdBox Upgrade

ContentBox has been upgraded to work with ColdBox 5.3.x

## Release Notes

### Bugs

* \[[CONTENTBOX-1070](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1070)\] - AdminBar not showing up anymore
* \[[CONTENTBOX-1071](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1071)\] - When cloning a content object, the markup type is not copied over
* \[[CONTENTBOX-1074](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1074)\] - contentbox-security/interceptors/CheckForForceTwoFactorEnrollment.cfc is fireing on too many events
* \[[CONTENTBOX-1076](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1076)\] - cb helper getCurrentCustomFields\(\) does not check for null custom field arrays
* \[[CONTENTBOX-1084](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1084)\] - Remove spaces from fb.min.js filenames in Filebrowser handler
* \[[CONTENTBOX-1085](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1085)\] - Preflight check has a race condition where duplicate settings can be inserted and stop app from starting
* \[[CONTENTBOX-1086](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1086)\] - Hello user module is missing version property - error when populating module config
* \[[CONTENTBOX-1088](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1088)\] - Deactivate modules if its directory does not exist in disk
* \[[CONTENTBOX-1091](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1091)\] - Widgets do not appear in panel until Reinit
* \[[CONTENTBOX-1092](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1092)\] - Folders in a module's widgets directory are treated as components
* \[[CONTENTBOX-1093](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1093)\] - Widgets - insert button missing
* \[[CONTENTBOX-1094](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1094)\] - CommentForm blowing up on previews on empty content objects
* \[[CONTENTBOX-1097](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1097)\] - Exception when import permission groups in a user
* \[[CONTENTBOX-1098](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1098)\] - Content types .print and .doc not rendered
* \[[CONTENTBOX-1099](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1099)\] - ACF blows up with async orm announcements
* \[[CONTENTBOX-1100](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1100)\] - Page preview not working throwing exception on missing layout
* \[[CONTENTBOX-1101](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1101)\] - Generated Meta Description showing HTML

### New Features

* \[[CONTENTBOX-1095](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1095)\] - Added better transactioning to tests
* \[[CONTENTBOX-1096](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1096)\] - categories widget to NOT show 0 count items
* \[[CONTENTBOX-1103](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1103)\] - Removed Old ForgeBox panels due to CommandBox first initiative

### Improvements

* \[[CONTENTBOX-497](https://ortussolutions.atlassian.net/browse/CONTENTBOX-497)\] - Move importer/exporters models from main contentbox module
* \[[CONTENTBOX-1069](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1069)\] - Refactor ContentBox UI to leverage the routing service instead of the SES interceptor
* \[[CONTENTBOX-1075](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1075)\] - Performance: settingService key cb\_enc\_key is called for each request
* \[[CONTENTBOX-1077](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1077)\] - page, comments are requested for each page view even if they are disabled
* \[[CONTENTBOX-1078](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1078)\] - Refactor the retrieval of ui categories to increase performance, lazy load for the win
* \[[CONTENTBOX-1081](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1081)\] - Current markup type and current editor are not shown as selected
* \[[CONTENTBOX-1082](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1082)\] - Upgrade messagebox to new version
* \[[CONTENTBOX-1083](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1083)\] - Upgrade cborm to support ACF2018

