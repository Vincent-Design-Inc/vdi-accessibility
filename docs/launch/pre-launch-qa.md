---
layout: default
title: Pre-Launch QA
parent: Launch
nav_order: "2"
---
[Original Google Doc](https://docs.google.com/document/d/1lOaxrz1EfKkC85CwM-lomJPM6_Ql08I5OlhMYoI7zdU/edit#heading=h.n15qgywbg022){: .btn .btn-outline .mt-4 }

# Pre-Launch QA
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## ❶ WCAG

All websites beginning in 2024 should be as accessible as possible. There are two main workflows, one for WCAG contracted websites, and one for the others. 

[Review Accessibility Page](/docs/processes/accessibility.html){: .btn .btn-outline }

## ❷ Browser Testing

All sites need to be properly functioning across 90-95% devices and browsers. Use local components and devices to test as many as you can, then use browserstack to test devices and browsers you don’t have access to. We should put together a master list for this. 

* <https://www.browserstack.com/screenshots>
* <https://preflight.com/cross-browser-testing>
* <https://www.browserstack.com/percy>
* Should find someone else’s checklist to use: [Example](https://www.gov.uk/service-manual/technology/designing-for-different-browsers-and-devices)

## ❸ SEO

Make sure you un-check the "discourage search engines" feature within the WordPress settings. 

We will do a more thorough SEO check after the website is launched with ahrefs. [Review SEO Page](/docs/processes/seo.html).

## ❹ Test Forms

Test all forms on the site, the number one most important functionality on most sites. Change the email sent to field to yours and make certain that emails are going out. 

This can be expanded in the future to have a more in-depth checklist.

## ❺ Plugins & Themes

Please remove any default WordPress themes, or, themes that you are not using. 

Make sure that all mandatory plugins are installed and running correctly. Please audit the plugins currently installed and remove anything we no longer need. This includes any default or automatically installed plugins. Our plugins page has more information.

[Review Plugins Page](/docs/processes/plugins.html){: .btn .btn-outline .mt-4 }
