# Multiple Render Function Widgets

Widgets are required to provide one function called `renderIt()`, but they can actually provide more than one render option. If you add another function, then the display of the Widget Form changes.

Now you will see a `Public Methods` menu, with a list of public functions in ths CFC. Below you can see the required function `renderIt()` and the 2 additional functions. `listOfPages()` and `listOfCategories()`

![](../../../assets/cb\_widget\_multiple\_render.jpg)

When you select a different Method, the options change, depending on the function. This means you could have 1 widget, with several different display options... each with their own set of arguments. Packaging them inside a single Widget CFC allows them to easily share functions.

Above, you can see the `renderIt()` function has 1 argument, with label, hint, required etc.

The `listOfPages()` function has 1 argument, a plain text field `numberOfPages`, as you can see below.&#x20;

![](../../../assets/cb\_widget\_multiple\_render2.jpg)

The `listOfCategories()`function has 1 argument, a plain text field `numberOfCategories`, as you can see below.&#x20;

![](../../../assets/cb\_widget\_multiple\_render3.jpg)

## Hiding UDF Functions

If you add a UDF to your Widget, to be able to dynamically create the select drop down for your Widget arguments, you might notice an unexpected side effect. This function / method shows up in the `Select a Method` drop down box.

![](../../../assets/cb\_widget\_argument\_optionsUDF.jpg)

Your first thought might be, to use a private function. The Widget form builder needs to call the UDF to generate the Select Boxes, so it cannot be a private function.

The solution, add Meta data about the function... including `cbignore`. You can add this with the function meta data in a comment.

```java
/**
* @cbignore
*/
function getTargetTypes(){
    return [ '_self','_blank','_top','_parent','ThisisfromTheUDF' ];
}
```

Or you could add this meta data with the inline meta style.

```java
function getTargetTypes() cbignore{
    return [ '_self','_blank','_top','_parent','ThisisfromTheUDF' ];
}
```

With either of these two options, you will see the list of Options provided by the UDF, but you will not see the `Public Methods` option, as there is only 1 public rendering function.

![](../../../assets/cb\_widget\_argument\_optionsUDF\_fixed.jpg)
