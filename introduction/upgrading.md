# Upgrading to 3.0.0

If you already have a ContentBox 2.X installation you will have to follow this guide in order to update your installation.  Please note that ContentBox 3 is a major upgrade and will require some manual steps on your part in order to have a seamless upgrade.

## Step 1: Backup
Like with any automated process, there is room for error. So backup your files and database, we will not be held responsible for any mishaps.

## Step 2: Download CBCMS3 Updater
We have created a special ContentBox 2 module that will update your installation.  Please visit https://github.com/Ortus-Solutions/cbcms-updater-v3 and download the **master** branch by clicking on the download button.

<img src="images/cb3updater-github.png">

## Step 3: Install CBCMS3 Updater

Unzip the download and copy over the folder to your current ContentBox installation in the `modules` folder.  Make sure the folder is called `cbcms-updater-v3`. It should be placed alongside the other ContentBox modules.

<img src="images/cb3updater-module.png">

## Step 4: Restart Application
In order for the module to take effect, you must restart your application or even better your server.  

## Step 5: Visit Module
Now open your application and visit the module by using the `/CB3Updater` URL entry point.  Here is an example: `http://mysite.com/cb3updater`

<img src="images/cb3updater-step1.png">