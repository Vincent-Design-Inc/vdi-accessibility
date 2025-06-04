---
layout: default
parent: New System Setup
title: Git Setup
nav_order: 3
---

# Install git, GitHub cli, and Connect to GitHub

To install git, execute `git` in the terminal.  This will tell you that `xcode-cli` needs to be installed.  Follow the wizard prompts to complete installation.

After `git` is installed, install the GitHub commandline interface using Homebrew: `brew install gh`.  When the install completes, you will need to connect it to your VDI GitHub account.  To do this, run `gh auth login` and follow the instructions.  Use the following answers for each prompt:

*   Account to log into? GitHub.com
*   Preferred protocol? SSH
*   Upload public key? Choose the key you created in the [SSH](/docs/new-system-setup/ssh-service-setup) step.
*   Key title? Name it whatever you'd like
*   How to authenticate? Login with browser.  Copy the code shown, and hit enter to open a browser.  Paste the code when prompted and accept the permissions request.

![](/images/screenshot_2023-12-06_at_10-10-29_build_software_better_together.png)

![](/images/screenshot_2023-12-06_at_10-10-50_build_software_better_together.png)

Your steps should look like the screenshot below (without the prompt about being already logged in):

![](/images/screenshot_2023-12-06_at_10.11.26_am.png)

----

Next Step: [Back to main setup page](/docs/new-system-setup)
{: .fs-5 }