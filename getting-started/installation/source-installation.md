# Source Installation

In this section you will install ContentBox by using the **source** download option and deploy it to your favorite ColdFusion (CFML) engine of choice.

## Step 1: Download Source

The first step is for you to download the ContentBox installer ([https://www.ortussolutions.com/products/contentbox](http://www.ortussolutions.com/products/contentbox)) or you can use the command below:

```
# stable
wget https://www.ortussolutions.com/parent/download/contentbox?type=installer

# bleeding edge
wget https://www.ortussolutions.com/parent/download/contentbox?type=installer&version=be
```

Expand the archive into your webroot or a subfolder of your favorite CFML engine.

```
unzip contentbox_{version}.zip
```

{% hint style="warning" %}
**Caution:** Due to a bug in some CFML engines, DO NOT use the subfolder name `contentbox`, use `cbox` or `site` or whatever you like if you will be deployed under a subfolder.
{% endhint %}

Please also note that you can also download two more types:

1. **Module** - The ContentBox module so you can deploy into any existing ColdBox application

```
wget https://www.ortussolutions.com/parent/download/contentbox
```

1. **Site** - A pre-configured site like the installer but with no DSN Creator and ContentBox Installer

```
wget https://www.ortussolutions.com/parent/download/contentbox?type=site
```

## Step 2: Create Your Database

Now that the source is deployed in your webserver, it is time to create your database in your favorite DBMS engine. ContentBox is built with Hibernate ORM technology, so in theory, it should work in all major database systems. You can even use an embedded database like Apache or Hypersonic.

Make sure your database supports utf-8 or utf-16 character sets if you will be using multi-lingual or localization support.

## Step 3: Create A Datasource

![](../../images/datasource\_wizard.png)

You can now visit your application and will be presented with our data source wizard. You can either use our data source wizard or you can create the data source yourself manually in the CFML administrator.

### Datasource Creation Wizard

The data source wizard requires your CFML Admin Password, or your ( Railo/Lucee ) Web Context Password to create the data source.

Note: Depending on your CFML Engine Install, the Web Context Password might not be set. To use the Datasource Creator Wizard, you will be required to access the admin, set the password, then continue the installation.

![](../../images/step2.png)

## Step 4: Run ContentBox Installer

![](../../images/installer\_wizard.png)

That's it! We are now ready to run the ContentBox installer wizard. ContentBox will automagically create all the necessary database tables, indexes, and constraints for you. After it does this, it will present you with our ContentBox installer, where you will fill in:

* Administrator Account
* Site Information
* Notification Emails
* Email Information
* URL Rewriting
* Enjoy your ContentBox installation!

{% hint style="warning" %}
**Caution:** We recommend that after you install ContentBox that you remove the installer and data source wizard modules from the disk. You can do so manually or via the Dashboard once you log in. `{Root}/modules/contentbox-installer and {Root}/modules/contentbox-dsncreator`
{% endhint %}
