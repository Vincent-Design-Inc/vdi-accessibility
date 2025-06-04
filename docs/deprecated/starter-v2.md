---
layout: default
title: "Starter V2: Setup"
has_children: true
nav_order: 
parent: Deprecated
---

{: .note }
YOU MUST BE RUNNING PHP 8 ON YOUR LOCAL MACHINE TO USE THIS THEME! This is a hard requirement for the new versions of Sage & Acorn.  All sites should be on at least PHP 8.1 going forward anyway, but we may need to revisit workstation builds to get everyone up to date.


## Starter v.2 Setup steps

1. Create new site in Local
2. Create new repo on [GitHub](https://github.com/organizations/Vincent-Design-Inc/repositories/new) **(don't add a readme file)**, make a note of the repo URL
    - make sure to select `Vincent-Design-Inc` in the owner dropdown
3. Clone Starter Theme from [GitHub](https://github.com/Vincent-Design-Inc/starter-theme-2) in site theme folder ($HOME/Local Sites/<sitename>/app/public/wp-content/themes/)
4. Change name of theme folder to reflect the site name
5. Inside theme folder, change git remote to repo from step 2: `git remote set-url origin <GitHub repo URL>`
    - Add all files to new repo: `git add .`
    - Commit files: `git commit -m 'Initial commit'`
    - Push theme to new repo: `git push -u origin main`
6. Inside theme folder, execute `composer install`, `yarn install`, `composer update`, and `yarn upgrade` to set up dependencies
7. Open theme folder in your editor, and update the theme meta info (name, URI, description) in style.css
8. Update `webpack.mix.js` with your local dev URL (e.g. `starter-theme-2.local`)
9. Activate the theme in the WordPress admin
10. Install typical plugins from [our plugin repo](https://github.com/Vincent-Design-Inc/typical-wordpress-plugins)
11. Begin developing with `yarn start`
