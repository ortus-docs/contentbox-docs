# Theme Development

A theme is composed of the following pieces

&#x20;ThemeDirectory

* &#x20;Theme.cfc (The CFC that models and configures your theme implementation)
* &#x20;layouts (The folder that contains layouts in your theme)
  * &#x20;blog.cfm (Mandatory layout used for all blog views by convention)
  * &#x20;pages.cfm (Mandatory layout used for all pages by convention)
  * &#x20;maintenance.cfm (Optional used when in maintenance mode, else defaults to pages)
  * &#x20;search.cfm (Optional used when doing searches, else defaults to pages)
* &#x20;views (The folder that contains views for rendering)
  * &#x20;archives.cfm (MANDATORY: The view used to render out blog archives.)
  * &#x20;entry.cfm (MANDATORY: The view used to render out a single blog entry with comments, etc.)
  * &#x20;error.cfm (MANDATORY: The view used to display errors when they ocurr in your blog or pages)
  * &#x20;index.cfm (MANDATORY: The view used to render out the home page where all blog entries are rendered)
  * &#x20;notfound.cfm (The view used to display messages to users when a blog entry requested was not found in our system.)
  * &#x20;page.cfm (MANDATORY: The view used to render out individual pages.)
  * &#x20;maintenance.cfm (OPTIONAL: Used when in maintenance mode)
* &#x20;templates (The folder that contains optional templates for collection rendering that are used using the quick rendering methods in the CB Helper. See below for additional information)
  * &#x20;category.cfm (The template used to display an iteration of entry categories using coldbox collection rendering)
  * &#x20;comment.cfm (The template used to display an iteration of entry or page comments using coldbox collection rendering)
  * &#x20;entry.cfm (The template used to display an iteration of entries in the home page using coldbox collection rendering)
* &#x20;widgets (A folder that can contain layout specific widgets which override core ContentBox widgets)
