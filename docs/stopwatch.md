---
title: Stopwatch
layout: default
parent: Features
nav_order: 2
---
# Stopwatch
{: .no_toc }
The stopwatch panel allows you to start a stopwatch and record lap times.

![A screenshot of the stopwatch panel item, highlighted in red and with a tooltip showing with the text "Stopwatch"](/assets/images/docs-Features/stopwatch/panelitem.png)

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Layout
![A screenshot of the stopwatch panel. The time shown is 00:00:15.801. The stopwatch is currently running.](/assets/images/docs-Features/stopwatch/stopwatch.png)

1. **Time display**
 - This shows the time elapsed on the stopwatch. It is displayed in the format of `hours:minutes:seconds.milliseconds`.
 - The font family is locked to Ubuntu Mono, as to keep the time display width consistent while the stopwatch is running.

2. **Control buttons**
 - <span style="color: #0d6efd;">**Start:**</span> Starts or resumes the stopwatch if it is not already running.
 - <span style="color: #ffc107;">**Pause:**</span> Pauses the stopwatch if it is currently running.
 - <span style="color: #dc3545;">**Reset:**</span> Stops and resets the stopwatch to 00:00:00.000.
 - <span style="color: #6c757d;">**Lap:**</span> Records the current time as a lap time.

3. **Lap history**
 - This shows a list of all the lap times recorded by the stopwatch.
 - You can add new times by clicking the **Lap** button.
 - You can resize the lap history window by dragging the bottom right corner.

    {: .note }
    The format of each lap is `#Index: Time since last lap - Total time elapsed`.

The stopwatch will continue to run until manually stopped or reset.

## Closing behavior
The code below shows which elements, if clicked on, will close the stopwatch panel. Pressing <kbd>Esc</kbd> will close all panels currently open.

When closed, the stopwatch will be automatically paused.

```ts
// Click outside to close stopwatch
document.addEventListener('DOMContentLoaded', function() {
    document.addEventListener('click', function(e) {
        const target = e.target as HTMLElement;
        const isMenuRelated = menu.options.contains(target) || 
                                   menu.obutton.contains(target) || 
                                   menu.cbutton.contains(target) || 
                                   stopwatch.container.contains(target) || 
                                   stopwatch.obutton.contains(target);
        const isStopwatchVisible = stopwatch.container.style.display !== 'none';
        const isTooltip = target.closest('.tooltip') !== null;
        const isCardOverlay = target.closest('[data-overlay="card-overlay"]') !== null;
        const isScannerOverlay = target.closest('[data-overlay="scanner-overlay"]') !== null;

        if (!isMenuRelated && !isTooltip && !isCardOverlay && !isScannerOverlay && isStopwatchVisible) {
            stopwatch.container.style.display = 'none';
            stopwatch.obutton.className = 'btn btn-secondary';
            logConsole('Stopwatch panel closed', 'info');
            pauseStopwatch();
        }
    });
});

// Esc down to close stopwatch
document.addEventListener('keydown', function(e) {
    const isStopwatchVisible = stopwatch.container.style.display !== 'none';
    const isCardOverlayVisible = document.querySelector('[data-overlay="card-overlay"]') !== null;
    const isScannerOverlayVisible = document.querySelector('[data-overlay="scanner-overlay"]') !== null;

    if (e.key === 'Escape' && isStopwatchVisible && !isCardOverlayVisible && !isScannerOverlayVisible) {
        stopwatch.container.style.display = 'none';
        stopwatch.obutton.className = 'btn btn-secondary';
        logConsole('Stopwatch panel closed', 'info');
        pauseStopwatch();
    }
});
```
The following table shows which elements, if clicked on, will close the stopwatch panel.  
Essentially, the stopwatch panel will only close if the stopwatch panel is opened, or if the user clicks outside the stopwatch panel.

| Element clicked | Will close stopwatch panel? |
| --- | --- |
| Stopwatch close button | ✅ |
| Countdown open button | ✅ |
| Outside area | ✅ |
| Menu open button | ❌ |
| Menu close button | ❌ |
| Menu panel | ❌ |
| Card overlay | ❌ |
| QR Scanner overlay | ❌ |

The menu opens and closes independently of the stopwatch panel, and will never close the stopwatch panel when interacted with.