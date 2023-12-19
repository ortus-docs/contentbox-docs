# Theme UDFs

UDF ( User Defined Functions ) are a great way to add more power to your theme, and your theme settings.

Below are some common UDFs you might want to use in your themes, or templates on how you could create some of your own.

## Example UDFs

### LoadHelpFile()

This is a useful method for standardizing loads HTML for the fieldHelp Modal. The fieldHelp setting using this function would look like this

`loadHelpFile( 'cbBootswatchTheme.html' );`

Since the `helpFilePath` is not passed in this example, it defaults to the Theme's `includes/help/` folder.

_Note: One concern when using this is relative pathing of assets, since the modal is generated in one folder, and the includes are in another folder._

```
/**
* loadHelpFile - helper function for loading html help into a variable for modal
* @helpFileName - the name of the file to read and return
* @helpFilePath - the relative directory for the help files. Defaulting to ./includes/help/ inside the theme.
* @return the contents of the file or empty string if the file does not exist
*/
function loadHelpFile( required string helpFileName, string helpFilePath='./includes/help/' ){
    try {
        return fileRead( arguments.helpFilePath & arguments.helpFileName );
    } catch( any e ){
        return '';
    }
}
```

### selectMediaManagerFolder()

This function gives you an array of Media Manager folders, so you could use in a optionsUDF setting, to allow the Theme Settings form to display a dropdown box with a list of folders. This would be great for a slide show, where the users select the folder, and all of the contents of the folder could be shown in the slideshow.

```
function selectMediaManagerFolder(){
    var event         = getRequestContext();
    var cbSettings     = event.getValue(name="cbSettings",private=true);
    var defaultDir = expandPath( cbSettings.cb_media_directoryRoot );
    var allDirectories = directoryList( path=defaultDir, recurse=true, listInfo="query" );
    var result = [];
    for( var directory in allDirectories ){
        if ( directory.type is 'dir' ){
            var theString = replaceNoCase( directory.directory, defaultDir, "", "all" ) & '/' & directory.name;
            theString = replaceNoCase( theString, "\", "/", "all");
            theString = replaceNoCase( theString, "//", "/", "all");
            result = result.append( theString );
        }
    }
    return result;
}
```

### getBootstrapStyles()

Bootstrap has a set of pre-defined styles, used in alerts, buttons, and many other styles you can use in your website. Having a UDF like this, allows you to create a setting that the User can select the button style type.

```
array function getBootstrapStyles(){
    return [ 
        "default",
        "primary",
        "success",
        "info",
        "warning",
        "danger"
    ];
}
```

### getBootstrapSwatches()

We use BootSwatch in several Themes, because it gives the user of the theme a lot of complete styles, in one theme. This UDF shows you how you can return a list as an array, so a user could select the BootSwatch they would like to use.

```
/**
* Build the swatches options
*/
array function getBootSwatches(){
    return listToArray( "cerulean,cosmo,cyborg,darkly,flatly,green,journal,lumen,paper,readable,sandstone,simplex,slate,spacelab,superhero,united,yeti" );
}
```
