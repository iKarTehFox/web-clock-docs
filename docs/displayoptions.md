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
The Menu Theme radio buttons allow you to change the theme of the menu panel, either Light or Dark. Theme functionality is included with Bootstrap, and can be changed with the `data-bs-theme` attribute.

![A screenshot of the Menu Theme radio buttons.](/assets/images/docs-Features/displayoptions/menutheme.png)

| Light theme | Dark theme |
| --- | --- |
| ![A screenshop of the page with Light theme enabled.](/assets/images/docs-Features/displayoptions/menutheme-light.png) | ![A screenshop of the page with Dark theme enabled.](/assets/images/docs-Features/displayoptions/menutheme-dark.png) |

Here's how the `data-bs-theme` attribute gets modified. To avoid breaking everything, it gets applied on a per-element container basis:

```ts
// Menu theme listener
menu.themeradio.forEach((radio) => {
    radio.addEventListener('change', () => {
        match(radio.id)
            .with('lightthememode', () => {
                menu.container.dataset.bsTheme = 'light';
                // Weather container
                weather.container.dataset.bsTheme = 'light';
                weather.container.style.color = '#212529';
                // Stopwatch container
                stopwatch.container.dataset.bsTheme = 'light';
                stopwatch.container.style.backgroundColor = '#ffffff';
                stopwatch.container.style.color = '#212529';
                // Countdown container
                countdown.container.dataset.bsTheme = 'light';
                countdown.container.style.backgroundColor = '#ffffff';
                countdown.container.style.color = '#212529';
                // Browser meta
                setMetaColor('theme', 'light');
                logConsole(`Menu theme set to: ${radio.id}`, 'debug');
                showToast('Theme set to light mode ☀️');
            })
            .with('darkthememode', () => {
                menu.container.dataset.bsTheme = 'dark';
                // Weather container
                weather.container.dataset.bsTheme = 'dark';
                weather.container.style.color = '#fff';
                // Stopwatch container
                stopwatch.container.dataset.bsTheme = 'dark';
                stopwatch.container.style.backgroundColor = '#313539';
                stopwatch.container.style.color = '#fff';
                // Countdown container
                countdown.container.dataset.bsTheme = 'dark';
                countdown.container.style.backgroundColor = '#313539';
                countdown.container.style.color = '#fff';
                // Browser meta
                setMetaColor('theme', 'dark');
                logConsole(`Menu theme set to: ${radio.id}`, 'debug');
                showToast('Theme set to dark mode 🌙');
            })
            .otherwise(() => {
                logConsole(`Invalid theme mode: ${radio.id}`, 'error');
            });
    });
});
```

<hr>

### Panel Visibility
This checkbox toggles visiblity of the panel buttons, including the buttons to open the countdown, stopwatch, and menu panels.

![A screenshot of the Panel Visibility checkbox.](/assets/images/docs-Features/displayoptions/panelvisibility.png)

| Panel buttons visible | Panel buttons hidden |
| --- | --- |
| ![A screenshop of the page with Panel Visibility enabled.](/assets/images/docs-Features/displayoptions/panelvisibility-on.png) | ![A screenshop of the page with Panel Visibility disabled.](/assets/images/docs-Features/displayoptions/panelvisibility-off.png) |

<hr>

### Tab Title
If you don't like the dynamic tab title, where it updates along with the time, you can disable it here. Additionally, the favicon also changes to a clock icon depending on the current hour. By default, the Tab Title is enabled.

![A screenshot of the Tab Title checkbox.](/assets/images/docs-Features/displayoptions/tabtitle.png)

| Tab Title enabled | Tab Title disabled |
| --- | --- |
| ![A screenshop of the page with Tab Title enabled.](/assets/images/docs-Features/displayoptions/tabtitle-on.png) | ![A screenshop of the page with Tab Title disabled.](/assets/images/docs-Features/displayoptions/tabtitle-off.png) |

## Fullscreen
This toggle button switches between fullscreen and windowed mode.

![A screenshot of the Fullscreen toggle button.](/assets/images/docs-Features/displayoptions/fullscreen.png)

{: .warning }
The fullscreen toggle may not function correctly if you manually entered fullscreen mode with <kbd>F11</kbd>.
