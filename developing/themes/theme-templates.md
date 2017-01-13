# Theme Templates

## Template Folder File Structure

- <i class="fa fa-folder-open"></i> templates (The folder that contains optional templates for collection rendering that are used using the quick rendering methods in the CB Helper. See below for additional information)

  + <i class="fa fa-folder-open"></i> category.cfm (The template used to display an iteration of entry categories using coldbox collection rendering)
  + <i class="fa fa-folder-open"></i> comment.cfm (The template used to display an iteration of entry or page comments using coldbox collection rendering)
  + <i class="fa fa-folder-open"></i> entry.cfm (The template used to display an iteration of entries in the home page using coldbox collection rendering)

## Functionality

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

