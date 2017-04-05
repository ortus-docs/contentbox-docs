# What's New in 3.5.0

This release we're focusing on feedback from ContentBox 3.x customers and the ability to containerize ContentBox. Building on top of the SEO updates in ContentBox 3.1.0, we're continuing to make ContentBox more SEO friendly, Search Engine Friendly and Social Media Friendly.  This update has a tremendous amount of updates and bug fixes for your current installations.  So let's start investigating all the major areas of improvement:

## New Installation Slugs

ContentBox has been partitioned into three installation slugs from ForgeBox in this version going forward:

1. `contentbox` - Installs ContentBox as a module into any ColdBox application.
1. `contentbox-site` - Installs a new ColdBox site enabled for ContentBox with a dependency on `contentbox` for its module.
1. `contentbox-installer` - Same as above but with our DSN Creator and Installer Module.

This new schema and re-organization allows us better flexibility when updating ContentBox and installing ContentBox under docker containers.  First of all, updating ContentBox will now be a matter of two simple steps:

1. Run `box update contentbox` in the root of the site
1. Apply the `contentbox-db` patch in the admin

We are trying to leverage CommandBox much more for updates and also for ease of use of installation.

## Container Based Updates

On our move to greater containerization we have made several improvements and re-structuring in ContentBox.

### Override ContentBox Settings via ColdBox.cfc

You can now override any runtime setting for ContentBox via a configuration structure in your main `ColdBox.cfc` configuration file.  This will allow developers to override any runtime setting for any site (yes multi-site is coming).

All you need to do is create the a `contentbox` structure in your `configure()` or any tier method, with the name of the site (`default` is the default site) and then any setting name-value pair.

```js
contentbox = {
	
 // Runtime Settings Override by site slug
 settings = {
  // Default site
  default = {
   "cb_search_adapter" 		= "my.search.adapter",
   "cb_media_directoryRoot" 	= "/docker/mount"
  }
 }
}
```

### Override ContentBox Settings via Java Environment Variables

You can also override any runtime ContentBox setting by passing them via Docker/Java Runtime variables.

Since these are string keys we can now use our fancy structures like the settings above, so you must adhere to our recognition pattern:

```
contentbox_{site}_{setting}=value
```

Here is an example on adding a custom media root:

```
-Dcontentbox_default_cb_media_directoryRoot=./build/docker/contentbox/content
```

This will allow especially Docker environments to override settings as environments or even provide secrets.  More is coming, so stay tuned to our updates.

## i18n Editor Integration

The ContentBox editors now accept a new markup for retrieving localized content from any resource bundle in the ColdBox application.  You can now use the following markup:

```
// Retrieve a key from the default resource bundle
${i18n:resourcekey}

// Retrieve a key from a named bundle
${i18n:resourceKey@bundleName}
```

This will allow you better localization in any page, blog entry or content store item.

## i18n Caching Updates

All the UI front-end caching mechanisms have been updated to incorporate the user's language locale via the `i18n` module included in ContentBox.  This means that you can localize any content now by using the `getFWLocale()` method included in the `i18n` module.


## Updated Dashboard

The ContentBox dashboard gets some love with two new reports:

<img src="/images/3.5.0/dashboard-reports.png">

* Future Published Content - Shows top 10 content that publishes in the future.
* Expired Content - Shows the top 10 expired content.

The *Latest Edits* widget also shows hit counts for the pages as a mini-report.

## Revamped Admin Global Search

<img src="/images/3.5.0/search.png">

The admin global search has been completely revamped.  The UI has been updated to reflect the different types of context searches: pages, contentstore, entries and authors.  It also allows you to edit or open directly to the site if available.  We have also introduced that ability to scope your search context with the following search prefixes:

* `author:{text}`
* `page:{text}`
* `contenstore:{text}`
* `entry:{text}`

You can replace the `{text}` with whatever you want to search for and ContentBox will search only the context you 
applied.

<img src="/images/3.5.0/search-author.png">
<img src="/images/3.5.0/search-page.png">

### Global Search Interceptors

You can add your own search contexts and search contributions by listening to the following two events:

* `onGlobalSearchRequest`
* `onGlobalSearchDisplay`



## Content Store Ordering

<img src="/images/3.5.0/ordering-actions.png">

The content store hierarchy has now been introduced to ordering digits. This means that instead of retrieving content store collections ordered by their natural keys, you now have full control of ordering hierarchies.  This will allow you to create ordered collections for things like photo galleries, metadata, etc.

## On Demand Sitemap Generation for Search Engines

In an effort to make ContentBox work better with search engines, we have added a Sitemap Generation Module for Search Engines.  You can now upload your XML sitemaps to Google, Yahoo, Bing and any other search engine you would like to work with.

The Sitemap generation is available on demand, and available in several formats. Following Google's convention, we have implemented the following url patterns:

- `/sitemap.xml`
- `/sitemap.txt`
- `/sitemap.json`
- `/sitemap.html`
- `/sitemap` - which defaults to `html`

Google recommends XML, but supports `txt` as well. XML allows for more information, including:

 - `loc` - location / url of the content
 - `lastmod` - last modified
 - `image`
    - image:loc - image location / url

If you use the featured image with your pages and blog entries, the image will be included in the site map, and the last modified date as well.

The site maps shows all pages and blog entries that are published, and not hidden via the show in search bit. If you disable the blog, all blog posts are removed from the site map.

> **Info** The HTML version of the sitemap does not take into consideration any of the hierarchy of your site. It simply outputs all visible content into a list. This can be used for a crawl-able site page, but it not intended for your website visitors, at this time.

### Sitemap Options

You can turn on/off the sitemap features of ContentBox via the *Settings* Panel.

<img src="/images/3.5.0/sitemap-options.png">


### Sitemap.txt support requires manual step

To support `sitemap.txt`, you will need to edit your `config/routes.cfm` file. 
Inside that file you will find a line:

`setValidExtensions('xml,json,jsont,rss,html,htm,cfm,print,pdf,doc');`

For the `.txt` extension to work inside of ContentBox ( and ColdBox the framework underneath ContentBox ), you will need to append `txt` to the list of existing supporting file extensions. 

`setValidExtensions('xml,json,jsont,rss,html,htm,cfm,print,pdf,doc,txt');`

Once you have made this change, reinitialize the site, the easiest way is to log into the admin, and then click the Setting Cog and click `Reload Application`. Once this is done, the /sitemap.txt  will function in addition to the `xml` and `json` formats.

## Opengraph support for Facebook and Twitter

More information on Facebook and OpenGraph can be found here: [https://developers.facebook.com/docs/sharing/webmasters](https://developers.facebook.com/docs/sharing/webmasters)


## CKEditor Updates

CKEditor has been updated to its latest stable release with its new skin which looks fantastic within ContentBox.

<img src="/images/3.5.0/ckeditor.png">


## Update of all JavaScript libraries + Widgets

All internally used JavaScript libraries and widgets have been updated to their latest stable versions.

## Release Notes

### Bugs    
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-827'>CONTENTBOX-827</a>] -         Widget - When loading widgets the error catching is ugly
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-829'>CONTENTBOX-829</a>] -         Widget - Test Widget in Firefox relocates to url and does not run js function
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-838'>CONTENTBOX-838</a>] -         Quick search in Contentstore ignores ajax traversing
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-840'>CONTENTBOX-840</a>] -         ContentStore - deleting an item with child throws a big bad error
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-841'>CONTENTBOX-841</a>] -         Forgebox - Cfloop uses lucee attributes not ACF and errors on ACF
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-842'>CONTENTBOX-842</a>] -         Javascript reloads like Application Reinit ignore rewrites
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-843'>CONTENTBOX-843</a>] -         Wrong link on the latest edits for content store items
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-854'>CONTENTBOX-854</a>] -         Ellusive contentbox filebrowser media root reset
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-864'>CONTENTBOX-864</a>] -         Installer for 3.5 fails - settings for file browser doesn&#39;t exist on load
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-865'>CONTENTBOX-865</a>] -         Default Theme Archive layout is not correct
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-866'>CONTENTBOX-866</a>] -         Textareas in Geek Settings should be disabled to stop editing
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-867'>CONTENTBOX-867</a>] -         Theme Service - adds settings without flushing setting cache
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-871'>CONTENTBOX-871</a>] -         Preference are not working properly
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-872'>CONTENTBOX-872</a>] -         Content caching was not working due to missing return
            
### New Features
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-837'>CONTENTBOX-837</a>] -         Sitemap admin settings
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-844'>CONTENTBOX-844</a>] -         admin latest content widgets hit counter support
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-845'>CONTENTBOX-845</a>] -         Ability for ordering content store items within hierarchies
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-846'>CONTENTBOX-846</a>] -         Integrate yarn for node dependencies
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-847'>CONTENTBOX-847</a>] -         update all node dev dependencies
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-848'>CONTENTBOX-848</a>] -         Update ckeditor to latest edition
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-849'>CONTENTBOX-849</a>] -         Updated all UI dependencies
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-850'>CONTENTBOX-850</a>] -         Revamped global search UI
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-856'>CONTENTBOX-856</a>] -         New dashboard reports: expired content, future published content
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-858'>CONTENTBOX-858</a>] -         Ability to override ContentBox settings from the ColdBox Config
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-859'>CONTENTBOX-859</a>] -         Ability to override ContentBox settings via environment variables
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-860'>CONTENTBOX-860</a>] -         New setting prefix: i18n which will retrieve any language key
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-861'>CONTENTBOX-861</a>] -         Incorporate fw locale for cachekeys for content to allow for multi-lingual front ends
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-862'>CONTENTBOX-862</a>] -         content viewelets UI updates and choice enhancements: showAuthor, showColorings, showHits, showPublishedStatus,showExpired 
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-863'>CONTENTBOX-863</a>] -         Ability to add a search context in the global admin search via a prefix (page,entry,contentstore,author:search):search
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-870'>CONTENTBOX-870</a>] -         UI Admin Bar
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-873'>CONTENTBOX-873</a>] -         Media Manager UI Updates
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-874'>CONTENTBOX-874</a>] -         Media Manager Image Editor
        
### Improvements

* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-784'>CONTENTBOX-784</a>] -         Don&#39;t let the tools spinners spin infinitely after a form submission
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-791'>CONTENTBOX-791</a>] -         Mega Menu - JSON / Struct Export to allow Theme more control of display
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-792'>CONTENTBOX-792</a>] -         Add support for Facebook / Twitter OGRAPH elements in pages / entries
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-826'>CONTENTBOX-826</a>] -         Exporter - Once export is complete, UI does not update
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-828'>CONTENTBOX-828</a>] -         Widgets - Widgets loaded from Themes are still marked as Layouts
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-832'>CONTENTBOX-832</a>] -         update admin to use prc.oCurrentAuthor for consistency
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-833'>CONTENTBOX-833</a>] -         Sitemap UI module
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-835'>CONTENTBOX-835</a>] -         Contentbox Modules should have Forgebox Entries
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-836'>CONTENTBOX-836</a>] -         Allow cbCKfileBrowserDefaultEvent variable to be set in interceptor
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-839'>CONTENTBOX-839</a>] -         Anything using a .keyUp should have a debounce for better user experience
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-851'>CONTENTBOX-851</a>] -         When creating a contentstore item, you have no page modifiers for parents
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-855'>CONTENTBOX-855</a>] -         Latest Edits Viewlet need a ID for multiple viewlet renderings
                                        