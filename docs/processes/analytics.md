---
layout: default
title: Analytics
parent: Processes
---

# Analytics
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## What is Google Tag Manager? 

Google Tag Manager (GTM) allows you to install multiple “tags” on a site. Google Analytics is one such tag. Each website at VDI needs to have Google Analytics set up before launch. No other tags are required.

## Account Types

Occasionally, we will have to work with an existing Google Tag Manager account. It can either be an old account that's been in use for years, or a new one set up from the client for this new website specifically.

{: .warning }
The following directions assume that we are setting up the account fresh for this website, with **no existing Google Tag Manager account**.

## ❶ Google Site Kit Setup

{: .note }
Through this whole process you will be using your own VDI Google account.

### ① Install WordPress Plugin

- Install the "Google Site Kit" WordPress plugin on your website. 
- Navigate to its main dashboard and start setup

### ② Plugin Setup
1. **Site Kit wants access to your Google Account**
	- Select all to allow all access
	- Continue
2. **Through the next 4 steps** just click the main action to progress
3. **Create your Analytics account**
	- Leave all account information here the defaults
	- If we were connecting an existing account, here is where we would do it
	- Leave "Enable enhanced measurement" on
	- Create account
4. **Site Kit wants additional access to your Google Account**
	- Allow any, and continue
5. **Terms of Service Agreement**
	- This will only show up your first time
	- Change the country to Canada
	- Agree and accept the data sharing settings you are comfortable with
6. **You're done!**

## ❷ Google Search Console

1. Open the site in the Google Search Console
	- [Search Console](https://search.google.com/search-console)
	- Select the site you're working on in the dropdown in the sidebar
2. Add the required users to the property (the website)
	- Open the site Settings
	- Navigate to Users and permissions
	- Add User
		- Keep yourself as Owner
		- Add seo@vincentdesign.ca as Owner
		- Add will@vincentdesign.ca as Owner
3. From here, anybody who needs to interact with this Google Search Console property (website) can do so. You are done!
