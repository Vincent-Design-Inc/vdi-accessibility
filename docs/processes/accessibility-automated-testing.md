---
layout: default
title: Automated Testing
parent: Accessibility
grand_parent: Processes
---
# Automated Accessibility Testing

{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

{: .note }
There is a large amount of web accessibility misinformation online. Not all resources can be trusted for accurate information.

## What is automated testing?

Automated accessibility testing is a set of fixed tests to find specific issues with the code. It can significantly speed up the process of checking for content-related accessibility issues, colour contrast issues, and syntax related code issues.

| Positives                                                                | Negatives                                                             |
| :----------------------------------------------------------------------- | :-------------------------------------------------------------------- |
| No training required                                                     | Produces any amount of false positives<br>and can miss many issues    |
| Immediate                                                                | Can't provide context-aware solutions                                 |
| Can be faster and more thorough  <br>than manual testing (in some tests) | Can't give you a full picture of a<br>website's current accessibility |
|                                                                          | Can be incredibly expensive                                           |

{: .warning }
Automated tools will **miss accessibility issues** and **flag issues that are not issues**. If you are feeling unsure, let Nicky know that you'd like a walkthrough of these tools.

## Automated Tools

 Not all automated testing tools are equally useful. Some tools are really good for a small set of issues (XYZ), where others are more comprehensive, but don't test the issues the previous tool tests (only A through W).

You can use many tools to combat this problem, or, find one tool that tests mostly everything you need it to, and move to manual testing from there. Whatever method works best for you.

In this section you will find some information on automated accessibility tools' strengths and weaknesses. This is not fully comprehensive of course, and if you use a tool you love and want to add it here, please go for it!

### Equalize Digital: Accessibility Checker

The WordPress Plugin from Equalize Digital called [Accessibility Checker](https://equalizedigital.com/accessibility-checker/) tests an incredibly wide range of things. The paid version is one of the most comprehensive tools at its price-point, and outperforms the much more expensive Siteimprove accessibility tool.

The paid version tests almost all your website pages at once and compiles them into one global dashboard. It won't catch 100% of colour contrast issues, and it doesn't give you an outline of your page structure. WAVE might be a good supplement.

The free version will only check one page at a time, and its interface can be difficult to use, and  glitchy. But when it's working right, it really has no weaknesses.

### Pa11y

[Pa11y](https://github.com/pa11y/pa11y) is a command-line interface for those who don't like GUI's. It's strong at quickly catching type and syntax errors in your HTML without much effort. It misses a lot, and is mainly good for a first line of defence.

### WAVE® by WebAIM

WebAIM's [WAVE browser extension](https://wave.webaim.org/extension/) tool is extremely strong at providing a visual representation of your HTML document structure. This will quickly help you figure out if you have correctly outlined landmarks, heading levels, and reading order. It's also good at catching colour contrast issues.

It does not offer much else, and it is difficult to use since it will only scan one page at a time.

### axe DevTools Browser Extension

Deque's free [axe DevTools browser extension](https://www.deque.com/axe/browser-extensions/) is easy to use and very clear in its instruction. It won't catch a lot of things, but when it does catch things, it's easy to resolve the issue. There is almost never a false positive.

It nests nicely with your other dev tools in your browser, so it feels very intuitive and less clunky than some other tools, but still only scans one page at a time.

### Siteimprove Browser Extension

[Siteimprove's free browser extension](https://www.siteimprove.com/integrations/browser-extensions/) has a unique interface where you can sort issues by different categories. It easily flags the issues noted on screen by highlighting the area.

It's more in line with Equalize Digital in the amount of issues it will log, but it can be overzealous. Siteimprove's suite of tools will sometimes flag things as WCAG violations when that is not the case. Please use this extension with caution, not all issues it flags need to be corrected for WCAG compliance, and it can spread harmful misinformation.

## How To

You may use any automated tools of your choosing, whatever works best for you and is the easiest to integrate into your workflow as often as possible.

With that said, this section will walk you through the recommended workflow.

### ① Install Equalize Digital: Accessibility Checker

We currently have one license of the plugin. Check if someone is currently using it. If not, go ahead and install it on your site.

- The license key can be found in Bitwarden
- The [pro plugin files](https://drive.google.com/drive/folders/1VwjJP2kAa5pRLqHM5DmvaJZhQcE-71X7?usp=drive_link) can be downloaded from Google Drive
- You may follow their [setup guide](https://equalizedigital.com/accessibility-checker/how-to-install-activate-accessibility-checker/)

### ② Update plugin settings

Navigate to Accessibility Checker > Settings > General

- **Post types to be checked:** Make sure all options are checked here
- **Full site scan speed:** You can leave this on normal, there are no known issues with that speed with WPEngine. Feel free to adjust this to your liking though.
- **Prompt for simplified summary:** Never
- **Simplified summary position:** Insert manually
- **Footer accessibility statement:** Unchecked

### ③ Run full site scan

Navigate to Accessibility Checker > Full Site Scan. No need to schedule a background scan schedule unless you desire. The full site scan make take some time.

### ④ Remediate!

Now comes the hard part. Once the scan is done you'll have between 0 and over 10,000 issues, woo hoo! The important thing to remember is that it's scanning all pages at once, and any repeated issues are counted each time they repeat. So, solving one issue in the footer will remove many issues, not just one.

- If you are having trouble figuring out issues related to headings being in the wrong order, or related to landmarks or other page structure issues, visit the page, and run the WebAIM WAVE tool. You can review a visually simplified version of the page structure to pinpoint what needs to be resolved.

{: .note }
You don't need to resolve every single issue it flags if you are only completing best practices. Talk to Nicky if you are unsure what to resolve, and what to leave.

### ⑤ Remove the plugin

Once you are done, uninstall the plugin. They provide [unlimited dev sites](https://equalizedigital.com/accessibility-checker/what-does-unlimited-dev-sites-mean/), but, we don't want this plugin to be on a live client website without the necessary client education.

From here, we'll have a solid foundation to move forward with more refined testing.
