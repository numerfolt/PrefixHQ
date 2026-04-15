# PrefixHQ

![Linux](https://img.shields.io/badge/Platform-Linux-%23FCC624?logo=linux)
![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)
![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg?logo=gnu)
![Downloads](https://img.shields.io/github/downloads/Nastas95/PrefixHQ/total?logo=github&label=Downloads)

> A visual manager for Steam Proton/Wine prefixes on Linux.

Steam names your prefix folders after AppIDs — so instead of "Starfield" you get "1091500". PrefixHQ turns that pile of numbers into a proper library with cover art, game names, and a clear indication of which prefixes are still attached to an installed game and which are just taking up space

<img width="1005" height="754" alt="PrefixHQ screenshot" src="https://github.com/user-attachments/assets/fba0f681-3ec1-41e0-ab05-12d24eb94ec7" />

---

## Features

+ **Visual library** — cover art fetched from Steam and cached locally, so subsequent launches are instant

+ **Multi-library support** — parses `libraryfolders.vdf` to find all your Steam libraries automatically, including secondary drives and external SSDs. Cross-library matching works even when game files and prefix live in different locations

+ **Orphan detection** — green means the game is installed, red means the prefix is stale and can be cleaned up

+ **Works with native Steam, Flatpak, and Snap** out of the box

+ **Safe deletion** — confirmation dialogs before anything gets removed. Deleting a prefix is permanent (saves, configs, mods — all gone), so PrefixHQ makes sure you mean it

+ **Right-click menu** to copy the prefix ID, load custom cover art (from file, URL, or SteamGridDB), or manually override the install status

---

## Requirements

- Linux
- Python 3.8+ (If you run directly the .py file)
- `PyQt6 >= 6.4.0`, `requests >= 2.28.0`, `Markdown>=3.3.0`

---

## Installation

**Binary (recommended):** grab the latest release from the [Releases page](https://github.com/Nastas95/PrefixHQ/releases)

**From source:**
```bash
git clone https://github.com/Nastas95/PrefixHQ
cd PrefixHQ
pip install -r requirements.txt
python PrefixHQ.py
```

---

## How it works

On launch, PrefixHQ scans your Steam installations and reads `libraryfolders.vdf` to find every library. It then looks through `steamapps/compatdata/` and matches each AppID folder to a game name — first via local `.acf` manifest files, then via the Steam API as a fallback

The result is a card grid where each prefix shows the game name, cover art, and whether the game is currently installed

---

## Data storage

Everything lives in `~/.config/PrefixHQ/`:

- `prefix_db.json` — custom names, manual status overrides, API cache
- `cache/` — downloaded cover art

---

> **Warning:** deleting a prefix removes everything inside that Proton container — saves, configs, mods. Make sure it's actually orphaned before you delete it. When in doubt, back it up first

---

## Contributing

Bug reports and feature requests go in [Issues](https://github.com/Nastas95/PrefixHQ/issues)

---

*Developed with ❤️ and a little AI assistance for the Steam Deck and PC gaming community*

## License

GNU General Public License v3.0 — see [`LICENSE`](LICENSE)
