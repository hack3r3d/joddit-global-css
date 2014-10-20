joddit-global-css
=================

This is a fork of the Joddit Global CSS WordPress plugin. This version works correctly with WordPress 4.

The problem with the official release of this WordPress plugin is that it uses the WP_List_Table class that comes
with WordPress and you aren't supposed to do that.

According to the WordPress documentation, plugin and theme developers are supposed to make a copy of the version
of WP_List_Table and include it with the plugin or theme that needs it. The one included with WordPress is 
subject to change and will break code that relies on it. That's what happened with Joddit Global CSS.

So I made a copy of the version of WP_List_Table (class-wp-list-table.php). I changed the name of the class
from WP_List_Table to My_List_Table to avoid collisions with WordPress core and other plugins or themes that could
load WP_List_Table.

You can see my version of WP_List_Table in lib/class-wp-list-table.php. I made one tweak to joddit-global-css.php.

In jgcss_admin_init, I'm loading my class-wp-list.php instead of WordPress's like this:

```
if(!class_exists('My_List_Table')){
  require_once( JGCSS_PATH . 'lib/class-wp-list-table.php' );
}
```
