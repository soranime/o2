# What is it?

O2 is a WordPress Customizer library for adding custom controls to the Customizer such as:

- Color Palette
- Code Highlighter
- Icon Picker
- Radio Button
- Radio Images
- Range Slider
- Select
- Toggle

Just breathe.

# Documentation

## Installing and Setting up

- Just download this repository and dump it into your `inc` folder inside your theme folder.
- Once you download, just add this code to your functions.php file
```
define( 'O2_DIRECTORY', get_template_directory() . '/inc/o2/' );
define( 'O2_DIRECTORY_URI', get_template_directory_uri() . '/inc/o2/' );
```
- Once you add this code, you are ready for the next mess! Now you may include the toolkits provided by this package further.

## Color scheme palette for WordPress

Install the Color Palette toolkit by adding this line of code to functions.php file.
```
require get_template_directory() . '/inc/o2/controls/color-palette/color-palette-control.php';
```
And that’s all you need to do.

You can add it to your customizer by dumping this code into the `inc/customizer.php` or `functions.php` if you don't have customizer.php file:
```
$wp_customize->add_setting( 'o2_color_palette', array(
	'default' => 'green',
	'capability' => 'edit_theme_options'
));

$wp_customize->add_control(new O2_Customizer_Color_Palette_Control($wp_customize, 'o2_color_palette', array(
	'label' => __('Color Scheme', 'textdomain'),
	'description' => __('Choose a color scheme for your website.', 'textdomain'),
	'section' => 'colors',
	'choices' => array (
		'green' => array(
			'label' => 'Green',
			'colors' => array( '#bbdb9b', '#abc4a1', '#9db4ab', '#8d9d90', '#878e76' )
		),
		'purple' => array(
			'label' => 'Purple',
			'colors' => array( '#29274c', '#7e52a0', '#d295bf', '#e6bccd' )
		),
		'slate' => array(
			'label' => 'Slate',
			'colors' => array( '#b9bbbb', '#a2a3bb', '#5e5f87', '#b3b7ee', '#fbf9ff' )
		)
	),
	'priority' => 5,
	'settings' => 'o2_color_palette'
)));
```

For more info, you may consider this [5 minute read](http://www.hardeepasrani.com/2017/10/color-palette-control-for-wordpress-customizer/).

## Default Image alignment on WordPress Customizer

Install the Image Alignment toolkit by adding this line of code to functions.php file.
```
require get_template_directory() . '/inc/o2/controls/radio-buttonset/radio-buttonset-control.php';
```
And that’s all you need to do.

You can add it to your customizer by dumping this code into the `inc/customizer.php` or `functions.php` if you don't have customizer.php file:
```
$wp_customize->add_setting( 'o2_radio_buttons', array(
    'default' => 'left',
    'capability' => 'edit_theme_options'
));

$wp_customize->add_control(new O2_Customizer_Radio_Buttonset_Control($wp_customize, 'o2_radio_buttons', array(
    'label' => __('Image Alignment', 'textdomain'),
    'description' => __('Choose the alignment for your blog images.', 'textdomain'),
    'section' => 'your_section',
    'priority' => 5,
    'settings' => 'o2_radio_buttons',
    'choices' => array(
        'left' => __('Left', 'textdomain'),
        'center' => __('Center', 'textdomain'),
        'right' => __('Right', 'textdomain'),
        'none' => __('None', 'textdomain'),
    )
)));
```
For more info, you may consider this [tutorial](http://www.hardeepasrani.com/2016/08/radio-buttonset-control-for-wordpress-customizer/).

## Syntax Highlighter Control For WordPress Customizer

Install the Syntax Highlighter toolkit by adding this line of code to functions.php file.
```
require get_template_directory() . '/inc/o2/controls/code/code-control.php';
```
And that’s all you need to do.

You can add it to your customizer by dumping this code into the `inc/customizer.php` or `functions.php` if you don't have customizer.php file:
```
$wp_customize->add_setting( 'o2_code', array(
    'capability' => 'edit_theme_options'
));

$wp_customize->add_control(new O2_Customizer_Code_Control($wp_customize, 'o2_code', array(
    'label' => __('CSS', 'textdomain'),
    'description' => __('Your custom CSS.', 'textdomain'),
    'section' => 'your_section',
    'priority' => 5,
    'settings' => 'o2_code',
    'choices' => array(
        'language' => 'css',
        'theme' => 'icecoder',
    )
)));
```
For more info, you may consider this [tutorial](http://www.hardeepasrani.com/2016/06/syntax-highlighter-control-for-wordpress-customizer/).

## Font Awesome Icon Picker For WordPress Customizer

Install the Icon-Picker toolkit by adding this line of code to functions.php file.
```
require get_template_directory() . '/inc/o2/controls/icon-picker/icon-picker-control.php';
```
And that’s all you need to do.

You can add it to your customizer by dumping this code into the `inc/customizer.php` or `functions.php` if you don't have customizer.php file:
```
$wp_customize->add_setting( 'o2_fa_icon_picker', array(
    'default' => 'fa-facebook',
    'capability' => 'edit_theme_options'
));

$wp_customize->add_control(new O2_Customizer_Icon_Picker_Control($wp_customize, 'o2_fa_icon_picker', array(
    'label' => __('Icons', 'textdomain'),
    'description' => __('Choose an icon', 'textdomain'),
    'iconset' => 'fa',
    'section' => 'your_section',
    'priority' => 5,
    'settings' => 'o2_fa_icon_picker'
)));
```
It will a list of all the icons. If only want to list few icons then you can do it like this:
```
$wp_customize->add_control(new O2_Customizer_Icon_Picker_Control($wp_customize, 'o2_fa_icon_picker', array(
    'label' => __('Icons', 'textdomain'),
    'description' => __('Choose an icon', 'textdomain'),
    'iconset' => 'fa',
    'section' => 'your_section',
    'priority' => 5,
    'settings' => 'o2_fa_icon_picker',
    'choices' => array(
        'fa-facebook' => __('Facebook', 'textdomain'),
        'fa-twitter' => __('Twitter', 'textdomain'),
        'fa-dribbble' => __('Dribbble', 'textdomain'),
        'fa-wordpress' => __('WordPress', 'textdomain'),
        'fa-github' => __('Github', 'textdomain'),
    )
)));
```
For more info, you may consider this [tutorial](http://www.hardeepasrani.com/2016/05/font-awesome-icon-picker-for-wordpress-customizer/).

# Contribute

O2 lacks documentation. If you like the library and want to contribute, help with documentation will be appreciated.
