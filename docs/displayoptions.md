---
title: Display Options
layout: default
parent: Features
nav_order: 7
---
# Display Options
{: .no_toc }
The Display Options section in the menu panel gives you options to change the look of the UI and other browser features. 

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

Here's how the `data-bs-theme` attribute gets modified. To avoid breaking everything, it gets applied on a per-container basis:

```ts
// Menu theme listener
menu.themeradio.forEach((radio) => {
    radio.addEventListener('change', () => {
        if (radio.id === 'lightthememode') {
            menu.container.dataset.bsTheme = 'light';
            menu.options.style.backgroundColor = '#ffffff';
            menu.options.style.color = '#212529';
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
            logConsole(`Menu theme set to: ${radio.id}`, 'info');
            showToast('Theme set to light mode ☀️');
        } else if (radio.id === 'darkthememode') {
            menu.container.dataset.bsTheme = 'dark';
            menu.options.style.backgroundColor = '#313539';
            menu.options.style.color = '#fff';
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
            logConsole(`Menu theme set to: ${radio.id}`, 'info');
            showToast('Theme set to dark mode 🌙');
        }
    });
});
```

### Panel Visibility
This checkbox toggles visiblity of the panel buttons, including the buttons to open the countdown, stopwatch, and menu panels.

![A screenshot of the Panel Visibility checkbox.](/assets/images/docs-Features/displayoptions/panelvisibility.png)

| Panel buttons visible | Panel buttons hidden |
| --- | --- |
| ![A screenshop of the page with Panel Visibility enabled.](/assets/images/docs-Features/displayoptions/panelvisibility-on.png) | ![A screenshop of the page with Panel Visibility disabled.](/assets/images/docs-Features/displayoptions/panelvisibility-off.png) |

### Tab Title
If you don't like the dynamic tab title, where it updates along with the time, you can disable it here. Additionally, the favicon also changes to a clock icon depending on the current hour. By default, the Tab Title is enabled.

![A screenshot of the Tab Title checkbox.](/assets/images/docs-Features/displayoptions/tabtitle.png)

| Tab Title enabled | Tab Title disabled |
| --- | --- |
| ![A screenshop of the page with Tab Title enabled.](/assets/images/docs-Features/displayoptions/tabtitle-on.png) | ![A screenshop of the page with Tab Title disabled.](/assets/images/docs-Features/displayoptions/tabtitle-off.png) |

## Fullscreen and Debugging
The fullscreen toggle and the debug checkbox are the last two Display options.

![A screenshot of the Fullscreen and debug logging options.](/assets/images/docs-Features/displayoptions/fullscreen-debug.png)

The fullscreen toggle is self-explanatory, and the debug checkbox enables and disables log debugging to the console.

To clarify, Online Web Clock uses a custom function called `logConsole()` to log messages to the console. It will only actually log if debug logging is enabled. Here's the function:

```ts
// Custom console logging function
export function logConsole(message: string, type: string = 'debug'):void {
    if (menu.debugcheckbox.checked && type === 'debug') {
        console.log(`DEBUG - ${message}`);
    } else if (type === 'error') {
        console.error(`ERROR - ${message}`);
    } else if (type === 'warning') {
        console.warn(`WARNING - ${message}`);
    } else if (menu.debugcheckbox.checked && type === 'info') {
        console.info(`INFO - ${message}`);
    }
}
```

The logic ensures that debug logging must be enabled to log DEBUG and <span style="color: #0DCAF0;">INFO</span> messages, but <span style="color: #FF5449;">ERROR</span> and <span style="color: #FE8D59;">WARNING</span> messages will always be logged.
