---
layout: default
title: Critical Error Issue
parent: WP Engine
---
{: .note }
> Zack is working to fix this issue, but until we hear back from WP Engine's support these steps should help resolve this issue. Sage is supported by WP Engine and this is their recommended way of dealing with simillar errors.
> 
> Refer: [WP Engine FAQ's](https://github.com/wpengine/example-sage-theme?tab=readme-ov-file#frequently-asked-questions)

# WP Engine Critical Error

## Why am I seeing critical error?

You may be seeing critical error on your site after pushing your local changes to WP Engine. This is because Sage is unable to create cache for your views. Sage compiles your blade templates and stores them under `wp-content/cache/acorn/framework/views`, this helps serve views faster without need to re-compile them every time page is loaded. These cache files are created the first time you visit a page and persist unless views are changed.

When you push an update, Sage may attemp to write these cache file and fail because [WP Engine has strict write permissions following security best practices](https://wpengine.com/support/wp-engines-security-environment/#Disk_Write_Protection).

## How can I solve this?

### Use GitHub Actions

{: .note }
> Actions use the same process as [Manually Creating Cache Files](#manually-creating-cache-files), which may not work in some edge cases. Refer [Known Issues](#known-issues) section for more information.

You should use [GitHub Actions](https://github.com/Vincent-Design-Inc/starter-theme-3/blob/main/.github/workflows/wpengine.yml) to push your updates whenever possible.

Actions use [post-deploy.sh](https://github.com/Vincent-Design-Inc/starter-theme-3/blob/main/post-deploy.sh) script to build cache files once the site has been deployed. This is the last step in your [`wpengine.yml`](https://github.com/Vincent-Design-Inc/starter-theme-3/blob/f43afbe101a4de0c44a28bd374b628336eeec4dd/.github/workflows/wpengine.yml#L64) file. When you are SSHed into the server you have enough user permissions to write cache files.

If you are still seeing crticial error after pushing updates via GitHub Actions, consider [SSHing into site environment and re-creating cache files](#manually-creating-cache-files) or [see known issues section](#known-issues).



### When using Local Push

If you push updates via Local, even if you are pushing cache files, you may encounter critical error.

Generally, if you log into Wordpress backend and revisit those pages, Sage should have enough permission to write cache files. Once done you can log out and everything should work as expected.

You can also manually create cache files after each push. [See Manually Creating Cache Files](#manually-creating-cache-files).

## Manually Creating Cache Files

{: .note }
> This may not work in some edge cases, please refer [Known Issues](#known-issues) section for more information.

### SSHing into your site

In order to SSH into your site you'd need to add your SSH public key in your account on WP Engine. [Refer WP Engine docs to add SSH keys](https://wpengine.com/support/ssh-gateway/#Add_SSH_Key).

Once you have successfully added SSH key, you'd be able to SSH into your site using terminal. To SSH into your site run the following command in your teminal:

```bash
ssh environment@environment.ssh.wpengine.net
```

{: .note }
> Replace {environment} with details from WP Engine.

### Building cache files

Once you have access to your site via SSH, you can navigate to your site using following command:
```bash
cd sites/{environment}
```

{: .note }
> Replace {environment} with details from WP Engine.

Now you can run following command to create cache files:

```bash
wp acorn view:cache
```

This should create cache files and your site should function as intended.

## Known Issues

### Dynamic Components

If you are using [dynamic componenets](https://laravel.com/docs/11.x/blade#dynamic-components) in your theme, then pages containing those are likely to break. This is because of [WP Engine's strict write policy](#why-am-i-seeing-critical-error).

Cache file for [dynamic componenets](https://laravel.com/docs/11.x/blade#dynamic-components) cannot be built during the build phase, it has to be built when the page is rendered and at this point the theme does not have write permission, hence the critical error. The above steps may not help in this case.

To solve this, try:

- Logging into Wordpress backend and then visiting broken pages. When you are logged in, the theme has enough permission to write to cache folder.

- You may want to move the site to Flywheel, until this is fixed.