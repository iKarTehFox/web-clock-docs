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
There are three methods of uploading your settings, either by uploading a JSON file, scanning a QR code, pasting in the JSON manually.

![A screenshot of the import upload button and text field upload form.](/assets/images/docs-Features/importexport/import.png)

After uploading your settings, Online Web Clock will automatically verify and load all of your settings.  
For an insight into how the site encodes, decodes, and verifies JSON settings, refer to the [code in the GitHub repository](https://github.com/iKarTehFox/web-clock/blob/prod/src/importExport.ts).

{: .note }
For more info on scanning and generating QR codes, refer to [this section](#qr-codes).

### Built-in presets
The menu includes a few presets which you can import. They contain pre-configured settings for different themes and styles.

![A screenshot of the built-in presets buttons.](/assets/images/docs-Features/importexport/presets.png)

You can also type the number next to the respective preset name to import it. For instance, you can press the number "<kbd>1</kbd>" on any screen to import the "AMOLED Theme" preset.

{: .note }
As they are not automatically preloaded, you may need an internet connection to load a preset if you are not serving the site locally and the presets are not already cached.

### Export settings
You can export your currently selected settings to a JSON file by clicking the "Export" button, by copying the raw JSON data to your clipboard, or by generating a QR code.

![A screenshot of the exporting buttons.](/assets/images/docs-Features/importexport/export.png)

#### Base keys
Below is a table of the top-level keys in the settings JSON object:

| Key | Valid values | Description |
| --- | --- | --- |
| exportTimestamp | `string` | The timestamp of when the settings were exported |
| version | `10` | Hardcoded version number. Do not change. |

#### clockConfig key
Below is a table of the subkeys of the `clockConfig` object and their valid values.

| Subkey | Valid values | Description |
| --- | --- | --- |
| clockDisplay | `binary`, `octal`, `decimal`, `hexa`, `emoji`, `roman`, `words`, `unixmillis`, `unixsec`, `unixcountdown`, `se_valentines`, `se_christmas`, `se_newyears`, `ii_christmas`, `ii_weekend`, `ii_leapyear` | Clock display system |
| secondsVis | `sviD`, `sviN` | Whether to display the seconds |
| dateFormat | `D`, `DD`, `DDD`, `DDDD`, `MMMM d`, `MMM d`, `d MMMM`, `d MMM`, `MMMM yyyy`, `yyyy`, `\'Q\'q, yyyy`, `\'Day\' o \'of\' yyyy`, `\'Week\' W`, `\'Day\' o`, **unset** | Format token for the date |
| dateAlign | `dpoL`, `dpoC`, `dpoR` | Alignment of the date |
| borderMode | `btyD`, `btyR`, `btyB` | Type of border, such as bottom, box, or disabled |
| borderStyle | `solid`, `dashed`, `dotted`, `double` | Style of the border |
| timeBar | `tbarWeekday`, `tbarMonth`, `tbarDay`, `tbarHour`, `tbarSec`, `tbarNone` | Type of time bar display |
| customNote | \<String\> | Custom note text to display |
| customNoteAlign | `nalT`, `nalB` | Alignment of the custom note |

{: .info }
For more info on these settings, see [Date and Time](/docs/datetime).

#### fontConfig key
Below is a table of the subkeys of the `fontConfig` object and their valid values.

| Subkey | Valid values | Description |
| --- | --- | --- |
| fontFamily | **unset**, \<Font name\> | Font family to set |
| fontStyle | `fsR`, `fsI` | Font style (Normal or Italic) |
| fontWeight | `fweL`, `fweN`, `fweB` | Font weight (Light, Normal, or Bold) |
| fontSize | `6vw`, `8vw`, `10vw`, `12vw`, `14vw`, `18vw` | Font size |
| dropShadow | \<Integer from 0 to 10\> | Size of the drop shadow |
| strokeWidth | \<Integer from 1 to 5\> | Width of the stroke |
| strokeColor | **unset**, \<Hexadecimal color value\> | Color of the stroke |

{: .info }
For more info on these settings, see [Font Customization](/docs/fontcustomization).

#### colorTheme key
Below is a table of the subkeys of the `colorTheme` object and their valid values.

| Subkey | Valid values | Description |
| --- | --- | --- |
| colorMode | `fademode`, `solidmode`, `imgmode` | Color mode setting |
| solidColor | \<Hexadecimal color value\> | Background color for Solid mode |
| textColorMode | `tcovD`, `tvovO` | Whether text color override is enabled |
| textColorValue | \<Hexadecimal color value\> | Text color value |
| bgImage | **unset**, \<Image URI\> | Background image URI scheme |
| bgImageSize | **unset**, `auto`, `cover`, `stretch` | Background image sizing |
| bgImageBlur | **unset**, \<Integer from 0 to 10\> | Background image blur size |

{: .info }
For more info on these settings, see [Background Theme](/docs/backgroundtheme).

### QR Codes
Settings can be exported as a QR code, which can then be scanned from the [Import settings](#import-settings) section to import them back.

#### Exported QR code
![A Bootstrap modal with a QR code in its body.](/assets/images/docs-Features/importexport/export-qr.png)

#### Scanning a QR code
![A screenshot of the QR code scanner.](/assets/images/docs-Features/importexport/import-qr.png)

{: .warning }
QR codes have a maximum capacity of *3KB* of data. If your JSON export exceeds this limit—for example, if you have a background image set—the QR code cannot be generated.

### What isn't exported?
1. Time Zone
2. Time Refresh Method
3. Custom Font
4. Color Transition length
5. Weather widget settings (Use [URL Parameters](/docs/url-params#weather-widget-parameters) to set these automatically)
6. Display Options (Use [URL Parameters](/docs/url-params#url-parameter-list) to set these automatically)

**Why?** Not all settings are meant to be exported. For instance, the time zone is set automatically based on your system settings, and not all custom fonts are available on everyone's device.

For Display Options specifically, they are meant to be tailored to your own preferences and device requirements and are not designed to be exported as a result.

Additionally, you can't (and shouldn't) export your weather settings as they contain your API key and precise location, which should obviously be kept private!
