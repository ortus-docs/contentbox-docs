# Settings
You can declare settings for your layouts that ContentBox will manage for you.

```
this.settings = [
	{ name="Title", defaultValue="My Awesome Title", required="true", type="text", label="Title:" },
	{ name="Colors", defaultValue="blue", required="false", type="select", label="Color:", options="red,blue,orange,gray" }
];
```

The value is an array of structures with the following keys:

- `name` : The name of the setting (required), the setting is saved as cb_layoutname_settingName
- `defaultValue` : The default value of the setting (required)
- `required` : Whether the setting is required or not. Defaults to false
- `type` : The type of the HTMl control (text=default, textarea, boolean, select)
- `label` : The HTML label of the control (defaults to name)
- `title` : The HTML title of the control (defaults to empty string)
- `options` : The select box options. Can be a list or array of values or an array of name-value pair structures