# theme colors

An [omalauncher](https://github.com/SimonSchubert/omarchy-widgets) home-screen widget that edits the active Omarchy theme's colors on the phone.

![tile](preview.png)

## What it does

- **Tile.** Shows every color in the theme's `colors.toml`; an asterisk marks the ones changed from the theme's defaults. Tap a color to open the picker.
- **Theme palette.** Pick any of the theme's own original colors; the variable's default is marked.
- **Custom color.** A collapsible picker with:
  - four palettes: tonal, functional, tonality grid and harmonic;
  - hue, saturation and lightness sliders that update live while you drag;
  - HEX, RGB and HSL input;
  - 12 slots for saved colors (tap an empty one to save, a filled one to pick, hold to clear).
- **reset** restores the theme's original colors.
- **Languages.** English by default; Russian, Ukrainian and Belarusian from the ⚙ menu. Those three are AI translations, and the menu says so.

The new color shows on the tile at once and in the whole theme about 2–3 seconds later.

| theme palette | tonal | functional | tonality grid | harmonic |
|---|---|---|---|---|
| ![](screenshots/theme.png) | ![](screenshots/tonal.png) | ![](screenshots/func.png) | ![](screenshots/grid.png) | ![](screenshots/harm.png) |

## Install

Copy `widget.owl` to `~/.config/omalauncher/widgets/` (for example as `60-theme-colors.owl`). It shows up on the home screen within a second. Needed packages: `bash`, `coreutils`, `grep`, `sed`, `util-linux`; the tile offers to install any that are missing.

## How it changes the theme

- **Writing the color.** It changes one `key = "#rrggbb"` line in the theme's `colors.toml`, after checking the key and the value.
  - A stock theme is first copied to `~/.config/omarchy/themes`, so the stock files are never modified.
  - Before the first change, the original colors are saved as `colors.orig.toml` next to it; **reset** puts them back.
- **Re-applying the theme.** The launcher rebuilds a theme only when the `theme` name in `style.toml` changes. So the widget briefly switches `theme` to an identical temporary twin, `<theme>-reload`, then back, and removes the twin. Nothing flickers, and `style.toml` ends as it was.

## Authors

Made by [Svffer](https://github.com/Svffer) together with Claude Opus 5.5, Anthropic's AI model. Claude wrote the code and the translations; Svffer designed the widget, tested it on the phone and guided every change.

## License

[MIT](LICENSE)
