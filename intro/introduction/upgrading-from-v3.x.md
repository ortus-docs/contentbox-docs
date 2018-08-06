# Upgrading From v3.x

ContentBox v4.x is a **major** version update and will require the following instructions to update your v3.x installations.  Please follow this guide or contact us at &lt;info@ortussolutions.com&gt; so we can assist you during your upgrade process.

{% hint style="danger" %}
We highly encourage you to start your upgrade process from version 3.7.1 and not from anything below. So please refer to the previous version upgrade guides to make sure you are on version 3.71.
{% endhint %}

## Requirements

All Upgrades to ContentBox should be done with the assistance of [CommandBox CLI.](https://www.ortussolutions.com/products/commandbox) So make sure you have CommandBox installed.

## Backups

Please make sure you backup your source code and your database.  We are not responsible for broken installations.

## Upgrade Process

There are two parts to the upgrade process:

1. Update the source code using our updater recipe
2. Run the database migrations via the ContentBox administrator panel

### 1. Source Code Updater

Please make sure your CFML engine has been completely stopped.

#### \*nix/Mac

If you are in a linux or mac environment you can execute the recipe using the following shell commands from the root directory of your application.

```bash
# Download recipe
curl -o updater.boxr http://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/4.1.0/updater.boxr
# Execute recipe
box updater.boxr
```

#### Windows

If you are in windows, download the following recipe:  

[http://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/4.1.0/updater.boxr](http://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/4.1.0/updater.boxr) 

and place it in the root of your project.  Then issue the following CommandBox shell command to execute it.

```bash
box updater.boxr
```

That's it! The updater will take care of upgrading your 3.x source code to the latest 4.x source code.

### 2. Database Updater

Once your recipe finalizes, startup the CFML server and go to the ContentBox administrator \(`localhost:port/cbadmin`\) and navigate to the **System &gt; Updates** section.  Then click on the **Download Update** tab and paste the following updater URL:

[https://downloads.ortussolutions.com/ortussolutions/contentbox/4.1.0/contentbox-patch-db-4.1.0.zip](http://downloads.ortussolutions.com.s3.amazonaws.com/ortussolutions/contentbox/4.1.0/contentbox-patch-db-4.1.0.zip)

This will download the database updater and run it.  Once finalized, your installation is ready to rock!



