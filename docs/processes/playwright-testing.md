---
layout: default
title: Playwright Testing
parent: Processes
---

# Playwright Testing

{: .note }
This is going to cover using PLaywright for automated testing using Axe Core.  This is barely scratching the surface of what Playwright can do.  It is a very powerful tool that can be used for a lot more than just accessibility testing.  This is just a starting point, and will be updated as we learn the tool.

{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## What is Playwright?

Playwright is a Node.js library to automate Chromium, Firefox, and WebKit with a single API. It enables cross-browser web automation that is ever-green, capable, reliable, and fast.

## Getting Started

### Install Playwright

In your theme folder, run the following commands in your terminal to install Playwright and the Axe Core library:

```bash
npm init playwright@latest --yes "--" . '--quiet' '--browser=chromium' '--browser=firefox' '--browser=webkit' '--lang=js'
npm install -D @axe-core/playwright
```

This will install Playwright and the Axe Core library, as well as the browsers needed for testing.  This will also create a `playwright.config.js` file in your theme folder, along with the output folders (`playwright-report` and `test-results`) it uses to store results and screenshots.

- `playwright-report` - This is where the HTML report will be generated.
- `test-results` - This is where the test results and screenshots made during the tests will be stored.  If there are errors found, a JSON file that contains the results of the tests will be in a subfolder named for whichever test caused the failure.  If you find an empty folder, congratulations!  You have a perfect test suite.  If you find a folder with a JSON file in it, you can open that file to see the results of the test.

### Set up your tests

Create a new file in the `tests` folder called `accessibility.spec.cjs`.  This is where we will put our tests.  This file will follow the layout below:

```javascript
const { test, expect } = require('@playwright/test');
const AxeBuilder = require('@axe-core/playwright').default;

test.describe('site-accessibility-test', () => {
  test('Homepage Test', async ({ page }, testInfo) => {
    await page.goto('http://your-site.local/');

    await page.screenshot({ path: 'test-results/homepage.png' });

    const accessibilityScanResults = await new AxeBuilder({ page })
      .withTags(['wcag2a', 'wcag2aa', 'wcag21a', 'wcag21aa', 'wcag22a', 'wcag22aa'])
      .analyze();

    await testInfo.attach('accessibility-scan-results', {
      body: JSON.stringify(accessibilityScanResults, null, 2),
      contentType: 'application/json'
    });

    expect(accessibilityScanResults.violations).toEqual([]);
  });

  test('Another Page Test', async ({ page }, testInfo) => {
    await page.goto('http://your-site.local/another-page/');

    await page.screenshot({ path: 'test-results/another-page.png' });

    const accessibilityScanResults = await new AxeBuilder({ page })
      .withTags(['wcag2a', 'wcag2aa', 'wcag21a', 'wcag21aa', 'wcag22a', 'wcag22aa'])
      .analyze();

    await testInfo.attach('accessibility-scan-results', {
      body: JSON.stringify(accessibilityScanResults, null, 2),
      contentType: 'application/json'
    });

    expect(accessibilityScanResults.violations).toEqual([]);
  });
});
```

It looks complicated, but it's really not.  For each page you want to test, there's only twhree lines you need to worry about.  The `test()` line defines the name of the test, and should be changed for each different page.  The `page.goto` line is where you will put the URL of the page you want to test.  The `page.screenshot` line is where the screenshot of the page will be saved.  Everything else can and should be ignored for now.  You can add as many tests as you want, just copy and paste the `test` block and change the test name, URL, and screenshot name.

### Ok, how do I use this?

To run the tests, you will need the following plugin for VSCode: [Playwright Test for VSCode](https://marketplace.visualstudio.com/items/?itemName=ms-playwright.playwright).  Install that, and there should be a new icon in your action bar that looks like a beaker.  You can run the tests from there (screenshots to come).  You can also run the tests from the command line by running the following command in your terminal `npx playwright test`, but I don't recommend using it until we figure out any potential issues from running it that way.
