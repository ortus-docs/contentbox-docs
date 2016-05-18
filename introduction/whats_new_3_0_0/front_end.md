# Front End

### New ContentBox Theme
We have a new official UI theme that you will come to love.  It has over 10 different skins and configurations that will give you a plethora of configuration patterns for your site.  It is based on bower and grunt assets, so you can easily fork and customize.

![](/images/themes_structure.png)


### RESTFul Response Formats
The UI module now allows you to be able to export your pages, or blog entries in many response formats:

* json
* XML
* PDF
* word

The JSON and XML support means you can now build alternative UI modules based on modern JavaScript or other language frameworks.  This is a game changer for ContentBox as it will provide you with the ability to export any piece of content or blog in a tranportable RESTFul format.

```js
{
    "HTMLDescription": "",
    "HTMLKeywords": "",
    "allowComments": false,
    "categories": [
        {
            "category": "coldbox",
            "slug": "coldbox"
        }
    ],
    "children": [],
    "comments": [],
    "content": "<p>Support services</p>\r\n\r\n<p><p>Sorry, no related content was found.</p></p>\r\n\r\n<p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Ut odio. Nam sed est. Nam a risus et est iaculis adipiscing. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Integer ut justo. In tincidunt viverra nisl. Donec dictum malesuada magna. Curabitur id nibh auctor tellus adipiscing pharetra. Fusce vel justo non orci semper feugiat. Cras eu leo at purus ultrices tristique.</p>\r\n\r\n<p>Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.</p>\r\n\r\n<p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Ut odio. Nam sed est. Nam a risus et est iaculis adipiscing. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Integer ut justo. In tincidunt viverra nisl. Donec dictum malesuada magna. Curabitur id nibh auctor tellus adipiscing pharetra. Fusce vel justo non orci semper feugiat. Cras eu leo at purus ultrices tristique.</p>\r\n\r\n<p>Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.</p>\r\n\r\n<p>&nbsp;</p>\r\n",
    "contentID": 147,
    "contentType": "Page",
    "createdDate": "20 Jul 2013 03:38 PM",
    "customfields": [],
    "excerpt": "",
    "expireDate": "N/A",
    "featuredImageURL": "",
    "isDeleted": false,
    "modifiedDate": "May 3, 2016 4:23:25 PM CDT",
    "publishedDate": "20 Jul 2013 03:38 PM",
    "relatedcontent": [],
    "showInMenu": true,
    "slug": "support",
    "title": "support"
}
```


### New Rendering Cache Headers
A new header will be sent to the browser if a content page is cached: `x-contentbox-cached-content`. This can provide proxies or cache engines the ability to tell when a page is cached by ContentBox.