# IconSwap for Windows

> sys-icon companion app — generate custom Nintendo Switch game icons on your PC

---

## What is it?

IconSwap for Windows lets you create custom game icons for your Nintendo Switch HOME menu.  
It generates the `icon.jpg` and `icon174.jpg` files required by **sys-icon**, given any game Title ID and a source image.

---

## Features

- Search any Nintendo Switch game by name and auto-fill its Title ID
- Shows regional variants with different Title IDs (e.g. `[JP]`, `[US]`, `[EU]`)
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

---

## Download

Head to the [Releases](../../releases) page and download the latest `IconSwap.exe`.  
Place it in its own folder before running.

---

## Usage

| Step | Action |
|------|--------|
| 1 | **Search** for your game by name — click a result to auto-fill the Title ID |
| 2 | Or type/paste a Title ID manually into the **TITLE ID** field |
| 3 | Select a **source image** via Browse or drag & drop |
| 4 | Choose **CROP** or **SQUEEZE** — preview updates instantly |
| 5 | Set an **output folder** |
| 6 | *(optional)* Fill in **config.ini** fields to override name/author/version |
| 7 | Click **GENERATE ICONS** |
| 8 | Copy the output `<TitleID>` folder to `sdmc:/atmosphere/contents/` |

### Game Search

On first search the app downloads the Nintendo Switch title database and saves it as `titledb_cache.json` next to the exe — **one time only**. Every search after that is instant and works offline.

If a game has different Title IDs across regions, each variant is shown separately:
```
Zelda: Breath of the Wild  [US]
Zelda: Breath of the Wild  [JP]
```
Most games have the same Title ID worldwide and will only show one result.

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
| Search returns no results | Delete `titledb_cache.json` and search again to rebuild |
| Search fails / no internet | Use manual Title ID entry — search requires internet on first use |

---

## Credits

- Title database: [blawar/titledb](https://github.com/blawar/titledb)
- Switch homebrew NRO original: [IconSwap](https://github.com/exelix11/SwitchThemeInjector)
- Windows companion by **eradicatinglove**
