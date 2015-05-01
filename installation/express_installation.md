# Express Installation

The express version of ContentBox is a fully integrated running server powered by Lucee, an open source CFML engine, and Tomcat.  

## Requirements
Make sure your system has a working Java Runtime 1.7+ environment.  A quick test to see if your system supports Java is to open a terminal or command prompt and typing:

```
java -version
```

You should see something like this:

```
java version "1.8.0_40"
Java(TM) SE Runtime Environment (build 1.8.0_40-b27)
Java HotSpot(TM) 64-Bit Server VM (build 25.40-b25, mixed mode)
```

Just make sure what it is Java 1.7+.


## Step 1: Download Express
The first step is for you to download ContentBox (http://www.ortussolutions.com/products/contentbox) or you can use the command below:

```
# stable
wget http://www.ortussolutions.com/parent/download/contentbox?type=express

# bleeding edge
wget http://www.ortussolutions.com/parent/download/contentbox?type=express&version=be
```

Once downloaded expand the archive

```
unzip contentbox-express-{version}.zip
```

This will expand into the folder of your liking.

## Step 2: Permissions

On some operating systems like Linux or Mac, you will need to enable run permissions. So drop into a shell or terminal in that folder you expanded and type:

```
chmod -R 777 bin
```

This will add execution and write permissions to the `bin` folder which is required.


## Step 3: Run it

Go into the `bin` folder and and execute either the `startup.bat` or `startup.sh` or `startup.app` according to your OS.  Then visit the site in a browser on port `8085` by default.



## Changing the Default Port

Go to the `conf/server.xml` and look for the following:

```xml
<Connector port="8085" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
```               

Just update the `port` to whatever you desire.

