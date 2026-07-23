# Pure CSS 3D Flip Glassmorphism Popover

A production-grade, accessible **Pure CSS Animated Popover** component featuring a realistic **3D Flip animation** and a polished **macOS/iOS Glassmorphism visual style**.

> **Zero JavaScript Dependency**: Implemented purely using semantic HTML5 and modern CSS 3D transforms, custom properties, and backdrop-filter utilities.

---

## ✨ Features

* **3D Perspective Flip Motion**: Smooth 3D tilt-and-rotate entrance using GPU-accelerated CSS `rotateX`, `perspective`, `transform-origin`, `scale`, and `translateY`.
* **Apple/iOS Glassmorphism Aesthetic**: Multi-layered frosted glass effect utilizing `backdrop-filter: blur()`, translucency, ambient inner lighting highlights, and soft depth shadows.
* **100% Pure CSS Interaction**: Uses the accessible Checkbox Hack pattern for zero-JS toggle capability.
* **Open-by-Default State**: Page loads with popover open by default for effortless zero-click screenshot capture in PR reviews.
* **Fully Themeable via CSS Variables**: Every animation timing, transform angle, blur radius, glass tint, and shadow parameter is exposed as a CSS variable in `:root`.
* **Accessible & Screen-Reader Ready**: Accessible semantic structure, focus states (`:focus-visible`), and full `@media (prefers-reduced-motion)` support.
* **Responsive & Mobile Friendly**: Centers gracefully across desktop, tablet, and mobile screens without horizontal scrollbars.

---

## 📁 Folder Structure

```
submissions/examples/css-popover-3d-flip-glassmorphism/
├── demo.html        # Self-contained HTML markup & accessible popover card
├── style.css        # Modular CSS with variables, 3D flip motion & glassmorphism
├── README.md        # Technical documentation & customization guide
└── preview.png      # Real screenshot reference
```

---

## 🛠️ CSS Custom Properties (Variables)

All motion and visual parameters are exposed in `:root` for customization without editing component CSS:

| Variable | Default Value | Description |
| :--- | :--- | :--- |
| `--popover-duration` | `480ms` | Transition duration for opening and closing |
| `--popover-easing` | `cubic-bezier(0.16, 1, 0.3, 1)` | Apple/Framer-inspired spring ease-out curve |
| `--popover-perspective` | `1200px` | 3D Perspective viewing distance |
| `--popover-rotate` | `-22deg` | Initial 3D X-axis tilt angle when closed |
| `--popover-scale` | `0.92` | Initial scale factor when closed |
| `--popover-translate-y` | `14px` | Vertical offset displacement when closed |
| `--popover-transform-origin` | `top center` | Origin point for the 3D flip animation |
| `--popover-width` | `350px` | Popover card width |
| `--popover-radius` | `22px` | Border radius for popover card |
| `--popover-blur` | `24px` | Glassmorphism background backdrop blur radius |
| `--popover-bg` | `rgba(255, 255, 255, 0.65)` | Translucent glass surface background color |
| `--popover-border` | `1px solid rgba(255, 255, 255, 0.55)` | Specular glass highlight border |

---

## 🔍 How It Works

### 1. Pure CSS Interaction Mechanism (Checkbox Hack)
An invisible, accessible `<input type="checkbox" id="popover-toggle">` controls the open/closed state.
When combined with a matching `<label for="popover-toggle">`:
* Toggling the checkbox state modifies the sibling selector `.popover-checkbox:checked ~ .popover-card`.
* Having `checked` on the HTML element by default displays the popover immediately upon opening `demo.html`.

### 2. 3D Perspective & Motion Mechanics
The parent `.popover-wrapper` sets up `perspective: var(--popover-perspective)`.

* **Closed State**:
  ```css
  transform: rotateX(-22deg) translateY(14px) scale(0.92);
  opacity: 0;
  visibility: hidden;
  pointer-events: none;
  ```
* **Open State**:
  ```css
  transform: rotateX(0deg) translateY(0) scale(1);
  opacity: 1;
  visibility: visible;
  pointer-events: auto;
  ```

### 3. Glassmorphism Rendering & Fallback
Uses `backdrop-filter: blur(24px) saturate(180%)` paired with an inset specular border highlight `inset 0 1px 1px 0 rgba(255, 255, 255, 0.85)`. Browsers without `backdrop-filter` support gracefully degrade to a clean solid white backdrop via `@supports not (backdrop-filter: blur(1px))`.

---

## ♿ Accessibility Features

* **Keyboard Navigation**: Pressing `Space` or `Enter` on the focusable trigger button toggles the popover.
* **Visible Focus Styles**: Focus rings are rendered via `:focus-visible` with high-contrast outlines.
* **Screen Reader Friendly**: Uses ARIA roles (`role="button"`, `role="dialog"`, `aria-expanded`, `aria-controls`).
* **Reduced Motion**: Respects `@media (prefers-reduced-motion: reduce)` by bypassing 3D rotation and scaling transforms while retaining clean opacity fades.

---

## 🎨 Customization Examples

### Dark Glass Variant
```css
:root {
  --popover-bg: rgba(15, 23, 42, 0.75);
  --popover-border: 1px solid rgba(255, 255, 255, 0.15);
  --color-text-primary: #f8fafc;
  --color-text-secondary: #94a3b8;
}
```

### High-Elasticity Bouncy Motion
```css
:root {
  --popover-duration: 600ms;
  --popover-easing: cubic-bezier(0.34, 1.56, 0.64, 1);
  --popover-rotate: -35deg;
}
```

---

## 🌐 Browser Support

* **Chrome/Edge**: 76+
* **Safari**: 13+ (iOS & macOS)
* **Firefox**: 103+
* **Opera**: 63+

---

## 📜 License

Part of the **EaseMotion CSS** open-source animation library. Licensed under MIT.
