# What's New With 2.1.0

ContentBox 2.1.0 is a minor release with some great new functionality and tons of fixes.  

## Release Notes
                
<h2>        Bugs Squashed
</h2>
<ul>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-424'>CONTENTBOX-424</a>] -         ContentBox express won&#39;t start on Windows
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-502'>CONTENTBOX-502</a>] -         Import Error When Using a Number as the Value in a Custom Field
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-517'>CONTENTBOX-517</a>] -         Application/zip needs to be added to upload mime types.
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-518'>CONTENTBOX-518</a>] -         Default keyword  parsing error on CF9
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-521'>CONTENTBOX-521</a>] -         Content services search() ignores sortOrder when filtering
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-523'>CONTENTBOX-523</a>] -         ConfirmIt actions not attached to right class element on many confirmations
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-524'>CONTENTBOX-524</a>] -         Global quick search links to ContentStore are not correct.
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-525'>CONTENTBOX-525</a>] -         The cb.isArchivesView() function incorrectly returns false when browsing archives
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-530'>CONTENTBOX-530</a>] -         Tabs don&#39;t stick on related content dialog for some reason
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-531'>CONTENTBOX-531</a>] -         Default content search results produces invalid html
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-534'>CONTENTBOX-534</a>] -          Categories bi-directional relationship has cascade delete effect on related content, not targeted content.
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-535'>CONTENTBOX-535</a>] -         Comments fields need to be trimmed to right db input size
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-540'>CONTENTBOX-540</a>] -         Apache rewrites don&#39;t work in sub directory
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-543'>CONTENTBOX-543</a>] -         sub page menu was not correctly passing activeShowChildren flags and incorrectly activating elements
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-544'>CONTENTBOX-544</a>] -         Issue with importing contents from another contentbox site
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-546'>CONTENTBOX-546</a>] -         Error deleting multiple blog comments
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-547'>CONTENTBOX-547</a>] -         rendering widget must not execute on search, or editing only on display views
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-550'>CONTENTBOX-550</a>] -         If a user set&#39;s an editor preference and the editor does not exist, exception is thrown
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-552'>CONTENTBOX-552</a>] -         Folder appending on secured url redirections
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-553'>CONTENTBOX-553</a>] -         Sort ordering needs to have url decoding or else it fails
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-555'>CONTENTBOX-555</a>] -         Exception on security reminders as missing resource bundle coming from security
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-569'>CONTENTBOX-569</a>] -         Linking to blog entry breaks if title has single tick
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-570'>CONTENTBOX-570</a>] -         Error when filtering by parent for ContentStore
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-574'>CONTENTBOX-574</a>] -         cbBootstrap not found in application scope on railo on first server hit
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-579'>CONTENTBOX-579</a>] -         Turn off this.compression for railo to avoid proxy errors, and allow user to turn as they see fit.
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-582'>CONTENTBOX-582</a>] -         RSS Exception on invalid XML content format for pages
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-586'>CONTENTBOX-586</a>] -         Railo provider not sending right attributes to cfthread for clearing by key snippets
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-588'>CONTENTBOX-588</a>] -         manual uploader rc variable not properly scoped
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-590'>CONTENTBOX-590</a>] -         Search display does not link to editor but actual UI links, this is wrong
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-592'>CONTENTBOX-592</a>] -         drag handle on pages not working on click
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-593'>CONTENTBOX-593</a>] -         JSMIN css * selector missing space
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-595'>CONTENTBOX-595</a>] -         Captcha needs expires headers to be delivered correctly
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-596'>CONTENTBOX-596</a>] -         Exception on page type on AOP&#39;ed save operations due to return type
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-602'>CONTENTBOX-602</a>] -         preview does not work for inherited layouts
</li>
</ul>
                        
<h2>        Improvements
</h2>
<ul>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-430'>CONTENTBOX-430</a>] -         Move Comment Settings to Main Settings Area
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-529'>CONTENTBOX-529</a>] -         On Related Content Dialog, make sure page slugs are shown to denote location on hierarchy
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-532'>CONTENTBOX-532</a>] -         Selectors for contentstore, pages and entries can use double click for certain selections
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-537'>CONTENTBOX-537</a>] -         Add ability to pass ul and li styles to the menu builders in the CB Helper
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-538'>CONTENTBOX-538</a>] -         drag and drop reordering UI improvements
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-539'>CONTENTBOX-539</a>] -         Sitemap wording more prominent and homepage display
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-554'>CONTENTBOX-554</a>] -         Updated semantic version and semantic version update changes for updater to comply to semantic standards
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-556'>CONTENTBOX-556</a>] -         Module execution now accounts if the module sets an internal view fro rendering.
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-578'>CONTENTBOX-578</a>] -         Remove import statements on Application.cfc to avoid Railo scope issues
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-584'>CONTENTBOX-584</a>] -         Add x-forwarded-proto checks on isSSL() verifications to allow for proxy configuraitons
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-589'>CONTENTBOX-589</a>] -         better unique locking strategy for multi-app deployments
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-599'>CONTENTBOX-599</a>] -         Allow Content layout to be set to &quot;-No Layout-&quot;
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-600'>CONTENTBOX-600</a>] -         Testing widget should save
</li>
</ul>
        
<h2>        New Features
</h2>
<ul>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-428'>CONTENTBOX-428</a>] -         SSL Option for Pages
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-478'>CONTENTBOX-478</a>] -         Localized DSN Creator
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-520'>CONTENTBOX-520</a>] -         Add creator to content services search() methods
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-522'>CONTENTBOX-522</a>] -         Add creator filtering on all content object panels
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-533'>CONTENTBOX-533</a>] -         Add a remember me for: session, day, etc on the ContentBox Admin login
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-536'>CONTENTBOX-536</a>] -         Widget to show child page menus: SubPageMenu
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-541'>CONTENTBOX-541</a>] -         Content store items can now have hierarchy
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-542'>CONTENTBOX-542</a>] -         Add bot protection for hits + session management
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-548'>CONTENTBOX-548</a>] -         Base content gets new property: showInSearch, which allows the ability to turn content on/off for searches
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-549'>CONTENTBOX-549</a>] -         EditorService new methods: hasEditor() and hasMarkup, to validate if editors and markups exist
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-551'>CONTENTBOX-551</a>] -         Add Create new Content store to global creation menu
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-557'>CONTENTBOX-557</a>] -         Versions now get two new interception points: cbadmin_onVersionIndex, cbadmin_onVersionDiff
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-581'>CONTENTBOX-581</a>] -         Lucee Support
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-583'>CONTENTBOX-583</a>] -         Cache entry keys need to contain the http host they are on to support multi-site capabilities
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-591'>CONTENTBOX-591</a>] -         JSMin less upgrade libraries
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-594'>CONTENTBOX-594</a>] -         RSS Feed static settings can now be set at the settings level thanks to Akitogo
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-597'>CONTENTBOX-597</a>] -         Track login attempts to Contentbox
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-598'>CONTENTBOX-598</a>] -         Reset hit counts on a piece of content and in bulk
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-603'>CONTENTBOX-603</a>] -         Request rate limiting security
</li>
<li>[<a href='https://ortussolutions.atlassian.net/browse/CONTENTBOX-604'>CONTENTBOX-604</a>] -         ability to render rc/prc variable right into content via ${rc:key} or ${prc:key} markup
</li>
</ul>
                        