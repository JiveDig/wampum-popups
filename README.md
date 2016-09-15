# Slim Popups
A lightweight developer-based popups plugin utilizing on oiubounce.
* Use a simple function to create 1 or more popups (or slideups) throughout your website
* Various options allow fine-tuning
* Content template system allows clean and efficient loading of popup content

![Slim Popups modal example](assets/slim-popups-modal.png)

![Slim Popups slideup example](assets/slim-popups-slideup.png)

## Basic Usage
1. Create a directory in your theme called /slim-popups/
1. Include one or more files with your popup content
1. File location is /child-theme-name/slim-popups/my-file-name.php
1. Use CSS to style your content any way you'd like
1. Use the template tag/function in anywhere before or in wp_footer, to ensure js file has time to load

```
slim_popup( 'my-file-name' );
```

### Example with default settings

```
$options = array(
	'css'  	=> true, 	// whether or not to load the stylesheet
	'style'	=> 'modal', // 'modal' or 'slideup'
	'time'	=> '4000',  // time in milliseconds
	'type' 	=> 'exit',  // 'exit' or 'timed'
);
slim_popup( 'my-file-name', $options );
```

### Example showing the ability to use multiple/different popups on the same site. (Please don't be annoying!)

```
$options = array(
	'css'	=> true, 		// whether or not to load the stylesheet
	'style'	=> 'slideup', 	// 'modal' or 'slideup'
	'time'	=> '4000',  	// time in milliseconds
	'type'	=> 'exit',  	// 'exit' or 'timed'
);
$args = array(
	'cookieName' => 'customCookieName_2',
);
slim_popup( 'my-file-name', $options, $args );
```

## Full example

```
add_action( 'wp_footer', 'prefix_do_slim_popup' );
function prefix_do_slim_popup() {
	// Bail if not a single post
	if ( ! is_singular('post') ) {
		return;
	}
	$options = array(
		'css'	=> true, 		// whether or not to load the stylesheet
		'style'	=> 'modal', 	// 'modal' or 'slideup'
		'time'	=> '4000',  	// time in milliseconds
		'type'	=> 'exit',  	// 'exit' or 'timed'
	);
	$args = array(
    	'cookieName' => 'prefixCustomCookiePosts',
	);
    slim_popup( 'my-file-name', $options, $args );
}
```