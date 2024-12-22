---
title: Debugging
layout: default
parent: Features (Development)
nav_order: 2
---
Coming Soon
{: .label .label-yellow}
# Debugging
{: .no_toc}
The Debugging section in the menu panel gives you many debug/testing options to help with development. This section is only visible when the `debugMode` URL parameter is set to true.

{: .info}
When `debugMode` is set to true, debug logging will also be enabled. See [URL Parameters](/docs/url-params).

![A screenshot of the Debugging menu options.](/assets/images/docs-Development/debugging/debugging.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## Options
### Debug info
This section currently displays your User Agent string and may be updated to display other information in the future.

![A screenshot of the Debug info User Agent text.](/assets/images/docs-Development/debugging/debuginfo.png)

{: .info }
The User Agent string shown above is of Chrome 131.0.0.0 running on Windows 11.

### Dev Colors
When [Solid mode](/docs/backgroundtheme#background-color-mode) is enabled, the Dev Colors section lets you choose a color from a list of hidden preset colors.

Here are the list of dev colors:
- `#27262B` - <span style="color: #27262B; font-weight: bolder; background-color: #FFF">Jekyll Dark</span>
- `#232327` - <span style="color: #232327; font-weight: bolder; background-color: #FFF">Firefox Dark</span>
- `#282828` - <span style="color: #282828; font-weight: bolder; background-color: #FFF">Chrome Dark</span>
- `#1F1F1F` - <span style="color: #1F1F1F; font-weight: bolder; background-color: #FFF">GitHub Dark</span>
- `#232327` - <span style="color: #232327; font-weight: bolder; background-color: #FFF">VS Code Dark</span>
- `#2B2B2C` - <span style="color: #2B2B2C; font-weight: bolder; background-color: #FFF">Windows Dark</span>
- `#212529` - <span style="color: #212529; font-weight: bolder; background-color: #FFF">Bootstrap Dark 1</span>
- `#313539` - <span style="color: #313539; font-weight: bolder; background-color: #FFF">Bootstrap Dark 2</span>

These specific colors were sourced from different UI elements from their respective applications.  
As for Jekyll Dark, it matches this website's dark theme color so screenshots with that background color will blend in with the site.

{: .warning }
As these colors are intended for testing purposes only, they cannot be imported back into Online Web Clock and will return a verification error when uploaded.

### Settings
The two options in this section are for testing settings exports, specifically to check for any anomalies in the exported JSON data.

![A screenshot of the Settings debugging options.](/assets/images/docs-Development/debugging/settings.png)

The "Log JSON" button exports the current settings in JSON format to the console. This is useful for checking exported JSON without having to download the file.

![A screenshot of the Settings "Log JSON" console output.](/assets/images/docs-Development/debugging/logjson.png)

The "Extract BG image" button extracts the current background image and shows it in a card overlay, allowing you to view it independently of other page elements and download it, if you wish.

![A screenshot of the Settings "Extract BG image" card overlay.](/assets/images/docs-Development/debugging/extractbg.png)

### Toasts
These buttons let you test the toast notifications and their different themes.

![A screenshot of the Toasts debugging options.](/assets/images/docs-Development/debugging/toasts.png)

When clicked, the buttons will spawn a Toastify toast with the corresponding theme. The default duration of 3 seconds is used.

![A screenshot of the Toasts debugging options.](/assets/images/docs-Development/debugging/toast.png)

### Card Overlay
Here you can test the two forms of card overlays, one with regular text and the other containing media.

![A screenshot of the Card Overlay debugging options.](/assets/images/docs-Development/debugging/cardoverlay.png)

{: .info }
For more info on card overlays, see [Card Overlay](/docs-dev/cardoverlay).
