# Global Variables

During the ContentBox request, common variables and supertype methods are made available to all templates and views used in that request.  When developing themes and modules for ContentBox, you may assume availability of the following:

`#cb#`
===

The `cb` object contains a variety of common methods for retrieving ContentBox content and settings.  Methods include:

Content Retreival Methods
------------------------

- `cb.contentStore( string slug )`: retrieves the HTML output of a [Content Store][1] item by its slug
- `cb.contentStoreObject( string slug )`: retrieves the associated [Content Store][1] object

Path and URL Utility Methods
----------------------------

- `cb.themeRoot()`: returns the location of your currently defined theme in the application, great for assets, cfincludes, etc
- `cb.siteRoot()`: returns the site root location using your configured module's entry point
- `cb.siteBaseURL()`: returns the site's SES base URL
- `cb.adminRoot()`: returns the root location of the admin using your configured module's entry point
- `widgetRoot()`: returns the location of your widgets, great for assets and includes

Development and Debugging Helper Methods:
----------------------------------------

- `cb.themeName()`: returns the currently active theme name
- `cb.layoutName()`: returns the currently active layout name 


[1]: /content/using/managers/contentstore.html