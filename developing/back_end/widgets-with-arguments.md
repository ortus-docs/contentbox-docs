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

