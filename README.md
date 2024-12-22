# Document Background and Transparency Adjuster

This tool allows you to upload (or drag-and-drop) an image or PDF file, then modify the background, transparency, gamma, and other settings. It can convert images (or the first page of a PDF) to either grayscale or preserve original colors, optionally applying a binarization process, adjusting a white scale threshold, or controlling transparency.

## Features

- **Image/PDF Upload**
  - Supports JPG, PNG, or PDF (first page only).
  - File selection or drag-and-drop.
- **PDF Render DPI**
  - For PDF input only, you can specify a DPI (dots per inch) value from 72 to 600.
  - Preset buttons (72, 150, 300, 600) for quick selection.
  - Automatically re-renders the PDF at the specified resolution.
- **Binarization**
  - Optional black/white conversion based on a threshold slider (0–255).
  - If binarized, images become strictly black and white (with optional transparent background).
- **White Scale & Gamma Correction** (if not binarizing)
  - **White Scale (0–255)**: A linear pre-gamma adjustment to push off-white pixels closer to full white. cnew=min⁡(ct×255,255)c_{\text{new}} = \min\bigl(\tfrac{c}{t} \times 255, 255\bigr)cnew=min(tc×255,255) where ttt is the selected scale, and ccc is the grayscale value.
  - **Gamma Correction (0.1–3.0)**: Post-scaling gamma to brighten/darken midtones.
- **Background Options**
  - **Transparent**: For grayscale modes, black pixels are fully opaque and white is fully transparent.
  - **White**: Produces a fully opaque PNG with white or black/colored areas, no transparency channel.
- **Output Types**
  - **Grayscale**: Convert everything to grayscale (with optional transparency if background is transparent).
  - **Preserve Colors**: Keep original colors and only adjust transparency or produce a fully opaque white background.
- **Download Result**
  - After applying all settings, you can preview the final PNG and download it.

## Getting Started

1. **Clone or Download** this repository onto your local machine.

2. **Open `index.html`**

   - Double-click `index.html` (or open it in your browser via localhost, e.g., a simple HTTP server).

3. **Upload or Drag-and-Drop**

   - You’ll see an area to select a file (`.pdf`, `.jpg`, `.png`, etc.) or drag a file in.

4. **Adjust PDF DPI (if PDF)**

   - If you uploaded a PDF, a **PDF Render DPI** slider and preset buttons will appear just below the file upload section.
   - Adjust the DPI as needed. A higher DPI yields a higher resolution (bigger canvas) rendering.

5. **Pick Background, Enable or Disable Binarization**

   - **Background**: Choose `Transparent` or `White`.

   - Binarization

     : Check or uncheck 

     ```
     Enable Binarization
     ```

     .

     - If enabled, you’ll see the binarization threshold slider. White scale and gamma controls are hidden.

6. **Fine-Tune White Scale & Gamma**

   - If binarization is **off**, you’ll see the White Scale threshold (0–255) and Gamma slider.
   - Adjust them to push mid/lighter areas to white or correct midtones.

7. **Choose Output Type**

   - **Grayscale** or **Preserve Colors**.

8. **Preview & Download**

   - The preview updates automatically each time you adjust a slider or setting.
   - Click **Download Converted PNG** to save your result.

## Technical Notes

- Binarization

   overrides scaling/gamma.

  - Black = intensity 0, White = intensity 255 (based on threshold).

- No Alpha

   in White Background Mode:

  - If background is white, the final PNG is fully opaque (no alpha channel).

- **Canvas**: Uses the HTML `<canvas>` element to manipulate pixel data.

- **PDF.js**: For PDF rendering. Only the **first page** of a multi-page PDF is processed.

- **Drag-and-Drop** support is built into `document.addEventListener('dragover', ...)` and `document.addEventListener('drop', ...)`.

## Performance Considerations

- Image processing is done in pure JavaScript, iterating over each pixel. For very large images/PDFs (especially at high DPI), performance may be slow.
- For advanced vectorization or GPU acceleration, consider WebAssembly or WebGL approaches.

## License

This software is licensed under the **GNU General Public License v3.0**. See LICENSE for details.

## Acknowledgments

Authored by **Yuting Zhang**.

Enjoy customizing your document backgrounds with **Document Background and Transparency Adjuster**!
