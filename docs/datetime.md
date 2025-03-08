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

{: .tip }
As of version 1.6.0, the clock mode is set automatically based on your system's current setting.

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
| Binary (Base 2) | Base 2, using only the digits 0 and 1.<br>**Example:** 6:30 is displayed as "110:11110". |
| Octal (Base 8) | Base 8, using the digits 0 to 7.<br>**Example:** 6:30 is displayed as "6:36". |
| Decimal (Base 10) | Base 10, the default way to represent numbers. |
| Hexadecimal (Base 16) | Base 16, using the digits 0 to 9 and the letters A to F.<br>**Example:** 6:30 is displayed as "6:1E". |
| Hexatrigesimal (Base 36) | Base 36, using the digits 0 to 9 and the letters A to Z.<br>**Example:** 6:30 is displayed as "6:U". |

![The time displayed using the Binary (Base 2) radix system. The time (4:30:15 PM) is shown as "100:11110:1111 PM".](/assets/images/docs-Features/datetime/displaysystem-binary.png)

<hr>

#### Conversions
Conversions give you fun ways to display the time:

| Conversion | Description |
| --- | --- |
| Emoji | Displays the time in number emoji blocks.<br>**Example:** 6:30 is displayed as "6️⃣:3️⃣0️⃣". |
| Roman Numerals | Displays the time in Roman numerals.<br>**Example:** 6:30 is displayed as "VI:XXX". |
| Words | Displays the time in English words.<br>**Example:** 6:30 is displayed as "six:thirty". |

![The time displayed using the Roman Numeral Conversion system. The time (4:30:15) is shown as "IV:XXX:XV".](/assets/images/docs-Features/datetime/displaysystem-romannumeral.png)

<hr>

#### Technical
These Display Systems are more geared towards tech-savvy users. They provide you with accurate Unix timestamps. 

| Technical Display System | Description |
| --- | --- |
| Unix timestamp (Milliseconds) | Displays the time as the number of milliseconds since the Unix epoch. |
| Unix timestamp (Seconds) | Displays the time as the number of seconds since the Unix epoch. |
| Time until Y2K38 problem | Displays remaining time until Y2K38 problem, where computers representing time with a signed 32-bit integer will overflow after 3:14:07 UTC on January 19, 2038 and likely explode. |

![The time displayed using the Unix timestamp (Milliseconds) experimental display system. The date (March 1, 2025 at 4:30:15 PM) is shown as "1740868215000".](/assets/images/docs-Features/datetime/displaysystem-unixmillis.png)

<hr>

### Time Bar
The time bar is a new addition which replaces the legacy Seconds Bar. It is a wide horizontal bar that displays the progress of time. It's width increases as time passes according to the chosen setting.

{: .tip }
You cannot enable the Time Bar if a border style is selected.

| Setting | Description |
| --- | --- |
| Week progress (Mon-Sun) | Displays the progress through the week, from Monday through Sunday. <br>**Example:** If it is Sunday, the bar will be 100% full. |
| Month progress | Displays the progress through the month.<br>**Example:** If it is the 15th of the month, the bar will be 50% full in a 30-day month. The calculation changes automatically based on the number of days in the month. |
| Day progress | Displays the progress through the day.<br>**Example:** If it is 6:00 PM (18:00), the bar will be 75% full. |
| Hour progress | Displays the progress through the hour.<br>**Example:** If it is 15 minutes into the hour, the bar will be 25% full. |
| Seconds | Displays the progress through the minute.<br>**Example:** If it is 15 seconds into the minute, the bar will be 25% full. |

![A screenshot of the Time Bar dropdown menu with "Off" selected](/assets/images/docs-Features/datetime/timebar.png)

<hr>

### Date Display
If you prefer a different date format other than the default, you can change that here. Each option is localized based on your browser's locale and updates automatically as the date changes.

![A screenshot of the Date Display dropdown menu with the first option selected](/assets/images/docs-Features/datetime/datedisplay.png)

The table below lists the different tokens Luxon uses for each date format:

| Date format token | Description |
| --- | --- |
| D | Localized numeric date (3/1/2025) |
| DD | Localized date with abbreviated month (Mar 1, 2025) |
| DDD | Localized date with full month (March 1, 2025) |
| DDDD | Localized date with full month and weekday (Saturday, March 1, 2025) |
| Off | The date is hidden |

![The date displayed using the "DDDD" date format. The date (3/1/2025) is shown as "Saturday, March 1, 2025".](/assets/images/docs-Features/datetime/datedisplay-dddd.png)

<hr>

### Date Alignment
You can change the alignment of the date relative to the clock's width. By default, the date is left aligned under the clock.

![A screenshot of the Date Alignment radio buttons with "Left" selected](/assets/images/docs-Features/datetime/datealignment.png)

![The date aligned to the right of the clock.](/assets/images/docs-Features/datetime/datealignment-right.png)

<hr>

### Border Style
You can set the border style of the clock to give it a sort of "frame" around the time, providing a bit of separation between the time and the date.

By default, there is no border style selected. You can change the border style to "Box" or "Bottom", both of which have the "Solid", "Dashed", "Dotted", and "Double" options.

{: .tip }
You cannot select a border style if the "Time Bar" is enabled.

![A screenshot of the Border Style radio buttons with "Box" and "Solid" selected](/assets/images/docs-Features/datetime/borderstyle.png)

| Border Style | Solid | Dashed | Dotted | Double |
| --- | --- | --- | --- | --- |
| Box | ![A screenshot of the Box border style with the "Solid" option selected](/assets/images/docs-Features/datetime/borderstyle-box-solid.png) | ![A screenshot of the Box border style with the "Dashed" option selected](/assets/images/docs-Features/datetime/borderstyle-box-dashed.png) | ![A screenshot of the Box border style with the "Dotted" option selected](/assets/images/docs-Features/datetime/borderstyle-box-dotted.png) | ![A screenshot of the Box border style with the "Double" option selected](/assets/images/docs-Features/datetime/borderstyle-box-double.png) |
| Bottom | ![A screenshot of the Bottom border style with the "Solid" option selected](/assets/images/docs-Features/datetime/borderstyle-bottom-solid.png) | ![A screenshot of the Bottom border style with the "Dashed" option selected](/assets/images/docs-Features/datetime/borderstyle-bottom-dashed.png) | ![A screenshot of the Bottom border style with the "Dotted" option selected](/assets/images/docs-Features/datetime/borderstyle-bottom-dotted.png) | ![A screenshot of the Bottom border style with the "Double" option selected](/assets/images/docs-Features/datetime/borderstyle-bottom-double.png) |

{: .note }
You may need to open the images in a new tab to see the border styles in detail.

<hr>

### Custom Note
You may add a custom note to the page. It can hold any text within 75 characters. A few examples of what it can be used for is quotes, reminders, jokes, etc. Additionally, you can choose between top and bottom alignment.

![A screenshot of the Custom Note text box with the text "Hello world!" entered](/assets/images/docs-Features/datetime/customnote.png)

![The custom note displayed at the bottom of the clock. The custom note says "Hello world!"](/assets/images/docs-Features/datetime/customnote-example.png)

{: .note }
> The custom note will also reflect any changes to [font customization](/docs/fontcustomization). However, font size is not applied to the custom note.
>
> The custom note can be exported along with your other settings.

<hr>

### Time Refresh Method
The Time Refresh Method checkbox lets you toggle between two methods of updating the time. By default, this is unchecked.

![A screenshot of the Time Refresh Method checkbox. It is currently unchecked](/assets/images/docs-Features/datetime/timerefreshmethod.png)

1. Default: The clock attempts to automatically sync with the system time by the second.
2. Legacy Refresh Method: The clock refreshes on a set interval, every 250 milliseconds.

**Why is this an option?** The new method of updating the time can be more accurate, but it depends on the browser's ability to keep a consistent interval, which browsers like Firefox struggle with.

**The legacy method,** on the other hand, maintains accuracy up to 250 milliseconds, updating much more frequently at the cost of slightly increasing CPU usage.

<hr>

Here's a look into the underlying code which is responsible with updating the clock display:
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
    const timeToNextSecond = 1000 - Number(getLuxNow('millis')) % 1000;

    setTimeout(() => {
        updateTime();
        updatePageDuration();

        // Start the regular interval updates
        let lastUpdateTime = Date.now();

        clockInterval = setInterval(() => {
            updateTime();
            updatePageDuration();
            logConsole('Time, date, and page duration updated...', 'info');

            const now = Date.now();
            const elapsed = now - lastUpdateTime;
            lastUpdateTime = now;

            const drift = elapsed - 1000;

            // Add a maximum drift threshold, e.g. 1000ms
            const cappedDrift = Math.max(Math.min(drift, 1000), -1000);

            if (Math.abs(drift) > 150) {
                logConsole(`Time drift detected: ${drift > 0 ? '+':''}${drift}ms.${Math.abs(drift) > 1000 ? ` Capped to ${cappedDrift}ms` : ''}`, 'debug');
                clearInterval(clockInterval!);
                setTimeout(startNewClock, 1000 - cappedDrift);
            }
        }, 1000);
    }, timeToNextSecond);
}

// Function to start the old clock method
function startOldClock() {
    clockInterval = setInterval(() => {
        updateTime();
        updatePageDuration();
        logConsole('Time, date, and page duration updated (Legacy method)...', 'info');
    }, timeRefresh) as unknown as NodeJS.Timeout;
}
```
