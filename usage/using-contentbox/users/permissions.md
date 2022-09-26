# Permissions

This option is under `Users` in the left side navigation bar. This is a list of all permissions available for the site.

There is a quick search box at the top of the permissions page if you are looking for a specific permission.

On the permissions page you will see 4 headings.

* Permission - This is the name of the permission
* Description - This explains the permission and what access it allows for the user
* Roles Assigned - This shows you how many users are using this permission currently.
* Actions&#x20;
  * Green Icon - Edit the permission
  * Red Delete Icon - Delete the permission.&#x20;

![](../../../assets/user-permissions-list.png)

## Creating Permissions

Click Create Permission to add a permission. A permission consists of:

* Permission ( commonly known as a slug / name )&#x20;
* Description

![](../../../assets/user-permissions-create.jpg)

A Permission Slug can be referenced from inside of code used in Widgets, Modules, Themes, restricting access however you see fit. Creating a permission allows you to assign the permission to Roles and/or Users, but will not be functional without code referencing the Permission ( slug ).

A Permission ( slug ) can also be referenced from inside the Security Rules as well. Security rules are used to secure ContentBox according to incoming events or URLs, much like a firewall. See that `System > Security Rules` for more information on how Permissions are used.

## Bulk Actions

In the top right section of the page, you will see a `Bulk Actions` button next to `Create Permission`. This allows you to do the following:

* Import
* Export All as JSON
* Export All as XML

### Import

This is a nice feature when you manage several sites. You can setup permissions on one site, and then export them, and import them into the other sites you manage.

![](../../../assets/user-permissions-import.jpg)

For safety reasons, when you Import Permissions, by default you will not override any content. If you have existing Permissions, that you want to be updated, please set `Override Content` to true. Otherwise existing content will be skipped during the import process.

### Export as JSON / XML

Exporting to JSON or XML is a simple process. Click `Bulk Actions` and select your format, and in seconds you will see a file download prompt pop up, asking you to open or save your file ( in most browsers ).

![](../../../assets/user-permissions-export.jpg)
