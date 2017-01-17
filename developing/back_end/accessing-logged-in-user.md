# Accessing Logged in User

Whether you are in a blog post, page, or a front end module ( anything using the Theme ), ContentBox makes it easy to work with the currently logged in User. In ContentBox, a user is called an Author. You can use these terms interchangeably.

During the PrepareUIRequest, that runs whenever we setup the ContentBox core, Theme etc, ContentBox gets the currently logged in user and stores it in the `PRC` ( Private Request Collection )`

To access the user, you can use this variable

`prc.oCurrentAuthor`

You can dump this variable out, but I would limit the number of rows deep you go, as this object has objects which has objects, and can give you a heap space error.

`<cfdump var="#prc.oCurrentAuthor#" top=3>`
or 
`writeDump( var=prc.oCurrentAuthor, top=3 );`


## What is available with the Current Logged in User?

- Author First Name `prc.oCurrentAuthor.getFirstName()`
- Author LastName `prc.oCurrentAuthor.getLastName()`
- Author Email `prc.oCurrentAuthor.getEmail()`
- Author Username `prc.oCurrentAuthor.getUserame()`
- Author Created Date `prc.oCurrentAuthor.getCreatedDate()`
- Author Modified Date `prc.oCurrentAuthor.getModifiedDate()`
- Author Last Login Date `prc.oCurrentAuthor.getLastLogin()`
- Author Biography `prc.oCurrentAuthor.getFirstName()`
- Author Preferences `prc.oCurrentAuthor.getFirstName()`
- Author Role `prc.oCurrentAuthor.getRole().getName()`

## Additional Author Content

`prc.oCurrentAuthor.entries()` returns an Array of entries / blog posts

`prc.oCurrentAuthor.getNumberOfEntries()` returns a count of entries / blog posts

`prc.oCurrentAuthor.pages()` returns an Array of pages

`prc.oCurrentAuthor.getNumberOfEntries()` returns a count of entries / blog posts

`prc.oCurrentAuthor.getPermissions()` returns an Array of A La Carte Permissions

`prc.oCurrentAuthor.getPermissionsList()` returns an string containing a list of A La Carte Permissions














































