---
theme: 'default'
background: 'https://source.unsplash.com/collection/94734566/1920x1080'
class: 'text-center'
highlighter: shiki
lineNumbers: false
info: |
  ## What's New in the Web Platform?
  Presentation by Sandeep Ramgolam about the latest features in HTML, CSS, JavaScript, and the Web Platform.
drawings:
  persist: false
transition: slide-left
title: What's New in the Web Platform?
mdc: true
colorSchema: 'dark'
fonts:
  sans: 'Roboto'
  mono: 'Fira Code'
---

# What's New in the Web Platform?

Exciting updates in HTML, CSS, JavaScript, and more

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---

# Agenda

<Toc maxDepth="1"></Toc>

---

# Baseline: A New Web Interoperability Initiative

<v-clicks>

- Baseline is a cross-browser initiative to improve web interoperability
- Aims to provide a consistent set of modern web APIs across all browsers
- Helps developers build with confidence, knowing features work everywhere
- Includes APIs for:
  - Responsive design (e.g., Container Queries)
  - Performance optimization (e.g., `loading="lazy"`)
  - Advanced styling (e.g., `:is()` and `:where()` selectors)
- Supported by major browser vendors: Google, Microsoft, Mozilla, and Apple
- Reduces the need for polyfills and browser-specific code

</v-clicks>

<div v-click="7" class="mt-4">

Learn more: [web.dev/baseline](https://web.dev/baseline/)

</div>

---

# HTML Updates

<v-clicks>

- The `<dialog>` element for native modal dialogs
- `<model>` element for 3D content (experimental)
- Lazy loading with `loading="lazy"` attribute
- Native image lazy-loading
- `inputmode` attribute for better mobile keyboards

</v-clicks>

---

# Dialog Element Demo

```html
<dialog id="myDialog">
  <h2>Dialog Example</h2>
  <p>This is a native dialog element.</p>
  <button onclick="closeDialog()">Close</button>
</dialog>

<button onclick="showDialog()">Open Dialog</button>

<script>
  const dialog = document.getElementById('myDialog');

  function showDialog() {
    dialog.showModal();
  }

  function closeDialog() {
    dialog.close();
  }
</script>
```

---

# CSS Innovations

<v-clicks>

- Container Queries for responsive design
- CSS Grid and Subgrid
- CSS Nesting
- `:has()` selector for parent selection
- New color functions: `lch()`, `lab()`, and `color()`
- Scroll Snap for improved scrolling experiences
- View Transitions for smooth page transitions
- Scroll-driven Animations for scroll-based effects

</v-clicks>

---

# New CSS Color Functions

<v-clicks>

- CSS now supports more advanced color functions for better color management and accessibility

</v-clicks>

<v-click>

| Function | Description | Gamut | Alpha Support | Example |
|----------|-------------|-------|---------------|---------|
| `rgb()` / `rgba()` | Red, Green, Blue | sRGB | Yes | `rgb(255, 0, 0)` |
| `hsl()` / `hsla()` | Hue, Saturation, Lightness | sRGB | Yes | `hsl(0, 100%, 50%)` |
| `lch()` | Lightness, Chroma, Hue | Wide gamut | Yes | `lch(50% 130 20)` |
| `lab()` | Lightness, a (green-red), b (blue-yellow) | Wide gamut | Yes | `lab(50% 50 -20)` |
| `color()` | Color space and values | Various | Yes | `color(display-p3 1 0.5 0)` |

</v-click>

<v-clicks>

- `lch()` and `lab()`: Perceptually uniform color spaces
- `color()`: Supports various color spaces (e.g., display-p3, rec2020)
- Wide gamut colors allow for more vibrant and saturated colors
- Better for color interpolation and accessibility

</v-clicks>

---

# View Transitions Demo

```html
<div id="app">
  <h1>View Transitions Demo</h1>
  <button onclick="toggleView()">Toggle View</button>
  <div id="content"></div>
</div>

<style>
  ::view-transition-old(root),
  ::view-transition-new(root) {
    animation-duration: 0.5s;
  }
  
  @keyframes fade-in {
    from { opacity: 0; }
  }

  @keyframes fade-out {
    to { opacity: 0; }
  }

  ::view-transition-old(root) {
    animation: 0.5s fade-out;
  }

  ::view-transition-new(root) {
    animation: 0.5s fade-in;
  }
</style>

<script>
  let isViewA = true;
  const content = document.getElementById('content');

  function toggleView() {
    if (document.startViewTransition) {
      document.startViewTransition(() => {
        isViewA = !isViewA;
        updateView();
      });
    } else {
      isViewA = !isViewA;
      updateView();
    }
  }

  function updateView() {
    content.innerHTML = isViewA
      ? '<h2>View A</h2><p>This is the first view.</p>'
      : '<h2>View B</h2><p>This is the second view.</p>';
  }

  updateView();
</script>
```

---

# Scroll-driven Animations Demo

<ScrollDrivenAnimationDemo />

---

# JavaScript Enhancements

<v-clicks>

- Private class fields and methods
- Top-level await
- Optional chaining (`?.`)
- Nullish coalescing operator (`??`)
- Dynamic `import()`
- `Promise.allSettled()`
- Logical assignment operators (`??=`, `&&=`, `||=`)

</v-clicks>

---

# Web APIs and Platform Features

<v-clicks>

- Web Components v1 specification
- Intersection Observer API
- Web Animations API
- Web Share API
- Payment Request API
- WebAuthn for passwordless authentication
- WebAssembly for near-native performance

</v-clicks>

---

# Future of the Web Platform

<v-clicks>

- WebGPU for high-performance graphics
- Web Machine Learning (WebML)
- WebXR for augmented and virtual reality
- Web Bluetooth and Web USB for hardware integration
- Progressive Web Apps on desktop

</v-clicks>

---

# Popover Target Demo

```html
<button popovertarget="foo" popovertargetaction="show">
  Show a popover
</button>

<article popover="auto" id="foo">
  This is a popover article!
  <button popovertarget="foo" popovertargetaction="hide">Close</button>
</article>
```

---
layout: center
class: text-center
---

# Thank You!

[Documentation](https://developer.mozilla.org/en-US/) · [W3C](https://www.w3.org/) · [TC39](https://tc39.es/)

Presentation by Sandeep Ramgolam
