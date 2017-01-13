# Theme Templates

The individual files included in the `templates` directory are a single `.cfm` files used by ContentBox to iterate over a collection (usually entries or categories or comments) and
render out all of them in uniformity.  

Please refer to ColdBox Collection Rendering for more information.  

__Each template receives
the following variables__:

- `_counter` (A variable created for you that tells you in which record we are currently looping on)
- `_items` (A variable created for you that tells you how many records exist in the collection)
- `{templateName}` The name of the object you will use to display: entry, comment, category

__Layout Local CallBack Functions__:
  - `onActivation()`
  - `onDelete()`
  - `onDeactivation()`

