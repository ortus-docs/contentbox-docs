---
description: The easiest way to install and run ContentBox CMS
---

# \*CommandBox Installation

![CommandBox CLI](../../.gitbook/assets/CommandBoxLogo.png)

[CommandBox](http://www.ortussolutions.com/products/commandbox) is a ColdFusion (CFML) Command Line Interface (CLI), REPL, Package Manager and Embedded Server. We will leverage the CLI in CommandBox to install, deploy and configure ContentBox.

### Requirements

* MacOS, Windows, or Linux
* JDK 11+
* A clean, empty directory on your machine

## Download CommandBox

You can download CommandBox from the official site: [http://www.ortussolutions.com/products/commandbox#download](http://www.ortussolutions.com/products/commandbox#download) and install it in your preferred Operating System (Windows, Mac, Unix).

{% embed url="https://commandbox.ortusbooks.com/setup/installation" %}
Installation Instructions
{% endembed %}

### Starting CommandBox

Once you download and expand CommandBox, you will have the `box.exe` or `box` binary, which you can place in your Windows Path or \*Unix `/usr/bin` folder to have it available system-wide. Then open the binary, and CommandBox will unpack itself in your user's directory: `{User}/.CommandBox`. This happens only once; the next thing you know, you are in the CommandBox interactive shell!

![box shell](<../../.gitbook/assets/image (8).png>)

We can execute a-la-carte commands from our command line or go into the interactive shell for multiple commands. We recommend the faster interactive shell, which can remain open in your project root.

## Install ContentBox-CLI

The first step in our adventure is to install the `contentbox-cli` package that will handle the installation, scaffolding, and management of ContentBox sites.

```bash
install contentbox-cli
```

Once installed, you can always run `contentbox help` to get the list of available commands and help information.

## Creating Your Database

Create a database in your RDBMS of choice. Ensure you note the name of the database, the connection details, and its credentials. You will need them in the next step.

{% hint style="danger" %}
If you are using MySQL, make sure you use `utf8mb4` for your database collation.
{% endhint %}

## Creating A ContentBox Site

Now that we have our CLI installed create a new directory where we will create our site.

```
# Create a new directory and go into it.
mkdir mysite --cd
# Run the installer wizard
contentbox install-wizard
```

The wizard will take you by the hand and ask you all the relevant questions about your installation:

1. Name of your site
2. Which CFML Engine you want to run it on (Lucee5, Adobe 2018+)
3. Password of the CFML engine administrator
4. Password for the ColdBox HMVC Reinits
5. Database of choice (MySQL5+, MSSQL, PostgreSQL, Oracle)
6. Database credentials
7. Development or production site
8. Latest ContentBox version, specific or `be` bleeding edge

Confirm your settings, and the installer will configure the entire site, including ORM dialects, environment variables, etc. The installer will also connect to your database and run the creation migrations to seed the database.

It can optionally start your server of choice.

{% hint style="success" %}
**Tip:** You can use the \`install --help\` command and see how to install ContentBox in an automated fashion without user interaction.
{% endhint %}

{% hint style="info" %}
The installer will create a `.env, .cfconfig.json` in the root so you can further tweak those files if needed.
{% endhint %}

### Web Installer

![](<../../.gitbook/assets/image (9).png>)

The web installer will then add your first administrator user, email configurations, and production and development site in one box. Once you follow the wizard, ContentBox is up and running! Enjoy!

{% hint style="info" %}
The admin URL will be `http://localhost:{port}/cbadmin`
{% endhint %}

### Starting & Stopping

You can use the CommandBox commands to interact with the embedded server:

* `server stop` to stop the server
* `server start` to start the server
* `server restart` to restart the server
* `server log` to view the log files
* `server help` to get help on your server commands

### What's Next

You now have a fully functional ContentBox installation with two sites: **development** and **production**. You can now start creating your content, themes, modules, and more.
