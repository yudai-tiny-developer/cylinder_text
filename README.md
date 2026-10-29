# Cylinder Text Animation

A browser-based 3D text animation that wraps customizable text around a cylinder. The app uses CSS 3D transforms and vanilla JavaScript, so no build step or server is required.

## Features

- Animated cylindrical text with customizable direction and speed
- Multiple text rows with independent, alternating rotation
- Adjustable font, weight, size, letter spacing, and row spacing
- Text and outline colors, background color, and outline width
- Optional top-and-bottom borders around all rows or each individual row, with customizable color and all CSS border styles
- Optional border rotation synchronized with the text
- Front/back tilt, side tilt, perspective, depth scaling, and opacity controls
- Optional text repetition and custom separators
- Optional mirrored/back-side text
- Pause/resume and reset-to-default controls
- Named presets stored locally in the browser
- English/Japanese interface selection based on the browser language
- Installed-font discovery where the browser supports the Local Font Access API
- Responsive layout and dark-mode-aware styling

## Run the app

1. Clone or download this repository.
2. Open `index.html` in a current desktop browser.

You can also serve the files with any static web server. For example:

```sh
python -m http.server 8000
```

Then visit `http://localhost:8000`.

## Create a cylinder animation

Open **Settings** and adjust the controls:

Settings are grouped into **Text appearance**, **Border**, **Cylinder layout**, and **Motion and display** sections.

| Setting | Description |
| --- | --- |
| Text | Text to display. Put each line on a separate row. |
| Separator | Text inserted between repeated units. |
| Font | Font family name or comma-separated font stack. |
| Weight | Font weight, from 100 to 900. |
| Text color | Fill color of each character. |
| Outline color | Stroke color used around characters. |
| Outline width | Outline thickness; `0` disables the outline. |
| Border | Adds no border, top-and-bottom borders around all rows, or top-and-bottom borders around each row. |
| Border color | Color of the border lines. |
| Border style | Sets the border to dotted, dashed, solid, or double. |
| Border width | Sets the border thickness from 0 to 12 pixels. |
| Border rotation | Chooses whether the border rotates with the text. |
| Background | Stage background color. |
| Rotation speed | Rotation in degrees per second. Negative values reverse direction. |
| Tilt (front/back) | Tilts the cylinder toward or away from the viewer. |
| Tilt (side) | Tilts the cylinder horizontally. |
| Perspective | Perspective distance; lower values make depth effects stronger. |
| Shrink distant text | Reduces the size of characters on the far side. |
| Distant opacity | Minimum opacity for characters on the far side. |
| Radius | Cylinder radius in pixels. |
| Font size | Character font size in pixels. |
| Letter spacing | Spacing between characters in em units. |
| Row gap | Vertical distance between rows in multiples of font size. |
| Repeat | Repeats text and its separator until each row fills the circumference. |
| Alternate direction per row | Reverses rotation direction on alternating rows, including borders set to rotate with the text. |
| Show back side | Controls whether text remains visible on the back of the cylinder. |
| Pause | Stops and resumes animation. |

Use **Reset to defaults** to restore the original configuration.

## Fonts

The app includes suggested web fonts and accepts any valid CSS font family or font stack. It also loads a small set of Google Fonts for the supplied presets. When the app is opened without internet access, the animation still works with local or system fonts.

On supported browsers, **Load installed fonts** requests permission through the Local Font Access API and adds detected font names to the font suggestions. Installation and permission are managed entirely by the browser; the app does not upload font data.

When entering a font stack, quote names that contain spaces as required by CSS, for example:

```text
"Arial", "Hiragino Sans", sans-serif
```

## Presets

The preset selector saves named snapshots of the animation settings in browser `localStorage`:

1. Choose **Save**.
2. Enter a preset name.
3. Select a saved preset to restore it.
4. Use **Delete** to remove the selected preset.

Presets remain on the current browser and origin. Clearing site data removes them. Preset names are limited to 40 characters. If browser storage is unavailable, the app reports that it cannot save the preset.

## Privacy

The animation is rendered locally in the browser. Entered text and settings are not transmitted by the app. Saved presets are stored only in local browser storage.

A hosted copy may contact Google Fonts and the hosting provider to load application resources. Those network requests are subject to the privacy policies of those services and the host. For details about app data handling, see [Privacy Policy](./privacy-policy.html).

## Browser support

Use a current browser with CSS 3D transform support. The built-in fonts, presets, and core animation work without JavaScript frameworks or plugins. The following are capability-dependent:

- **Local Font Access:** Chromium browsers that expose `window.queryLocalFonts()`
- **Dark mode:** browsers that support `prefers-color-scheme`
- **Resize observation:** browsers that support `ResizeObserver`
- **Preset dialogs:** browsers that support the HTML dialog element

## Project structure

- [`index.html`](./index.html) — application markup, styles, settings, and animation logic
- [`privacy-policy.html`](./privacy-policy.html) — privacy information for the app
- [`LICENSE-MIT`](./LICENSE-MIT) — MIT license
- [`LICENSE-APACHE`](./LICENSE-APACHE) — Apache License 2.0

## Development

The project has no package manager, dependencies, build pipeline, or test suite. To make changes, edit `index.html` and refresh the browser.

## License

This project is available under the MIT License and Apache License 2.0. See the corresponding license files for details.
