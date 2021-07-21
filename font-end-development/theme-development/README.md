# Theme Development

A theme is composed of the following pieces

 ThemeDirectory

*  Theme.cfc \(The CFC that models and configures your theme implementation\)
*  layouts \(The folder that contains layouts in your theme\)
  *  blog.cfm \(Mandatory layout used for all blog views by convention\)
  *  pages.cfm \(Mandatory layout used for all pages by convention\)
  *  maintenance.cfm \(Optional used when in maintenance mode, else defaults to pages\)
  *  search.cfm \(Optional used when doing searches, else defaults to pages\)
*  views \(The folder that contains views for rendering\)
  *  archives.cfm \(MANDATORY: The view used to render out blog archives.\)
  *  entry.cfm \(MANDATORY: The view used to render out a single blog entry with comments, etc.\)
  *  error.cfm \(MANDATORY: The view used to display errors when they ocurr in your blog or pages\)
  *  index.cfm \(MANDATORY: The view used to render out the home page where all blog entries are rendered\)
  *  notfound.cfm \(The view used to display messages to users when a blog entry requested was not found in our system.\)
  *  page.cfm \(MANDATORY: The view used to render out individual pages.\)
  *  maintenance.cfm \(OPTIONAL: Used when in maintenance mode\)
*  templates \(The folder that contains optional templates for collection rendering that are used using the quick rendering methods in the CB Helper. See below for additional information\)
  *  category.cfm \(The template used to display an iteration of entry categories using coldbox collection rendering\)
  *  comment.cfm \(The template used to display an iteration of entry or page comments using coldbox collection rendering\)
  *  entry.cfm \(The template used to display an iteration of entries in the home page using coldbox collection rendering\)
*  widgets \(A folder that can contain layout specific widgets which override core ContentBox widgets\)

