---
layout: default
title: Colour Contrast Testing
parent: Accessibility
grand_parent: Processes
---
# Colour Contrast Testing

{: .note }
There is a large amount of web accessibility misinformation online. Not all resources can be trusted for accurate information.

## Contrast Thresholds

Colour contrast must meet a specific threshold for WCAG compliance ([SC 1.4.3](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)). For different elements and text sizes, there are different ratios:

- WCAG AA - Regular or large text size
- WCAG AAA - Regular or large text size
- WCAG AA - UI / Graphics

### Large Text

Large text according to WCAG V2.2 is considered:

<span style="font-size: 19px">**14 point (19px) bold text**</span>

<span style="font-size: 24px">18 point (24px) normal text</span>

## Testing Tools

It is easiest for colour contrast to be checked in Figma if the file is set up correctly. All features have to have been designed, and followed exactly with code. The palette can then be reliably tested with automation. We are assuming this has not been done, and that we must test individually. 

There are hundreds, if not thousands, of different colour contrast checkers all over the internet. You can test most quickly on a built website using an eyedropper tool. [Colour Contrast Analyzer](https://www.tpgi.com/color-contrast-checker/) is a good one.

If you have trouble using the eyedropper tool, you may use another method (like pasting hex codes into this tool or another tool), or, request someone else complete this test. It is not required of you to be able to use an eyedropper tool.

## Process

1. Simply eyedrop the background colour, and then the text/graphic element's colour. Test:
	- All text colour combinations (including image/pattern background colors).
		- This does not include disabled components, or, placeholders.
	- All UI colour combinations (button icons, graphics that convey information).
2. The tool will tell you if it passes the threshold or not. 
	- If not, we must communicate this with the design team to resolve. You can note your findings with screenshots making sure to include both hex codes.
	- If it passes, we can move on to the next colour and repeat.
