# Quick Guide

## Quick Setup

The Quick Setup will take you through 8 easy steps in order to configure and install a ContentBox Express Edition with an embedded database so we can start working with ContentBox. Ready, set, go!

> **Note** If you prefer a container (Docker) approach, then use the [Docker getting started guide](installation/docker.md).

### Step 1: Download

Go to [https://www.ortussolutions.com/products/contentbox#downloads](https://www.ortussolutions.com/products/contentbox#downloads) and click on the download ContentBox Express Edition for your operating system.

![](../.gitbook/assets/express\_download.png)

Once downloaded, extract the `contentbox-express-{version}.zip` (we recommend you to do this in a new folder).

![](../.gitbook/assets/express\_structure.png)

### Step 2: Start it up!

Open the `bin` folder and double click `startup.bat` (Windows) or execute the `startup.sh` (Linux, Mac) and Kaboom! ContentBox will start to deploy a local embedded server with an embedded database.

> **Warning** If you are in Unix or Mac OS X, make sure you give the `bin` folder execution permissions. You can do this by running `chmod -R +x bin` to give the directory execution permissions.

### Step 3: Running the Installer

Once the server is online go to your browser and type `http://localhost:8085` which is the port that ContentBox Express uses and hit enter. Your browser should now open the install wizard. Read the instructions and click on the **Start Installer** button to start the process.

![](../.gitbook/assets/installer\_step1.png)

> **Hint** If you go back again to the `bin` folder you are going to find a new folder called `contentboxDB`. This is the ContentBox Express embedded database. This doesn’t mean you can’t use other data bases with ContentBox Express Edition, but it has been done this way out of convenience.

### Step 4: Administrator Information

Fill out the setup details for your ContentBox Administrator and click Next Step.

![](../.gitbook/assets/installer\_step2.png)

### Step 5: Site Setup

Fill out basic information for your ContentBox Site and click Next Step.

![](../.gitbook/assets/installer\_step3.png)

### Step 6: Email Setup

You can connect ContentBox to any email system in order to send notifications. By clicking Next Step without changing anything ContentBox will use by default the email settings in your application server (default).

![](../.gitbook/assets/installer\_step4.png)

### Step 7: URL Rewrites

ContentBox Express Edition already has Full URL Rewrites enabled. So just use the dropdown to select `ContentBox Express` and it will automatically configure ContentBox for full URL rewrites. We also support iis, nginx, apache, and CommandBox.

![](../.gitbook/assets/installer\_step5.png)

### Step 8: Done!

Click Start Installation! ContentBox will prepare the database and process the final configurations so it can start running.

![](../.gitbook/assets/installer\_done.png)

You are done! Go ahead and visit your site by clicking **Visit Site** and log into your Contentbox Administration by clicking **Visit Administrator**.

> **Danger** : Please make sure you delete the `contentbox-installer` and `contentbox-dsncreator` modules after installation. The administrator will warn you about it and you can even delete those modules from the admin dashboard.

Welcome to ContentBox!
