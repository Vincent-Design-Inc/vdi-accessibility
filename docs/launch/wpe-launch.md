---
layout: default
title: WPEngine Launch
parent: Launch
nav_order: "3"
---
[Original Google Doc](https://docs.google.com/document/d/1lOaxrz1EfKkC85CwM-lomJPM6_Ql08I5OlhMYoI7zdU/edit#heading=h.n15qgywbg022){: .btn .btn-outline .mt-4 }

# WPEngine Hosted Launch
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

This is a rough draft !! I warned you !!

this assumes the client is hosting with us 

- test forms before launch and after
- most clients will have their own domain already
- check with the project manager that we have access to the domain registrar account
	- if we do not have access, and the client has an IT team we need their contact information instead
	- this is where we will be adding information from WPE
- have domain and we have access
	- check domain provider what it is https://wpengine.com/support/point-domain/
		- wp supports some providers and we can do the automated process
		- otherwise we will need to do the manual process
	- manual process - aarish is sending documentation for this
		- one way via cname on v a record
			- cname is the modern way
			- a record is the more traidtional old way
			- wpe recommends cname
				- have to check if the registrar support cname flattening - aarish is sending for this
				- red warning: "do not use this if you are not 100% sure that it will work, aarish will send better wording with technical bits"
		- aarish will send documentation on how to do this process
	- automated process - go through the Entri setup dialogs, we will only need registrar username and password
- fill out repo readme template [https://github.com/Vincent-Design-Inc/NRT](https://github.com/Vincent-Design-Inc/NRT)