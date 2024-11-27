---
title: Date and Time
layout: default
parent: Features
nav_order: 3
---
# Date and Time
{: .no_toc }
The Date and Time section in the menu panel allows you to change how the clock looks and behaves.

![A screenshot of the Date and Time menu options."](/assets/images/docs-Features/datetime/datetime.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## Options
### Clock Mode
This radio button allows you to change the clock mode between 12-hour and 24-hour time.

![A screenshot of the Clock Mode radio buttons](/assets/images/docs-Features/datetime/clockmode.png)

When using the 24-hour clock mode, the AM/PM indicator is hidden.

| 12-hour mode | 24-hour mode |
| --- | --- |
| ![A screenshot of the clock in 12-hour clock mode](/assets/images/docs-Features/datetime/12h.png) | ![A screenshot of the clock in 24-hour clock mode](/assets/images/docs-Features/datetime/24h.png) |

<hr>

### Time Zone
Customize your clock's timezone with this dropdown menu. By default, your current time zone is selected.

![A screenshot of the Time Zone dropdown menu with "America/New York" selected](/assets/images/docs-Features/datetime/timezone.png)

The dropdown menu is automatically populated with the time zones your browser supports via `Intl.supportedValuesOf('timeZone')`.

```ts
// Function to get the list of time zones and group them by region
function getTimeZonesByRegion() {
    const timeZones = (Intl as any).supportedValuesOf('timeZone');
    const timeZoneGroups: { [key: string]: string[] } = {};
  
    timeZones.forEach((timeZone) => {
        const [region] = timeZone.split('/');
      
        if (!timeZoneGroups[region]) {
            timeZoneGroups[region] = [];
        }
  
        timeZoneGroups[region].push(timeZone);
    });
  
    return timeZoneGroups;
}
```

<hr>

### Display System
This menu allows you to change how the clock is displayed, offering different radix systems, conversions, and a few experimental options.

![A screenshot of the Display System dropdown menu with "Decimal (Base 10)" selected](/assets/images/docs-Features/datetime/displaysystem.png)

<hr>

#### Radix Systems
Choosing a different radix system will change the number of digits used to represent numbers:

| Radix | Description |
| --- | --- |
| Binary (Base 2) | Base 2, using only the digits 0 and 1. |
| Octal (Base 8) | Base 8, using the digits 0 to 7. |
| Decimal (Base 10) | Base 10, the default way to represent numbers. |
| Hexadecimal (Base 16) | Base 16, using the digits 0 to 9 and the letters A to F. |
| Hexatrigesimal (Base 36) | Base 36, using the digits 0 to 9 and the letters A to Z. |

![The time displayed using the Binary (Base 2) radix system. The time (4:30:15 PM) is shown as "100:11110:1111 PM".](/assets/images/docs-Features/datetime/displaysystem-binary.png)

<hr>

#### Conversions
Conversions give you fun ways to display the time:

| Conversion | Description |
| --- | --- |
| Emoji | Displays the time in emojis like 1️⃣2️⃣:0️⃣0️⃣. |
| Roman Numerals | Displays the time in Roman numerals like XII:00. |
| Words | Displays the time in words like twelve:o'clock. |

![The time displayed using the Roman Numeral Conversion system. The time (4:30:15) is shown as "IV:XXX:XV".](/assets/images/docs-Features/datetime/displaysystem-romannumeral.png)

<hr>

#### Experimental...
These specific Display Systems are only included for fun. They are coded in a non-standard, jerry-rigged way and are not guaranteed to work properly.

| Experimental Display System | Description |
| --- | --- |
| Unix timestamp (Milliseconds) | Displays the time as the number of milliseconds since the Unix epoch. |
| Unix timestamp (Seconds) | Displays the time as the number of seconds since the Unix epoch. |
| Time until Y2K38 problem | Time in seconds until the Y2K38 problem, where computers representing time with a signed 32-bit integer will overflow and probably explode. |

![The time displayed using the Unix timestamp (Milliseconds) experimental display system. The date (November 1st, 2024 at 4:30:15 PM) is shown as "1730496615000".](/assets/images/docs-Features/datetime/displaysystem-unixmillis.png)

<hr>

### Date Display
If you prefer a different date format other than the default, you can change that here. Each option is localized based on your browser's locale and updates automatically as the date changes.

![A screenshot of the Date Display dropdown menu with "Short" selected](/assets/images/docs-Features/datetime/datedisplay.png)

The table below lists the different tokens Luxon uses for each date format:

| Date Display | Description |
| --- | --- |
| D | Localized numeric date |
| DD | Localized date with abbreviated month |
| DDD | Localized date with full month |
| DDDD | Localized date with full month and weekday |
| Off | The date is hidden |

![The date displayed using the DDDD date display. The date (11/1/2024) is shown as "Friday, November 1st, 2024".](/assets/images/docs-Features/datetime/datedisplay-dddd.png)

<hr>

### Date Alignment
You can change the alignment of the date relative to the clock's width. By default, the date is left aligned under the clock.

![A screenshot of the Date Alignment radio buttons with "Left" selected](/assets/images/docs-Features/datetime/datealignment.png)

![The date aligned to the right of the clock.](/assets/images/docs-Features/datetime/datealignment-right.png)

<hr>

### Border Style
You can set the border style of the clock to give it a sort of "frame" around the time, providing a bit of separation between the time and the date.

By default, there is no border style selected. You can change the border style to "Box" or "Bottom", both of which have the "Solid", "Dashed", "Dotted", and "Double" options.

**You cannot select a border style if the "seconds bar" is visible.**

![A screenshot of the Border Style radio buttons with "Box" and "Solid" selected](/assets/images/docs-Features/datetime/borderstyle.png)

| Border Style | Solid | Dashed | Dotted | Double |
| --- | --- | --- | --- | --- |
| Box | ![A screenshot of the Box border style with the "Solid" option selected](/assets/images/docs-Features/datetime/borderstyle-box-solid.png) | ![A screenshot of the Box border style with the "Dashed" option selected](/assets/images/docs-Features/datetime/borderstyle-box-dashed.png) | ![A screenshot of the Box border style with the "Dotted" option selected](/assets/images/docs-Features/datetime/borderstyle-box-dotted.png) | ![A screenshot of the Box border style with the "Double" option selected](/assets/images/docs-Features/datetime/borderstyle-box-double.png) |
| Bottom | ![A screenshot of the Bottom border style with the "Solid" option selected](/assets/images/docs-Features/datetime/borderstyle-bottom-solid.png) | ![A screenshot of the Bottom border style with the "Dashed" option selected](/assets/images/docs-Features/datetime/borderstyle-bottom-dashed.png) | ![A screenshot of the Bottom border style with the "Dotted" option selected](/assets/images/docs-Features/datetime/borderstyle-bottom-dotted.png) | ![A screenshot of the Bottom border style with the "Double" option selected](/assets/images/docs-Features/datetime/borderstyle-bottom-double.png) |

**Note:** You may need to open the images in a new tab to see the border styles in detail.

<hr>

### Seconds Bar Visibility
Here, you can set the visibility of the "seconds bar", a thin, animated line that runs below the clock to indicate the current progress along the minute.

**You cannot enable the seconds bar if a border style is selected.**

![A screenshot of the Seconds Bar Visibility radio buttons with "Hide" selected](/assets/images/docs-Features/datetime/secondsbarvis.png)

<video controls controlslist="nodownload nofullscreen" loop muted>
    <source src="/assets/images/docs-Features/datetime/secondsbarvis.mp4" type="video/mp4">
    <source src="/assets/images/docs-Features/datetime/secondsbarvis.webm" type="video/webm">
</video>

**How does it work?** It is simply a horizontal line with a CSS animation that changes the width of the line based on the current seconds.

```ts
// Seconds progress bar
if (menu.secondsbarradio[0].checked) { // Check if visible, 0% if not.
    const secBarWidth = (Number(sec) / 59) * 100;
    dtdisplay.secondsBar.style.width = `${secBarWidth}%`;
} else {
    dtdisplay.secondsBar.style.width = '0%';
}
```

The width is calculated by dividing the current seconds by 59.  
**Why not 60**? If the number of seconds is divided by 60, the bar will never reach 100% width since a clock never displays 60, only 0-59.

<hr>

### Time Refresh Method
The Time Refresh Method checkbox lets you toggle between two methods of updating the time. By default, this is unchecked.

![A screenshot of the Time Refresh Method checkbox. It is currently unchecked](/assets/images/docs-Features/datetime/timerefreshmethod.png)

1. Default: The clock attempts to automatically sync with the system time by the second.
2. Legacy Refresh Method: The clock refreshes on a set interval, every 250 milliseconds.

**Why is this an option?** The new, default method of updating and syncing the time can be accurate, but it is dependent on the browser's ability to keep the interval consistent. If it isn't, such as on Firefox or non-Chromium-based browsers, the time may update erratically.

**The legacy method,** on the other hand, maintains accuracy up to 250 milliseconds, updating much more frequently at the cost of slightly increasing CPU usage.

Here's a look into the underlying code:
```ts
// Sync clock to system time function
let clockInterval: NodeJS.Timeout | null = null; // Variable to store the interval ID

// Function to start the clock based on the selected method
function startClock() {
    // Clear any existing interval
    if (clockInterval) {
        clearInterval(clockInterval);
    }

    if (menu.legacyrefreshcheckbox.checked) {
        startOldClock();
    } else {
        startNewClock();
    }
}

// Function to start the new clock method
function startNewClock() {
    const now = luxon.DateTime.now();
    const timeToNextSecond = 1000 - now.toMillis() % 1000;

    setTimeout(() => {
        updateTime();
        updatePageDuration();

        // Start the regular interval updates
        let lastUpdateTime = Date.now();

        clockInterval = setInterval(() => {
            updateTime();
            updatePageDuration();
            logConsole('Time and page duration updated...', 'info');

            // Correct the interval drift
            const now = Date.now();
            const elapsed = now - lastUpdateTime;
            lastUpdateTime = now;

            const drift = elapsed - 1000;
            if (Math.abs(drift) > 50) {
                logConsole(`Time drift detected: ${drift}ms.`, 'info');
                clearInterval(clockInterval!);
                setTimeout(startNewClock, 1000 - drift);
            }
        }, 1000);
    }, timeToNextSecond);
}

// Function to start the old clock method
function startOldClock() {
    clockInterval = setInterval(() => {
        updateTime();
        updatePageDuration();
        logConsole('Time and page duration updated (Legacy method)...', 'info');
    }, 250) as unknown as NodeJS.Timeout;
}
```
