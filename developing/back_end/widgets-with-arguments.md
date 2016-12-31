# Widgets with Arguments

Widgets do not need to have arguments or parameters, but most Widgets are best designed with some customization available to the user. 

Let us add a few arguments to our Simple Widget.

## Add an Simple Text Argument

Our starting point looks like this.

```
function renderit( ){
		var thehtml = '<a href="https://www.contentboxcms.org/" target="_blank">
				<img src="https://www.ortussolutions.com/__media/ContentBox_300.png" 
				alt="ContentBox CMS Logo"></a>';
		return thehtml;
}
```	

We want to give the user an option to change the target of the link. To start we will add the `urlTarget` argument to the `renderIt()` and then use that argument in our link.

```
function renderit( urlTarget ){
		var thehtml = '<a href="https://www.contentboxcms.org/" target="#arguments.urlTarget#">
				<img src="https://www.ortussolutions.com/__media/ContentBox_300.png" 
				alt="ContentBox CMS Logo"></a>';
		return thehtml;
}
```	

When the user tries to use the widget now, they'll see this added to the Widget selector.

![](/assets/cb_widget_argument.text1.jpg)

## Adding more User Friendly Options to Arguments

You will see the argument name `urlTarget` shown, with the type `(any)`. We can add some more options to the arguments to make it more user friendly, including: 

- Label
- Required
- Hint
- Type
- Default
- Options
- OptionsUDF
- MultiOptions
- MultiOptionsUDF

These are all added via the JavaDoc syntax for the RenderIt() function. Below is an example of the label being used.

```
/**
* Descript of the function
* @argumentName.label
*/
```

### Argument Label

The Label is used when you want to have a more meaningful label for the form field than the name of the argument itself. In our example, by default, the label is `urlTarget`, but we can change it to something like `This is my Label`

```
/**
* Renders this widget
* @urlTarget.label This is my label 
*/
function renderit( urlTarget ){
```	

The Widget Form now shows this label instead of the Argument name

![](/assets/cb_widget_argument_label.jpg)

### Required Argument

Required does what it says, it makes a field a required field. This will show a label and add the necessary validation. 

To make a field required, add Javadoc Meta comment `@urlTarget.required` to the function meta.

```
/**
* Renders this widget
* @urlTarget.label This is my label 
* @urlTarget.required
*/
function renderit( urlTarget ){
```

![](/assets/cb_widget_argument_required.jpg)

### Argument Hint

A label goes a long way in helping the user understand the purpose of a field, but you can also use Hints to make this crystal clear. 

To add a field hint, add Javadoc Meta comment `@urlTarget.hint` to the function meta.

```
/**
* Renders this widget
* @urlTarget.label This is my label 
* @urlTarget.required
* @urlTarget.hint This is the html target type for the link. _self _blank _top _parent frameName
*/
function renderit( urlTarget ){
```	

![](/assets/cb_widget_argument_hint.jpg)

### Default Value 

You can set a default Value for the field. 

To add a default value for an argument, add Javadoc Meta comment `@urlTarget.default _blank` to the function meta.

```
/**
* Renders this widget
* @urlTarget.label This is my label 
* @urlTarget.required
* @urlTarget.hint This is the html target type for the link. _self _blank _top _parent frameName
* @urlTarget.default _blank
*/
function renderit( urlTarget ){
```

![](/assets/cb_widget_argument_default.jpg)

### Options for Arguments

Using Labels, Hints and Required fields helps the user, but in some cases its best if you can give your users a set list of options to pick from. This will provide the user a select drop down box, instead of a text box. This ensures there are no typos. 

To add options for an argument, add Javadoc Meta comment `@urlTarget.options _self,_blank,_top,_parent` to the function meta.

```
/**
* Renders this widget
* @urlTarget.label This is my label 
* @urlTarget.required
* @urlTarget.hint This is the html target type for the link. _self _blank _top _parent frameName
* @urlTarget.options _self,_blank,_top,_parent
*/
function renderit( urlTarget ){
```

![](/assets/cb_widget_argument_options.jpg)

As you can see, the Default value even works with the options drop down, so you can have the default, pre-selected.

### Options for Arguments via UDF

Option lists work great for some use cases, but sometimes you might need some dynamic information. This allows you to write a function, and the Widget form builder calls that function for you to load the options. To use an optionsUDF instead of options you need to do 2 things.

1- To add options for an argument via UDF, add Javadoc Meta comment `@urlTarget.optionsUDF getTargetTypes` to the function meta. The function should be the name without the parenthesis.

```
/**
* Renders this widget
* @urlTarget.label This is my label 
* @urlTarget.required
* @urlTarget.hint This is the html target type for the link. _self _blank _top _parent frameName
* @urlTarget.default _blank
* @urlTarget.optionsUDF getTargetTypes
*/
function renderit( urlTarget ){
```

2- Add the new function. The new function can be named anything ( other than RenderIt - the default function for a widget ). The function must return an array of elements that can be converted to a string. Here is the UDF function that matches the previous list of options, but this time, we added one, to be sure it is from the UDF.

```
function getTargetTypes(){
	return [ '_self','_blank','_top','_parent','ThisisfromTheUDF' ];
}
```

Reload and test the widget, we see the list of Target Types. 

![](/assets/cb_widget_argument_optionsUDF.jpg)

You might see a side effect of adding the function. Now you will see another option, `Public Methods` with a list of public functions in ths CFC. Widgets are required to implement the default `RenderIt()` function, but the Widget can actually have several methods. 

To hide this function ( since this is outputting an array, not a string ), you cannot use a private function ( otherwise the UDF cannot be called by the Form Builder ), you need to add some meta data to ignore the function.

```
/**
* @cbignore
*/
function getTargetTypes(){
	return [ '_self','_blank','_top','_parent','ThisisfromTheUDF' ];
}
```	

or you could use the inline meta

```
function getTargetTypes() cbignore{
	return [ '_self','_blank','_top','_parent','ThisisfromTheUDF' ];
}
```	

With either of these two options, you will see the list of Options provided by the UDF, but you will not see the `Public Methods` option, as there is only 1 public rendering function.

![](/assets/cb_widget_argument_optionsUDF_fixed.jpg)

### MultiOptions - Multiple Choice Options

Using Labels, Hints and Required fields helps the user, but in some cases its best if you can give your users a set list of options to pick from, especially if they user could/should pick one or more options. This will provide the user a multi select drop down box, instead of a text box. This ensures there are no typos. 

To add options for an argument, add Javadoc Meta comment `@urlTarget.multioptions _self,_blank,_top,_parent` to the function meta.

```
/**
* Renders this widget
* @urlTarget.label This is my label 
* @urlTarget.required
* @urlTarget.hint This is the html target type for the link. _self _blank _top _parent frameName
* @urlTarget.multioptions _self,_blank,_top,_parent
*/
function renderit( urlTarget ){
```

![](/assets/cb_widget_argument_multioption.jpg)

### MultiOptionsUDF - Multiple Choice Options via UDF

MultiOptionsUDF works the same as OptionsUDF except the user can select none, one or more of the options.

Add the meta to the RenderIt() function
```
/**
* Renders this widget
* @urlTarget.label This is my label 
* @urlTarget.required
* @urlTarget.hint This is the html target type for the link. _self _blank _top _parent frameName
* @urlTarget.default _blank
* @urlTarget.multioptionsudf getTargetTypes
*/
function renderit( urlTarget ){
```	

Add the UDF ( include the cbignore meta data so the Widget Form builder ignores the function ) 
```
function getTargetTypes() cbignore {
	return [ '_self','_blank','_top','_parent','ThisisfromTheUDF' ];
}
```

![](/assets/cb_widget_argument_multioptionudf.jpg)

