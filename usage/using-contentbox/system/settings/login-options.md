# Login Options

![](../../../../assets/login\_options.png)

## Two Factor Authentication

In this settings pane, you can control global settings related to two-factor authentication.

### Force 2 Factor Authentication

Turning this flag on will require two-factor authentication for your app. Any users who have not enrolled will be required to enroll on their next login. Keep in mind that if you as an admin are not enrolled in two-factor and this setting is turned on you will be forced to enroll in two factor after saving this configuration.

### Trusted Device Timespan

The number of days to keep trusting a user's device. If you set this value to `0`, two factor authentication will be required on every log in.

### Default Two Factor Provider

Two factor authentication uses a provider system to allow new methods of two factor authentication to be provided via a module. A good example of this extension is [Amazon SNS Provider](https://github.com/contentbox-modules/contentbox-awssns-twofactor).

> Note that if you decide to change the default two factor provider, all currently enrolled users will be unenrolled.
