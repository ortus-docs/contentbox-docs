---
description: >-
  Let’s get started with Pages. Inside pages on your right panel, you see that
  we have set up filters to filter out the view of the pages. You also have
  Global Actions: Delete Selected, Draft Selected,
---

# Pages

### Page Editor

Inside Pages click Create Page and the Page Editor will open. Name your page by giving it a Title and ContentBox will give you the permalink for the page. By default, the Page Editor uses CKeditor for a WYSIWYG editor. ContentBox also offers different other editors that are available in your installation.

> **Hint** Remember that editors are programmable so any module developer can actually register new editors in your system.

The Page editor has markup support \[button right beside Editor Button\]. HTML markup is currently supported by default.

ContentBox’s implementation of CKEditor comes with support for a number of plugins, including:

* Insert code snippets \[page icon beside \(right\) to World\],
* iframe \[the world\]
* Youtube or embedded media
* Insert Lorem Ipsum Dolor \[T\] to create content.
* Contentbox Widgets

On the right panel, you have the Paging Details.

### **Publishing**

ContentBox allows you to publish the page on a specific date and time, as well as set an expiration date to expire the content on any schedule you choose. Additionally, commit messages can be included \(and even required\) via the change log, providing built-in version control of your content.

When saving content, a number of options are available:

* Save: Preserve a snapshot of the page as is, and continue editing
* Draft: Save a draft of the content and close Page Editor
* Publish: Publish the content to your site and close Page Editor

> **Hint** You can collapse the side bar and still have your Quick Edits controls right from the gear widget \[on the up right corner\].

### **Display Options**

Display options allow you to control many aspects related to how the page will be displayed within your site.

* Parent: Choosing a parent determines the hierarchy of the page within your site. For a “top-level” page, simply choose “No Parent”
* Layout: Specifies which layout the page will use. It can inherit default settings, or use a custom setting.
* Mobile Layout; Specifies what layout the page should use when viewed on a mobile device. Set to “None” to use the normal layout for the page.
* Show In Menus: Tells ContentBox whether this page should show up in automatic menu builders. If set to “No”, the page will not show in ContentBox menus.
* Menu Order: If your page is shown in menus, you can specify the order that this page should appear.

### **Modifiers**

Modifiers allow you to configure extra information about how your page will be accessed.

* Creator: Allows you to configure who is displayed as the author of this page. This is particularly useful if several editors have modified the page, but a specific author should be acknowledged
* Allow Comments: Allows you to configure if comments should be allowed for the page.
* Password Protection: Allows you to specify a particular password needed to access this content. This password can be shared with allowed visitors to provide secure access to specific pages.

### **Caching Settings**

ContentBox provides administrators with granular control over how content is cached within your site. Each page can be configured with the following caching settings:

* Cache Page Content: When set to “Yes”, the content of your page will be cached \(based on global or page-specific timeouts\)
* Cache Page Layout: When set to “Yes”, the content of your page, as well as the page layout HTML, will be cached \(based on global or page-specific timeouts\).
* Cache Timeout: Specifies how long \(in minutes\) the page should be cached. Set to “0” to use the global setting
* Idle Timeout: Specifies \(in minutes\) the idle timeout for your page. Set to “0” to use the global setting

### **Categories**

ContentBox allows you to provide additional organization of your content by setting one or more categories. You can choose from a list of already-configured categories, or even add new categories by adding a comma-separated list of categories in the “New Categories” text field.

### **HTML Attributes**

To help you configure your page for Search Engine Optimization \(SEO\), ContentBox provides the ability to specify HTML attributes for your page, including:

* Keywords: List of keywords that will be added to the `<head>` of your page
* Description: Text description of the content that will be added to the `<head>` of your page

At the bottom of the page, you have the Page Excerpts. You can create summaries of your Page Excerpts pages and then in your UI use them as you see fit.

### **Custom Fields**

One of the most powerful features of ContentBox content is the ability to attach metadata which can be done via Custom Fields. You can add as many Custom Fields as you like in the form of key-value pairs.

* A little Tale: How the metadata works

  The metadata is stored in the object itself and then you can retrieve it using the CBhelper when you are building themes, widgets, and events.

After you are done editing your page, you can go ahead and Publish it \[click publish\]. You will then be redirected to the Pages page where you will see that your page is published.

### Child Pages

In addition to specifying the parent of a page via the Page Editor, ContentBox also allows you to quickly create “child” pages via the main Page Manager.

On the Pages page, find a page you have already created and click Page Actions and select Create Child. Page actions button\) in the product row at the right edge; click ‘Create Child’\]. The Page Editor will open as normal. However, in this scenario, the new page will automatically be added to the selected parent page.

When you Publish your Child Page you will be redirected to the Parent Page Hierarchy View where you will be able to see all the Child Pages for the parent page. Just like with Pages, when you have created multiple Child Pages you have also complete control of manipulating how the Child Pages are rendered. So again, you can choose which Child Page should be last or first with simple drag and drop.

You can then continue to go back in your hierarchy and you can go back home \[click home button\]. The “+” sign beside a page indicates that that page has at least one Child Page.

> **Hint** Visit your page to see the changes you have made to your site. We recommend you Clear Content Caches.

### Global Actions

The Pages manager provides a number of global actions \[Global Action button; drop-down menu\/beside create page button\] that make managing your content easy. These actions include:

* Delete Selected: Will delete all selected pages \(via checkboxes\)
* Draft Selected: Will put all selected pages into draft status \(via checkboxes\)
* Publish Selected: Will publish all selected pages \(via checkboxes\)
* Import: If you have a ContentBox page export file \(.json\) from another site, you can use the Import option to quickly import the file and add the page to your site\*
* Export All: Allows you to export all your pages as either XML o_r JSON. This is particularly useful if you need to transfer content from one site to another._
* Show All: By default, ContentBox “pages” your view to provide the best performance. However, you can select “Show All” to view the full list of all the pages on your site.

