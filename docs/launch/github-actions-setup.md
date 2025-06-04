---
layout: default
title: GitHub Actions Setup
parent: Launch
nav_order: "1"
---

# GitHub Actions Setup

To setup github actions for your project you'd need to do the following things:
-
1. Set-up GitHub Actions workflow file
2. Set-up repository secrets

## Github Actions Workflow
If you are using the latest version of starter theme you'd probably have main.yml file in .github/workflows folder. Hence you can skip this step.

If you don't have the main.yml file then create .github/workflows folder and inside workflows create main.yml file.

Copy & paste the following code in main.yml:
```
name: SSH Deploy
on: [ workflow_dispatch ]
        
jobs:
  call-deploy-workflow:
    uses: Vincent-Design-Inc/ssh-deploy/.github/workflows/main.yml@main
    secrets:
      SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
      REMOTE_USER: ${{ secrets.REMOTE_USER }}
      REMOTE_TARGET: ${{ secrets.REMOTE_TARGET }}
```

Here,

* Name: Defines your workflow name that would be shown under actions tab.
* On: Defines the trigger, that would run the workflow.
	* On is set to workflow_dispatch by default which means you would have to run it manually each 			time.
  * On can be set to push, pull or fork. Refer to documentation for more details https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows.
* Job: Defines all the steps Action needs to perform to successfully deploy the changes. These steps are defined in a separate repository which we will reuse here.
* Uses: Defines the path to the reuseable workflow stored in a private repository under same organization.
* Secrets: Passes the necessary variables that we will define in the next step that are needed to properly connect to WPE server.

## Setting GitHub Secrets/Variables
Each repo has it's own set of secrets and variables under the setting tab:

![screen_shot_2023-04-28_at_12.07.47_pm.png](/images/screen_shot_2023-04-28_at_12.07.47_pm.png)

Look for secrets and variables under security section on the left hand side bar.

![screen_shot_2023-04-28_at_12.10.39_pm.png](/images/screen_shot_2023-04-28_at_12.10.39_pm.png)

Under the Secrets tab > select Actions:

![screen_shot_2023-04-28_at_12.13.40_pm.png](/images/screen_shot_2023-04-28_at_12.13.40_pm.png)

Under the Actions setting you will have access to two types of secrets (make sure you are setting secrets and not variables):

**Repository secrets:** These pertain particularly to the repository in question. You will need 2 unique secrets for each repository:

### WPEngine Secrets
* **WPE_INSTALL_NAME:** This is the "user" that will be used for ssh login on the server. This can be found on the WPE page for the site in question.  For example, in the screenshot below, you would use "alamosesgrepo1"
![wpe_install_name](/images/screenshot_2024-04-26_at_13-46-13_overview_user_portal_-_wp_engine.png)
* **THEME_NAME:** Defines the path where the theme needs to be deployed.  This will be whatever you named the folder when you set up your theme.

**Organizational secrets:** Every private repo inside Vincent Design organization will have access to these.

### WPEngine Secrets
* **WPE_SSHG_KEY_PRIVATE:** You will have access to this by default. This is the key that actions will use to validate your deploy with WPEngine.

Once you have completed the steps mentioned above you are ready to deploy your project.

## Deploying through GitHub Actions
* Go to Actions tab
	* **NOTE:** If the Actions tab isn't available, go to the repo settings, then the Actions section, and enable actions for the repo.
* Under actions select the workflow you defined using main.yml file.
* Click on Run Workflow and select the correct branch to be used.
* Sit back and relax.

![screen_shot_2023-05-11_at_1.29.32_pm.png](/images/screen_shot_2023-05-11_at_1.29.32_pm.png)

