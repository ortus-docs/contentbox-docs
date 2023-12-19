# Theme SEO Functionality

ContentBox for some time has had a ContentBox site title, keywords and descriptions. Most themes also overrode those values with Blog Post and Page Titles, and if you use the SEO tab in the editor, you can override the Keywords and descriptions too.

## New SEO CBHelper Functions for your Theme

In ContentBox 3.1, we added some additional logic into the default Theme ( as a reference ) to allow even more flexibility with Title, Keywords, Meta etc. In previous versions, logic checked to see if the content was a blog, or a page, and how to determine if overrides were used or not. Now the CBHelper contains all of that logic, and you can just request the Title, Description or Keywords from CBHelper.

```
<title>#cb.getContentTitle()#</title>
<meta name="description"     content="#cb.getContentDescription()#" />
<meta name="keywords"          content="#cb.getContentKeywords()#" />
```

This is in addition to already existing functions like:

`<base href="#cb.siteBaseURL()#" />`

## Adding Meta to your Modules

One common issue with using the theme for your module is the way Meta Tags are generated. Having your own module, its hard to set your Title, Keywords and Description. As of ContentBox 3.1, since we have added the SEO and Meta functions to CBHelper, you can actually set and retrieve that data easily. To add Meta to your modules, you can now add this to your Module Handler Events.

```
function index(event,rc,prc){
    cbhelper.setMetaTitle( 'My cool module' );
    cbhelper.setMetaKeywords( 'ContentBox, Ortus, Themes, Modules' );
    cbhelper.setMetaDescription( 'My new module now has Meta Data to be used my the Theme.' );
    cbhelper.prepareUIRequest( "pages" );
    event.setView( "home/index" );
}
```
