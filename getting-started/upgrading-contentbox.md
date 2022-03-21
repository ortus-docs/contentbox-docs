---
description: Learn how to upgrade ContentBox CMS with just a couple of steps.
---

# Updates

ContentBox is upgraded using CommandBox via the CLI.  If you are upgrading from minor to minor/patch level, most likely you won't need to follow an upgrade guide.  However, if you are upgrading between major versions make sure you visit each of the major versions' upgrade guide first.

## Make a full backup

Make sure you backup your database and source, just in case.  We recommend running this against a development instance first and then moving on to production instances.

## Update Command

When you are ready with your backups, open up a CommandBox shell using `box` in the root of your project.

{% hint style="danger" %}
Make sure your `.env` and credentials are seeded
{% endhint %}

```bash
# Run the update of the core dependencies
update --force
```

## Run database migrations

Now that the ContentBox source has been upgraded, let's run the database migrations

```
# Run the migrations
run-script contentbox:migrate:up
```

Once they run, you are ready to roll!

## Professional Updating

The ContentBox team can also do the heavy lifting for you as we are a professional open source project. So just contact us and we will update or install any ContentBox instances in a secure and fast way!
