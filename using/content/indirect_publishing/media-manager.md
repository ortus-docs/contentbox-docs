# Media Manager

The Media manager is a WEB UI to be able to interact with your Media. You can access the Media Manager from the Admin Menu under Content, in addition to buttons within different Content Editors.

![Media Manager is listing under Content in the ContentBox CMS Admin](/assets/cbcms_mediamanager_menu.jpg)

The Media Manager has many options, but by default will look like the image below.

![Media Manager U View](/assets/cbcms_mediamanager_view1.jpg)

## Icons

![Media Manager Icon - Refresh Listing](/assets/cbcms_mediamanager_icon_refresh.jpg) Refresh Listing - Refreshes the current folder location

![Media Manager Icon - Go Home](/assets/cbcms_mediamanager_icon_home.jpg) Go Home - Return to the Home ( Root ) directory of the current library

![Media Manager Icon - Create Folder](/assets/cbcms_mediamanager_icon_create.jpg) Create Folder - Create a new folder in the current location

![Media Manager Icon - Rename](/assets/cbcms_mediamanager_icon_rename.jpg) Rename - Rename the currently selected File or Folder

![Media Manager Icon - Delete](/assets/cbcms_mediamanager_icon_delete.jpg) Delete - Delete the currently selected File or Folder

![Media Manager Icon - Upload](/assets/cbcms_mediamanager_icon_upload.jpg) Upload - Brings up the Upload form, to allow you to select a file to upload. Remember, Media Manager also allows HTML5 styled uploading, so you can drag file(s) into the media manager to upload them. Folder Uploading is not supported in this version, but will be added in an upcoming update.

![Media Manager Icon - Download](/assets/cbcms_mediamanager_icon_download.jpg) Download - Download the currently selected file. 

![Media Manager Icon - Quick View](/assets/cbcms_mediamanager_icon_quickview.jpg) Quick View - Preview the currently selected image in a modal window. Only supports Images.

![Media Manager Icon - File Listing](/assets/cbcms_mediamanager_icon_filelisting.jpg) File Listing - This shows the current folder in File Listing / Details view. This is the default listing style, shown in the screenshot above.

![Media Manager Icon - Grid Listing](/assets/cbcms_mediamanager_icon_gridlisting.jpg) Grid Listing - This shows the current folder in Grid Listing / Thumbnails view. This is a great way to preview directories of images. This view can seen in the screenshot below.

![Media Manager showing files in Grid Listing / Thumbnail style](/assets/cbcms_mediamanager_view2.jpg)

## File / Folder Context Menus

Context Menus ( otherwise known as right click menus ) are available for Files and Folders. Files have the following context menu items

![Media Manager - Context Menu for Files](/assets/cbcms_mediamanager_file_contextmenu.jpg)

Folders have the following context menu items

![Media Manager - Context Menu for Folders](/assets/cbcms_mediamanager_folder_contextmenu.jpg)

## Status Bar

The Status Bar has useful quick view information.

- Full file path breadcrumbs
- Filename, File Size, and last modified date-time stamp.

![Media Manager Status Bar](/assets/cbcms_mediamanager_statusbar.jpg)

## Libraries

Next to the Module Name - 'Media Manager' you will see `Content` in a yellow label. That is the current Library you are looking at. There are several Libraries available for you to choose. To switch library, click the drop down select labelled `Switch Library` in the top right like the image below.

![The drop down menu inside of the Media Manager to switch from one library to another](/assets/cbcms_mediamanager_switch.jpg)

Depending on your security settings, you will be able to directly browse, upload, rename and delete filtes from the Content, Modules, Updates and Widgets locations.

# Media Manager Settings

There are a lot of configurable options for the Media Manager, to fit in with your use cases.  Media Manager Settings are found in the administrator under `System > Settings > Media Manager`

## Directory Root:

The relative path or ColdFusion mapping in your server that will be the expanded root of your media manager. The default is `modules/contentbox/content`. This is restricted to relative paths to ensure the user of the Media Manager cannot access content outside of the web root. If you would like to use a folder outside of the web root, please create a coldfusion mapping ( and web accessible mapping if required by the Media Provider ) to ensure the folder is relative to the web root.

## Media Providers

Media providers are used to deliver your media files securely and with greater flexibility as you can place your entire media root outside of the webroot.

### CF Content Media Provider ( default )

This provider uses the ColdFusion cfcontent tag to deliver and stream files securely to the user. This uses a ContentBox route `__media`, that translates the path into a cfcontent call and delivers the content.

### Forward Media Provider

This provider will forward to the real physical location in the server for the media path requested via the internal servlet page context, so no real media path URL will be shown to the user. Use only if the media root is web accessible and a relative web root path, so double check your media root. 

### Relocation Media Provider

This provider will relocate to the real physical location in the server for the media path requested. Use only if the media root is web accessible, so double check your media root. 

## Provider Caching Headers:

If enabled, the media provider system will issue caching headers for all assets. You can use the `cbcache=true` URL param to issue no caching headers on any asset. 

Default: `true`

## FileBrowser Options

![Media Manager Settings - FileBrowser Options](/assets/cbcms_mediamanager_settings_bottom.jpg)

File Browser options includes a series of user options ( Yes / No ):

- Allow Creation
- Allow Deletes
- Allow Downloads
- Allow Uploads

### Accepted Upload File Mime Types

### HTML5 Uploads

**Size Limit** - Maximum size of the file upload in mb - defaults to 100mb

**Max Similtaneous Uploads** - Number of uploads allowed at the same time - defaults to 25

### Quick View Image Width ( Pixels )

When using the Quick View for images, images are shown in a modal window, with a maximum width defined by this setting. 




