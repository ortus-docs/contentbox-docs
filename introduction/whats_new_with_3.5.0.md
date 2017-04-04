# What's New in 3.5.0

This release we're focusing on feedback from ContentBox 3.x customers and the ability to containerize ContentBox. Building on top of the SEO updates in ContentBox 3.1.0, we're continuing to make ContentBox more SEO friendly, Search Engine Friendly and Social Media Friendly.  This update has a tremendous amount of updates and bug fixes for your current installations.  So let's start investigating all the major areas of improvement:

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

To support sitemap.txt, you will need to edit your `config/routes.cfm` file. 
Inside that file you will find a line:

`setValidExtensions('xml,json,jsont,rss,html,htm,cfm,print,pdf,doc');`

For the `.txt` extension to work inside of ContentBox ( and ColdBox the framework underneath ContentBox ), you will need to append `txt` to the list of existing supporting file extensions. 

`setValidExtensions('xml,json,jsont,rss,html,htm,cfm,print,pdf,doc,txt');`

Once you have made this change, reinitialize the site, the easiest way is to log into the admin, and then click the Setting Cog and click `Reload Application`. Once this is done, the /sitemap.txt  will function in addition to the `xml` and `json` formats.

## Opengraph support for Facebook and Twitter

More information on Facebook and OpenGraph can be found here: [https://developers.facebook.com/docs/sharing/webmasters](https://developers.facebook.com/docs/sharing/webmasters)

