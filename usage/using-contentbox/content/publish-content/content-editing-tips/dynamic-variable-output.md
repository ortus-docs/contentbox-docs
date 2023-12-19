# Dynamic Variable Output

As you can imagine, there are a lot of widgets you can use in ContentBox. Most widgets have specific and larger functionality… sometimes you might want something quick and simple… like outputting a single variable. You can output any RC or PRC variable with a simple helper function.

## What does RC and PRC mean:

* RC - Request Collection
* PRC - Private Request Collection

_The underlying framework (ColdBox) will merge the incoming URL/FORM/REMOTE variables into a single structure called the request collection structure that will live inside the request context object. We also internally create a second collection called the private request collection that is useful to store data and objects that have no outside effect._

## Syntax

The code below allows you to easily output from any of these source:

`${rc:name}`

This will output the `name` variable from the RC scope.

## Accessing URL Variables

This means you can output URL variables in your content. Look at this example, with the following url

`mydomain.com/?name=Gavin Pickin`

You could access the name with `${rc:name}`

You can tap into more items in the RC and PRC scopes as well, but you have to remember, you cannot output a struct to the page, only strings.

This gives you some nice options for form submissions, searches, and ways to add more information to a normal pages if you write your own modules.

## Escaping Dynamic Output

If you actually want to use the text above, without trying to output a variable, you can escape the code.

`<escape>${rc:name}</escape>`

If you do not escape the variables, and the variable doesn't exist, you'll see an error message like this:

`Error translating setting on target prc:page.renderContent(): The variable: page.renderContent() is undefined in the request collection (private=true) Keys Found: META,currentLayout,CBENTRYPOINT,currentRoutedURL,layoutmodule,currentView,CBROOT,layoutoverride,CBWIDGETROOT,CBSETTINGS,COMMENTSCOUNT,CATEGORIES,cbox_incomingContextHash,currentRoute,CBADMINENTRYPOINT,COMMENTS,PAGEOVERRIDE,OCURRENTAUTHOR,CBTHEME,CBTHEMEROOT,currentViewArgs,PAGE,viewModule Error translating setting on target rc:lastname: The variable: lastname is undefined in the request collection (private=false) Keys Found: namespaceRouting,event,pageSlug,format,namespace`

## Settings

Any setting stored in ContentBox can be output using the following markup: ${setting\_name}. This is a great way to create site-wide static settings that can be output in any editor.
