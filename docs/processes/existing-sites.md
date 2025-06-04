---
layout: default
title: "Site Setup: Existing"
parent: Processes
---

{: .note }
**You must be running PHP 8.0 or higher on your local machine** (This is a hard requirement for the new versions of Sage & Acorn.  All sites should be on at least PHP 8.1 going forward anyway, but we may need to revisit workstation builds to get everyone up to date.)

# Set up an existing site using Starter v.3

The bulk of the following steps will be completed in terminal.

## Get Started

1. **Find the repository** on [GitHub](https://github.com/orgs/Vincent-Design-Inc/repositories). 
2. **Make a new LocalWP site.** Make sure to change the local site domain to be the same as the one set in `bud.config.js` local dev URL (`setProxyUrl`).
3. **Clone the repository** to your new site's theme folder. Make sure to name this the same as the one set in `bud.config.js` public path (`setPublicPath`).
4. **Open a terminal** in the theme folder in VS Code, or, open your terminal of choice and `cd` into that theme directory.
5. Execute `composer install`.
6. Execute `yarn install`.
7. Execute `yarn build`.
  	- **The build step is important, as the theme won't work if you don't do a preliminary build.**
8. Update `bud.config.js` with the following info:
  	- your local dev port (`.setUrl` directive, e.g. `3000`)
9. Activate the new theme in your Wordpress dashboard
10. Ensure that the required plugins are installed and activated (e.g. Advanced Custom Fields Pro)
  	- Script is included in the repo. Open a site shell from Local (**MUST** be from Local), and change to the theme folder (e.g., `cd wp-content/themes/starter3`).
  	- Execute `bash plugins.sh` to install the plugins.
11. Begin developing with `yarn start`.
12. To get your theme changes to the WPE environment, use the GitHub Action either manually, or automated.

### Import Content
You may import content from a WPE environment using Local. 
1. Press "Pull
2. Select **only**:
   - Database
   - Select Files > WP Uploads Folder