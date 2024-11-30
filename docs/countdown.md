---
title: Countdown
layout: default
parent: Features
nav_order: 1
---
# Countdown
{: .no_toc }
The countdown panel allows you to set a timer for any specified amount of time up to 100 hours.

![A screenshot of the countdown panel item, highlighted in red and with a tooltip showing with the text "Countdown"](/assets/images/docs-Features/countdown/panelitem.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## Layout
![A screenshot of the countdown panel. The time remaining shown is 29 minutes and 57 seconds. The countdown timer is set to 30 minutes and is enabled.](/assets/images/docs-Features/countdown/countdown.png)

1. **Time display**
 - This shows the time remaining on the countdown timer after it has been set and started. It is displayed in the format of `hours:minutes:seconds`.
 - The font family changes automatically depending on the currently set font in the menu.

2. **Time input**
 - These are the three input fields for the hours, minutes and seconds. You can type in the values directly, or use the up and down arrows to increase or decrease the value.
 - You cannot set a time greater than 100 hours.

    {: .note }
    Not all fields have to be filled in. If you leave a field blank, it will default to **0**.

3. **Control buttons**
 - <span style="color: #0d6efd;">**Start:**</span> Starts or resums the countdown timer if the time has been set, the time set is not greater than 100 hours, and the timer is not already running.
 - <span style="color: #ffc107;">**Pause:**</span> Pauses the countdown timer if it is currently running.
 - <span style="color: #dc3545;">**Reset:**</span> Stops and resets the countdown timer to 00:00:00.

After the countdown has finished, a green popup will appear at the bottom right notifying you that the countdown has finished.

![A screenshot of the page with a green toast notification at the bottom right with the text "Countdown finished!"](/assets/images/docs-Features/countdown/toast.png)

## Closing behavior
The code below shows which elements, if clicked on, will close the countdown panel. Pressing <kbd>Esc</kbd> will close all panels currently open.

When closed, the countdown will continue to run in the background.

```ts
// Click outside to close countdown
document.addEventListener('DOMContentLoaded', function() {
    document.addEventListener('click', function(e) {
        const target = e.target as HTMLElement;
        const isMenuRelated = menu.options.contains(target) || 
                                   menu.obutton.contains(target) || 
                                   countdown.container.contains(target) || 
                                   countdown.obutton.contains(target);
        const isTooltip = target.closest('.tooltip') !== null;

        if (!isMenuRelated && !isTooltip && countdown.container.style.display !== 'none') {
            countdown.container.style.display = 'none';
            countdown.obutton.className = 'btn btn-secondary';
            logConsole('Countdown panel closed', 'info');
        }
    });
});

// Esc down to close countdown
document.addEventListener('keydown', function(e) {
    if (e.key === 'Escape' && countdown.container.style.display !== 'none') {
        countdown.container.style.display = 'none';
        countdown.obutton.className = 'btn btn-secondary';
        logConsole('Countdown panel closed', 'info');
    }
});
```

| Element clicked | Will close countdown panel? |
| --- | --- |
| Countdown close button | ✅ |
| Stopwatch open button | ✅ |
| Menu close button | ✅ |
| Outside area | ✅ |
| Menu open button | ❌ |
| Menu panel | ❌ |