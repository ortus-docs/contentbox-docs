---
description: >-
  This interface will allow you to configure the mail server details that
  ContentBox will use for sending email notifications
---

# Mail Server

## `Site Options`

<figure><img src="../../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

**`Mail Server:`**` ``This is the web address for the SMTP server.  The address for the SMTP server may be an Internet address, such as mail.company.com, or the IP address of the mail server, such as 127.0.0.1.`\
\
`If not specified, ContentBox will use the mail server address from the ColdFusion Administrator.`

**`Mail Server Username:`**` ``This is the username for the mail server, if necessary.`

`If not specified, ContentBox will use the username address from the ColdFusion Administrator.`

**`Mail Server Password:`**` ``This is the password for the mail server, if necessary.`

`If not specified, ContentBox will use the password from the ColdFusion Administrator.`

**`Mail SMTP Port:`**` ``This is the port number on which the mail server is running.  This value will default to 25.`

**`Use TLS:`**` ``This enables/disables (default) the Transport Level Security (TLS) on the connection to the mail server.`

**`Use SSL:`**` ``This enables/disables (default) SSL encryption on the connection to the mail server.`



`After you have configured the mail server settings, you can click the`` `**`Test Connection`**` ``button to send a test email message to the email address associated with the current logged in user.`

### `When running ContentBox in Development Mode:`

When running ContentBox in development mode, the mail server details are not utilized.  Instead, all emails will be written to the file system logs for review.  This prevents inadvertent emails from being sent during development.

The logs for every email sent will be located in:

`[ContentBox Root Folder]\config\logs\mail`
