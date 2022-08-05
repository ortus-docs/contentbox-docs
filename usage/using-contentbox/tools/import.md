# Import

## Importing from a \*.cbox file

Once you have exported the content, you will have a \*.cbox file. To import the file, in the admin, click on `Tools > Import.`

![ContentBox Import Tools User Interface](../../../.gitbook/assets/cbcms\_import.jpg)

To import your cbox file, select `Import ContentBox Package` and then select the file by browsing your computer, and click Start Import.

_**Word of Warning - Whenever you are migrating data, you should always create a full database back up just in case. We have designed the import and export to be as effective as possible, but it always pays to be safe, when working with data.**_

## Importing from another Blog System

To get to the Import Tools, in the admin, click on `Tools > Import`.

The Import Tools page displays 2 main options, ContentBox Package ( .cbox ) or Database Import. In Tip 10, we talked about importing from a ContentBox package, but in this tip, we are going to click Import from Database and then enter your database connection criteria to complete the import.

![ContentBox Import Tools - Importing Database from Other Blog](../../../.gitbook/assets/cbcms\_migrate\_1.jpg)

### Datasource Options

This server must have a defined datasource to the source blog database in order to import it. Please make sure this datasource exists in the ColdFusion administrator. If you have not done this yet, please login into your ColdFusion Administrator ( or Lucee admin ) and setup the datasource for the database you wish to import.

Enter the Datasource name that you created, and Username/ Password if required.

![Datasource Options - Database Import - ContentBox Import Tools](../../../.gitbook/assets/cbcms\_migrate\_2.jpg)

### Source Content

1. Next we have to choose the type of data you are importing, and any special setup you might have used. Select the Importer Source - Mango, WordPress, BlogCFC or MachBlog ( please let us know if your CMS is not on this list and would like us to enter it )
2. Table Prefix - when installing the blog, some blog software allow you to select a table prefix. To import your data correctly, we need to know what Prefix the database is using.
3. Default Author Password - Since systems encrypt passwords, we cannot simple copy them over, we need to create new ones. Please enter a default author password to set this as the default, and then you can modify them once they are imported into ContentBox.
4. Since Roles are not the same between blogs, please select the default Author Role you wish to use for Authors imported through this process. You can manually change them after the import.

When you are all set, click Start Import, and be patient. This process might take some time.

![Source Content - Database Import - ContentBox Import Tools](../../../.gitbook/assets/cbcms\_migrate\_3.jpg)

_Note: We have worked hard to make sure this process is as smooth as possible. There may be some data that does not transfer over automatically, but this should give you a great starting point, if converting from another blog._

_**Remember, always back up your data and files before doing imports like this, to be sure… and never do this in production.**_
