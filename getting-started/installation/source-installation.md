---
description: Deploy ContentBox into any Adobe or Lucee CFML Engine
---

# Source Installation

In this section you will deploy ContentBox so it can run on any running Adobe or Lucee CFML engine. The first step is to use CommandBox and our `contentbox-cli` package so we can install and configure ContentBox for usage in any CFML Engine. We won't be using CommandBox as our server, just as a package manager and CLI.

## Install CommandBox

​

![CommandBox CLI](https://files.gitbook.com/v0/b/gitbook-legacy-files/o/assets%2F-LA-UVvYQ9YKIVXFz01w%2F-LA-UcIjNIclM\_mn00Gl%2F-LA-UmLcoyZgINuAvL99%2FCommandBoxLogo.png?generation=1523647992482088\&alt=media)

​[CommandBox](http://www.ortussolutions.com/products/commandbox) is a ColdFusion (CFML) Command Line Interface (CLI), REPL, Package Manager and Embedded Server. We will leverage the CLI in CommandBox to install, deploy and configure ContentBox.

### Requirements <a href="#requirements" id="requirements"></a>

* MacOS, Windows or Linux
* JDK 8+
* A clean, empty directory on your machine

### Download CommandBox

You can download CommandBox from the official site: [http://www.ortussolutions.com/products/commandbox#download](http://www.ortussolutions.com/products/commandbox#download) and install it in your preferred Operating System (Windows, Mac, Unix).

{% embed url="https://commandbox.ortusbooks.com/setup/installation" %}
Installation Instructions
{% endembed %}

### Starting CommandBox

Once you download and expand CommandBox you will have the `box.exe` or `box` binary, which you can place in your Windows Path or \*Unix `/usr/bin` folder to have it available system-wide. Then open the binary and CommandBox will unpack itself your user's directory: `{User}/.CommandBox`. This happens only once and the next thing you know, you are in the CommandBox interactive shell!

![box shell](<../../.gitbook/assets/image (8).png>)

We will be able to execute a-la-carte commands from our command line or go into the interactive shell for multiple commands. We recommend the interactive shell as it is faster and can remain open in your project root.

## Install ContentBox-CLI

We can now install the `contentbox-cli` package:

```bash
install contentbox-cli
```

Once installed you can always run `contentbox help` to get the list of available commands and help information.

## Creating Your Database

Create a database in your RDBMS of choice. Make sure you note the name of the database, the connection details and the credentials for it.

{% hint style="danger" %}
If you are using MySQL, make sure you use `utf8mb4` for your database collation.
{% endhint %}

## Creating Your Datasource

Now go to your CFML engine administrator and register the `contentbox` datasource that points to the database you just created.

#### Resources

* [https://docs.lucee.org/guides/cookbooks/datasource-define-datasource.html](https://docs.lucee.org/guides/cookbooks/datasource-define-datasource.html)
* [https://helpx.adobe.com/coldfusion/configuring-administering/data-source-management-for-coldfusion.html](https://helpx.adobe.com/coldfusion/configuring-administering/data-source-management-for-coldfusion.html)

{% hint style="success" %}
You can use _ANY_ name for the datasource, but we will use `contentbox` for ease of use.
{% endhint %}

## Creating A ContentBox Site

Now that we have our CLI installed, database and datasource created, go or create a new directory where we will create our site. Most likely this folder will be your web root in your CFML engine installation or a sub-folder within that web root. Let's assume it's the web root of your current CFML Engine installation.

```
# Create a new directory and go into it.
mkdir mysite --cd
# Run the installer wizard
contentbox install-wizard
```

The wizard will take you by the hand and ask you all the relevant questions about your installation:

1. Name of your site
2. Which CFML Engine you will be running ContentBox on (Lucee5, Adobe 2018+)
3. Password for the ColdBox HMVC Reinits
4. Database of choice (MySQL5+, MSSQL, PostgreSQL, Oracle)
5. Database credentials
6. Development or production site
7. Latest ContentBox version, specific or `be` bleeding edge
8. **Deploy a CommandBox server or not. This should be false, as we are only deploying our code to the CFML engine we have already installed.**

Confirm your settings and the installer will configure the entire site for you including ORM dialects, environment variables and much much more.

{% hint style="success" %}
**Tip:** You can use the \`install --help\` command and see how you can install ContentBox in an automated fashion with no user-interaction.
{% endhint %}

## Web Installer

Now that we have installed ContentBox on disk and configured your CLI to connect to your database for delivering database migrations, we can finalize the installation via the web installer. Now open the installer by navigating to the root of the project. Let's assume you are running your CFML engine on port 8500:

```
http://localhost:8500
```

![](../../images/installer\_wizard.png)

ContentBox will automagically create all the necessary database tables, indexes, and constraints for you. After it does this, it will present you with our ContentBox installer, where you will fill in:

* Administrator Account
* Site Information
* Notification Emails
* Email Information
* URL Rewriting
* Enjoy your ContentBox installation!

{% hint style="warning" %}
**Caution:** We recommend that after you install ContentBox that you remove the installer and data source wizard modules from the disk. You can do so manually or via the Dashboard once you log in. `{Root}/modules/contentbox-installer and {Root}/modules/contentbox-dsncreator`
{% endhint %}
