# CSS Overlap Image Grid

## What does this do?
The CSS Overlap Image Grid component creates an intentional, multi-layered image layout using pure CSS Grid tracks, dynamic `z-index` layering, custom depth variables, and smooth keyboard-accessible focus elevation.

## How is it used?
Wrap `<article class="overlap-card">` elements within an `<div class="overlap-grid">` container, defining the grid column/row spans and z-index layer elevation with inline CSS variables or utility classes:

```html
<div class="overlap-grid overlap-grid--hero">
  <!-- Card 1: Background Layer -->
  <article class="overlap-card" style="--layer: 1; --span-col: 1 / 7; --span-row: 1 / 7;">
    <a href="#link" class="overlap-card__link" aria-label="View photo details">
      <figure class="overlap-card__figure">
        <img src="path/to/image.jpg" alt="Descriptive alt text" class="overlap-card__img">
        <figcaption class="overlap-card__caption">
          <span class="caption-tag">Category</span>
          <span class="caption-title">Image Title</span>
        </figcaption>
      </figure>
    </a>
  </article>

  <!-- Card 2: Foreground Layer -->
  <article class="overlap-card" style="--layer: 4; --span-col: 4 / 10; --span-row: 2 / 8;">
    <a href="#link" class="overlap-card__link" aria-label="View photo details">
      <figure class="overlap-card__figure">
        <img src="path/to/image2.jpg" alt="Descriptive alt text" class="overlap-card__img">
        <figcaption class="overlap-card__caption">
          <span class="caption-tag">Featured</span>
          <span class="caption-title">Hero Title</span>
        </figcaption>
      </figure>
    </a>
  </article>
</div>
```

## Why is it useful?
In modern editorial web design, overlapping image layouts create rich visual hierarchy and depth. Traditional implementations often rely on absolute positioning or complex JavaScript libraries, which break responsiveness or hinder accessibility. This component leverages modern CSS Grid overlapping tracks and custom property `z-index` management to deliver a responsive, zero-JavaScript, fully keyboard-accessible image collage that fits seamlessly into EaseMotion CSS's zero-dependency philosophy.
