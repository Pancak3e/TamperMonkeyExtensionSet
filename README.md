Alldata New Tab — Tampermonkey Userscript
A lightweight Tampermonkey script that lets you automatically click a specific UI element on any webpage (using a CSS selector) and then open Alldata Repair in a new tab using a keyboard shortcut.

This was designed to speed up navigating into Alldata’s vehicle selection page during workflow-heavy automotive diagnostics or estimate building.

🚀 Features
✔️ Clicks a specific page element via CSS/JS path

✔️ Supports clicking normal elements + SVG icons

✔️ Opens a customizable URL in a new browser tab

✔️ Triggered by a keyboard shortcut (Ctrl + ⌘ + Z on Mac)

✔️ Works on any website (wide @match rule)

✔️ 100% client-side — no external libraries required

🎯 Why This Exists
When switching between systems like Tekmetric, AllData, and internal tools, it can be tedious to open Alldata’s vehicle lookup page by hand.

This script automates that:

Press Ctrl + ⌘ + Z

Script clicks the targeted menu item (via CSS selector)

Script opens:
https://my.alldata.com/repair/#/select-vehicle
in a new tab.

This creates a rapid workflow shortcut for shops and power-users.

⌨️ Keyboard Shortcut
Ctrl + ⌘ + Z
(you can modify inside the script)

🧠 How It Works
1. Element Clicking
The script finds an element using:

js
Copy code
document.querySelector(jsPath)
It checks whether the element is:

A regular clickable HTML element

An SVG icon (requires synthetic events)

Or non-clickable (logs an error)

2. SVG Click Simulation
SVG elements don’t always respond to .click(), so the script dispatches a custom MouseEvent.

3. New Tab Navigation
The script opens the target URL using:

js
Copy code
window.open(url, '_blank');
🛠️ Installation
Install Tampermonkey

Chrome: https://www.tampermonkey.net

Firefox, Edge, Safari also supported

Click Create a new script

Paste in the script from this repository.

Save and enable the script.

🧩 Customization
🔹 Customizing the Keyboard Shortcut
Modify this block:

js
Copy code
if (event.ctrlKey && event.metaKey && event.key === 'z') {
Examples:

Ctrl + Alt + Z → event.altKey

Shift + Z → event.shiftKey

🔹 Changing the Click Target
Edit the CSS selector inside:

js
Copy code
clickElementByJSPath('YOUR_SELECTOR_HERE');
🔹 Changing the URL to Open
Edit:

js
Copy code
openInNewTab('https://my.alldata.com/repair/#/select-vehicle');
Replace with any URL you want.

🧪 Notes / Limitations
The script runs on all pages (*://*/*) by design.

Some websites block scripts from opening tabs unless triggered by direct user input.

If your browser blocks popups, allow popups for the site.

📜 License
MIT — free to modify and use commercially.
