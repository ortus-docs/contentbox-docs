# Static Site Generator

![](/images/static_site_generator.png)

ContentBox 3.1 now supports the generation of static sites from your content and even your blog. This is a great addition to ContentBox as now you can produce static versions and workflows, deploy to CDN networks, secure your content and much more.  Once you click on the **Start Generation** button, ContentBox will go over your entire site and produce a static archive for you in the associated theme.  It will also announce two interception points for you during the process:

* `cbadmin_preStaticSiteExport` : Receives all the export `options` in the intercept data so you can alter the export behavior.
* `cbadmin_postStaticSiteExport` : Receives all the export `options` and also a `results` structure with the following keys: `exportLog:builder, exportDirectory, exportArchive`.  This is a great way to listen for the export and send to S3 for archiving, etc.

> **Warning** Dynamic elements like commenting, searching, etc must require a JavaScript implementation.  So make sure you have a static export strategy in place.

