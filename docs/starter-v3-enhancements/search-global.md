---
layout: default
title: Search - Global
parent: Starter V3.0 - Enhancements
---

{: .note }
This is a living document subject to change as this feature is currently a work in progress.

# Global Website Search Form
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## File Structure Overview

### Global Website Search Form

- `views/form/search.blade.php`
    - Contains the markup. See the Markup section of this documentation for more information.
    - Includes inline Tailwind styles. See the Styling section of this documentation for more information.
    - Includes a class of `global-search-form` in order to add theme support for HTML5 markup in the `setup.php` file.

## Markup

### search

    <search role="search">

The main search form is inside a [`<search>` element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/search) with a [`role` of "search"](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/search_role) to introduce redundancy to support older screen reader software. The search element is relatively new, and it seems to be supported without issue. [Read more on the search element](https://www.scottohara.me/blog/2023/03/24/search-element.html) from Scott O'Hara, an editor of ARIA and HTML specification.

### form

    <form>

Other than our styling, it has a [method](https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data#the_method_attribute) of `get` and an [action](https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data#the_action_attribute) of `home_url('/')`. This is the default WordPress form setup for a website search. 

Note that we do not need a role of search, since our outer containing element already takes care of this.

### label

	<label for="globalSearch">

We are using a [`for` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/for) so we can assign this label to our `<input>` with the matching ID.

In this instance, our label content is an SVG search icon marked up to expose its accessible name as the content for the label. Iconography is always a great way to give quick visual indication for well established website functions. 

This is acceptable for meeting WCAG Level AA. An additional text-based label is not required if the button for the input already describes the purpose. [Reference: WCAG Technique G167](https://www.w3.org/WAI/WCAG22/Techniques/general/G167). 

### input

	<input id="globalSearch" type="search" placeholder="" name="s">

WordPress requires a `name` attribute of "s". 

We are setting [input `type="search"`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/search) so that we can benefit from browser defaults such as stripping line breaks and a search icon as an enter key on some mobile browsers.

Placeholder value is empty in order to support visitors who may confuse placeholder content with an already filled input. We are already reinforcing this search feature with a magnifying glass icon, and, the word "search" in the button which will have sufficient contrast (placeholders normally don't). 

Placeholder values for a search field are also tricky, since they are for showing an example of the type of content expected in the field. Search fields can contain a wide range of content, so showing an example of expected content is not normally helpful in this scenario.

## Styling

### Methods

All styling is accomplished with:
- Inline Tailwind utility classes
- Global (base.css) Tailwind(?) styles
- Custom global classes
	- `outline-default`
	- `global-search-form`

### Appearance

We have a minimum width pre-set for between 25 and 35 characters shown at a time. [WebAIM recommends](https://webaim.org/techniques/sitetools/) this threshold in order for most searches to be fully displayed without getting cut off. You may need to adjust this for your project depending on the typeface glyph width and font size.

## Content

	esc_attr_x('Search', 'search-label', 'sage')
	esc_attr_x('Search', 'search-submit', 'sage')

We have two translatable strings in this component. One for a the search label (search-label) and one for the search submit button (search-submit). 

