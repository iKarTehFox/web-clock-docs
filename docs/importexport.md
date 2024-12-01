---
title: Import and Export
layout: default
parent: Features
nav_order: 8
---
# Import and Export
{: .no_toc }
The Import/Export section of the menu lets you import and export your current settings to a JSON file. You can also choose built-in presets to import.

![A screenshot of the import and export menu options.](/assets/images/docs-Features/importexport/importexport.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## Options
### Import settings
There are two methods of uploading your settings, either by uploading a JSON file or by pasting in the JSON manually.

![A screenshot of the import upload button and text field upload form.](/assets/images/docs-Features/importexport/import.png)

After uploading your settings, Online Web Clock will automatically verify and load all of your settings.  
For an insight into how the site encodes, decodes, and verifies your JSON exports, refer to the [code in the GitHub repository](https://github.com/iKarTehFox/web-clock/blob/prod/src/importExport.ts).

### Built-in presets
The menu includes a few presets which you can import. They contain pre-configured settings for different themes and styles.

![A screenshot of the built-in presets buttons.](/assets/images/docs-Features/importexport/presets.png)

{: .note }
As they are not automatically preloaded, you may need an internet connection to apply a preset if you are not serving the site locally and the presets are not already cached.

## Export settings
You can export your currently selected settings to a JSON file by clicking the "Export" button, or by copying the raw JSON data to your clipboard.

![A screenshot of the exporting buttons.](/assets/images/docs-Features/importexport/export.png)

### Base keys
Below is a table of the base keys of the JSON object:

| Key | Valid values | Description |
| --- | --- | --- |
| exportTimestamp | `string` | The timestamp of when the settings were exported |
| version | `7` | Hardcoded version number |

### clockConfig key
Below is a table of the subkeys of the `clockConfig` object and their valid values.

| Subkey | Valid values | Description |
| --- | --- | --- |
| clockMode | `cmo12`, `cmo24` | The clock mode (12 or 24-hour) |
| clockDisplay | `binary`, `octal`, `decimal`, `hexa`, `emoji`, `roman`, `words` | Clock display system |
| secondsVis | `sviD`, `sviN` | Whether to display the seconds |
| dateFormat | `D`, `DD`, `DDD`, `DDDD`, unset | Format token for the date |
| dateAlign | `dpoL`, `dpoC`, `dpoR` | Alignment of the date |
| borderMode | `btyD`, `btyR`, `btyB` | Type of border, such as bottom, box, or disabled |
| borderStyle | `solid`, `dashed`, `dotted`, `double` | Style of the border |
| secondsBarVis | unset, `sbaB`, `sbaN` | Whether to display the seconds bar |

{: .info }
For more info on these settings, see [Date and Time](/docs/datetime).

### fontConfig key
Below is a table of the subkeys of the `fontConfig` object and their valid values.

| Subkey | Valid values | Description |
| --- | --- | --- |
| fontFamily | unset, \<Font name\> | Font family to set |
| fontStyle | `fsR`, `fsI` | Font style (Normal or Italic) |
| fontWeight | `fweL`, `fweN`, `fweB` | Font weight (Light, Normal, or Bold) |
| fontSize | `6vw`, `8vw`, `10vw`, `12vw`, `14vw`, `18vw` | Font size |
| dropShadow | \<Integer from 0 to 10\> | Size of the drop shadow |
| strokeWidth | \<Integer from 1 to 5\> | Width of the stroke |
| strokeColor | unset, \<Hexadecimal color value\> | Color of the stroke |

{: .info }
For more info on these settings, see [Font Customization](/docs/fontcustomization).

### colorTheme key
Below is a table of the subkeys of the `colorTheme` object and their valid values.

| Subkey | Valid values | Description |
| --- | --- | --- |
| colorMode | `fademode`, `solidmode`, `imgmode` | Color mode setting |
| solidColor | \<Hexadecimal color value\> | Background color for Solid mode |
| textColorMode | `tcovD`, `tvovO` | Whether text color override is enabled |
| textColorValue | \<Hexadecimal color value\> | Text color value |
| bgImage | unset, \<Image URI\> | Background image URI scheme |
| bgImageSize | unset, `auto`, `cover`, `stretch` | Background image sizing |
| bgImageBlur | unset, \<Integer from 0 to 10\> | Background image blur size |

{: .info }
For more info on these settings, see [Background Theme](/docs/backgroundtheme).
