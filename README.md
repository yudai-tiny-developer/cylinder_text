# Cylinder Text Animation

A browser-based 3D text animation that wraps customizable text around a cylinder. The app uses CSS 3D transforms and vanilla JavaScript, so no build step or server is required.

## Features

- Animated cylindrical text with customizable direction and speed
- Multiple text rows with independent, alternating rotation
- Adjustable font, weight, size, letter spacing, and row spacing
- Text and outline colors, background color, and outline width
- Optional top-and-bottom borders around all rows or each individual row, with customizable color and dotted, dashed, solid, or double styles
- Optional border rotation synchronized with the text
- Front/back tilt, side tilt, perspective, depth scaling, and opacity controls
- Optional text repetition and custom separators
- Optional mirrored/back-side text
- Pause/resume and reset-to-default controls
- Automatically restores the last-used settings on the next visit
- Undo and redo setting changes with Ctrl+Z and Ctrl+Y (or Ctrl+Shift+Z)
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

Settings are grouped into **Text appearance**, **Colors**, **Border**, **Cylinder layout**, and **Motion and display** sections.

| Setting | Description |
| --- | --- |
| Text | Text to display. Put each line on a separate row. |
| Separator | Text inserted between repeated units. |
| Font | Font family name or comma-separated font stack. |
| Weight | Font weight, from 100 to 900. |
| Outline width | Outline thickness; `0` disables the outline. |
| Text color | Fill color of each character. |
| Outline color | Stroke color used around characters. |
| Border color | Color of the border lines. |
| Background | Stage background color. |
| Border | Adds no border, top-and-bottom borders around all rows, or top-and-bottom borders around each row. |
| Border style | Sets the border to dotted, dashed, solid, or double. |
| Border width | Sets the border thickness from 0 to 24 pixels. |
| Border spacing | Sets the gap between the text and border from 0 to 48 pixels. |
| Border rotation | Chooses whether the border rotates with the text. |
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

Hold **Reset to defaults** for one second, then release while the pointer is still over the button to restore the original configuration. You can also hold Space or Enter while the button is focused. The button's progress indicator turns green when the reset is ready; releasing sooner or releasing the pointer outside the button cancels it.

Use **Ctrl+Z** to undo setting changes and **Ctrl+Y** or **Ctrl+Shift+Z** to redo them. Text fields keep the browser's native text-editing undo and redo.

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

After changing a setting, the selector returns to its placeholder. Returning all settings to the preset values selects it again. Presets remain on the current browser and origin. Clearing site data removes them. Preset names are limited to 40 characters. If browser storage is unavailable, the app reports that it cannot save the preset.

Use **Download JSON** to export the current settings to a JSON file, or **Import JSON** to load settings from a previously exported file.

Use **Download animated WebP** to export one full rotation as a seamlessly looping animated WebP. The export uses the current text, appearance, and rotation speed (the Pause setting does not affect export). It uses a steady 17 ms frame delay (about 59 fps) to avoid uneven playback timing, choosing the frame count that most closely matches the requested rotation speed. The output is cropped to the animation bounds with a small safety margin, scaled to up to twice the available scene dimensions, and capped at 1920 pixels on its longest side, with high-quality WebP encoding. Rotation speed must be non-zero, and exports longer than 25 seconds are not supported. This feature requires browser support for WebP canvas encoding.

## Privacy

The animation is rendered locally in the browser. Entered text and settings are not transmitted by the app. The last-used settings and saved presets are stored only in local browser storage.

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
