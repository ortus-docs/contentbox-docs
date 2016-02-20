# Global Variables

During the ContentBox request, common variables and supertype methods are made available to all templates and views used in that request.  When developing themes and modules for ContentBox, you may assume availability of the following:

`#cb#`
===

The `cb` object contains a variety of common methods for retrieving ContentBox content and settings.  Methods include:

- `contentStore(required string slug)`: retrieves the HTML output of a [Content Store](/content/using/managers/contentstore.html) item by its slug
- `contentStoreObject(required string slug)`: retrieves the associated [Content Store](/content/using/managers/contentstore.html) object.