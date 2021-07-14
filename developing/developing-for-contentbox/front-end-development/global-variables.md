# Global Variables

## Global Variables and Functions

During the ContentBox request, common variables and super-type methods are made available to all templates and views used in that request. When developing themes and modules for ContentBox, the following methods and variables are available for use in customization:

## `#cb#`

The `cb` object contains a variety of common methods for retrieving ContentBox content and settings. Below are some common methods used to retrieve and create HTML content:

### Content and Settings Retrieval Methods

#### Settings Retreival

* `cb.siteName()`: retrieves the configured name of Contentbox installation
* `cb.siteTagline()`: retrieves the configured tagline for the ContentBox installation
* `cb.siteDescription()`: retrieves the configured description for the Contentbox installation
* `cb.siteKeywords()`: retrieves the configured global keywords
* `cb.siteEmail()`: retrieves the default site email
* `cb.siteOutgoingEmail()`: retreives the configured email used in outbound deliveries

#### Theme Views

* `cb.quickView( viewTemplate )`: Renders a view partial located in the `[theme home]/views` directory.  A `.cfm` file extension is not required.
* `cb.mainView( args )`: Renders the main view for the handler action.  A struct containing the args necessary for view rendering should be passed in.  By default, this struct is available in your layout and is also named `args`.

#### Entry Retrieval

* `cb.getCurrentEntries()`:
* `cb.getCurrentEntriesCount()`:
* `cb.getCurrentCategories()`:
* `cb.getCurrentPage()`:
* `cb.getCurrentComments()`: Returns the published comments for the current entry
* `cb.getCurrentCommentsCount()`: Returns the count of published comments for the current entry
* `cb.getCurrentRelatedContent()`: Returns an array of content related to the active post or entry
* `cb.getCurrentCustomFields()`: Returns a structure of custom fields for the active post or entry
* `cb.getCustomField( string fieldName, any defaultValue )`: Returns the value of a custom field for the active post or entry

#### Content Store Retrieval

* * `cb.contentStore( string slug )`: retrieves the HTML output of a [Content Store](https://github.com/ortus/contentbox-modular-cms/tree/76cb63aa894e4f019c2d324f6bfb86f8d0142a92/content/using/managers/contentstore.html) item by its slug
* `cb.contentStoreObject( string slug )`: retrieves the associated [Content Store](https://github.com/ortus/contentbox-modular-cms/tree/76cb63aa894e4f019c2d324f6bfb86f8d0142a92/content/using/managers/contentstore.html) object
* `cb.widget( string widgetName, struct args )`: executes a named widget's `renderit` method and returns the HTML.  A structure of arguments may be passed.
* `cb.getWidget( string widgetName )`: retreives the associated \[widget\]\[2\] object
* `cb.themeSetting( string settingName, any defaultValue )`: retrieves a theme setting by name. A default value may be specified
* `cb.isCommentsEnabled()`: returns a true\|false value of whether site comments are enabled and if the current entry accepts comments
* `cb.quickSearchForm()`: returns the HTML of a standard ContentBox Search Form according to the SearchForm widget
* `cb.getSearchResults()`: returns an array of results for an active search

#### Link Building Methods

* `cb.linkAdmin()`: creates a link to the ContentBox admin
* `cb.linkAdminLogin()`: creates a link to the ContentBox administration login form
* `cb.linkAdminLogout()`: creates a link to logout of ContentBox administration
* `cb.linkBlog()`: creates a link to the site's blog
* `cb.linksSelf()`: creates a link to the current page
* `cb.linkPageRSS( any categoryFilter)`: creates a link to the RSS feed applicable to the active request
* `cb.linkSiteRSS( any categoryFilter )`: creates a link to the site's RSS feed
* `cb.linkCategory( string categorySlug )`: creates a link to a specific category page
* `cb.quickCategoryLinks( string categorySlug )`: creates an HTML unordered list of category links
* **Path and URL Utility Methods**
* `cb.themeRoot()`: returns the location of your currently defined theme in the application, great for assets, cfincludes, etc
* `cb.siteRoot()`: returns the site root location using your configured module's entry point
* `cb.siteBaseURL()`: returns the site's SES base URL
* `cb.adminRoot()`: returns the root location of the admin using your configured module's entry point
* `widgetRoot()`: returns the location of your widgets, great for assets and includes

#### Interception Points

A number of built-in interception points are avaialble within the ContentBox request, which may be run using the `cb.event()` method. For examples of how these are used, see the default theme layout files. Examples include:

* `cb.event( "cbui_beforeHeadEnd" )`
* `cb.event( "cbui_afterBodyStart" )`
* `cb.event( "cbui_afterContent" )`
* `cb.event( "cbui_beforeBodyEnd" )`

#### Development and Debugging Helper Methods:

* `cb.themeName()`: returns the currently active theme name
* `cb.layoutName()`: returns the currently active layout name 
* `cb.isPrintFormat()`: returns true if you are in printing or exporting format

#### UI Utility Functions

* **Easily Render Captcha Images** - ContentBox supports native captcha support and now your themes can render out a nice captcha image by using the new ContentBox helper method:
  * `cb.renderCaptcha()` method.

\[2\]: /content/using/managers/widgets.html

