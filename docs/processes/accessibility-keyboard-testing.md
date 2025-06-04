---
layout: default
title: Keyboard Testing
parent: Accessibility
grand_parent: Processes
---
# Keyboard Testing

{: .note }
There is a large amount of web accessibility misinformation online. Not all resources can be trusted for accurate information.
## Test for complete keyboard navigation

Read [WebAIM's Keyboard Accessibility](https://webaim.org/techniques/keyboard/) article to gain a pretty good understanding of how to complete most keyboard testing. You can combine this with other resources.

You may also need to update some browser or computer settings in order to use keyboard navigation. [How to Enable Tab-Key Navigation on a Mac](https://access.articulate.com/support/article/How-to-Enable-Tab-Key-Navigation-on-a-Mac).

Some important notes:
- Website main navigation interaction is *not* a 'tree' menu, menu bar, tab panel, dialog, or select interaction. It should combine button and link interactions only.
- Custom focus indicator styles should not be styled using outlines, only things like border, pseudo elements, box shadow, etc. We want the default outline for focus to be very easy to override by the visitor's custom browser settings.
- When in doubt, remove all custom tabindex declarations before an audit. Default reading order is always okay.