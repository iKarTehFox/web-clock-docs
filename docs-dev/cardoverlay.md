---
title: Card Overlay
layout: default
parent: Features (Development)
nav_order: 3
---
Coming Soon
{: .label .label-yellow}
# Card Overlay
{: .no_toc}
A card overlay is a customizable container that can be used to display any kind of information in a pop-up. It displays over all other elements on the page.

![An example of a card overlay titled "Overlay example" with Lorem ipsum placeholder text in the body](/assets/images/docs-Development/cardoverlay/cardoverlay.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## How it works
The card overlay function can take any content type of `HTMLElement` or `string`.

Its styling is all hardcoded—the function handles everything related to the sizing and positioning of the card. The theme is set to the currently chosen theme in the menu.

```ts
// Function to create an overlay card element
export function makeCardOverlay(title: string, content: HTMLElement | string): void {
    // Create container
    const container = document.createElement('div');
    container.dataset.overlay = 'card-overlay';
    container.dataset.bsTheme = menu.container.dataset.bsTheme;
    Object.assign(container.style, {
        position: 'fixed',
        top: '0',
        left: '0',
        width: '100%',
        height: '100%',
        backgroundColor: 'rgba(0, 0, 0, 0.5)',
        display: 'flex',
        justifyContent: 'center',
        alignItems: 'center',
        zIndex: '10',
        overflow: 'hidden'
    });

    // Create card
    const card = document.createElement('div');
    Object.assign(card.style, {
        width: 'clamp(300px, 80%, 600px)',
        maxHeight: '90vh',
        overflow: 'hidden',
        display: 'flex',
        flexDirection: 'column'
    });
    card.className = 'card';

    // Create card body
    const cardBody = document.createElement('div');
    Object.assign(cardBody.style, {
        overflowY: 'auto',
        overflowX: 'auto',
        flexGrow: '1',
        maxWidth: '100%',
        width: '100%',
        wordBreak: 'break-word',
        overflowWrap: 'anywhere',
        marginBottom: '0',
        marginTop: '0',
        paddingBottom: '0',
        paddingTop: '0',
        userSelect: 'text'
    });
    cardBody.className = 'card-body';

    // Create title
    const titleElement = document.createElement('h5');
    Object.assign(titleElement.style, {
        textAlign: 'center',
        fontSize: '1.5rem',
        position: 'sticky',
        top: '0',
        backgroundColor: 'var(--bs-card-bg)',
        padding: '1rem',
        borderBottom: '1px solid #dddddd',
        zIndex: '1'
    });
    titleElement.className = 'card-title';
    titleElement.textContent = title;

    // Create content container
    const contentContainer = document.createElement('div');
    contentContainer.className = 'd-flex justify-content-center align-items-center';

    if (typeof content === 'string') {
        contentContainer.textContent = content;
    } else {
        content.style.maxWidth = '100%';
        content.style.maxHeight = '80vh';
        content.style.objectFit = 'contain';
        contentContainer.appendChild(content);
    }

    // Create button container
    const buttonContainer = document.createElement('div');
    buttonContainer.className = 'mb-0 d-flex gap-2 justify-content-center';
    Object.assign(buttonContainer.style, {
        marginTop: '8px',
        position: 'sticky',
        bottom: '0',
        backgroundColor: 'var(--bs-body-bg)',
        padding: '1rem',
        borderTop: '1px solid #dddddd'
    });

    // Create close button
    const closeButton = document.createElement('button');
    closeButton.className = 'btn btn-secondary';
    closeButton.textContent = 'Close';

    // Create escape key handler
    function escapeHandler(e: KeyboardEvent) {
        if (e.key === 'Escape') {
            document.body.removeChild(container);
            document.removeEventListener('keydown', escapeHandler);
            logConsole(`Overlay card container with settings (${title}, ${content}) removed`, 'debug');
        }
    }

    closeButton.onclick = () => {
        document.body.removeChild(container);
        document.removeEventListener('keydown', escapeHandler);
        logConsole(`Overlay card container with settings (${title}, ${content}) removed`, 'debug');
    };

    // Create download button if content is downloadable media
    if (content instanceof HTMLCanvasElement || content instanceof HTMLImageElement || content instanceof HTMLVideoElement) {
        const downloadButton = document.createElement('button');
        downloadButton.className = 'btn btn-primary';
        downloadButton.textContent = 'Download';
        downloadButton.onclick = () => {
            const dlTime = luxon.DateTime.now().toFormat('X');
            const link = document.createElement('a');
            // Set filename based on content type
            const extension = content instanceof HTMLVideoElement ? '.mp4' : '.png';
            link.download = `${title}_${dlTime}${extension}`;
            
            // Get appropriate data URL based on content type
            link.href = content instanceof HTMLCanvasElement ? 
                content.toDataURL('image/png') : 
                content.src;
                
            link.click();
        };
        buttonContainer.appendChild(downloadButton);
    }

    // Append buttons
    buttonContainer.appendChild(closeButton);

    // Append elements
    cardBody.appendChild(titleElement);
    cardBody.appendChild(contentContainer);
    cardBody.appendChild(buttonContainer);
    card.appendChild(cardBody);
    container.appendChild(card);

    // Add to document
    document.body.appendChild(container);
    document.addEventListener('keydown', escapeHandler);

    logConsole(`Overlay card container created with settings: (${title}, ${content})`, 'debug');
}
```

## Parameters
### title (string)
The title of the overlay card. It will be displayed at the top of the card in a heading element.

### content (HTMLElement | string)
The content of the overlay card. HTMLElements are appended as-is, and strings will be set to the contentContainer's textContent.

## Media elements
The function accepts `HTMLImageElement`, `HTMLCanvasElement`, and `HTMLVideoElement` as media content. If passed one of these types, a download button will be added next to the close button.

![An example of a card overlay titled "Overlay example" with an image in the body and a download button at the bottom](/assets/images/docs-Development/cardoverlay/cardoverlay-img.png)

Images and other media will need to be included in the project's files, locally. External links to media will be blocked by the CSP (Content Security Policy) header.

## In-use examples
Currently, card overlays are used for QR code settings exports and debugging purposes.

![The card overlay titled with "QR Code" and has a QR code image in the body](/assets/images/docs-Development/cardoverlay/cardoverlay-qr.png)

{: .note }
The QR code contains the JSON data of the settings. While it can be generated at any time, at the moment, it can't be scanned within Online Web Clock to import settings.


