# System Requirements

Let's get started with some system requirements for running ContentBox sites:

## Java
ContentBox will run in any Java 1.7+ enabled servlet container.

## CFML Engine
ContentBox source can be deployed to the following ColdFusion CFML engines:

* Adobe ColdFusion 9.01+
* Railo 3+
* Lucee 4.5+

## Databases
ContentBox can run on any database engine that Hibernate ORM supports, but we officially support the following:

MySQL 5+ (InnoDB ONLY!)
Microsoft SQL Server 2008+
Oracle
PostgreSQL
Hypersonic
H2
Apache Derby
If you have another database engine that needs ContentBox support, please let us know and we will be able to help you.

MySQL Caveats: If you are running MySQL server with MyISAM as your default table engine, you will need to either make the default InnoDB or use the InnoDB dialect.  You can do this by adding a dialect section to the ORM settings in the Application.cfc:  dialect = "MySQLWithInnoDB";
URL Rewriting
ContentBox relies on Search Engine Safe (SES) URLs.  The majority of CFML engines already allow for these types of URLs out of the box and ContentBox supports it out of the box.  However, if you would like to use full URL rewriting (which we recommend) you will need to use a web server rewriting tool and ContentBox will configure it for you.  So before you install Contentbox make sure that you are using one of the supported rewriting engines show below:

Apache mod_rewrite
IIS 7 rewrite module
Tuckey rewrite filter
File Permissions
ContentBox needs some files/folders to be writable at runtime.  We use this for our installer, ForgeBox cloud deployments, auto-updates and more.  The following directories need read/write permissions for the installer only to work:

{Root}/Application.cfc
{Root}/config/ColdBox.cfc
{Root}/coldbox/system/aop/tmp
The following locations need read/write permissions for normal operations after the installer:

{Root}/coldbox/system/aop/tmp
{Root}/modules/contentbox/content
{Root}/modules/contentbox/email_templates
{Root}/modules/contentbox/layouts
{Root}/modules/contentbox/modules
{Root}/modules/contentbox/updates
{Root}/modules/contentbox/widgets