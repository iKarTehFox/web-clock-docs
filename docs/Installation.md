---
title: Installation
layout: default
parent: Docs
nav_order: 1
---
# Installation
{: .no_toc}
This page will guide you through the installation process. You may choose to manually build the website or download a pre-built version.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Prerequisites
- [Node.js](https://nodejs.org/)
- Git
- Basic CLI knowledge

## Downloading the website

### Cloning the repository (Method 1)
To start off, you'll first need to download (or "clone") the website's files.

1. Ensure you have Git installed on your PC
 - If you're on Ubuntu or Debian-based distros, you can install Git with the following command:  
 `sudo apt-get install git`
 - If you're on Windows, you can download Git from the [official website](https://git-scm.com/download/win)

2. Open the Terminal (or Command Prompt) and clone the repository and `cd` into it with this command:  
 `git clone https://github.com/iKarTehFox/web-clock.git && cd web-clock`

3. If you are using an IDE like VS Code, you can clone the repository using this URL: `https://github.com/iKarTehFox/web-clock.git`

4. Skip to [Building the website](#building-the-website-if-cloned)

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

If you are using Node.js, you can use `http-server` to serve the website.
1. Install `http-server` by running `npm install -g http-server`
2. Run `http-server -p 80 ./dist` to serve the website on port 80 (or whatever port you want)

    ![A screenshot of the http-server command running in a Terminal.](/assets/images/docs-Installation/http-server-example.png)

3. Open your browser and go to `http://127.0.0.1` to view the website.
 - Don't forget to include the port number `http://IP:PORT` if you're using a port other than 80.

    ![A screenshot of the website running in a browser.](/assets/images/docs-Installation/website-page.png)
