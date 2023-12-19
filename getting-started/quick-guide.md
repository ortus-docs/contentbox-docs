# Quick Guide

## Quick Setup

The Quick Setup will take you through 6 easy steps in order to configure and install a ContentBox Express Edition with an embedded database so we can start working with ContentBox. Ready, set, go!

> **Note** If you prefer a container (Docker) approach, then use the [Docker getting started guide](installation/docker.md).

### Step 1: Download and Install using CommandBox

Go to [https://contentbox.ortusbooks.com/getting-started/installation/commandbox-installation](https://contentbox.ortusbooks.com/getting-started/installation/commandbox-installation).

Once downloaded, and the server is running, return here and follow the rest of the steps.&#x20;

### Step 2: Administrator Information

Fill out the setup details for your ContentBox Administrator and click Next Step.

![](../.gitbook/assets/installer\_step2.png)

### Step 3: Site Setup

Fill out basic information for your ContentBox Site and click Next Step.

![](../.gitbook/assets/installer\_step3.png)

### Step 4: Email Setup

You can connect ContentBox to any email system in order to send notifications. By clicking Next Step without changing anything ContentBox will use by default the email settings in your application server (default).

![](../.gitbook/assets/installer\_step4.png)

### Step 5: URL Rewrites

ContentBox Express Edition already has Full URL Rewrites enabled. So just use the dropdown to select `ContentBox Express` and it will automatically configure ContentBox for full URL rewrites. We also support iis, nginx, apache, and CommandBox.

![](../.gitbook/assets/installer\_step5.png)

### Step 6: Done!

Click Start Installation! ContentBox will prepare the database and process the final configurations so it can start running.

![](../.gitbook/assets/installer\_done.png)

You are done! Go ahead and visit your site by clicking **Visit Site** and log into your Contentbox Administration by clicking **Visit Administrator**.

> **Danger** : Please make sure you delete the `contentbox-installer` and `contentbox-dsncreator` modules in the /modules folder after installation. The administrator will warn you about it and you can even delete those modules from the admin dashboard.

Welcome to ContentBox!
