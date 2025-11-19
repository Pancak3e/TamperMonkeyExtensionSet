Alldata New Tab — Tampermonkey Userscript

A lightweight Tampermonkey script that automatically clicks a specific UI element on any webpage (using a CSS selector) and opens Alldata Repair in a new tab using a keyboard shortcut.

This is designed to speed up navigating into Alldata’s vehicle selection page during workflow-heavy automotive diagnostics or estimate building.

------------------------------------------------------------
FEATURES
------------------------------------------------------------
- Clicks a specific page element using a CSS/JS selector
- Supports clicking normal elements and SVG icons
- Opens a customizable URL in a new browser tab
- Triggered by a keyboard shortcut (Ctrl + Command + Z on Mac)
- Works on any website (*://*/*)
- No external libraries required (pure client-side script)

------------------------------------------------------------
WHY THIS EXISTS
------------------------------------------------------------
Switching between systems like Tekmetric, AllData, and internal tools can be slow. Opening Alldata’s vehicle lookup page repeatedly is inconvenient.

This script automates the process:

1. Press Ctrl + Command + Z
2. The script clicks the targeted element (via CSS selector)
3. The script opens the following URL in a new tab:

https://my.alldata.com/repair/#/select-vehicle

This creates a fast workflow shortcut for shops and power users.

------------------------------------------------------------
KEYBOARD SHORTCUT
------------------------------------------------------------
Ctrl + Command + Z
(Shortcut can be modified inside the script)

------------------------------------------------------------
HOW IT WORKS
------------------------------------------------------------
1. Element Clicking
   The script finds an element using:
   document.querySelector(jsPath)

   It checks:
   - If the element is a normal clickable HTML element
   - If the element is an SVG (requires synthetic click)
   - If the element is non-clickable (logs an error)

2. SVG Click Simulation
   Since SVG elements don't always respond to .click(),
   a synthetic MouseEvent is dispatched.

3. New Tab Navigation
   The URL is opened using:
   window.open(url, "_blank")

------------------------------------------------------------
INSTALLATION
------------------------------------------------------------
1. Install Tampermonkey:
   https://www.tampermonkey.net

2. In Tampermonkey, click “Create a new script.”

3. Paste in the script from this repository.

4. Save and enable the script.

------------------------------------------------------------
CUSTOMIZATION
------------------------------------------------------------

• Changing the Keyboard Shortcut:
  Modify this section:
  if (event.ctrlKey && event.metaKey && event.key === 'z')

  Examples:
  - Ctrl + Alt + Z → add event.altKey
  - Shift + Z → add event.shiftKey

• Changing the Click Target:
  Edit this selector:
  clickElementByJSPath("YOUR_SELECTOR_HERE");

• Changing the URL to Open:
  Update this line:
  openInNewTab("https://my.alldata.com/repair/#/select-vehicle");

------------------------------------------------------------
NOTES AND LIMITATIONS
------------------------------------------------------------
- Script runs on all pages (*://*/*) intentionally.
- Some websites block new tabs unless triggered by direct user action.
- If the browser blocks the popup, allow popups for the website.

------------------------------------------------------------
LICENSE
------------------------------------------------------------
MIT License. Free to use, modify, and distribute.
