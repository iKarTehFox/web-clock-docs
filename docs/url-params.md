---
title: URL Parameters
layout: default
parent: Features
nav_order: 9
---
# URL Parameters
{: .no_toc }
In Online Web Clock, you can use URL Parameters to directly pass options into the site on load. This is useful for deploying the site to an embedded device to ensure settings are consistent.

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## URL Parameter list
### Base URL Parameters

| Parameter | Type | Description |
| --- | --- | --- |
| debugMode | boolean | Enables debug logging and Debugging menu options |
| darkMode | boolean | Enables dark mode |
| panelVis | boolean | Toggles panel buttons visibility |
| preset | filename | Load the `<filename>` JSON preset file from `/assets/` |
| tabTitle | boolean | Toggles dynamic tab title functionality |
| autoRestart | integer | Auto reloads the website after `<integer>` seconds (Min `15`, max `86400`) |
| lockSettings | boolean | Prevent end-user settings modification |

#### MORE INFO
**How do I load my custom preset file?** Download or build the site, and serve locally. You can place your own preset JSON file in the `/assets/` directory, then specify the filename in the parameter! 

**What purpose does autoRestart serve?** When set to an integer within `15` and `86400` inclusive (15 seconds to 24 hours), the page will start a background timer to reload the page after the specified duration. This ensures the page is up-to-date and maintains a stable internet connection.

**How does lockSettings work?** When this parameter is set to `true`, the **entire** menu container element and panel buttons are **deleted from the DOM**. This ensures the end-user cannot change any settings after the page is deployed.

For **deployment**, the following parameters are recommended: `?preset=<filename>&autoRestart=<integer>&lockSettings=true`

**Example:** `?darkMode=true&panelVis=false&tabTitle=false&preset=onlinewebclock-amoled-preset` loads the `onlinewebclock-amoled-preset` preset file, enables the dark theme, hides the panel buttons, and disables the tab title.

<hr>

### Weather widget parameters
To **enable** the weather widget, **all of the following parameters must be set**:

| Parameter | Type | Description |
| --- | --- | --- |
| weatherApi | string | OpenWeatherMap API key |
| weatherLat | float | Latitude of the location |
| weatherLon | float | Longitude of the location |
| weatherUnits | string | Units to use for weather data (`metric` or `imperial`) |

**Example:** `?weatherApi=API_KEY&weatherLat=40.7128&weatherLon=-74.0060&weatherUnits=imperial` would load the weather widget with the specified OWM API key, using imperial units, and the coordinates of New York City.

<hr>

### Weather widget positioning
To set a custom position offset for the weather widget, the **weather widget must be enabled** via the parameters above! The default position, with no parameters set, is the bottom left corner of the screen.

Additionally, **both parameters** below **must be set** to position the widget:

| Parameter | Type | Description |
| --- | --- | --- |
| weatherWidgetPosX | integer | Horizontal offset of the weather widget from the left edge of the screen |
| weatherWidgetPosY | integer | Vertical offset of the weather widget from the top edge of the screen |

**Example:** `?weatherWidgetPosX=10&weatherWidgetPosY=10` would position the widget **10px from the left** and **10px from the top**.

