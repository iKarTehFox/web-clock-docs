---
title: Font Customization
layout: default
parent: Features
nav_order: 4
---
# Font Customization
{: .no_toc }
The Font Customization section in the menu panel allows you to change the font styling of the clock, including the font family, sizing, and other text effects.

![A screenshot of the Font Customization menu options.](/assets/images/docs-Features/fontcustomization/fontcustomization.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## Options
### Font Family and Custom Font
These two options allow you to set the font family for the clock and countdown time display. There are only a few fonts built into the website, but you have the option to choose any font installed on your device.

| Menu options | Included fonts |
| --- | --- |
| ![A screenshot of the Font Family and Custom Font dropdown menus.](/assets/images/docs-Features/fontcustomization/fontfamily.png) | ![A screenshot of the Font Family dropdown menu with all the included, built-in fonts](/assets/images/docs-Features/fontcustomization/fontfamily-dropdown.png) |

As for setting a custom font, you must specify the exact filename of the font file. If the requested font is not installed on your device or isn't compatible with your browser, the clock may revert to the default system font.

{: .note }
Some *built-in fonts* may not be compatible with older devices or browsers, such as smart TVs and embedded systems which often use older browser technologies.
<hr>

### Font Style and Weight
The Font Style and Font Weight radio buttons let you change... well—*the font style and weight*! You can change between Regular and Italic styles, and between Light, Normal, and Bold weights.

![A screenshot of the Font Style and Font Weight radio buttons.](/assets/images/docs-Features/fontcustomization/fontstyleweight.png)

**Note:** Most fonts support Regular and Italic styles, but **not all of them support each font weight**.

Here's a table of each built-in font and their supported font styling and weights:

| Font family | Regular | *Italic* | <span style="font-weight: lighter;">Light</span> | Normal | <span style="font-weight: bolder;">Bold</span> |
| --- | --- | --- | --- | --- | --- |
| Lato | ✅ | ✅ | ✅ | ✅ | ✅ |
| Montserrat | ✅ | ✅ | ✅ | ✅ | ✅ |
| Open Sans | ✅ | ✅ | ✅ | ✅ | ✅ |
| Oswald | ✅ | ✅ | ✅ | ✅ | ✅ |
| Poppins | ✅ | ✅ | ✅ | ✅ | ✅ |
| Roboto | ✅ | ✅ | ✅ | ✅ | ✅ |
| Tektur | ✅ | ✅ | ❌ | ✅ | ✅ |
| Ubuntu | ✅ | ✅ | ✅ | ✅ | ✅ |
| Ubuntu Mono | ✅ | ✅ | ❌ | ✅ | ✅ |
| Dancing Script | ✅ | ✅ | ❌ | ✅ | ✅ |
| Merriweather | ✅ | ✅ | ✅ | ✅ | ✅ |
| Nanum Brush Script | ✅ | ✅ | ❌ | ✅ | ✅ |
| Pangolin | ✅ | ✅ | ❌ | ✅ | ✅ |

<hr>

### Font Size
The Font Size dropdown menu lets you change the font size of the clock. This is useful for very large or small displays, as well as **to prevent the clock from being cut off at the edges of the screen** (such as when using the Words Display System).

![A screenshot of the Font Size dropdown menu and its options.](/assets/images/docs-Features/fontcustomization/fontsize.png)

Font sizes are measured in viewport width units (vw). The larger the screen, the larger the font is proportional to the screen size. As such, the smaller the screen, the smaller the font size.

| Huge (18vw) | Smaller (6vw) |
| --- | --- |
| ![A screenshot of the clock with the "Huge (18vw)" font size option selected.](/assets/images/docs-Features/fontcustomization/fontsize-huge.png) | ![A screenshot of the clock with the "Smaller (6vw)" font size option selected.](/assets/images/docs-Features/fontcustomization/fontsize-smaller.png) |

<hr>

### Text Effects
The included text effects let you add a shadow or colored stroke outline to the time and date.

![A screenshot of the Text Effects menu options.](/assets/images/docs-Features/fontcustomization/texteffects.png)

![An example of the use of text effects. A 12px drop shadow and a gray, 3px wide stroke outline is added.](/assets/images/docs-Features/fontcustomization/texteffects-example.png)

{: .tip-title }
> Dev tip
>
> This functionality is built into CSS and can be enabled by using the `text-shadow` and `-webkit-text-stroke` CSS style attributes.
