# ASCII Studio

Turn any image into ASCII art, right in your browser. Then select a region of the result and replace its text or recolor it.

Everything runs locally in a single HTML file. It has no dependencies and no build step, and your images are never uploaded anywhere.

<!-- Add a screenshot: save it as docs/screenshot.png and uncomment the line below -->
<!-- ![ASCII Studio screenshot](docs/screenshot.png) -->

## Features

- **Drag-and-drop upload**: PNG, JPG, WebP and GIF are supported, at any aspect ratio.
- **Fine-grained controls**
  - Resolution: 40–240 columns
  - Contrast: 0.5–3.5×
  - Edge strength: adds `- / | \` outline characters, based on Sobel edge detection
- **8 character sets**: Dense (70 chars), Standard, Blocks `█▓▒░`, Braille `⠿⠷⠯`, Numbers, Letters, Hangul consonants, or your own custom set
- **5 color modes**: Black on white, full color (each character takes the color of its pixel), and green, amber or blue terminal
- **Editable output**: The result is directly editable, and you can insert symbols at the cursor from a character palette.
- **Selection editing**: Drag across part of the art to:
  - replace it with your own text, repeated to fill the selection (spaces and line breaks are kept)
  - give it a custom text color, or clear that color
- **Fill with text**
  - Repeat: every character is replaced with your text, in order.
  - Silhouette: only the dark areas are filled with your text.
- **Global colors**: Pick background and text colors, or swap them in one click.
- **Export**: Copy to the clipboard or save as a `.txt` file. Revert takes you back to the original conversion.
- **Apple-inspired UI**: Supports light and dark mode and adapts to smaller screens.

## How to Use

1. Drop an image onto the upload area, or click it to browse.
2. Adjust the resolution, contrast and edge strength, then choose a character set and color mode.
3. Click **Convert to ASCII**.
4. To edit the result, drag across part of the art and use the **Edit Selection** panel. You can also use **Fill with Text** to fill the whole image with a word.
5. Click **Copy** or **Save TXT** to export.

> **Tip:** Plain-text exports (copy and `.txt`) don't keep colors. To preserve colors, take a screenshot of the result.

## How It Works

1. The image is drawn onto a hidden `<canvas>`, scaled down to the chosen number of columns. The row count is adjusted for the aspect ratio of monospace characters.
2. Each pixel's brightness is computed as `0.299R + 0.587G + 0.114B`, after the contrast adjustment.
3. Brightness is mapped to a character from the selected set, from dark to light.
4. When edge strength is above 0, a Sobel filter finds strong gradients. Those pixels are drawn as `-`, `/`, `|` or `\`, depending on the edge direction.

## Tech

Vanilla HTML, CSS and JavaScript, in a single file with no frameworks and no external requests.
