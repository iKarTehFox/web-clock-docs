---
title: "Background Theme"
layout: default
parent: Features
nav_order: 5
---
# Background Theme
{: .no_toc }
The Background Theme section in the menu panel lets you personalize the background of the page, including preset background colors, custom images, and other options.

![A screenshot of the Background Theme menu options.](/assets/images/docs-Features/backgroundtheme/backgroundtheme.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## Options
### Background Color Mode
The Background Color Mode dropdown menu lets you choose between the Color Fade, Solid Color, and Image modes.

![A screenshot of the Background Color Mode dropdown menu.](/assets/images/docs-Features/backgroundtheme/colormode.png)

#### Color Fade
In this mode, the background color fades between a preset list of colors, with a default <a href='#current-color-and-transition'>interval</a> of 2.8 seconds.  
In order, these colors are: 
- `#FFC0CB` - <span style="color: #FFC0CB; font-weight: bolder;">Pink</span>
- `#FFD700` - <span style="color: #FFD700; font-weight: bolder;">Gold</span>
- `#7FFFD4` - <span style="color: #7FFFD4; font-weight: bolder;">Aquamarine</span>
- `#FFA500` - <span style="color: #FFA500; font-weight: bolder;">Web Orange</span>
- `#9370DB` - <span style="color: #9370DB; font-weight: bolder;">Dull Lavendar</span>
- `#00FFFF` - <span style="color: #00FFFF; font-weight: bolder;">Cyan</span>
- `#E969B4` - <span style="color: #E969B4; font-weight: bolder;">Deep Blush</span>
- `#8BCE25` - <span style="color: #8BCE25; font-weight: bolder;">Atlantis</span>
- `#40E0D0` - <span style="color: #40E0D0; font-weight: bolder;">Turquoise</span>
- `#FF7C4C` - <span style="color: #FF7C4C; font-weight: bolder;">Coral</span>
- `#DA70D6` - <span style="color: #DA70D6; font-weight: bolder;">Orchid</span>
- `#00FA9A` - <span style="color: #00FA9A; font-weight: bolder;">Spring Green</span>

This is the function that handles the Color Fade mode:
```ts
export function startColorFade() {
    logConsole('Color fade started', 'info');
    const colors = {
        'Pink': '#FFC0CB',
        'Gold': '#FFD700',
        'Aquamarine': '#7FFFD4',
        'Web Orange': '#FFA500',
        'Dull Lavender': '#9370DB',
        'Cyan': '#00FFFF',
        'Deep Blush': '#E969B4',
        'Atlantis': '#8BCE25',
        'Turquoise': '#40E0D0',
        'Coral': '#FF7C4C',
        'Orchid': '#DA70D6',
        'Spring Green': '#00FA9A'
    };
    const colorNames = Object.keys(colors);
    let currentIndex = 0;

    // Initial color update
    bodyElement.style.backgroundColor = colors[colorNames[currentIndex]];

    const fadetime = menu.fadetransrange.value; // Get fade transition length value when restarted
    bodyElement.style.transition = `background-color ${fadetime}s ease-in-out`;
    menu.colorbadge.textContent = colors[colorNames[currentIndex]]; // Initial color badge update

    fadeIntervalID = setInterval(() => {
        currentIndex = (currentIndex + 1) % colorNames.length;
        const currentColor = colors[colorNames[currentIndex]];
        bodyElement.style.backgroundColor = currentColor;
        menu.colorbadge.textContent = currentColor;
        setMetaColor('color', currentColor);
        logConsole(`Fade background color to: ${currentColor}`, 'debug');
    }, 3000);
}
```

#### Solid Color
When Solid Color Mode is selected, you can choose between 33 preset background colors.  
Here's the list of all the built-in preset colors: (<a href='#image'>Skip to Image section</a>)
##### Basic Colors
- `#FF0000` - <span style="color: #FF0000; font-weight: bolder;">Basic red</span>
- `#FFA500` - <span style="color: #FFA500; font-weight: bolder;">Basic orange</span>
- `#FFFF00` - <span style="color: #FFFF00; font-weight: bolder;">Basic yellow</span>
- `#00FF00` - <span style="color: #00FF00; font-weight: bolder;">Basic green</span>
- `#0000FF` - <span style="color: #0000FF; font-weight: bolder;">Basic blue</span>
- `#FF00FF` - <span style="color: #FF00FF; font-weight: bolder;">Basic magenta</span>
- `#FFFFFF` - <span style="color: #FFFFFF; font-weight: bolder;">Basic white</span>
- `#808080` - <span style="color: #808080; font-weight: bolder;">Basic gray</span>
- `#000000` - <span style="color: #000000; font-weight: bolder;">Basic black</span>

##### Bright Colors
- `#F2B5D4` - <span style="color: #F2B5D4; font-weight: bolder;">Pale pink</span>
- `#C2E0E9` - <span style="color: #C2E0E9; font-weight: bolder;">Pale blue</span>
- `#E1D5E7` - <span style="color: #E1D5E7; font-weight: bolder;">Lavender</span>
- `#B0E0E6` - <span style="color: #B0E0E6; font-weight: bolder;">Powder blue</span>
- `#F7D5AA` - <span style="color: #F7D5AA; font-weight: bolder;">Pale peach</span>
- `#D5E8D4` - <span style="color: #D5E8D4; font-weight: bolder;">Mint green</span>
- `#92A8D1` - <span style="color: #92A8D1; font-weight: bolder;">Periwinkle blue</span>
- `#E6AF75` - <span style="color: #E6AF75; font-weight: bolder;">Apricot</span>
- `#D9B5A5` - <span style="color: #D9B5A5; font-weight: bolder;">Dusty rose</span>
- `#9AC1B7` - <span style="color: #9AC1B7; font-weight: bolder;">Seafoam green</span>
- `#D0B9C3` - <span style="color: #D0B9C3; font-weight: bolder;">Mauve</span>
- `#C4B7D9` - <span style="color: #C4B7D9; font-weight: bolder;">Lilac</span>

##### Dark Colors
- `#D72C6F` - <span style="color: #D72C6F; font-weight: bolder;">Deep pink</span>
- `#227FBF` - <span style="color: #227FBF; font-weight: bolder;">Deep blue</span>
- `#7E3F9D` - <span style="color: #7E3F9D; font-weight: bolder;">Deep lavendar</span>
- `#367F89` - <span style="color: #367F89; font-weight: bolder;">Deep powder blue</span>
- `#FF713F` - <span style="color: #FF713F; font-weight: bolder;">Deep peach</span>
- `#549F55` - <span style="color: #549F55; font-weight: bolder;">Dark mint green</span>
- `#2B4771` - <span style="color: #2B4771; font-weight: bolder;">Deep periwinkle blue</span>
- `#C55324` - <span style="color: #C55324; font-weight: bolder;">Deep apricot</span>
- `#954A3E` - <span style="color: #954A3E; font-weight: bolder;">Deep dusty rose</span>
- `#457E70` - <span style="color: #457E70; font-weight: bolder;">Deep seafoam green</span>
- `#8B2C5A` - <span style="color: #8B2C5A; font-weight: bolder;">Deep mauve</span>
- `#7C5793` - <span style="color: #7C5793; font-weight: bolder;">Dark lilac</span>

{: .note }
The color names were sourced from [Name that Color](https://chir.ag/projects/name-that-color/) and other sources.

When a preset color is selected and [Text Color Override](#text-color) is disabled, the color of the clock display dynamically changes between black and white based on the luminance of the selected color.

Essentially, if the luminance of the selected color is greater than 62%, the text color will be set to black. Otherwise, the text color will be set to white.

#### Image
Here you can set a custom image as the background. You can use whatever image file type is covered by the `data:image` URI scheme, including but not limited to PNG, JPG, and GIF. (Yes, you can set an animated background!)

![A screenshot of the Custom Image section in the Background Color Mode section of the menu.](/assets/images/docs-Features/backgroundtheme/imagemode.png)

You can also mess with some sizing effects for the background image. You may choose Automatic, Cover, or Stretch, all of which are explained in the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/background-size#values).

The Image Blur slider lets you blur the background image, possibly to enhance clock visibility.

![A screenshot of the site with a custom image set and a 10px image blur range.](/assets/images/docs-Features/backgroundtheme/imageblur-example.png)

{: .warning }
Because of the way the blur effect is rendered, it may cause the page to **continuously** use more GPU resources when enabled. Make sure you have hardware acceleration enabled! If you notice performance issues, consider lowering the blur value or disabling it entirely.

<hr>

### Current Color and Transition
The Current Color badge shows the hex value of the current background color. It will change when the Color Fade mode is enabled and when a preset color is manually selected.

The Color Transition slider lets you set the duration of the [CSS transition property](https://developer.mozilla.org/en-US/docs/Web/CSS/transition) when the background color changes. It defaults to 2.8 seconds, but can be changed to any value between 0 and 3 seconds.

Just like the Current Color badge, the transition is visible when using the Color Fade mode or when a preset color is chosen.

![A screenshot of the Color Transition section of the menu.](/assets/images/docs-Features/backgroundtheme/colortransition.png)

Changing the value of the Color Transition slider will **not** change the interval of the Color Fade mode. It is limited to 3 seconds max, as that is how often the Color Fade mode cycles through colors.

{: .note }
This setting is affected by your system's reduced motion preferences. If you have reduced motion enabled, the color change will be instant (no transition) regardless of this setting.

<hr>

### Text Color
The Text Color Override and the Text Color picker options let you change the color of the clock display. They are only visible when in Solid or Custom Image mode.

![A screenshot of the Text Color Override section of the menu.](/assets/images/docs-Features/backgroundtheme/textcolor.png)

Text Color Override is forced enabled when in Image mode, but can be freely toggled in Solid mode.
