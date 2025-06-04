---
layout: default
title: DeployHQ Setup
parent: Flywheel
grand_parent: Deprecated
---

# Set Up DeployHQ

_This guide assumes you’ve already set up your project to track a git repo hosted in our GitLab instance._

_Basic dev workflow (_[_Figma link_](https://www.figma.com/file/3n165t0Zvt8xe2dLcXjrZD?embed_host=share&kind=&t=pX0td2KPQ65u6Y6U-1&viewer=1)_):_

![](/images/images/screenshot_2023-04-18_at_20-11-13_figma.png)

1\. Log into DeployHQ, and create a new project

![](/images/screenshot_2023-04-18_at_17-28-32_projects_-_vincent_design_-_deploy.png)

2\. Give the project a title (suggestion: name of client), select GitLab as the source, and set the zone to US-East (shouldn’t make a difference, but it should be the closest)

![](/images/screenshot_2023-04-18_at_17-35-01_projects_-_vincent_design_-_deploy.png)

  
3\. Click Create Project.  The first time, GitLab will ask you to authorize the connection to your account.  Allow it, then select the vincent-design organization.  This will take you to a screen to choose the repository for your project.  Select your repo, and it will link it to the DeployHQ project.

![](/images/screenshot_2023-04-18_at_18-47-26_choose_a_repository_-_vincent_design_-_deploy.png)

![](/images/screenshot_2023-04-18_at_18-48-45_choose_a_repository_-_vincent_design_-_deploy.png)

  
 4. After the repo is linked, you get to the Server screen.  Here, give the server a name (suggestion: Flywheel), and select SSH/SFTP.  Set the Hostname under the SSH Configuration to sftp.flywheelsites.com and the port to 22.  The username and password will be your login credentials for Flywheel (will be different if the site isn’t hosted on Flywheel).  The Deployment Path for a Flywheel hosted site will generally look like this: `/org-vincent-design/<project>/wp-content/themes/<theme folder>`.  Nothing else on this screen should need to be changed.  Click Create Server.

![](/images/screenshot_2023-04-18_at_18-55-25_amc_-_vincent_design_-_deploy.png)

  
5\. On the Project Configuration screen, you shouldn’t need to do anything.  Click Add Suggestions to Project and move on.

![](/images/screenshot_2023-04-18_at_19-13-32_amc_-_vincent_design_-_deploy.png)

  
6\. You should now be at the New Deployment screen. This will show you the current revisions of the repo, start should be empty, end should be the most current commit/push to your repo.  This screen will do the initial deployment to the site.  Click the Deploy button, and the process will start.  This process will take some time, monitor it for any errors.

![](/images/screenshot_2023-04-18_at_19-17-24_amc_-_vincent_design_-_deploy.png)

  
7\. When it finishes successfully, you should see a screen similar to the following.  At this point, you can check the site to make sure it’s working.  It’s not a bad idea to make a change to your local repo and make sure the pipeline works as intended.

![](/images/screenshot_2023-04-18_at_19-50-06_amc_-_vincent_design_-_deploy.png)