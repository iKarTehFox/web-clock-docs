---
title: Display Options
layout: default
parent: Features
nav_order: 7
---
# Display Options
{: .no_toc }
The Display Options section in the menu panel gives you options to change the look of the UI and other browser features.

{: .tip }
All of these settings can be set with [URL parameters](/docs/url-params#base-url-parameters).

![A screenshot of the Display Options menu options.](/assets/images/docs-Features/displayoptions/displayoptions.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## Options
### Menu Theme
The Menu Theme radio buttons allow you to change the theme of the menu panel, either to Light, Dark, or Midnight. Theme functionality is included with Bootstrap, and can be changed with the `data-bs-theme` attribute.

![A screenshot of the Menu Theme radio buttons.](/assets/images/docs-Features/displayoptions/menutheme.png)

| Light theme | Dark theme | Midnight theme |
| --- | --- | --- |
| ![A screenshot of the page with Light theme enabled.](/assets/images/docs-Features/displayoptions/menutheme-light.png) | ![A screenshot of the page with Dark theme enabled.](/assets/images/docs-Features/displayoptions/menutheme-dark.png) | ![A screenshot of the page with Midnight theme enabled.](/assets/images/docs-Features/displayoptions/menutheme-midnight.png) |

{: .note }
The theme is automatically set based on your system's color scheme.

Here's how the `data-bs-theme` attribute gets modified. For modularity purposes, the theme is applied on a per-container basis.

```ts
// Menu theme function
export function setMenuTheme(theme: string | 'toggle', quiet: boolean = false): void {
    // Get current theme
    const currentTheme = menu.container.dataset.bsTheme || 'light';
    
    // Handle auto
    if (theme === 'auto') {
        theme = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light';
        menu.themeradio[theme === 'light' ? 0 : 1].checked = true;
    }

    // Handle toggle (cycle through themes)
    if (theme === 'toggle') {
        const themeKeys = Object.keys(themes);
        const currentIndex = themeKeys.indexOf(currentTheme);
        const nextIndex = (currentIndex + 1) % themeKeys.length;
        theme = themeKeys[nextIndex];
        menu.themeradio[nextIndex].checked = true;
    }
    
    // Validate theme exists
    if (!themes[theme]) {
        logConsole(`Invalid theme: ${theme}, defaulting to light`, 'error');
        theme = 'light';
    }

    const themeConfig = themes[theme];
    
    // Apply theme to all containers
    const containers = [
        menu.container,
        weather.container,
        stopwatch.container,
        countdown.container
    ];
    
    containers.forEach(container => {
        // Set data-bs-theme attribute
        container.dataset.bsTheme = theme;
        
        // Set text color
        if (container !== menu.container) {
            container.style.color = themeConfig.textColor;
        }
        
        // Set background color for popup containers
        if (container === stopwatch.container || container === countdown.container) {
            container.style.backgroundColor = themeConfig.backgroundColor || 
                (theme === 'light' ? '#ffffff' : '#313539');
        }
    });
    
    // Browser meta
    setMetaColor('theme', themeConfig.metaTheme);
    
    logConsole(`Menu theme set to: ${theme}`, 'debug');
    if (!quiet) showToast(i18next.t(`toasts.global.theme${theme}`));
}
```

<hr>

### Panel Visibility
This checkbox toggles visiblity of the panel buttons, including the buttons to open the countdown, stopwatch, and menu panels.

![A screenshot of the Panel Visibility checkbox.](/assets/images/docs-Features/displayoptions/panelvisibility.png)

| Panel buttons visible | Panel buttons hidden |
| --- | --- |
| ![A screenshot of the page with Panel Visibility enabled.](/assets/images/docs-Features/displayoptions/panelvisibility-on.png) | ![A screenshot of the page with Panel Visibility disabled.](/assets/images/docs-Features/displayoptions/panelvisibility-off.png) |

<hr>

### Tab Title
If you don't like the dynamic tab title, where it updates along with the time, you can disable it here. Additionally, the favicon also changes to a clock icon depending on the current hour. By default, the Tab Title is enabled.

![A screenshot of the Tab Title checkbox.](/assets/images/docs-Features/displayoptions/tabtitle.png)

| Tab Title enabled | Tab Title disabled |
| --- | --- |
| ![A screenshot of the page with Tab Title enabled.](/assets/images/docs-Features/displayoptions/tabtitle-on.png) | ![A screenshot of the page with Tab Title disabled.](/assets/images/docs-Features/displayoptions/tabtitle-off.png) |

## Fullscreen
This toggle button switches between fullscreen and windowed mode.

![A screenshot of the Fullscreen toggle button.](/assets/images/docs-Features/displayoptions/fullscreen.png)

{: .warning }
The fullscreen toggle may not function correctly if you manually entered fullscreen mode with <kbd>F11</kbd>.
