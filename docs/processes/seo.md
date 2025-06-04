---
layout: default
title: SEO
parent: Processes
---
{: .note }
This is a living document subject to change as this process is currently a work in progress.

# Basic SEO: Ahrefs Site Audit
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## What is Ahrefs?

Ahrefs is a software suite that covers a wide range of website SEO tools. It can run automated website audits to find SEO issues, as well as give ranking, keywords, and competitor insights. We'll be focusing on development related issues to resolve before launch using the ["Site Audit" tool](https://ahrefs.com/site-audit).

{: .note}
The marketing team will have a wider range of knowledge on functionality and features within Ahrefs. That said, if you run into any issues that are not outlined here and you are not sure what to do, or, just have other questions, ask Keith & Sarah. 

## Access, Add Site & Run Audit

There is a single shared login for the whole VDI team to access Ahrefs. 
1. In Bitwarden, search for "ahrefs", the email address will be "radio@..."
2. Each new IP address login will trigger a 2FA check
	- Contact one of several people set up to receive these: Keith, Sarah, Faith, Holly.
	- You will receive a link from one of them to confirm new log in location
3. [Add your site to Ahrefs](https://help.ahrefs.com/en/articles/1433362-how-to-add-a-project-in-your-dashboard)
	- Follow "Method 1: Importing from GSC"
4. Navigate to the "Site Audit" tab for your newly added site, and run an audit.
5. Check the site health score. If it is above 90, just check for any really bad errors, otherwise, proceed with improving the score until it hits 90.

## Ahrefs Site Audit Walkthrough
### Orphan Pages
Ahref examples (not all-inclusive):

![](/images/orphan-page.png)
#### What

An orphan page is just a page that isn't linked anywhere on the website. This means that visitors won't be able to find this page unless they are given the URL directly, or, it's found on the website search.
#### Why

Any pages in the orphan page list should have a clear purpose of why it needs to be there. Sometimes campaigns are run with really specific landing pages, and we don't want those to be in the site navigation. Normally, anything flagged as an orphan simply just needs to be added to the navigation.
#### To Do

To decide what to do with an orphan page, you may want to refer to the [Ahrefs decision tree](https://ahrefs.com/blog/orphan-pages/#how-to-fix-orphan-pages), as well as discussing with other project team members (content team mainly).

Anything that needs to be an orphan can be noted in your audit notes (within the GitHub Issue) so that we have a clear picture of the website during launch at post-launch. 

### X Missing, Empty, Duplicates
Ahref examples (not all-inclusive):

![](/images/meta-description.png)
![](/images/h1-missing.png)
![](/images/h1-multi.png)
![](/images/title-missing.png)
#### What

The element or attribute could be completely missing, or could be empty, or could have more than the allowed amount (1) for the following:
- H1
- Title
- Meta Description
- Document/HTML Language

#### Why

The language of the HTML document must be declared (using the [`lang` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/lang)), and it must contain a valid language tag. If the site is multi-language, this tag needs to change when the language changes. 

The meta description and title is automatically generated with our SEO plugin of choice (The SEO Framework), so these should not be coming up as missing, empty, or duplicated.

There needs to be a singular H1 (level 1 [heading element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements)) for each website page. Most sites are built in such a way that zero or multiple H1 elements can be accepted page content. This is considered user-error and needs to be corrected. 
#### To Do

Check that the plugin "The SEO Framework" is installed, set up, and running correctly. The theme should not be manually declaring a title or meta description, and there should be no other SEO related plugins installed. 

Check that the file(s) generating the document `<head>` declare the document language. If not, add it, or check that the translation plugin is correctly configured to be adding/updating it. 

Manually resolve content on pages where H1 issues have been indicated. If the path forwards is not clear, you may need to discuss solutions with other project team members (content team mainly).

### Redirects
Ahref examples (not all-inclusive):

![](/images/3xx-redirect.png)
![](/images/302-redirect.png)
![](/images/links-to-redirect.png)
![](/images/broken-redirect.png)
![](/images/image-redirect.png)
![](/images/no-incoming.png)
![](/images/redirect-chain.png)
![](/images/sitemap-redirect.png)
#### What

There are quite a few issues that fall under this "redirects" umbrella. We'll be resolving all flagged [300 range HTTP status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#redirection_messages) and other issues names with "redirect" in the title.
#### Why

On new websites this is not a common issue since we usually won't have any redirects set up. On sites with old/existing content that was migrated, this will become more of an issue. 

Linking to a URL that then gets redirected to another one just takes more time and server resources, slowing down the experience. In general, people should only be reaching a URL that gets redirected if they've bookmarked it, or, if it was on old printed material. 

Redirects aren't *bad*, but we don't want to launch a brand new website with internal links to redirected URL's.
#### To Do

You can do a page content search (ctrl + F) for the word "redirect" on the final audit page.

If this is a new website with new content, there should be **no** internally linked redirects. If there is some older content, you will likely be able to resolve all issues without bringing in the content team or the client. Ahrefs will be able to give you enough information on each error/warning type in order for you to make a call on how to resolve. 

Resolving it usually looks like manually editing a link destination to directly go to the page it's redirecting to. 

If this is a website with a *lot* of older content, this task may get out of hand quickly with hundreds of issues. If so, reach out to Keith.
### 4xx Errors
Ahref examples (not all-inclusive):

![](/images/4xx-page.png)
![](/images/404-page.png)

--- coming soon ---

### Http
Ahref examples (not all-inclusive):

![](/images/https-to-http.png)
![](/images/https-to-http-2.png)
![](/images/mixed-content.png)
#### What

HTTP related errors and warnings stem from any link printed with "http://..." instead of "https://...". 

#### Why

Generally, we'll be serving our sites using an HTTPS connection, so we want everything on our site to be as well. Sometimes old links after upgrading to HTTPS were never corrected, or, we're using old embedded content that has not been updated. 
#### To Do

Resolve all HTTP related issues, you may do a page content search (ctrl + F) for the word "http". You may also be able to use [WPEngine's "secure all URLs" options](https://wpengine.com/support/add-ssl-site/#Secure_URL_Options). 

If there's anything here you cannot manually resolve (check out Ahrefs "why and how to fix" for more information) reach out to Keith to see if there's anything we can do. Sometimes old integrations just do not have an HTTPS option and we'll need to devise a communication plan.

## Missing alt text
Ahref examples (not all-inclusive):

![](/images/missing-alt-text.png)

Generally, alternative text for images needs to be written unless it is a purely decorative image. Some images also have a context that requires an alternative text different to a description of image content. 

You may refer to, or refer others to:
- The [WCAG alt Decision Tree](https://www.w3.org/WAI/tutorials/images/decision-tree/).
- Adrian Roselli's article: "[My Approach to Alt Text](https://adrianroselli.com/2024/05/my-approach-to-alt-text.html)" which contains a large amount of additional resources that are excellent as well.

If there are only a few issues (under 10) you may choose to just write these yourself if you are confident you can do so correctly. Depending on the website scope, you may also choose to leave this for someone else. If in doubt, ask Nicky. 

If this is a large issue, you will need to communicate this with the other project team members in order to determine who will be completing the work and what standards it must contractually reach. Some of this work may also fall to the client.

Regardless, we'll want to export (CSV) the report of all missing alt text and attach it to the ongoing GitHub Issue. This way we can send this information to a wide range of people without having to go back into Ahrefs each time.

![](/images/alt-text-export.png)

## Ahrefs Site Audit Checklist

This checklist can be used after you have a good understanding of the overall process and only need a simple checklist to guide you.

1. Resolve the following list of issues:
	- [ ] Orphan pages
	- [ ] 3xx errors, redirect issues
	- [ ] 4xx errors, did not respond issues
	- [ ] Missing, Empty or Duplicate issues for H1, Title, Meta Description, Language
	- [ ] Http flags
	- [ ] URL formatting issues like double slashes
	- [ ] Large images
2. Export report for missing alt text; Include in your notes in the GitHub Issue.
3. Check for any leftover Site Audit Errors (red '!' triangle symbol), and resolve these.
4. Time allowing, move to other Site Audit Warnings (yellow 'i' circle symbol).