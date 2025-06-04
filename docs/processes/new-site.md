---
layout: default
title: "Site Setup: New"
parent: Processes
---

{: .note }
**You must be running PHP 8.0 or higher on your local machine** (This is a hard requirement for the new versions of Sage & Acorn.  All sites should be on at least PHP 8.1 going forward anyway, but we may need to revisit workstation builds to get everyone up to date.)

# Starter v.3 Setup steps
The bulk of the following steps will be completed in terminal.
To get started using the starter theme:

1. Create new site in Local
2. Create new repo on [GitHub](https://github.com/organizations/Vincent-Design-Inc/repositories/new) **(don't add a readme file)**, make a note of the repo URL
    - Make sure to select `Vincent-Design-Inc` in the owner dropdown
3. Clone Starter Theme from [GitHub](https://github.com/Vincent-Design-Inc/starter-theme-3) in site theme folder (`$HOME/Local Sites/<sitename>/app/public/wp-content/themes/`)
4. Rename the directory to match your project name
5. `cd` into that new directory
6. Run `composer install && yarn install && yarn build` to install theme dependencies.
  	- **The build step is important, as the theme won't work if you don't do a preliminary build.**
  	- Running each command one at a time is the best way to do this.
7. Update `bud.config.js` with the following info:
  	- your local dev URL (`.setProxyUrl` directive, e.g. `starter3.local`)
  	- your local dev port (`.setUrl` directive, e.g. `3000`)
  	- your public path (`app.setPublicPath` directive, e.g. `/wp-content/themes/starter3/public/`)
8. Update `style.css` with your theme name, description, etc.
9. Change the GitHub repo URL:
  	- `git remote set-url origin <new repo address>`
10. Activate the new theme in your Wordpress dashboard
11. Ensure that the required plugins are installed and activated (e.g. Advanced Custom Fields Pro)
  	- Script is included in this repo. Open a site shell from Local (**MUST** be from Local), and change to the theme folder (e.g., `cd wp-content/themes/starter3`).
  	- Execute `bash plugins.sh` to install the plugins.
12. Begin developing with `yarn start`
13. To get your theme changes to the WPE environment, use the GitHub Action either manually, or automated.

### Theme Notes
* Colors are defined in `resources/styles/common/theme.scss`, which then get loaded in `tailwind.config.js`
* ACF Color Picker field colors are defined in `app/setup.php`
* Sage handles updating the `theme.json` file, **do not edit directly**