---
description: The ContentBox system requirements
---

# System Requirements

Let's get started with some system requirements for running ContentBox sites on all deployable options

## Java

You need Java 8+ to run ContentBox.

{% hint style="warning" %}
Java 17+ is not currently supported
{% endhint %}

## CommandBox

You will need  to have CommandBox for installation, upgrading and optionally for running your ContentBox sites. Please see our [CommandBox Installation](commandbox-installation.md) section.

## ColdFusion (CFML) Engine

ContentBox can be deployed to the following CFML Engines:

* Adobe ColdFusion
  * ~~_2016_~~_ (End of life is December 2021)_
  * 2018
  * 2021
* Lucee 5+

## Databases

Here are the supported databases for ContentBox:

* MySQL 5.7 (InnoDB ONLY!)
* MySQL 8+ (InnoDB ONLY!)
* Microsoft SQL Server 2012+
* HypersonicSQL
* Apache Derby
* PostgreSQL
* Oracle 11g+

If you have another database engine that needs ContentBox support, please let us know and we will be able to help you ([https://www.ortussolutions.com/contact](https://www.ortussolutions.com/contact)).

### Microsoft SQL Caveats

We have seen an issue where an error will be reported that `cbPermission` cannot be inserted. This is an issue where for some reason the JDBC driver will switch context and create the tables in the `master` schema and not the schema you chose. So please verify that the `master` schema has tables that start with `cb_*` and remove them and re-run the installer.

## URL Rewriting

ContentBox relies on Search Engine Safe (SES) URLs and URL Routing. The majority of CFML engines already allow for these types of URLs out of the box and ContentBox supports it out of the box. However, if you would like to use full URL rewriting (which we recommend, that's where the `index.cfm` is not showing in the URLs) you will need to use a web server rewriting tool and ContentBox will configure it for you.&#x20;

So before you install ContentBox make sure that you are using one of the supported rewriting engines show below:

* **CommandBox Server (Default)**
* Apache mod\_rewrite
* IIS 7 rewrite module
* Tuckey rewrite filter
* Nginx

The ContentBox installer will create rewrite files automatically for you for Apache, IIS7, and express editions. For Nginx or other rewrite engines, you will need to add the rewrites yourself and then manually modify the routing file.

### ContentBox Routing Full Rewrite Support

Edit `config/Router.cfc` and set `setFullRewrites` to `true`. That's it!

```javascript
function configure(){
    // Configuration
    setValidExtensions( 'xml,json,jsont,rss,html,htm,cfm,print,pdf,doc,txt' );
    // Process Full Rewrites then true, else false and an `index.cfm` will always be included in URLs
    setFullRewrites( true );
}
```

## File Permissions

ContentBox needs some files/folders to be writable at runtime.

### Installer

```
{Root}/Application.cfc
{Root}/config/ColdBox.cfc
{Root}/coldbox/system/aop/tmp
```

{% hint style="success" %}
You can remove the first two after installation.
{% endhint %}

### Engine

Here are the folders for the core engine to work accordingly

```
# Engine Operation (REQUIRED)
{Root}/coldbox/system/aop/tmp

# Media Manager
{Root}/modules_app/contentbox-custom/content
```

****
