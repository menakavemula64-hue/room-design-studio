# Room Design Studio

A small, responsive interior-design preview built with HTML, CSS, and JavaScript.

**Live website:** [Open Room Design Studio](https://menakavemula64-hue.github.io/room-design-studio/)

## What it does

- Choose a room type to see a matching sample photo.
- Choose a visual style to apply a photo filter.
- Choose an accent color to tint the preview and its bottom stripe.
- Upload a room photo to preview it in your browser.
- Switch back to the sample room photo at any time.

## How the code works

All the page markup, CSS, and JavaScript currently live in `index.html`. The JavaScript listens for selections and updates the preview. For example:

```js
function updatePreview() {
  const room = document.querySelector(".option.selected").textContent.trim();
  const style = document.querySelector(".style-option.selected").textContent.trim();
  const selectedColor = document.querySelector(".swatch.selected").dataset.color;

  previewStyle.textContent = style + " " + room.toLowerCase();
  previewImage.style.setProperty(
    "--room-photo",
    `url("${uploadedPhotoUrl || roomImages[room]}")`
  );
  previewImage.style.setProperty("--style-filter", styleFilters[style]);
  previewImage.style.setProperty("--accent-color", selectedColor);
}
```

The selected room chooses a sample image. The selected style and color are passed to CSS as custom properties, which change the preview's appearance.

## Run it locally

Open `index.html` in a web browser. The sample photos are loaded from Unsplash, so an internet connection is needed for them.

## Current limitations

This is a front-end prototype: style choices apply visual filters and do not rearrange furniture or generate a new room. Uploaded photos are previewed locally and are not sent to a server or shared with other people. The save and create buttons currently show confirmation messages but do not store a design.
