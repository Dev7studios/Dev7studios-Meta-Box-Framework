# Dev7studios Meta Box Framework

A simple WordPress meta box framework for creating custom meta boxes in your themes and plugins.

## Usage

1. Download `dev7_meta_box_framework.php` to your theme/plugin folder
2. Open up functions.php (or equivelant plugin file) and do the following:

```php
include('dev7_meta_box_framework.php');

function add_custom_meta_boxes() {
	$meta_box = array(
		'id'         => 'dev7_page_settings', // Meta box ID
		'title'      => 'Page Settings', // Meta box title
		'pages'  	 => array('post', 'page'), // Post types this meta box should be shown on
		'context'    => 'normal', // Meta box context
		'priority'   => 'high', // Meta box priority
		'fields' => array(
			array(
	            'id' => 'text',
	            'title' => 'Text',
	            'desc' => 'This is a description.',
	            'type' => 'text',
	            'std' => 'This is std'
	        ),
	        array(
	            'id' => 'textarea',
	            'title' => 'Textarea',
	            'desc' => 'This is a description.',
	            'type' => 'textarea',
	            'std' => 'This is std'
	        ),
	        array(
	            'id' => 'select',
	            'title' => 'Select',
	            'desc' => 'This is a description.',
	            'type' => 'select',
	            'std' => 'green',
	            'choices' => array(
	                'red' => 'Red',
	                'green' => 'Green',
	                'blue' => 'Blue'
	            )
	        ),
	        array(
	            'id' => 'radio',
	            'title' => 'Radio',
	            'desc' => 'This is a description.',
	            'type' => 'radio',
	            'std' => 'green',
	            'choices' => array(
	                'red' => 'Red',
	                'green' => 'Green',
	                'blue' => 'Blue'
	            )
	        ),
	        array(
	            'id' => 'checkbox',
	            'title' => 'Checkbox',
	            'desc' => 'This is a description.',
	            'type' => 'checkbox',
	            'std' => 1
	        ),
	        array(
	            'id' => 'checkboxes',
	            'title' => 'Checkboxes',
	            'desc' => 'This is a description.',
	            'type' => 'checkboxes',
	            'std' => array(
	                'red',
	                'blue'
	            ),
	            'choices' => array(
	                'red' => 'Red',
	                'green' => 'Green',
	                'blue' => 'Blue'
	            )
	        )
		)
	);
	dev7_add_meta_box( $meta_box );
}
add_action( 'dev7_meta_boxes', 'add_custom_meta_boxes' );
```

Then in your theme/plugin simply use `get_post_meta()`. For example:

```php
$my_field = get_post_meta(get_the_ID(), 'my_field_id', true);
```

A field has the following structure:

* `id` (required) - The ID of the field (must be unique)
* `title` - The title of the field
* `desc` - The field description
* `type` (required) - The type of field (see list below)
* `std` - The default value of the field
* `choices` - An array of key-value pairs for fields with multiple choices (e.g. radio, select, checkboxes)

Possible field types are:

* text
* textarea
* select
* radio
* checkbox
* checkboxes

## Credits

The Dev7studios Meta Box Framework was created by [Gilbert Pellegrom](http://gilbert.pellegrom.me) from [Dev7studios](http://dev7studios.com).

Please contribute by reporting bugs and submitting pull requests. Released under the MIT license.
