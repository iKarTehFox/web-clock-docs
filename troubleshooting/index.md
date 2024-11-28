---
title: Troubleshooting
layout: default
nav_order: 4
---
# Troubleshooting
{: .no_toc}

# Table of contents
{: .no_toc .text-delta}

1. TOC
{:toc}

## Error loading settings from the imported file
The following errors are a result of a JSON settings file failing verification. This could be due to many reasons, but the most common are explained below.

### Invalid value of version: [number]
This is likely due to your JSON settings file being outdated or corrupted. To fix this, please export a new settings file.  

![A screenshot of the invalid version error popup in Mozilla Firefox.](/assets/images/docs-Troubleshooting/import-version-firefox.png)

### Invalid value of [key]: [value]
You have a valid JSON file, but some settings have invalid values, as they might have been tampered with. Review the error to fix your settings file.  
For instance, the screenshot below shows an error for the `clockDisplay` setting set to `invalid`, but the only valid values are "binary", "octal", "decimal", "hexa", "emoji", "roman", and "words". The solution would be to set the setting's value to one of those.

![A screenshot of the general invalid value error popup in Mozilla Firefox.](/assets/images/docs-Troubleshooting/import-invalidvalue-firefox.png)

### Unexpected keys: [keyName]
The JSON file has extraneous, garbage data. You either imported the wrong file, your settings file is corrupted, or your settings file has been tampered with. Remove or replace the affected keys, or export a new settings file.

![A screenshot of the unexpected keys error popup in Mozilla Firefox.](/assets/images/docs-Troubleshooting/import-unexpectedkeys-firefox.png)

### Missing subkeys: [subkeys]
Your JSON file is missing important subkeys. Either the file is badly corrupted, or you simply selected the wrong JSON file. Select the correct settings file or export a new settings file.

![A screenshot of the missing subkeys error popup in Mozilla Firefox.](/assets/images/docs-Troubleshooting/import-missing-firefox.png)

### Invalid settings file toast
This toast may appear if you import a file that doesn't have valid JSON, or doesn't have a `.json` extension. Reselect the correct file and try again.

![A screenshot of the invalid settings file toast error popup.](/assets/images/docs-Troubleshooting/import-invalidfile.png)

<hr>

## Network problems
Online Web Clock is designed to work completely offline, however, it may display an error for certain actions which require an internet connection.

### Iconify icons not loading
Iconify MDI icons are used in a few places on the website, such as the menu panel buttons and weather widget. If there is no internet connection and icons are not cached, as a fall-back, the menu and panel buttons use emoji or Unicode characters.

| Iconify icon | Fallback |
| --- | --- |
| ![](/assets/images/docs-Troubleshooting/iconify-enabled.png) | ![](/assets/images/docs-Troubleshooting/iconify-disabled.png) |

The weather widget also uses Iconify icons, but there is no fallback as the weather widget is not displayed if there is no internet connection.

### Weather widget
In order to enable the weather widget, you need an active internet connection. If connection to the OpenWeatherMap API fails, the weather widget will not be displayed, and an error **will not** be displayed.

Additionally, the widget will be hidden and disabled if connection is lost between its automatic refresh.
