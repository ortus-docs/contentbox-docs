# Upgrading From v4.x

ContentBox v5.x is a **major** version update and will require the following instructions to update your v4.x installations. Please follow this guide or contact us at [info@ortussolutions.com](mailto:info@ortussolutions.com) so we can assist you during your upgrade process.

{% hint style="danger" %}
If you are in version 3.x then you will need to upgrade to version 4.x before upgrading to the 5.x series [https://contentbox.ortusbooks.com/v/v4.x/intro/introduction/upgrading-from-v3.x](https://contentbox.ortusbooks.com/v/v4.x/intro/introduction/upgrading-from-v3.x)
{% endhint %}

## 1. Requirements

All Upgrades to ContentBox should be done with the assistance of [CommandBox CLI.](https://www.ortussolutions.com/products/commandbox) So make sure you have CommandBox installed in the server/machine you will be upgrading.

### Upgrade Dependencies

Once you have CommandBox installed, let's make sure we have some global dependencies installed so CommandBox can work with ContentBox automated upgrades:

```bash
# install env controls and db migrations
box install commandbox-dotenv,commandbox-migrations
```

This will install the [environment](https://forgebox.io/view/commandbox-dotenv) module and the [database migrations](https://forgebox.io/view/commandbox-migrations) module that will be used to provide upgrades in the future.

### Environment \(`.env`\)

The upgrade process and the database migrations rely on environment variables/secrets in order to connect to your database and migrate it.  Create an `.env` file in the root of the ContentBox installation and add in your database credentials according to your database below:

```text
######################################################
# ColdBox App Name and Environment
######################################################
APPNAME=ContentBox Modular CMS
ENVIRONMENT=development or staging or production

######################################################
# MySQL 5.7 DB Driver
######################################################
DB_CLASS=com.mysql.cj.jdbc.Driver
DB_DRIVER=MySQL
# Lucee Bundle Info: 5.1.40 IS THE ONLY ONE THAT WORKS FOR HIBERNATE
DB_BUNDLEVERSION=5.1.40
DB_BUNDLENAME=com.mysql.cj
# DB Location
DB_HOST=127.0.0.1
DB_PORT=3306
DB_CONNECTIONSTRING=jdbc:mysql://127.0.0.1:3306/contentbox?useSSL=false&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC&useLegacyDatetimeCode=true
# DB Credentials
DB_DATABASE=contentbox
DB_USER=root
DB_PASSWORD=mysql

######################################################
# MySQL 8 DB Driver
######################################################
#DB_CLASS=com.mysql.cj.jdbc.Driver
#DB_DRIVER=MySQL
#DB_BUNDLEVERSION=8.0.19
#DB_BUNDLENAME=com.mysql.cj
## DB Location
#DB_HOST=127.0.0.1
#DB_PORT=3306
#DB_CONNECTIONSTRING=jdbc:mysql://127.0.0.1:3306/contentbox?useSSL=false&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC&useLegacyDatetimeCode=true
## DB Credentials
#DB_DATABASE=contentbox
#DB_USER=root
#DB_PASSWORD=mysql

######################################################
# PostgreSQL DB Driver #
######################################################
#DB_CLASS=org.postgresql.Driver
#DB_DRIVER=PostgreSQL
## Lucee Bundle Info: 5.1.40 IS THE ONLY ONE THAT WORKS FOR HIBERNATE
#DB_BUNDLEVERSION=9.4.1212
#DB_BUNDLENAME=org.postgresql.jdbc42
## DB Location
#DB_HOST=127.0.0.1
#DB_PORT=5432
#DB_CONNECTIONSTRING=jdbc:postgresql://localhost:5432/contentbox
## DB Credentials
#DB_DATABASE=contentbox
#DB_USER=contentbox
#DB_PASSWORD=contentbox

######################################################
# JWT Information
######################################################
JWT_SECRET=

######################################################
# S3 Information
######################################################
S3_ACCESS_KEY=
S3_SECRET_KEY=
S3_REGION=us-east-1
S3_DOMAIN=amazonaws.com

```

{% hint style="success" %}
Please note that once you are on ContentBox 5 none of these steps will be necessary anymore.
{% endhint %}

{% hint style="danger" %}
Please note that this `.env` file should **NEVER** be in source control and **NEVER** be web accessible
{% endhint %}

Once your environment file is seeded open the `box.json` of the ContentBox 4 installation and add the following `cfmigrations` root element:

```javascript
"cfmigrations":{
    "schema":"${DB_DATABASE}",
    "connectionInfo":{
        "password":"${DB_PASSWORD}",
        "connectionString":"${DB_CONNECTIONSTRING}",
        "class":"${DB_CLASS}",
        "username":"${DB_USER}",
        "bundleName":"${DB_BUNDLENAME}",
        "bundleVersion":"${DB_BUNDLEVERSION}"
    },
    "defaultGrammar":"AutoDiscover@qb"
}
```

This will tell CommandBox migrations how to connect to your database in preparation for upgrades. Once this is done we can reload the CommandBox shell with the command `reload` and it's time to make sure migrations can connect to your database with the variables and connection information:

```bash
# Run the migration installation
migrate install
```

If this command succeeds, then we are ready to go to the next step.  If it fails, then check your credentials, connection information and that you can actually connect to the database. If not, ask away in our community forum: [https://community.ortussolutions.com/c/communities/contentbox/15](https://community.ortussolutions.com/c/communities/contentbox/15)

## 2. Backups

Please make sure you backup your source code and your database. We are not liable for broken installations.

## 3. Run the Upgrade

We have prepared a CommandBox recipe that will upgrade your installation in one easy execution.

### 1. Update the source code

Please make sure your CFML engine has been completely stopped before continuing.

#### \*nix/Mac

If you are in a Linux or Mac environment you can execute the recipe using the following shell commands from the root directory of your application.

```bash
# Download recipe
curl -o updater.boxr https://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/5.0.0/updater.boxr
# Execute recipe
box recipe updater.boxr
```

#### Windows

If you are in windows, download the following recipe:

[http://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/5.0.0/updater.boxr](http://raw.githubusercontent.com/Ortus-Solutions/ContentBox/development/build/patches/5.0.0/updater.boxr)

and place it in the root of your project. Then issue the following CommandBox shell command to execute it.

```bash
box recipe updater.boxr
```

That's it! The updater will take care of upgrading your 3.x source code to the latest 4.x source code.



