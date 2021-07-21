# JS and CSS Assets

## Working with Assets in the Admin

To make Asset management easier in the Admin, we have provided a few arrays, that you can append your assets to. We have JS and CSS arrays, as well as convention based, and full path arrays.

### Javascript Assets

We have two options for working with Javascript in the admin.

**jsAppendList**

This expects the name of the js file \( without the .js extension \) which is located in the ContentBox includes/js folder. This is a simple convention based approach, so you can easily just append a file, for example `arrayAppend( jsAppendList, 'dragula' )` to load `/includes/js/dragula.js`

**jsFullAppendList**

This expects the full path of the js file \( including the .js extension \), including the location. This is useful, because you may be using grunt or gulp to compile files, store them in different locations, or actually link out to a CDN for some of your scripts.

For example:

* `arrayAppend( jsFullAppendList, '/includes/js/dragula.js' );`
* `arrayAppend( jsFullAppendList, 'https://code.jquery.com/jquery-3.1.1.min.js' );`

#### How the JS is output

Inside of `/modules/contentbox-admin/layouts/inc/HTMLBodyEnd.cfm` you will see the following code.

```text
<cfloop list="#event.getValue( "jsAppendList", "", true )#" index="js">
    <script src="#prc.cbroot#/includes/js/#js#.js"></script>
</cfloop>
<cfloop list="#event.getValue( "jsFullAppendList", "", true )#" index="js">
    <script src="#js#"></script>
</cfloop>
```

### CSS Assets

We have two options for working with CSS in the admin.

**cssAppendList**

This expects the name of the CSS file \( without the .css extension \) which is located in the ContentBox includes/css folder. This is a simple convention based approach, so you can easily just append a file, for example `arrayAppend( cssAppendList, 'dragula' )` to load `/includes/css/dragula.css`

**cssFullAppendList**

This expects the full path of the css file \( including the .css extension \), including the location. This is useful, because you may be using grunt or gulp to compile files, store them in different locations, or actually link out to a CDN for some of your scripts.

For example:

* `arrayAppend( cssFullAppendList, '/includes/css/dragula.css' );`
* `arrayAppend( cssFullAppendList, 'https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css' );`

#### How the CSS is output

Inside of `/modules/contentbox-admin/layouts/inc/HTMLHead.cfm` you will see the following code.

```text
<cfloop list="#event.getValue( "cssAppendList", "", true )#" index="css">
    <cfset addAsset( "#prc.cbroot#/includes/css/#css#.css" )>
</cfloop>
<cfloop list="#event.getValue( "cssFullAppendList", "", true )#" index="css">
    <cfset addAsset( "#css#" )>
</cfloop>
```

