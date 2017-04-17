ContentBox allows you to override global site settings dynamically.  This approach is great for container based deployments, but also for traditional overrides for testing or staging environments. 

## Override ContentBox Settings via ColdBox.cfc

You can override any runtime setting for ContentBox via a configuration structure in your main `ColdBox.cfc` configuration file. This will allow developers to override any runtime setting for any site.

All you need to do is create the a `contentbox` structure in your `configure()` or any tier method, with the name of the site (`default` is the default site) and then any setting name-value pair.

```js
contentbox = {
// Runtime Settings Override by site slug
settings = {
// Default site
default = {
"cb_search_adapter" = "my.search.adapter",
"cb_media_directoryRoot" = "/docker/mount"
}
}
}
```

### Override ContentBox Settings via Java Environment Variables

You can also override any runtime ContentBox setting by passing them via Docker/Java Runtime variables.

Since these are string keys we can now use our fancy structures like the settings above, so you must adhere to our recognition pattern:

```
contentbox_{site}_{setting}=value
```

Here is an example on adding a custom media root:

```
-Dcontentbox_default_cb_media_directoryRoot=./build/docker/contentbox/content
```

This will allow especially Docker environments to override settings as environments or even provide secrets. More is coming, so stay tuned to our updates.