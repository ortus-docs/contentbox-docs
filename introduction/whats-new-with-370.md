# What's New in 3.7.0

This release has a major focus on security, authentication, testing and automatino.  Below you can find the major changes and updates for this release and our full release notes.

## Security Updates

### Two Factor Authentication

![](/assets/3.7_twofactor_challenge.png)

This is one of our biggest features for ContentBox is our two factor authentication framework.  That's right, we built a two factor module framework that will allow you to build or use any two factor or multi-factor authentication mechanism.  We have included one in the core which is Email verification.

![](/assets/3.7_twofactor_uml.png)

#### Global Settings

An admin can force two factor authentication for all users in the system and even provided a trusted device registry so  ContentBox can track their devices and challenge only after a few days.

![](/assets/3.7_twofactor_settings.png)


#### User Settings

The user can also setup two factor authentication for their account if so desired.

![](/assets/3.7_twofactor_user.png)

### Permission Groups

We have introduced the ability to create and organize permissions not only in roles but in our new permission groups. This will allow you to create more complex and robust permission schemas and be able to assign multiple permission groups to users. The entire permissions tab for authors has been revamped to allow you better visualization of rules and permissions.

![](/assets/3.7_permission_groups.png)

### Improved Rate Limiting

The rate limiting module has been revamped to help with Denial of Service attacks or even just pesky scrapers. You can now configure more options for fine-tuning including relocation URLs, custom messages and improved logging.


### Password Enhancements

There have been many updates on both the UI and the security of user passwords.  

#### Password Meter
We have introduced the concept of a visual password meter, which can guide users when changing, resetting or setting passwords:

![](/assets/3.7_password_meter.png)

#### Password Length Options

You can now also as an admin decide on the minimum length of user passwords.

![](/assets/3.7_password_options.png)

#### Password Reset Options

![](/assets/3.7_password_reset_ui.png)

As an administrator, you can now reset user passwords a-la-carte or for every single user in the system.  This will issue a notification to the user with instructions on resetting their system password.  User password reset workflow has now been improved with our new password reset screens instead of bulky double email validation mechanisms.

![](/assets/3.7_password_reset_bulk.png)

![](/assets/3.7_password_reset_notification.png)

#### New Interception Events

Here are the new interception events you can listen on for password reset workflows:

* `cbadmin_onGlobalPasswordReset`
* `cbadmin_onPasswordReset`
* `cbadmin_onPasswordReset`
* `cbadmin_onInvalidPasswordReset`




## Author Updates


### New Author Wizard

We have introduced a new approach to creating authors in ContentBox. You will now be presented with the new author wizard which will allow you to pre-fill author details in a secure manner.  A notification will be sent to the new author's email address with a password setup token so they can secure their account.  

### Improved Author Listings

The author listings have been improved with tons of new filters, reporting and even sorting options.  Go admin like a mad man!

![](/assets/3.7_user_listing.png)


### Improved Author Snapshot

The Author Profile Snapshot has been updated to include a better UI, better visualization and a new action toolbar for direct Author actions and Author exporting.

![](/assets/3.7_user_snapshot.png)


## Content Updates


### Markdown Support++

We introduced markdown support for all content in many versions before.  This update includes a brand new markdown engine with table support, code syntax highlighting and much more.  We also made several settings and author specific details available as markdown content.  In other words, viva markdown!


### Markdown Editors

We have also updated our markdown UI editor and it can be used everywhere in the admin were markdown is allowed.

### Publishing Workflows

We have added a new two-step workflow for publishing any piece of content.  This will allow you better visibility when working with drafts or live content.  The new flow will also assist users that do not have any publishing capabilities.

![](/assets/3.7_content_publishing.png)



### Content Hierarchy Navigation History

![](/assets/3.7_hierarchy_history.png)

We have improved the navigation of the content store and the sitemap by taping into the browser history API and providing history support for hierarchy navigation.  Never again loose your place in the hierarchy.

## Full Release Notes

### Bugs

* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-882'>CONTENTBOX-882</a>] -When cloning blog posts ( possibly pages too ) the code format is lost
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-891'>CONTENTBOX-891</a>] -Trying to delete a single user with checked boxes fails
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-907'>CONTENTBOX-907</a>] -&quot;notify me&quot; checkbox is forgotten on comment submission failure
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-913'>CONTENTBOX-913</a>] -Fix issue of installer failing when rewrites turned off
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-914'>CONTENTBOX-914</a>] -Adobe Incompatibilities for sidebar
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-915'>CONTENTBOX-915</a>] -Render Markdown correctly on auto updates description
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-925'>CONTENTBOX-925</a>] -Installer issues with new radio buttons
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-936'>CONTENTBOX-936</a>] -Change $forgebox.load to GET request instead of POST for pagination to work
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-943'>CONTENTBOX-943</a>] -MSSQL Regression due to Category Formulas
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-950'>CONTENTBOX-950</a>] -Adobe 2016 Syntax Error
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-953'>CONTENTBOX-953</a>] -Check Permissions fails on User with a null Role

### New Feature

* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-647'>CONTENTBOX-647</a>] - Add a password meter on the installer and user profile page with key enforcements
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-875'>CONTENTBOX-875</a>] - Add content hierarchy history as URL doesn&#39;t reflect navigation into content hierarchy
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-916'>CONTENTBOX-916</a>] - User Permissions Groups
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-917'>CONTENTBOX-917</a>] - New setting for rate limiter to choose either a message or a redirection URL
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-918'>CONTENTBOX-918</a>] - New setting to control if blocked attempts are logged or not
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-920'>CONTENTBOX-920</a>] - New author quick report: numberOfContentStore
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-921'>CONTENTBOX-921</a>] - Creation of new author toolbar for actions in snapshot location
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-922'>CONTENTBOX-922</a>] - New export capabilities from new author toolbar
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-926'>CONTENTBOX-926</a>] - Ability to showcase raw content in history panel
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-927'>CONTENTBOX-927</a>] - Ability for a author password to be reset by an admin
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-928'>CONTENTBOX-928</a>] - New reset interception points: cbadmin_onGlobalPasswordReset, cbadmin_onPasswordReset, &quot;cbadmin_onPasswordReset&quot;, &quot;cbadmin_onInvalidPasswordReset&quot;
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-929'>CONTENTBOX-929</a>] - Ability for admin to reset all author passwords
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-930'>CONTENTBOX-930</a>] - When resetting a password and you have a previous password, they should not be the same
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-932'>CONTENTBOX-932</a>] - New publishing details workflow
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-933'>CONTENTBOX-933</a>] - Ability for authors to be sorted in the listing by different common orderings
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-938'>CONTENTBOX-938</a>] - Make password length for authors a customizable rule
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-939'>CONTENTBOX-939</a>] - Update all range settings to new slider UI
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-940'>CONTENTBOX-940</a>] - New author creation wizard
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-944'>CONTENTBOX-944</a>] - Enable markdown for site maintenance
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-945'>CONTENTBOX-945</a>] - Enable MD Editors for settings for better usability
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-946'>CONTENTBOX-946</a>] - Two Factor Auth Framework and Authentication
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-948'>CONTENTBOX-948</a>] - Update markdown processor to latest version
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-949'>CONTENTBOX-949</a>] - Create server.json for site and installers, so we can have rewrites and nice logos
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-951'>CONTENTBOX-951</a>] - New preFlight checks for settings to avoid setting upgrade issues and better encapsulation
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-954'>CONTENTBOX-954</a>] - Email two factor authentication provider
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-955'>CONTENTBOX-955</a>] - Refactor captcha out of the core and into an addon module.
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-957'>CONTENTBOX-957</a>] - Security services now rely on the CacheStorages instead of session to provide distribution out of the box if necessary via CacheBox
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-958'>CONTENTBOX-958</a>] - Ability to make the datasource portable for container deployments via config/runtime.properties.cfm convention
        
### ImprovementS

* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-568'>CONTENTBOX-568</a>] - Allow user to choose new password on reset
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-725'>CONTENTBOX-725</a>] - User Management: Allows duplicate emails
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-919'>CONTENTBOX-919</a>] - Author snapshot updates
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-923'>CONTENTBOX-923</a>] - Added auto height to select boxes
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-924'>CONTENTBOX-924</a>] - Page Publishing Permissions
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-931'>CONTENTBOX-931</a>] - Content cloning needs to clone all new properties
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-934'>CONTENTBOX-934</a>] - Added pagination to ForgeBox installer
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-935'>CONTENTBOX-935</a>] - Don&#39;t show data snapshot donut charts if there is no data
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-937'>CONTENTBOX-937</a>] - Make admin bar responsive
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-941'>CONTENTBOX-941</a>] - Cache installer detection query to improve performance
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-942'>CONTENTBOX-942</a>] - Global HTML not flushing settings cache
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-952'>CONTENTBOX-952</a>] - Refactor formulas for category reports and optimized for better performance
* [<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-956'>CONTENTBOX-956</a>] - Deprecated ColdBox fileUtils to internal Utility
