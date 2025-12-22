---
title: Troubleshooting
layout: default
nav_order: 6
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

![A screenshot of the invalid version error popup.](/assets/images/docs-Troubleshooting/import-version.png)

{: .tip }
There is a possibility that you can manually edit your JSON settings file to fix this error. If you'd like to take your chances, refer to the [Import and Export](/docs/importexport#base-keys) page regarding this. Otherwise, share your old settings file in the dedicated [GitHub issue](https://github.com/iKarTehFox/web-clock/issues/53).

### Invalid value of [key]: [value]
**Reason**: A subkey was found with an invalid or disallowed value.  
**Solution**: Review the error to fix your settings file, or export a new settings file.

![A screenshot of the general invalid value error popup.](/assets/images/docs-Troubleshooting/import-invalidvalue.png)

{: .tip }
As seen in the example screenshot above, it mentions that the value of `clockDisplay` was invalid, as it doesn't match any of the expected values. Change the value of the subkey in your JSON file to one of the allowed values.

### Unexpected keys: [keyName]
**Reason**: Extraneous keys or garbage data was found in the JSON file.  
**Solution**: Remove the extra keys from your JSON file, or export a new settings file.

![A screenshot of the unexpected keys error popup.](/assets/images/docs-Troubleshooting/import-unexpectedkeys.png)

### Missing subkeys: [subkeys]
**Reason**: Critical subkeys were missing in the JSON file.  
**Solution**: Ensure you are importing the correct JSON file. Export a new settings file if the current file is corrupted.

![A screenshot of the missing subkeys error popup.](/assets/images/docs-Troubleshooting/import-missing.png)

### Incompatible values of [subkeys]: [key1] and [key2]
**Reason**: The values of two or more subkeys conflict with each other in a way that is not possible with the regular menu options.  
**Solution**: Review the error to fix your settings file, or export a new settings file

![A screenshot of the incompatible values error popup.](/assets/images/docs-Troubleshooting/import-incompatible.png)

{: .tip }
In the example above, it mentions that `borderMode` and `timeBar` are both enabled with the values `btyB` and `tbarSec` respectively. As only one or the other can be enabled at a time normally, you'd need to change one of the values in your JSON file to disable it (for example, setting `borderMode` to `btyD`).

### Invalid settings file toast
**Reason**: The data you imported couldn't be decoded as valid JSON or didn't have a `.json` file extension.  
**Solution**: Check that the data you uploaded was actual JSON. Export a new settings file if the current file is corrupted.

![A screenshot of the invalid settings file toast error popup.](/assets/images/docs-Troubleshooting/import-invalidfile.png)

<hr>

## Network problems
Online Web Clock is designed to work completely offline, however, it may display an error for certain actions which require an internet connection.

### Weather widget
In order to enable the weather widget, you need an active internet connection. If the connection to the OpenWeatherMap API fails, the weather widget will not be enabled and an error **will not** be displayed. This behavior may be changed in the future.

Additionally, the widget will be hidden and disabled if connection is lost in between automatic refreshes.

### Built-in presets
When importing a built-in preset, an internet connection is required to fetch the preset JSON file from the site. If you are not self-hosting the site or you lose connection and the preset is not already cached, the preset will fail to load and an error will be shown.

This error also occurs if the preset filename simply doesn't exist, i.e you typed its name incorrectly in the `preset` URL parameter.

![A screenshot of the preset load error toast.](/assets/images/docs-Troubleshooting/import-couldnotfetch.png)
