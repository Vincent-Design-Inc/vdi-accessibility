---
layout: default
title: Accessible Navigation Markup
grand_parent: Starter V3.0 - Enhancements
nav_order: 2
parent: Navigation
---
# Navigation: Accessible Markup
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## nav

`<nav class="nav-main" role="navigation" aria-label="Main">`

The main navigation element is a [`<nav>` element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/nav) with:

- An [`aria-label` attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label) of "Main".
- A [`role` of "navigation"](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/navigation_role) to introduce redundancy to support older screen reader software.

This follows best practices of main website navigation elements being contained in a `<nav>` and appropriately labeled so that as many screen readers as possible can differentiate between all navigation elements. 

The label does not need to include the word "Navigation" since the HTML element and role already announce this.

## ul

`<ul>`

`<ul class="menu-vdi__submenu">`

The links are contained in an unordered list so we can easily convey nested hierarchy for secondary and tertiary navigation items. Currently, there is no handling of tertiary navigation  elements.

We are hiding and showing this unordered list instead of the nav element when moving to mobile navigation. This is so that the nav is discoverable by assistive technology on page load.

## a

`<a href="https://yourwebsite.com/page" aria-current="false">`

Links are marked as such using an anchor element.

Current page is indicated using the [`aria-current` attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-current). It is marked either “page” or “false”. This attribute should be used to style the current page differently.

## button

### Use 1: Primary Navigation Items

```
<button aria-expanded="false" class="menu-vdi__toggle">
	{{ $item->title }}
	<svg...
```

Primary navigation items that open up secondary navigation are marked as [buttons](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button), not [links](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a).

Both labels (accessible and visual) match and is the text displayed on the screen.

### Use 2: Main Navigation Toggle

```<button id="navMainToggle" aria-label="Menu" aria-expanded="false">```

The mobile menu toggle functionality is marked using a [button](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button).

Its visual label is generally going to be a three lined “hamburger” icon. For sites with one navigation being controlled with a toggle, we can label it with an [`aria-label` attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label) of “Menu”. **If we have more than one, its accessible label will match the name of the navigation it controls.**

Using an aria-label means that everything inside the button (text, icons, etc.) should not have any names or labelling.

### General

Buttons generally do not receive the pointer [cursor](https://developer.mozilla.org/en-US/docs/Web/CSS/cursor), which according to specification is used to indicate a link. However, in this context we force a pointer cursor since the styling is ambiguous.

Functionality communication is further enforced with the [attribute `aria-expanded`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-expanded). It is toggled dynamically using javascript.

Please note that we are *not* using the aria-haspopup attribute. It is only intended for use with `menu`, `listbox`, `tree`, `grid` or `dialog` elements/roles. The [`menu` element/role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/menu_role) is for use in more complex scenarios than a list of links for website navigation. It also comes with different interaction expectations.
