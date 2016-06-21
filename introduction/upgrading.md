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

The module will be active and it will tell you to upgrade your application's `config/ColdBox.cfc` that you must do so manually according to the instructions presented.  Once you have done this manual step, then save your file and click on the **Continue** button.

## Step 6: Automation
Now you will be in step2 of the module wizard.  It will show you an updated `Application.cfc` according to your old `Application.cfc` on disk.  If there are any custom changes that are not reflected, then update as you see fit.  Once done, then click on the continue and save button. This will start the upgrade process, grab a cup of coffee and wait for the installer to show you the finalization screens.

<img src="images/cb3updater-step2.png">

## Step 7: Finalizations
<img src="images/cb3updater-final.png">

If all went well, then you should see the screenshot above.  You can now log in to your new application and site.  We would recommend a final server restart if possible as well.