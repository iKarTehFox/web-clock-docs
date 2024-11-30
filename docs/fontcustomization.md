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

As for setting a custom font, you must specify the exact filename of the font file, including the file extension. If the specific font is not installed on your device or your browser isn't compatible with said font, the clock may revert to the default system font.

{: .note }
Not all of the *built-in fonts* are compatible with all devices. For instance, Montserrat may not work on older devices such as smart TVs (they usually have old browsers) and other embeddded devices.

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

The sizes are in measures of viewport width, so the larger the screen, the larger the font, and vice versa (the smaller the screen, the smaller the font).

| Huge (18vw) | Smaller (6vw) |
| --- | --- |
| ![A screenshot of the clock with the "Huge (18vw)" font size option selected.](/assets/images/docs-Features/fontcustomization/fontsize-huge.png) | ![A screenshot of the clock with the "Smaller (6vw)" font size option selected.](/assets/images/docs-Features/fontcustomization/fontsize-smaller.png) |

<hr>

### Text Effects
The included text effects let you add a shadow or colored stroke outline to the time and date.

![An example of the use of text effects. A 12px drop shadow and a gray, 3px wide stroke outline is added.](/assets/images/docs-Features/fontcustomization/texteffects-example.png)

This functionality is built into CSS and can be enabled by using the `text-shadow` and `-webkit-text-stroke` CSS style attributes.

Here's how it works, along with the function that handles font styling:

```ts
// Font text shadow listener
font.shadowrange.addEventListener('input', function() {
    const value = Number(this.value);
    const opacity = value / 5;
    const strength = value * 3;
    const dropShadowValue = `5px 5px ${strength}px rgba(0, 0, 0, ${opacity})`;
    font.shadowlabel.textContent = `Drop shadow: ${strength}px`;

    dtdisplay.ccontainer.style.textShadow = value > 0 ? dropShadowValue : '';
    logConsole(`Font text shadow set to: ${dropShadowValue}`, 'info');
});

// skipping over some irrelevant code...

const fontSizeOptions: Record<FontSizeKey, string> = {
    '6vw': '1vw',
    '8vw': '1.25vw',
    '10vw': '1.5vw',
    '12vw': '2vw',
    '14vw': '2.25vw',
    '18vw': '3vw'
};

// Font style handler function
function modifyFontStyle(type: string, value: string) {
    const fontSize = value as FontSizeKey;
    match(type)
        .with('style', () => {
            dtdisplay.ccontainer.style.fontStyle = value;
            stopwatch.display.style.fontStyle = value;
            countdown.display.style.fontStyle = value;
            logConsole(`Font style set to: ${value}`, 'info');
        })
        .with('weight', () => {
            dtdisplay.ccontainer.style.fontWeight = value;
            stopwatch.display.style.fontWeight = value;
            countdown.display.style.fontWeight = value;
            logConsole(`Font weight set to: ${value}`, 'info');
        })
        .with('size', () => {
            if (fontSize in fontSizeOptions) {
                dtdisplay.ccontainer.style.fontSize = value;
                dtdisplay.indicatorSlot.style.fontSize = fontSizeOptions[fontSize];
                dtdisplay.date.style.fontSize = fontSizeOptions[fontSize];
                logConsole(`Font sizing set to: ${value}`, 'info');
            } else {
                logConsole(`Invalid font size: ${value}`, 'error');
            }
        })
        .with('family', () => {
            dtdisplay.ccontainer.style.fontFamily = value;
            countdown.display.style.fontFamily = value;
            logConsole(`Font family set to: ${value}`, 'info');
        })
        .with('strokewidth', () => {
            dtdisplay.ccontainer.style.webkitTextStrokeWidth = `${value}px`;
            font.strokerangelabel.textContent = `Stroke width: ${value}px`;
            logConsole(`Font stroke width set to: ${value}px`, 'info');
        })
        .with('strokecolor', () => {
            dtdisplay.ccontainer.style.webkitTextStrokeColor = value;
            font.strokecolorlabel.textContent = `Stroke color: ${value}`;
            logConsole(`Font stroke color set to: ${value}`, 'info');
        })
        .otherwise(() => {
            logConsole(`Invalid font modification type: ${type}`, 'error');
        });
}
```
