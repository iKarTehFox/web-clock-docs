---
title: Dev Console
layout: default
parent: Features (Development)
nav_order: 1
---
# Dev Console
{: .no_toc}
The Dev Console panel gives you a near-complete "terminal" interface to interact with the clock and its settings. This panel is only visible when the `debugMode` URL parameter is set to true.

{: .info}
When `debugMode` is set to true, debug logging will also be enabled. See [URL Parameters](/docs/url-params).

![A screenshot of the Dev Console panel Console tab.](/assets/images/docs-Development/devconsole/panelitem.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## Layout
![A screenshot of the Dev Console panel](/assets/images/docs-Development/devconsole/devconsole.png)
<br>
![A screenshot of the Dev Console panel Logs tab.](/assets/images/docs-Development/devconsole/devconsole-logs.png)

1. **Tab switcher**
  - This allows you to switch between the Console and Logs tabs.
  - Console tab: Lets you input commands to change settings manually
  - Logs tab: Displays debug logs from the browser DevTools console
  
2. **Command input/output**
  - Here is where you can type in commands. Their outputs will be displayed in the textarea above.
  - You can use the `help` command to see a list of available commands, and use your keyboard's up and down arrow keys to cycle through previously entered commands.

3. **Console log output**
  - This displays a live output of the debug logs that are sent to the browser DevTools console.

4. **Log level filters**
  - These button toggles let you filter which log levels are shown in the Logs tab.
  - By default, all log levels are enabled. You can toggle the following levels: <span style="color: #6C757D;">**Debug**</span>, <span style="color: #0DCAF0;">**Info**</span>, <span style="color: #FFC107;">**Warning**</span>, and <span style="color: #DC3545;">**Error**</span>.
