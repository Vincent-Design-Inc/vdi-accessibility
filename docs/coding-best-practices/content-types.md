---
layout: default
title: WordPress Content Type Handling
parent: Coding Best Practices
---

# How to handle various content types in WordPress

By default, WordPress includes content types for Posts and Pages, while giving you the ability to add custom types as needed. This document will outline how to handle these content types and others in WordPress.

## A basic outline of the various content types included in WordPress and our theme
- Posts - "Generic" content type for blog posts, news, etc.  Supports tags and categories, but can have custom taxonomies attached.
- Pages - "Static" content type for pages that don't change often.  Can have custom taxonomies attached, but generally don't.
- Testimonials - Included in our starter.  A custom content type for testimonials.  Mainly included to serve as a boilerplate for building your own content types as needed.

## How to handle content types in your theme

### General considerations
For most sites we build, you won't need anything beyond Posts and Pages.  However, for any content that is more specific than a news or blog post, it should always live in a custom post type.  There is almost never a good reason to put a specific content type (for example, Events) into Posts and rely on categories or tags to differentiate it.  Not only does this cause issues for development (filtering those posts out of the main blog/news feed, for example), but it also makes it harder for the client to manage their content (having to remember to add the proper category, for example).

A good example of this would be an "Events" content type.  This content type could have fields for the event date, location, ticket info, etc.  It could also have a taxonomy for the event type (class, conference, etc).  This would allow the client to easily manage their events and display them on the site in a way that makes sense for that content.  Even if the content is styled exactly the same as what a blog/news post would be, it should still be in a custom post type.  It's not a matter of presentation, but of the content being inherently different.

### How to create a custom content type
The easiest way is to duplicate the `app/Include/testimonials.php` file and modify it to suit your needs.  You'll need to change the name of the post type (in the `register_post_type` function call), the labels, and the arguments.  Once you've done that, your new post type should show up in the admin, ready to populate.

If you'd rather build it yourself, you can use [this generator](https://generatewp.com/post-type/) to create the code for you.  You can then paste that code into a file in the theme's `app/Include` folder, making sure to follow the outline below.

```php
<?php
/**
 * On init...
 */
add_action('init', function () {
    /**
     * Register custom content type.
     */
    $labels = array(
      // Add your labels from GenerateWP here
    );

    $args = array(
      // Add your args from GenerateWP here
    );

    register_post_type('content_type', $args);
}, 0);
```
