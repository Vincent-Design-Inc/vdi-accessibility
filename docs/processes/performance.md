---
layout: default
title: Performance
parent: Processes
---
# Performance
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


## Getting the initial benchmark 
1. Run the live website through [PageSpeed Insights](https://pagespeed.web.dev/). You will get desktop and mobile performance numbers that look like:
    - ![](https://lh7-us.googleusercontent.com/docsz/AD_4nXfnetr7v7wONXvEXjNPE50rxICSTnkWa20zOFvvuX1_qMIBeWjjjGuVNVghcLlIOK18YLmmKhlaMPcIxCBQ3ao4iGkQKOCEyH3brssT8Hira0ChjELisQhimst7gknY99ONflT6RnxomPl2MbNQAlwUyiR-?key=ZAvcsTdwyK1CxBNsVY7zpg)
2. You will need to hit the target number of 90 for mobile and 100 for desktop.
3. Please review the ongoing performance setup section for your initial improvement steps.

## Basic Performance fixes

### Imagify
1. **Install the plugin** using our license key.
2. Go to the **plugin settings** and match the following:
   
   ![](/images/imagify-settings.png)
3. **Save and go to bulk optimize!** It will take a while. 
	1. If you are finding it is not helping, try figuring out if too many of your images are PNG when they should be JPG instead.


### WPRocket

1. **Install the plugin** using our license key. 
2. **It's best to install this on a staging site** prior to launch so you can test out the settings before using it on a live site. 
	1. **Note:** This precaution can only get you so far, sometimes unexpected things do happen on the live site! If that's the case, please just revert changes, or uninstall the plugin. 
3. **Update the plugin settings.** There is no magic formula, so you will just have to improve the score with trial and error. You are balancing between improving page speed, but not creating too many visual issues during content load. Generally the following works as a good baseline:
   
   ![](/images/wprocket-file-optimization-1.png)
   ![](/images/wprocket-file-optimization-2.png)
   ![](/images/wprocket-media.png)
   ![](/images/wprocket-preloading.png)
   
## Advanced Performance Fixes

Cloudflare optimization package + Imagify

TBD

## Getting the final benchmark

1. Run the live website through [PageSpeed Insights](https://pagespeed.web.dev/) 3 times. Record the average of each number over the three trials.
2. Resolve performance issues until the target number of 90 for mobile and 100 for desktop is hit. 
3. If those numbers can't be hit, please leave a note attached to the website in WPEngine explaining why. 
    - ![](/images/wpengine-note.png)


## Performance Report

If you need to create a performance report, there is a template you can use. 

[Performance Report Template](https://docs.google.com/document/d/1iAiaovanJU_a-cKvVzwWQErVyWFx8j0ZvegOTRTowN8/edit?usp=sharing){: .btn .btn-outline :mt-4 }