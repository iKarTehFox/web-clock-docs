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
**Reason**: Your settings file is outdated.  
**Solution**: Export a new settings file with the same settings.

![A screenshot of the invalid version error popup in Mozilla Firefox.](/assets/images/docs-Troubleshooting/import-version-firefox.png)

### Invalid value of [key]: [value]
**Reason**: A subkey was found with an invalid or disallowed value.  
**Solution**: Review the error to fix your settings file, or export a new settings file.

![A screenshot of the general invalid value error popup in Mozilla Firefox.](/assets/images/docs-Troubleshooting/import-invalidvalue-firefox.png)

{: .tip }
As seen in the example screenshot above, it mentions that the value of `clockDisplay` was invalid, as it doesn't match any of the expected values. Change the value of the subkey in your JSON file to one of the allowed values.

### Unexpected keys: [keyName]
**Reason**: Extraneous keys or garbage data was found in the JSON file.  
**Solution**: Remove the extra keys from your JSON file, or export a new settings file.

![A screenshot of the unexpected keys error popup in Mozilla Firefox.](/assets/images/docs-Troubleshooting/import-unexpectedkeys-firefox.png)

### Missing subkeys: [subkeys]
**Reason**: Critical subkeys were missing in the JSON file.  
**Solution**: Ensure you are importing the correct JSON file. Export a new settings file if the current file is corrupted.

![A screenshot of the missing subkeys error popup in Mozilla Firefox.](/assets/images/docs-Troubleshooting/import-missing-firefox.png)

### Invalid settings file toast
**Reason**: The file you uploaded couldn't be decoded as valid JSON or didn't have a `.json` file extension.  
**Solution**: Check that the file you uploaded was a valid JSON file. Export a new settings file if the current file is corrupted.

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
