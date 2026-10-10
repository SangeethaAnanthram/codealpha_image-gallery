# Image Gallery

A responsive image gallery built with plain HTML, CSS, and JavaScript. No frameworks or build tools required.

## Features

- **Responsive grid** that adapts from desktop to mobile (CSS Grid, with wide and tall tiles)
- **Hover effects**: image zoom, dimming, and a caption that slides up
- **Lightbox viewer** with next/previous buttons, close button, image counter, and caption
- **Navigation**: mouse, keyboard (`←` `→` `Esc`), touch swipe, and click-outside-to-close
- **Category filters** with fade transitions; the lightbox only cycles through the filtered images
- **Smooth transitions** throughout, including image cross-fade in the lightbox and preloading of neighbouring images
- **Accessibility**: visible focus outlines, ARIA labels, focus returns to the clicked image on close, and reduced-motion support

## Getting Started

1. Download `gallery.html`.
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge).

The demo uses placeholder photos from [picsum.photos](https://picsum.photos) and a Google Font, so an internet connection is needed for them to load.

## Project Structure

```
gallery.html   # HTML, CSS, and JavaScript in one file
README.md
```

## Using Your Own Images

1. Put your images in an `images/` folder next to `gallery.html`.
2. In the `<script>` section, edit the `photos` array. Each entry needs a `title` and a `cat` (category).
3. Replace the generated `thumb` and `full` URLs with your own paths:

```js
const photos = [
  { title: "Mountain lake", cat: "Nature", thumb: "images/lake-small.jpg", full: "images/lake.jpg" },
  { title: "City at night", cat: "City",   thumb: "images/city-small.jpg", full: "images/city.jpg" }
];
```

Filter buttons are created automatically from the unique `cat` values. You can use the same file for `thumb` and `full` if you don't have separate sizes.

## Customization

| What | Where |
|------|-------|
| Colors | CSS variables in `:root` (`--bg`, `--ink`, `--accent`) |
| Grid column width | `minmax(240px, 1fr)` in `.grid` |
| Row height | `grid-auto-rows` in `.grid` |
| Wide / tall tiles | the `size` rule in the `photos` map (or remove it for a uniform grid) |
| Animation speed | `--ease` and the `transition` values |

## How It Works

- **Filtering:** each tile has a `data-cat` attribute. Selecting a category fades tiles out, hides non-matching ones, then fades the rest back in. A `visible` array tracks which photos are currently shown.
- **Lightbox:** `show(position)` swaps the image, caption, and counter, wrapping around at both ends. It uses the `visible` array, so navigation respects the active filter.
- **Responsiveness:** `auto-fill` columns handle most screen sizes, and a media query at 560px switches to a two-column layout with always-visible captions.

## Browser Support

Any modern browser with CSS Grid and `:focus-visible` support (all current versions of Chrome, Firefox, Safari, and Edge).

## Possible Extensions

- Search box to filter by title
- Image zoom or pan inside the lightbox
- Slideshow mode with autoplay
- Loading photos from an API or JSON file

## License

Free to use and modify for personal and educational projects.
