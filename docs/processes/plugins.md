---
layout: default
title: Plugins
parent: Processes
---

# Typical plugins

{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Plugin use

Generally, we should be trying to use as few plugins as possible.  Anything we can realistically build ourselves, we should.  If we can’t, plugins can be used, but **BEFORE** any plugin is installed, it has to be vetted for accessibility, performance, and security.  There have been too many instances where a plugin has been picked fails these criteria.  This is a waste of time and money.  If a plugin can't be made accessible, performant, or secure, it can't be used unless there is a compelling reason (for example, Instagram or other social feeds).

If a plugin is **not** on this list, it does not need to be installed in an activated or deactivated state.

See [https://github.com/Vincent-Design-Inc/typical-wordpress-plugins](https://github.com/Vincent-Design-Inc/typical-wordpress-plugins) for more info on typical plugins.

## Always in use: Live & Dev

* ACF Pro <span class="label label-purple">licensed</span> [Download](/files/advanced-custom-fields-pro.zip)
* Akismet <span class="label label-purple">licensed</span>
* Simple History
* Imagify <span class="label label-purple">licensed</span>
* The SEO Framework

## Always in use: Live

* Google Site Kit

## As needed: Dev

* Better Search Replace <span class="label label-red">Use with caution</span>
* Equalize Digital: Accessibility Checker [Download](/files/accessibility-checker-pro-1.8.1.zip)

## As needed: Live & Dev

* Gravity Forms <span class="label label-purple">licensed</span> [Download](/files/gravity-forms.zip)
  * [How to make Gravity Forms meet WCAG V2.2 AA](/docs/processes/gravity-forms).
* Updraft Plus
* WP Rocket <span class="label label-purple">licensed</span>
* Redirection (for 301 and other redirects)

## Other helpful plugins

* [Change Admin Email](https://wordpress.org/plugins/change-admin-email-setting-without-outbound-email/) - Change the admin email in WordPress without needing a confirmation email.
* [Export media with selected content](https://wordpress.org/plugins/export-media-with-selected-content/) - Add media to selective exports in WordPress
* [Database Management tool - Adminer](https://wordpress.org/plugins/pexlechris-adminer/) - Adds the Adminer database management tool to WordPress <span class="label label-red">DANGER!! - DO NOT LEAVE THIS PLUGIN ACTIVE!!</span>
  * This will give anyone with an admin login direct database access.  It should only be used in situations where Better Search Replace is too limited (which should not be very often).  Use it and delete it when you’re done.
* [ACF Quick Edit Fields](https://wordpress.org/plugins/acf-quickedit-fields/) - Add quick edit and bulk edit functionality to ACF content.
* [Find My Blocks](https://wordpress.org/plugins/find-my-blocks/) - Show all blocks that are being used on a site.  Good for tracking down theme blocks that are no longer needed.
