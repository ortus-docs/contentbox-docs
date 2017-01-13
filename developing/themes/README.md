# Themes

A theme is composed of the following pieces

<i class="fa fa-folder-open"></i> ThemeDirectory
 
 - <i class="fa fa-file"></i> Theme.cfc (The CFC that models and configures your theme implementation)
 
 - <i class="fa fa-folder-open"></i> layouts (The folder that contains layouts in your theme)
   + <i class="fa fa-folder-open"></i> blog.cfm (Mandatory layout used for all blog views by convention)
   + <i class="fa fa-folder-open"></i> pages.cfm (Mandatory layout used for all pages by convention)
   + <i class="fa fa-folder-open"></i> maintenance.cfm (Optional used when in maintenance mode, else defaults to pages)
   + <i class="fa fa-folder-open"></i> search.cfm (Optional used when doing searches, else defaults to pages)
 
 - <i class="fa fa-folder-open"></i> views (The folder that contains views for rendering)
 	 + <i class="fa fa-folder-open"></i> archives.cfm (MANDATORY: The view used to render out blog archives.)
 	 + <i class="fa fa-folder-open"></i> entry.cfm (MANDATORY: The view used to render out a single blog entry with comments, etc.)
 	 + <i class="fa fa-folder-open"></i> error.cfm (MANDATORY: The view used to display errors when they ocurr in your blog or pages)
 	 + <i class="fa fa-folder-open"></i> index.cfm (MANDATORY: The view used to render out the home page where all blog entries are rendered)
 	 + <i class="fa fa-folder-open"></i> notfound.cfm (The view used to display messages to users when a blog entry requested was not found in our system.)
 	 + <i class="fa fa-folder-open"></i> page.cfm (MANDATORY: The view used to render out individual pages.)
 	 + <i class="fa fa-folder-open"></i> maintenance.cfm (OPTIONAL: Used when in maintenance mode)

- <i class="fa fa-folder-open"></i> templates (The folder that contains optional templates for collection rendering that are used using the quick rendering methods in the CB Helper. See below for additional information)

  + <i class="fa fa-folder-open"></i> category.cfm (The template used to display an iteration of entry categories using coldbox collection rendering)
  + <i class="fa fa-folder-open"></i> comment.cfm (The template used to display an iteration of entry or page comments using coldbox collection rendering)
  + <i class="fa fa-folder-open"></i> entry.cfm (The template used to display an iteration of entries in the home page using coldbox collection rendering)

- <i class="fa fa-folder-open"></i> widgets (A folder that can contain layout specific widgets which override core ContentBox widgets)





