# Upgrading From v5.x

ContentBox v6.x is a **major** version update and will require the following instructions to update your v5.x installations. Please follow this guide or contact us at [info@ortussolutions.com](mailto:info@ortussolutions.com) so we can assist you during your upgrade process.

{% hint style="danger" %}
If you are in version 4.x then you will need to upgrade to version 5.x before upgrading to the 6.x series&#x20;
{% endhint %}

## 1. Requirements

All Upgrades to ContentBox should be done with the assistance of [CommandBox CLI.](https://www.ortussolutions.com/products/commandbox) So ensure you have CommandBox installed on the server/machine you will be upgrading.

### Upgrade System Dependencies

Once you have CommandBox installed, let's make sure we have some global dependencies installed so CommandBox can work with ContentBox automated upgrades:

```bash
# install env controls and db migrations
box install commandbox-dotenv,commandbox-migrations --force
```

This will install the [environment](https://forgebox.io/view/commandbox-dotenv) module and the [database migrations](https://forgebox.io/view/commandbox-migrations) module that will be used to provide upgrades in the future.  This is only done once. ContentBox 5 already ships with these dependencies once you install it.

## 2. Backups

Please make sure you backup your source code and your database. We are not liable for broken installations.

{% hint style="danger" %}
Make sure the database, the tables and columns are using `utf8mb4` if you are using MySQLx
{% endhint %}

## 3. MySQL UTF8mb4

If you are using MySQL you will need to make sure your database and your tables are all using the following character set: `utf8mb4` and NOT just `utf8`.  ContentBox 5 requires the charset to be `utf8mb4`.&#x20;

We also suggest you use the `utf8mb4_general_ci` collation for your database, tables and columns as well.

## 4. Run the Updater

We have prepared a CommandBox task to upgrade your installation in one easy execution.  This will upgrade your files and run the database migrations for you.

### \*nix/Mac

If you are in a Linux or Mac environment, you can execute the task using the following shell commands from the root directory of your application.

```bash
# Download the updater
curl -o Updater.cfc https://raw.githubusercontent.com/Ortus-Solutions/ContentBox/master/build/patches/6.0.0/Updater.cfc
# Execute the task
box task run Updater.cfc
# Clean it up
rm Updater.cfc
```

### Windows

If you are in Windows, download the following task:

[https://raw.githubusercontent.com/Ortus-Solutions/ContentBox/master/build/patches/6.0.0/Updater.cfc](https://raw.githubusercontent.com/Ortus-Solutions/ContentBox/master/build/patches/6.0.0/Updater.cfc)

and place it at the root of your project. Then, issue the following CommandBox shell command to execute it.

```bash
# Run the task
box task run Updater.cfc
# Clean it up
rm Updater.cfc
```

## 5. Final Steps

The updater will update your installation and run the migration scripts. However, it will also override the following files:

```
Application.cfc
readme.md
config/CacheBox.cfc
config/Coldbox.cfc
```

**It will create `.bak` files for the originals so you can manually merge in any changes you had before.**&#x20;

Once you do, go ahead and start up the engines! You are upgraded!

### Optional Steps

If you have developed themes, modules, models, or any type of extension based on ContentBox 5, you will most likely have to update your code to match the new interfaces, methods, and approaches.  Especially since ContentBox 6 runs on ColdBox 7.



