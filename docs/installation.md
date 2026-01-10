---
title: Installation Guide
layout: default
nav_order: 3
---
# Installation Guide
{: .no_toc}
This page will guide you through the installation process. You may choose to manually build the website or download a pre-built version.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Building requirements
- [Node.js](https://nodejs.org/)
- Git
- Basic CLI knowledge

{: .important }
Ensure you have **at least** Node.js installed on your system. Regardless of whether you choose to clone the repository or download a pre-built release, Node.js is required to serve the website locally.

## Downloading the website

### Cloning the repository (Method 1)
To start off, you'll first need to download (or "clone") Online Web Clock's source code.

1. Ensure you have Git installed on your PC
 - If you're on Ubuntu or a Debian-based distro, you can install Git with the following command:  
 `sudo apt install git -y`
 - If you're on Windows, you can download Git from the [official website](https://git-scm.com/download/win)

2. Open the Terminal (or Command Prompt) and clone the repository and `cd` into it with this command:  
 `git clone https://github.com/iKarTehFox/web-clock.git && cd web-clock`
 - If you are using an IDE like VS Code, you can clone the repository using this URL: `https://github.com/iKarTehFox/web-clock.git`

3. Skip to [Building the website](#building-the-website-if-cloned)

### Downloading a release (Method 2)
If you would rather download a pre-built version of the website, you can download the latest release from the [releases page](https://github.com/iKarTehFox/web-clock/releases)

1. In the releases page, find the latest release and decide whether you want to download the `.zip` or `.7z` file.
 - If you have 7-zip on your system, use the `.7z` file, else just download the `.zip` file.
 
    ![A screenshot of the v1.4.4 release in the GitHub Releases page. At the bottom, you have the option to download the archive with a .7z extension or .ZIP extension.](/assets/images/docs-Installation/releases-page.png)

2. Extract the archive and open the new folder.

3. Skip to [Serving the website](#serving-the-website)

## Building the website (if cloned)
If you cloned the repository, you'll need to build the website before you can run it.

To build the website, you'll first need to install the dependencies.

1. Run `npm install` to install the dependencies.
2. Run `npm run build:prod` to build the website for production.
 - If you want to build the website for development, run `npm run build:dev` instead.

## Serving the website
After you have downloaded or built the website, you can now serve it locally.

{: .important }
Ensure you have a tool to serve the website (e.g. Node.js `http-server`, Python `http.server`, etc.). Double-clicking the `index.html` file will **<span style="color: red;">NOT</span>** work!

With Node.js, you can use the `http-server` command to serve the website.
1. Install `http-server` globally by running `npm install -g http-server` (use `sudo` if necessary).
- **If you built from source**: Run `http-server -p 80 ./dist` to serve the built website in ./dist on port 80.
- **If you downloaded a release**: Run `http-server -p 80 ./` to serve the website in the current directory on port 80.

    ![A screenshot of the http-server command running in a Terminal.](/assets/images/docs-Installation/http-server-example.png)

2. Open your browser and go to `http://127.0.0.1` to view the website.
 - Don't forget to include the port number `http://IP:PORT` if you're using a port other than 80.

    ![A screenshot of the website running in a browser.](/assets/images/docs-Installation/website-page.png)
