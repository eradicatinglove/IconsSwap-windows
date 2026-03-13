# IconSwap for Windows

> sys-icon companion app — generate custom Nintendo Switch game icons on your PC

---

## What is it?

IconSwap for Windows lets you create custom game icons for your Nintendo Switch HOME menu.  
It generates the `icon.jpg` and `icon174.jpg` files required by **sys-icon**, given any game Title ID and a source image.

---

## Features

- Generate `icon.jpg` (256×256) and `icon174.jpg` (174×174) for any Title ID
- **CROP mode** — centre-crops your image to a square (standard HOME menu themes)
- **SQUEEZE mode** — stretches full image to square (vertical NX themes)
- Live preview that shows exactly how your icon will look in each mode
- Optional `config.ini` generation to override game name, author, and version
- Drag & drop image support
- Supports JPG, PNG, BMP, TGA, WEBP, GIF, ICO, TIFF, PSD, AVIF, HEIC

---

## Requirements

- Nintendo Switch running **Atmosphere CFW**
- [sys-icon](https://github.com/exelix11/SwitchThemeInjector) installed and enabled
- Python 3.9+
- [Pillow](https://pypi.org/project/Pillow/) — `pip install Pillow`
- *(optional)* [tkinterdnd2](https://pypi.org/project/tkinterdnd2/) for drag & drop — `pip install tkinterdnd2`

---

## Installation

```bash
# 1. Clone the repo
git clone https://github.com/yourusername/iconswap-windows.git
cd iconswap-windows

# 2. Install dependencies
pip install Pillow

# 3. Run the app
python iconswap.py
```

> `tkinter` is included with Python on Windows — no extra install needed.

---

## Usage

| Step | Action |
|------|--------|
| 1 | Enter your game's 16-character **Title ID** (e.g. `0100A0A03ADE6000`) |
| 2 | Select a **source image** via Browse or drag & drop |
| 3 | Choose **CROP** or **SQUEEZE** — preview updates instantly |
| 4 | Set an **output folder** |
| 5 | *(optional)* Fill in **config.ini** fields to override name/author/version |
| 6 | Click **GENERATE ICONS** |
| 7 | Copy the output `<TitleID>` folder to `sdmc:/atmosphere/contents/` |

### Output structure

```
<output_folder>/
└── <titleid>/
    ├── icon.jpg        (256×256, max 100 KB)
    ├── icon174.jpg     (174×174, max 64 KB)
    └── config.ini      (only if name/author/version were filled in)
```

### CROP vs SQUEEZE

| Mode | Best for |
|------|----------|
| CROP | Square or landscape images — standard HOME menu themes |
| SQUEEZE | Tall 2:3 images (e.g. 600×900) — vertical NX themes |

---

## Building an EXE

To distribute as a standalone executable with no Python required:

```bash
pip install pyinstaller
pyinstaller --onefile --windowed --icon=app.ico --add-data "app.ico;." --name IconSwap iconswap.py
```

The finished `IconSwap.exe` will be in the `dist/` folder.  
If drag & drop doesn't work in the exe, add `--collect-all tkinterdnd2` to the build command.

---

## Optional image format support

| Format | Install |
|--------|---------|
| AVIF | `pip install pillow-avif-plugin` |
| HEIC | `pip install pillow-heif` |

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Icon didn't change after reboot | Check sys-icon is installed and enabled |
| Question mark instead of icon | Try a different image — JPEG may be malformed |
| Vertical icon looks squished | Correct — use SQUEEZE with a vertical NX theme |
| App won't start | Run `pip install Pillow` |
| Drag & drop not working | Run `pip install tkinterdnd2` |

---

## Credits

- Switch homebrew NRO original: [IconSwap](https://github.com/exelix11/SwitchThemeInjector)
- Windows companion by **eradicatinglove**
