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

### New Rendering Cache Headers
A new header will be sent to the browser if a content page is cached: `x-contentbox-cached-content`. This can provide proxies or cache engines the ability to tell when a page is cached by ContentBox.