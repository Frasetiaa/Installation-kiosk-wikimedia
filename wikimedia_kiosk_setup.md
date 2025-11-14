# Wikimedia Kiosk Setup for Arch Linux + Hyprland

This document explains how to set up a fullscreen kiosk mode displaying Wikimedia on Arch Linux with Hyprland.

## Requirements
- Arch Linux
- Hyprland
- Chromium browser
- Optional: `unclutter` for hiding cursor

## Install Dependencies
```bash
sudo pacman -S chromium unclutter
```

## Launch Wikimedia in Kiosk Mode
Run this:
```bash
chromium --kiosk --start-fullscreen --incognito --noerrdialogs --disable-infobars https://www.wikimedia.org
```

## Hide Cursor (Optional)
```bash
unclutter --fork
```

## Autostart Kiosk in Hyprland
Edit your Hyprland config:
```
~/.config/hypr/hyprland.conf
```
Add the following lines:
```
exec = chromium --kiosk --start-fullscreen --incognito https://www.wikimedia.org
exec = unclutter --fork
```

## Disable Common Escape Key Combos
To prevent kiosk users from exiting the browser, block shortcuts:
```
bind = ALT, TAB, nop
bind = SUPER, Q, nop
bind = CTRL ALT, DEL, nop
bind = SUPER, RETURN, nop
```

## Alternative Wikimedia Projects
Replace the URL in the kiosk command with:
- **Wikibooks** → https://www.wikibooks.org
- **Wikiquote** → https://www.wikiquote.org
- **Wiktionary** → https://www.wiktionary.org
- **Wikiversity** → https://www.wikiversity.org
- **Wikimedia Commons** → https://commons.wikimedia.org

## Example Final Kiosk Command
```bash
chromium --kiosk --start-fullscreen --incognito --noerrdialogs --disable-infobars https://commons.wikimedia.org
```

## Notes
- Chromium cannot run as root without `--no-sandbox`. Do not run kiosk as root.
- Ensure your Hyprland config does not override fullscreen rules.

---
You can now upload this README to a GitHub repo as documentation.

