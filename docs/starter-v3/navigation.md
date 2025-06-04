---
layout: default
title: Navigation - Components
parent: Starter V3.0
---
# Starter V3.0: MMenu

## Overview

The navigation menu has been moved to a component-based setup. The starter includes 2 components:

*   `views/components/nav-menu.blade.php` - Standard drop-down navigation
*   `views/components/mega-menu.blade.php` - Mega menu/column-based navigation
*   To switch between the two, change the component in `partials/header.blade.php`
*   To make the menu span the width of the header content instead of the nav, remove the `relative` class from the top-level `<nav>` element in the mega menu component
*   The info column is built based on the menu item having an image in the `Info Column Image` field
*   **Mega menu classes (used in WP menu editor to build the mega menu, see screenshots):**
    *   `mmBlock` - Mega menu block, assigned to parent items
    *   `mmCol` - Mega menu column, assigned to child links that set up the columns
    *   `mmHead` - Mega menu header, assigned to other child links that become in-column section headers

## Navigation Images

### Front End Sample

![Front End Sample](/images/starter3-megamenu-frontend.png)

### Basic Menu Layout

![Basic Menu Layout](/images/starter3-megamenu-1-layout.png)

### Mega Menu Parent

![Mega Menu Parent](/images/starter3-megamenu-2-parent.png)

### Mega Menu Column

![Mega Menu Column](/images/starter3-megamenu-3-column.png)

### Mega Menu In-Column Section Heading

![Mega Menu In-Column Section Heading](/images/starter3-megamenu-4-column-section-heading.png)

### Mega Menu Info Block

![Mega Menu Info Block](/images/starter3-megamenu-5-info-column.png)