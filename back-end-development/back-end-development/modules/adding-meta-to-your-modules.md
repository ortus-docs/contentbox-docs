# Adding Meta to your Modules

One common issue with using the theme for your module is the way Meta Tags are generated. Having your own module, its hard to set your Title, Keywords and Description.

You are able to do this inside your Module Handler Events

```
function index(event,rc,prc){
    cbhelper.setMetaTitle( 'Gavins cool module' );
    cbhelper.setMetaKeywords( 'Gavins cool keywords' );
    cbhelper.setMetaDescription( 'Gavins cool description' );
    cbhelper.prepareUIRequest( "pages" );
    event.setView( "home/index" );
}
```
