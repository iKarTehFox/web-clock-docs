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

4. **Notification toggle**
 - Enables the website to post a notification when the countdown finishes. This requires notifications to be allowed in your browser.

   {: .tip }
   After the countdown finishes, a toast will appear in the bottom right indication that the countdown has elapsed. With notifications enabled, the toast will have its duration decreased.
