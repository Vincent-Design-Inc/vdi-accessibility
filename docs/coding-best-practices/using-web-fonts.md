---
layout: default
title: Using web fonts the Sage/Tailwind way
parent: Coding Best Practices
---

# Using web fonts the Sage/Tailwind way

This is how we should be importing web fonts.  If you’re doing it any other way (`@import` in a css file, `<link>` in a HTML file, etc>), it will still work, but it’s not best practices.  These instructions are specific to Google Fonts, but should be similar for any service that uses a CSS style sheet to add fonts.

### Get your Google Font stylesheet link

1. Go to [Google Fonts](https://fonts.google.com/) and pick out the font(s) you need for your Project,
2. Click the “Get embed code” button in the upper-right of the page.
3. Make sure you're on the Web tab (it should be selected by default) and the `<link>` option is selected
4. Copy ONLY the URL from the last line in the code.

![Screenshot 2024-08-01 at 14-59-40 Selection - Google Fonts.png](/images/Screenshot_2024-08-01_at_14-59-40_Selection_-_Google_Fonts.png)

![Screenshot 2024-08-01 at 15-02-21 Selection Embed Code - Google Fonts.png](/images/Screenshot_2024-08-01_at_15-02-21_Selection_Embed_Code_-_Google_Fonts.png)

### Add stylesheet link to Sage setup

Open the `app\setup.php` file.  If it doesn’t exist, add the following directly below the `include 'helpers.php';` line:

```php
/**
 * Add preconnect for Google fonts to head
 *
 * @return void
 */
add_action('wp_head', function () {
?>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<?php
}, 0);
```

In the “Register the theme assets” and “Register the theme assets with the block editor” sections, replace both instances of `https://use.typekit.net/lfw8vhb.css` with the URL you copied from Google Fonts.  It should look something like this:

```php
add_action('wp_enqueue_scripts', function () {
    bundle('app')->enqueue();

    // Remove WP default styles
    wp_dequeue_style('wp-block-library');
    wp_dequeue_style('wp-block-library-theme');

    // This is fairly hacky, but it solves the problem of not having WP default styles for things like paragraph alignment defined.
    wp_enqueue_style('default-styles', '/wp-includes/css/dist/block-library/style.min.css', false, null);

    wp_enqueue_style('google-font', 'https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap', false, null);
}, 100);

/**
 * Register the theme assets with the block editor.
 *
 * @return void
 */
add_action('enqueue_block_editor_assets', function () {
    bundle('editor')->enqueue();

    wp_enqueue_style('google-font', 'https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap', false, null);
}, 100);
```

### Add font(s) to Tailwind config

Open the `tailwind.config.js` file.  In the `Extend: {...}` section, update the `fontFamily` object with the info for your font(s).  It should look something like the following:

{: .note }
If your font name has a space, you will need double quotes inside the single quotes in the object.  For example, a font named “Some Font” would be added like this: ‘”Some Font”’

```jsx
fontFamily: {
  'fontello': 'fontello',
  roboto: [
    'Roboto',
  ],
  sans: [
    'Roboto',
    'system-ui',
    '-apple-system',
    'BlinkMacSystemFont',
    '"Segoe UI"',
    '"Helvetica Neue"',
    'Arial',
    '"Noto Sans"',
    'sans-serif',
    '"Apple Color Emoji"',
    '"Segoe UI Emoji"',
    '"Segoe UI Symbol"',
    '"Noto Color Emoji"',
  ],
},
```

You can add other font definitions, for example, a second font as `secondary`, or a serif font as `serif`, etc.  Tailwind uses the `sans` font stack for it’s default, so as long as your font is listed first in the `sans` array, that will be the default font for your site.  Adding the fonts here let you do things like applying a specific font using a Tailwind class, like `font-roboto` using the example above.
