# What's New With 4.0.0

## Intro

ContentBox v4.0.0 is the first major release of ContentBox and it sports tons of new updates, improvements and bug fixes including a major upgrade to [ColdBox v5.x](https://coldbox.ortusbooks.com/intro/introduction/whats-new-with-5.0.0) which in itself gives us tons of new updates and features.

## Release Notes

### Bugs

* \[[CONTENTBOX-775](https://ortussolutions.atlassian.net/browse/CONTENTBOX-775)\] - Error clicking Tools --&gt; Export in admin
* \[[CONTENTBOX-961](https://ortussolutions.atlassian.net/browse/CONTENTBOX-961)\] - Bulk remove comments throws an error
* \[[CONTENTBOX-962](https://ortussolutions.atlassian.net/browse/CONTENTBOX-962)\] - Calling right function for bulk remove comments
* \[[CONTENTBOX-963](https://ortussolutions.atlassian.net/browse/CONTENTBOX-963)\] - Update TwoFactorService to check for provider only if enabled
* \[[CONTENTBOX-975](https://ortussolutions.atlassian.net/browse/CONTENTBOX-975)\] - Media provider HTML producing non-unique IDs
* \[[CONTENTBOX-984](https://ortussolutions.atlassian.net/browse/CONTENTBOX-984)\] - Force users to enroll in MFA if the global MFA setting is turned ON.
* \[[CONTENTBOX-987](https://ortussolutions.atlassian.net/browse/CONTENTBOX-987)\] - RenderView widget errors due to event arguments
* \[[CONTENTBOX-989](https://ortussolutions.atlassian.net/browse/CONTENTBOX-989)\] - ThemeService was erroring when saving settings
* \[[CONTENTBOX-990](https://ortussolutions.atlassian.net/browse/CONTENTBOX-990)\] - quickLayout defaults to the contentbox module not the module the theme belongs to
* \[[CONTENTBOX-991](https://ortussolutions.atlassian.net/browse/CONTENTBOX-991)\] - Widget Discovery Mode regression in Theme location change
* \[[CONTENTBOX-992](https://ortussolutions.atlassian.net/browse/CONTENTBOX-992)\] - Submodules of ContentBox Modules are not registered
* \[[CONTENTBOX-993](https://ortussolutions.atlassian.net/browse/CONTENTBOX-993)\] - Modules default value for Module Type is Core
* \[[CONTENTBOX-994](https://ortussolutions.atlassian.net/browse/CONTENTBOX-994)\] - Module Deactivation Failures throw errors instead of catching nicely?
* \[[CONTENTBOX-998](https://ortussolutions.atlassian.net/browse/CONTENTBOX-998)\] - When admin close the 'Quick View' pop-up the 'ContentBox Asset Chooser' also closed.
* \[[CONTENTBOX-999](https://ortussolutions.atlassian.net/browse/CONTENTBOX-999)\] - Do not show error message for expired content. Currently when I create expired Content Store Items. When the expiration happens I get an Error message. There should be no error message.
* \[[CONTENTBOX-1001](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1001)\] - Checkboxes alignment issue in Content store -&gt; Categories menu
* \[[CONTENTBOX-1002](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1002)\] - 'Transform' tab displaying alignment issue in Image edit model window
* \[[CONTENTBOX-1003](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1003)\] - Invalid return type while Search and Apply filters on Comments-&gt;Inbox
* \[[CONTENTBOX-1004](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1004)\] - blog paging bootstrap compatable
* \[[CONTENTBOX-1008](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1008)\] - Error Installing ContentBox-installer@be -security interceptor not found
* \[[CONTENTBOX-1009](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1009)\] - Issue while uploading files With Long name in Media manager

### New Features

* \[[CONTENTBOX-973](https://ortussolutions.atlassian.net/browse/CONTENTBOX-973)\] - Creation of new contentbox-custom module for storing all custom user data
* \[[CONTENTBOX-974](https://ortussolutions.atlassian.net/browse/CONTENTBOX-974)\] - Refactor media content to new contentbox-custom/content location
* \[[CONTENTBOX-976](https://ortussolutions.atlassian.net/browse/CONTENTBOX-976)\] - Allow for modules to exist in internal contentbox module and also in contentbox-custom/modules location
* \[[CONTENTBOX-978](https://ortussolutions.atlassian.net/browse/CONTENTBOX-978)\] - Update exporter/importer for custom modules location
* \[[CONTENTBOX-979](https://ortussolutions.atlassian.net/browse/CONTENTBOX-979)\] - Update themes to work with core and custom location
* \[[CONTENTBOX-980](https://ortussolutions.atlassian.net/browse/CONTENTBOX-980)\] - Create widgets at custom location with override capabilities to core.
* \[[CONTENTBOX-982](https://ortussolutions.atlassian.net/browse/CONTENTBOX-982)\] - Migrate away from bower to yarn for UI
* \[[CONTENTBOX-988](https://ortussolutions.atlassian.net/browse/CONTENTBOX-988)\] - Enable MFA enrollment and unenrollment
* \[[CONTENTBOX-1000](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1000)\] - ContentBox Module executions now support child modules and also full URL Routing

### Improvements

* \[[CONTENTBOX-960](https://ortussolutions.atlassian.net/browse/CONTENTBOX-960)\] - Revamps of many-to-many relationships with cascading side effects
* \[[CONTENTBOX-964](https://ortussolutions.atlassian.net/browse/CONTENTBOX-964)\] - Media manager bug fixes concerning uploads and styles
* \[[CONTENTBOX-966](https://ortussolutions.atlassian.net/browse/CONTENTBOX-966)\] - Add interception points around lost password form
* \[[CONTENTBOX-969](https://ortussolutions.atlassian.net/browse/CONTENTBOX-969)\] - Update lost password instructions to match new flow
* \[[CONTENTBOX-970](https://ortussolutions.atlassian.net/browse/CONTENTBOX-970)\] - Restrict Administrators from setting User Passwords
* \[[CONTENTBOX-971](https://ortussolutions.atlassian.net/browse/CONTENTBOX-971)\] - Improve two factor flow by adding enrollment and unenrollment screens and interface updates
* \[[CONTENTBOX-983](https://ortussolutions.atlassian.net/browse/CONTENTBOX-983)\] - Update all JS libraries to their latest versions
* \[[CONTENTBOX-985](https://ortussolutions.atlassian.net/browse/CONTENTBOX-985)\] - content search improvements to do fuzzy searches instead of eq searches
* \[[CONTENTBOX-1006](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1006)\] - Var scoping issues in Widget Render lead to variable bleeding
* \[[CONTENTBOX-1007](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1007)\] - Contentbox installer doesn't allow you to select a special port for the datasource
* \[[CONTENTBOX-1010](https://ortussolutions.atlassian.net/browse/CONTENTBOX-1010)\] - config and environment overrides are now reloaded if the settings cache is flushed.

