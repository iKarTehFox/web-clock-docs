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
The mode radio buttons let you choose between the Color Fade, Solid, and Custom Image modes.

![A screenshot of the Background Color Mode radio buttons.](/assets/images/docs-Features/backgroundtheme/colormode.png)

#### Color Fade
In this mode, the background color fades between a preset list of colors, with a default <a href='#color-transition'>interval</a> of 2.8 seconds.  
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
function startColorFade() {
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

    bodyElement.style.backgroundColor = colors[colorNames[currentIndex]];
    const fadetime = menu.fadetransrange.value; // Get fade transition length value when restarted
    bodyElement.style.transition = `background-color ${fadetime}s ease-in-out`;
    menu.colorbadge.textContent = colors[colorNames[currentIndex]]; // Initial color badge update

    fadeIntervalID = setInterval(() => {
        currentIndex = (currentIndex + 1) % colorNames.length;
        const currentColor = colors[colorNames[currentIndex]];
        bodyElement.style.backgroundColor = currentColor;
        menu.colorbadge.textContent = currentColor;
        logConsole(`Fade background color to: ${currentColor}`, 'info');
    }, 3000);
}
```

#### Solid
When Solid mode is selected, you can choose between 33 preset background colors.  
Here are the list of preset colors: (<a href='#custom-image'>Skip to Custom Image section</a>)
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

```ts
// Preset color buttons listener
menu.presetcolors.forEach((radio) => {
    radio.addEventListener('change', () => {
        const color = radio.dataset.color;
        // Determine the luminance of the background color
        const luminance = getLuminance(color as string);

        // Set the text color based on the background luminance
        if (luminance > 0.62 && tcoO === 0) {
            dtdisplay.ccontainer.style.color = '#212529'; // Set black text color
            dtdisplay.secondsBar.style.backgroundColor = '#212529';
        } else if (tcoO === 0) {
            dtdisplay.ccontainer.style.color = '#FFF'; // Set white text color
            dtdisplay.secondsBar.style.backgroundColor = '#FFF';
        }
    });
});

function getLuminance(color: string): number {
    // Assuming color is in RGB format, convert it to relative luminance
    const r = parseInt(color.substring(1, 3), 16) / 255;
    const g = parseInt(color.substring(3, 5), 16) / 255;
    const b = parseInt(color.substring(5, 7), 16) / 255;

    // Calculate the relative luminance using the sRGB color space formula
    const luminance = 0.2126 * r + 0.7152 * g + 0.0722 * b;
    logConsole(`Luminance for ${color}: ${luminance}`, 'info');

    return luminance;
}
```

#### Custom Image
You can also set a custom image as the background. You can use whatever image file type is supported by the `data:image` URI scheme, including but not limited to PNG, JPG, and GIF.

![A screenshot of the Custom Image section in the Background Color Mode section of the menu.](/assets/images/docs-Features/backgroundtheme/customimage.png)

You can also mess with some sizing effects for the background image. You may choose Automatic, Cover, or Stretch, all of which are explained in the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/background-size#values).

The Image Blur slider lets you blur the background image, possibly to enhance clock visibility.

![A screenshot of the site with a custom image set and a 10px image blur range.](/assets/images/docs-Features/backgroundtheme/imageblur-example.png)

{: .warning }
Because of the way the blur effect is rendered, it may cause the page to **continuously** use more GPU resources when enabled.

<hr>

### Current Color and Transition
The Current Color badge dynamically shows the current background color set. It will change during Color Fade mode, and when a preset color is manually selected.

The Color Transition slider lets you set the duration of the [CSS transition property](https://developer.mozilla.org/en-US/docs/Web/CSS/transition) when the background color changes. It defaults to 2.8 seconds, but can be changed to a value between 0 and 3 seconds. Just like the Current Color badge, the transition is visible when using the Color Fade mode or when a preset color is manually selected.

![A screenshot of the Color Transition section of the menu.](/assets/images/docs-Features/backgroundtheme/colortransition.png)

The maximum value of 3 seconds is to prevent the transition from being too long, as the Color Fade mode changes colors every 3 seconds.

{: .note }
Changing the value of the Color Transition slider will not change the interval of the Color Fade mode. It is always locked to 3 seconds.

<hr>

### Text Color
The Text Color Override radio buttons and the Text Color picker lets you change the color of the clock display. They are only visible when in Solid or Custom Image mode.

![A screenshot of the Text Color Override section of the menu.](/assets/images/docs-Features/backgroundtheme/textcolor.png)

When using a custom image, the Text Color Override is forced on, but can be toggled in Solid mode.
