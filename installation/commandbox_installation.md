# CommandBox Installation

![](../images/CommandBoxLogo.png)

[CommandBox](http://www.ortussolutions.com/products/commandbox) is a ColdFusion (CFML) Command Line Interface (CLI), REPL, Package Manager and Embedded Server.  We will leverage the CLI in CommandBox to install, deploy and configure ContentBox.  The full CommandBox installation instructions can be found here: http://commandbox.ortusbooks.com/content/setup/installation.html.  We will do the short version.


## Download CommandBox
You can download CommandBox from the official site: http://www.ortussolutions.com/products/commandbox#download and install in your preferred Operating System (Windows, Mac, *unix).  CommandBox comes in two flavors:

1. No Java Runtime (30mb)
2. Embedded Runtime (80mb)

So make sure you choose your desired installation path and follow the instructions here: [http://commandbox.ortusbooks.com/content/setup/installation.html](http://commandbox.ortusbooks.com/content/setup/installation.html)


### Starting CommandBox
Once you download and expand CommandBox you will have the `box.exe` or `box` binary, which you can place in your Windows Path or *Unix `/usr/bin` folder to have it available system wide.  Then just open the binary and CommandBox will unpack itself your user's directory: `{User}/.CommandBox`.  This happens only once and the next thing you know, you are in the CommandBox interactive shell!

![](../images/commandbox-terminal.png)

We will be able to execute a-la-carte commands from our command line or go into the interactive shell for multiple commands.  We recommend the interactive shell as it is faster and can remain open in your project root.

