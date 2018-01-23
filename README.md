# Cherry X Breadcrumbs module

Module adds breadcrumbs functionality

## How to use:

1. Copy this module into your theme/plugin
2. Add path to `cherry-x-breadcrumbs.php` file to `CX_Loader` initialization.
3. Initialize module on `wp` hook or later, Example:

```php
add_action( 'wp_head', 'twentyseventeen_breadcrumbs' );
function twentyseventeen_breadcrumbs() {
	new CX_Breadcrumbs( array(
		'separator'         => '&#47;',
		'before'            => '',
		'after'             => '',
		'show_mobile'       => true,
		'show_tablet'       => true,
		'wrapper_format'    => '<div>%1$s</div><div>%2$s</div>',
		'page_title_format' => '<h1 class="page-title">%s</h1>',
		'item_format'       => '<div class="%2$s">%1$s</div>',
		'home_format'       => '<a href="%4$s" class="%2$s is-home" rel="home" title="%3$s">%1$s</a>',
		'link_format'       => '<a href="%4$s" class="%2$s" rel="tag" title="%3$s">%1$s</a>',
		'target_format'     => '<span class="%2$s">%1$s</span>',
		'show_on_front'     => true,
		'network'           => false,
		'show_title'        => true,
		'show_items'        => true,
		'show_browse'       => true,
		'echo'              => true,
		'strings'           => array(
			'browse'              => esc_html__( 'Browse:', 'twentyseventeen' ),
			'home'                => esc_html__( 'Home', 'twentyseventeen' ),
			'error_404'           => esc_html__( '404 Not Found', 'twentyseventeen' ),
			'archives'            => esc_html__( 'Archives', 'twentyseventeen' ),
			'search'              => esc_html__( 'Search results for &#8220;%s&#8221;', 'twentyseventeen' ),
			'paged'               => esc_html__( 'Page %s', 'twentyseventeen' ),
			'archive_minute'      => esc_html__( 'Minute %s', 'twentyseventeen' ),
			'archive_week'        => esc_html__( 'Week %s', 'twentyseventeen' ),
			'archive_minute_hour' => '%s',
			'archive_hour'        => '%s',
			'archive_day'         => '%s',
			'archive_month'       => '%s',
			'archive_year'        => '%s',
		),
		'date_labels'       => array(
			'archive_minute_hour' => 'g:i a',
			'archive_minute'      => 'i',
			'archive_hour'        => 'g a',
			'archive_year'        => 'Y',
			'archive_month'       => 'F',
			'archive_day'         => 'j',
			'archive_week'        => 'W',
		),
		'action'            => 'cx_breadcrumbs/render',
		'css_namespace'     => array(),
		'path_type'         => 'full',
		'post_taxonomy'     => apply_filters(
			'cx_breadcrumbs/trail_taxonomies',
			array(
				'post' => 'category',
			)
		),
	) );
}
```

## Arguments:
`CX_Breadcrumbs` accepts an array of options with next structure:
* `separator` - separator between 
* `before` - HTML before breadcrumbs
* `after` - HTML after breadcrumbs
* `show_mobile` - Callback that returns array of all available fonts in next format - 'CSS font-family value' => 'Font name'. This is required option.
* `show_tablet` - registered options array
* `wrapper_format` - breadcrumbs & page title HTML markup
* `page_title_format` - Page title HTML format
* `item_format` - breadcrumbs items HTML format
* `home_format` - home link HTML format
* `link_format` - breadcrumbs links HTML format
* `target_format` - breadcrumbs target page HTML foramt
* `show_on_front` - show/hide breadcrumbs on home page
* `network` - works with network
* `show_title` - show/hide page title
* `show_items` - show/hide page breadcrumbs item
* `show_browse` - show/hide browse label
* `echo` - directly print breadcrumbs or return
* `strings` - array of strings for translations
* `date_labels` - date labels format
* `action` - action name to show breadcrumbs on
* `css_namespace` - CSS namespace array
* `path_type` - full/minified breadcrums path type
* `post_taxonomy` - supported taxonomies array (allows to build parent/child trail for taxonomy)

## Strings array structure:
`browse`
`home`
`error_404`
`archives`
`search`
`paged`
`archive_minute`
`archive_week`
`archive_minute_hour`
`archive_hour`
`archive_day`
`archive_month`
`archive_year`
