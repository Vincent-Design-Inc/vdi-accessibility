---
layout: default
title: Gravity Forms
parent: Processes
---

# How to make Gravity Forms accessible

To make Gravity Forms conform to WCAG V2.2 Level AA, some additional work is required. 

{: .note }
Starter V3 needs to be updated to handle status updates.

Please read through the [Accessibility Checklist for Gravity Forms](https://docs.gravityforms.com/accessibility-checklist-for-gravity-forms/). This information should be used each time you have to set up Gravity Forms as whole, and for each new form. The client will also need to be aware of this information each time they make a new form.

## Initial Setup: After installing the plugin

### General Settings

Go to the Gravity Forms settings page under [Dashboard > Settings](https://docs.gravityforms.com/settings-page/) and set:

*   **Output Default CSS:** “On”.
*   **Output HTML5**: “On”.

### Form Settings

For a newly created form, go to the [Form Settings tab](https://docs.gravityforms.com/form-settings/) and check the following settings that are important for accessibility:

*   **Label Placement**: “Top aligned”
*   **Sub-Label Placement**: “Above Inputs”.
*   **Validation Summary**: “On”.
*   **Required Field Indicator**: Ensure the option to show a required field indicator is selected.
*   **Form button**: Choose “Text”. Use descriptive text.
*   **Form button Conditional Logic**: Do not enable conditional logic
*   **Enable legacy markup**: “Off”.