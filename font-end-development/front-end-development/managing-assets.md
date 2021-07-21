# Managing Assets

By default the `includes` directory of your theme is used to store your static assets.

Because these assets are called from your customized theme, however, you may use any directory conventions you prefer. If you plan to use customized paths or CDN links in your template, it's best to create a setting in your `Theme.cfc` which will then be configured through the admin.

## AddAsset\(\) Method for CSS and JS

In the Front End of the Website, the Theme takes over the rendering. To ensure all Assets are added correctly from various modules, for every theme, we recommend using the htmlHelper's `addAsset()` method.

Since the SuperType \( which all ColdBox items inherit from \) implements addAsset\(\) you can call it directly from almost any file in your application.

`addAsset( "#prc.cbroot#/includes/css/#css#.css" );`

You might have noticed, that even in the [Admin Asset Management methods explained here](js-and-css-assets.md), the actual implementation of the cssFullAppendList and cssAppendList use the addAsset to add the CSS to the head of the HTML page.

_This applies to both CSS and JS. The main downside to this approach is that all assets added with addAsset are added to the head. The order of the assets is not strictly \( or easily \) controlled either._

### Better Asset Management coming soon

We recommend using a similar approach to the admin, using an array, and outputting in the theme. We will be standardizing an approach soon, so all themes can easy implement these features, with a single line `cbhelper` method.

