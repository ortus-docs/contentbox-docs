# Accessing Logged in User

Whether you are in a blog post, page, administrative module, or a front end module, ContentBox makes it easy to work with the currently logged in User. In ContentBox, a user is called an Author. You can use these terms interchangeably.

During the PrepareUIRequest, that runs whenever we setup the ContentBox core, Theme etc, ContentBox gets the currently logged in user and stores it in the `PRC` ( Private Request Collection )`

To access the user, you can use this variable

`prc.oAuthor`

You can dump this variable out, but I would limit the number of rows deep you go, as this object has objects which has objects, and can give you a heap space error.

`<cfdump var="#prc.oauthor#" top=3>`
or 
`writeDump( var=prc.oAuthor, top=3 );`


## What is available with the Current Logged in User?

- Author First Name `prc.oAuthor.getFirstName()`
- Author LastName `prc.oAuthor.getLastName()`
- Author Email `prc.oAuthor.getEmail()`
- Author Username `prc.oAuthor.getUserame()`
- Author Created Date `prc.oAuthor.getCreatedDate()`
- Author Modified Date `prc.oAuthor.getModifiedDate()`
- Author Last Login Date `prc.oAuthor.getLastLogin()`
- Author Biography `prc.oAuthor.getFirstName()`
- Author Preferences `prc.oAuthor.getFirstName()`
- Author Role `prc.oAuthor.getRole().getName()`

## Additional Author Content

`prc.oAuthor.entries()` returns an Array of entries / blog posts

`prc.oAuthor.getNumberOfEntries()` returns a count of entries / blog posts

`prc.oAuthor.pages()` returns an Array of pages

`prc.oAuthor.getNumberOfEntries()` returns a count of entries / blog posts

`prc.oAuthor.getPermissions()` returns an Array of A La Carte Permissions

`prc.oAuthor.getPermissionsList()` returns an string containing a list of A La Carte Permissions














































