# alumna-css
Alumna CSS is a micro-library for rapid and responsive front-end interface development.

## Index

- [Install and Quick Start](#install-and-quick-start)
- [Stack](#stack)
- [Cluster](#cluster)
- [Overlay](#overlay)
- [Table wrap](#table-wrap)
- [App shell](#app-shell)
- [Changelog](#changelog)

## Install and Quick Start

### Step 1

1. Create a `CSS` folder inside your project.
2. Download [Alumna CSS](https://raw.githubusercontent.com/alumna/alumna-css/master/alumna.min.css) and place it in the `CSS` folder.
3. Create a new file `design.css` inside the `CSS` folder.
4. Include these files in your HTML project:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Your Incredible Website</title>
  <link rel="stylesheet" href="css/alumna.min.css">
  <link rel="stylesheet" href="css/design.css">
</head>
<body>
  
</body>
</html>
```

### Step 2 - Basic Section (No Box)

 1. Create a `<div class="section">` to act as a horizontal row of columns.
 2. Add columns inside it using classes like `col-1-3` for one-third width:

```html
<div class="section">
    
  <div class="col col-1-3">
    <!-- First column of three -->
  </div>

  <div class="col col-1-3">
    <!-- Second column of three -->
  </div>

  <div class="col col-1-3">
    <!-- Third column of three -->
  </div>

</div>
```

### Optional - Using `.box` or `.hero-box` with Sections

 1. Add the `box` class to a section for a constrained width (91.5rem) with responsive padding.
 2. Use `hero-box` instead for a constrained width without padding (e.g., for full-width hero sections):

```html
<div class="section box">
    
  <div class="col col-1-3">
    <!-- First column of three -->
  </div>

  <div class="col col-1-3">
    <!-- Second column of three -->
  </div>

  <div class="col col-1-3">
    <!-- Third column of three -->
  </div>

</div>
```

### Optional - Adding gaps between columns with `--gap`

 1. Every `.section` and `.sub-section` starts with `--gap: 0rem`.
 2. Override it per section to add space between columns without breaking the proportions. The grid automatically subtracts the gap from each column width.

```html
<div class="section box" style="--gap:2rem">
    
  <div class="col col-1-3">
    <!-- First column -->
  </div>

  <div class="col col-1-3">
    <!-- Second column -->
  </div>

  <div class="col col-1-3">
    <!-- Third column -->
  </div>

</div>
```

 3. Use any valid CSS length (rem is recommended). Gaps are local to the section, so other sections keep their own value:

```html
<!-- no gap -->
<div class="section">...</div>

<!-- 1rem gap only here -->
<div class="section" style="--gap:1rem">...</div>
```

 4. Works the same for nested grids:

```html
<div class="col col-1-2 sub-section" style="--gap:.75rem">
  <div class="col col-1-2">...</div>
  <div class="col col-1-2">...</div>
</div>
```

### Optional - Sub-Columns with `.sub-section`

 1. Add the `sub-section` class to a column to create sub-columns directly inside it, simplifying your HTML by reducing nesting:

```html
<div class="section">
    
  <div class="col col-1-3 sub-section">
    <div class="col col-1-2">
      <!-- First sub-column -->  
    </div>

    <div class="col col-1-2">
      <!-- Second sub-column -->  
    </div>
  </div>

  <div class="col col-1-3">
    <!-- Second column of three -->
  </div>

  <div class="col col-1-3">
    <!-- Third column of three -->
  </div>

</div>
```

The classes below are layout only. Put colors and type in `design.css`.

## Stack

`.stack` is a vertical flex column. The gap is `--stack-gap` (`1rem` on `:root`). Nested stacks inherit that gap until you set a new value.

```html
<div class="stack">
  <label for="email">Email</label>
  <input id="email" type="email" name="email">
</div>
```

A form is a stack of fields. Tighten the gap inside each field.

```html
<form class="stack">
  <div class="stack" style="--stack-gap: 0.5rem">
    <label for="field-email">Email</label>
    <input id="field-email" type="email" name="email">
  </div>
  <div class="stack" style="--stack-gap: 0.5rem">
    <label for="field-name">Name</label>
    <input id="field-name" type="text" name="name">
  </div>
  <button type="submit">Save</button>
</form>
```

## Cluster

`.cluster` is a wrapping row of items that keep their own width. The gap is `--cluster-gap` (`0.5rem` on `:root`).

`.section` is the page grid. It uses `--gap`. Children with `col-*` become full width at `40rem` and below. `.cluster` children do not. Do not put `col-*` on cluster children.

```html
<div class="cluster">
  <button type="button">Save</button>
  <button type="button">Cancel</button>
</div>
```

A grid column can hold a cluster. The columns follow the section. The buttons stay a row.

```html
<div class="section">
  <div class="col col-2-3">
    <p>Article text.</p>
  </div>
  <div class="col col-1-3">
    <div class="cluster" style="--cluster-gap: 0.75rem">
      <button type="button">Edit</button>
      <button type="button">Share</button>
      <button type="button">More</button>
    </div>
  </div>
</div>
```

## Overlay

`.overlay` covers the viewport: `position: fixed`, `inset: 0`, `z-index: 50`. It does not paint a background. Add that in `design.css`. Native `<dialog>` already has `::backdrop`. Skip `.overlay` there.

```html
<button class="overlay" type="button" aria-label="Dismiss"></button>
```

The overlay sits on top of the page. Clicking it should hide it. You will not see the layer until you paint a background.

```html
<div class="stack">
  <p>Page content.</p>
  <button type="button" id="open-layer">Open layer</button>
</div>
<button class="overlay" type="button" aria-label="Dismiss" id="layer" hidden></button>
<script>
  document.getElementById("open-layer").onclick = function () {
    document.getElementById("layer").hidden = false;
  };
  document.getElementById("layer").onclick = function () {
    this.hidden = true;
  };
</script>
```

## Table wrap

`.table-wrap` is full width with `overflow-x: auto`. Put a real `<table>` inside. It does not style cells.

```html
<div class="table-wrap">
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Role</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Ada</td>
        <td>Engineer</td>
      </tr>
    </tbody>
  </table>
</div>
```

A heading and a cluster can sit above the wrap. Wide rows scroll inside the wrap, not the page.

```html
<div class="stack">
  <div class="cluster">
    <span>Invoices</span>
    <button type="button">Export</button>
  </div>
  <div class="table-wrap">
    <table>
      <thead>
        <tr>
          <th>Invoice</th>
          <th>Status</th>
          <th>Method</th>
          <th>Amount</th>
          <th>Issued</th>
          <th>Due</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>INV-001</td>
          <td>Paid</td>
          <td>Card</td>
          <td>250.00</td>
          <td>2026-01-12</td>
          <td>2026-01-26</td>
        </tr>
        <tr>
          <td>INV-002</td>
          <td>Due</td>
          <td>Transfer</td>
          <td>150.00</td>
          <td>2026-02-03</td>
          <td>2026-02-17</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>
```

## App shell

`.shell` is a viewport-tall row: `.sidebar` plus `.shell-main`. The main column is a `.topbar` over `.shell-body`.

In that frame the bar does not need `position: sticky`: it sits above `.shell-body`, which is the scroller. When the bar lives **inside** a scrolling column, add `data-pin`:

```html
<header class="topbar" data-pin>
  <span>Inbox</span>
</header>
```

Without `data-pin`, the same markup scrolls away with the column.

```html
<div class="shell" id="app">
  <button class="shell-backdrop" type="button" aria-label="Close menu"></button>
  <aside class="sidebar" id="app-sidebar">
    <div class="sidebar-header">
      <a class="sidebar-link" href="/">
        <svg width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><circle cx="8" cy="8" r="6" fill="currentColor"></circle></svg>
        <span>Acme</span>
      </a>
    </div>
    <div class="sidebar-content">
      <nav class="sidebar-menu" aria-label="Main">
        <a class="sidebar-link" href="/">
          <svg width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><circle cx="8" cy="8" r="6" fill="currentColor"></circle></svg>
          <span>Inbox</span>
        </a>
        <a class="sidebar-link" href="/settings">
          <svg width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><circle cx="8" cy="8" r="6" fill="currentColor"></circle></svg>
          <span>Settings</span>
        </a>
      </nav>
    </div>
    <div class="sidebar-footer">
      <a class="sidebar-link" href="/account">
        <svg width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><circle cx="8" cy="8" r="6" fill="currentColor"></circle></svg>
        <span>Account</span>
      </a>
    </div>
  </aside>
  <div class="shell-main">
    <header class="topbar">
      <button class="shell-fold" type="button">Fold</button>
      <button class="shell-menu" type="button" aria-controls="app-sidebar">Menu</button>
    </header>
    <div class="shell-body">
      <p>Main content.</p>
    </div>
  </div>
</div>
<script>
  var app = document.getElementById("app");
  document.querySelector("#app .shell-menu").onclick = function () {
    app.setAttribute("data-open", "");
  };
  document.querySelector("#app .shell-backdrop").onclick = function () {
    app.removeAttribute("data-open");
  };
  document.querySelector("#app .shell-fold").onclick = function () {
    app.toggleAttribute("data-collapsed");
  };
</script>
```

At `40rem` and below, the sidebar is off-canvas. `.shell-menu` becomes visible. Set `data-open` on `.shell` to slide the rail in. `.shell-backdrop` covers the page; clear `data-open` when it is clicked.

Wider than `40rem`, `.shell-fold` is the desktop control. `.shell-menu` stays hidden. Set `data-collapsed` to shrink the rail to `--sidebar-width-icon`. Then `.sidebar-label`, `.sidebar-sub`, `.sidebar-chevron`, `.stack` in the header or footer, and a `<span>` inside `.sidebar-link` hide. Put a small icon before the span so the rail still has a mark.

Widths (set on `:root` or on `.shell`):

- `--sidebar-width` — `16rem`. Desktop rail.
- `--sidebar-width-icon` — `3rem`. Desktop rail when `data-collapsed`.
- `--sidebar-width-mobile` — `18rem`. Off-canvas width at `40rem` and below.

A collapsed rail with groups, a search field that hides, and nested links:

```html
<div class="shell" id="app-fold" data-collapsed style="--sidebar-width: 18rem">
  <button class="shell-backdrop" type="button" aria-label="Close menu"></button>
  <aside class="sidebar" id="fold-sidebar">
    <div class="sidebar-header">
      <a class="sidebar-link" href="/">
        <svg width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><circle cx="8" cy="8" r="6" fill="currentColor"></circle></svg>
        <span>Acme</span>
      </a>
      <div class="stack" style="--stack-gap: 0.5rem">
        <input type="search" placeholder="Search" aria-label="Search">
      </div>
    </div>
    <div class="sidebar-content">
      <div class="sidebar-group">
        <div class="sidebar-label">Platform</div>
        <nav class="sidebar-menu" aria-label="Platform">
          <details open>
            <summary class="sidebar-link">
              <svg width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><circle cx="8" cy="8" r="6" fill="currentColor"></circle></svg>
              <span>Playground</span>
              <svg class="sidebar-chevron" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="m9 6 6 6-6 6"></path></svg>
            </summary>
            <div class="sidebar-sub">
              <a class="sidebar-link" href="/history">History</a>
              <a class="sidebar-link" href="/starred">Starred</a>
            </div>
          </details>
          <a class="sidebar-link" href="/projects">
            <svg width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><circle cx="8" cy="8" r="6" fill="currentColor"></circle></svg>
            <span>Projects</span>
          </a>
        </nav>
      </div>
    </div>
    <div class="sidebar-footer">
      <div class="cluster">
        <a class="sidebar-link" href="/account">
          <svg width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><circle cx="8" cy="8" r="6" fill="currentColor"></circle></svg>
          <span>Ada</span>
        </a>
      </div>
    </div>
  </aside>
  <div class="shell-main">
    <header class="topbar">
      <button class="shell-fold" type="button">Fold</button>
      <button class="shell-menu" type="button" aria-controls="fold-sidebar">Menu</button>
      <span>Inbox</span>
    </header>
    <div class="shell-body">
      <div class="stack">
        <p>Main content.</p>
        <div class="cluster">
          <button type="button">New</button>
          <button type="button">Filter</button>
        </div>
      </div>
    </div>
  </div>
</div>
<script>
  var fold = document.getElementById("app-fold");
  document.querySelector("#app-fold .shell-menu").onclick = function () {
    fold.setAttribute("data-open", "");
  };
  document.querySelector("#app-fold .shell-backdrop").onclick = function () {
    fold.removeAttribute("data-open");
  };
  document.querySelector("#app-fold .shell-fold").onclick = function () {
    fold.toggleAttribute("data-collapsed");
  };
</script>
```

## Changelog

- 3.1.0
    - **New:** `.topbar[data-pin]` sticks a topbar to the top of a scrolling ancestor (`position: sticky`, `top: 0`, `z-index: 10`). Background is not included.
- Docs
    - **Docs:** README examples for `.stack`, `.cluster`, `.overlay`, `.table-wrap`, and the app shell.
- `3.0.0` - `2026-08-30`
    - **New:** Vertical `.stack` (`--stack-gap`) and wrapping `.cluster` (`--cluster-gap`) that are not the page `.section` grid.
    - **New:** App shell structure: `.shell`, `.sidebar`, `.shell-main`, `.topbar`, `.shell-body`, `.shell-menu`, `.shell-backdrop`, `.shell-fold`, with `data-open` / `data-collapsed` and `--sidebar-width` / `--sidebar-width-icon` / `--sidebar-width-mobile`.
    - **New:** Sidebar regions `.sidebar-header`, `.sidebar-content`, `.sidebar-footer`, `.sidebar-group`, `.sidebar-menu`; nested `.sidebar-sub` / `.sidebar-chevron` (layout only); `.overlay`; `.table-wrap`.
- `2.1.0` | `2026-05-01`
    - **New:** Gap-aware grid. Every `.section` and `.sub-section` now supports `--gap` (defaults to `0rem`). Column widths automatically subtract the gap, so `col-1-3` stays one-third even with spacing.
    - **Changed:** Column classes now use CSS variables (`--p`) for proportional widths, enabling clean `calc()` support for gaps.
    - **Improved:** `.col` defaults to `flex: 1 1 0%` for better equal distribution with gaps.
- `2.0.1` | `2025-12-29`
    - **Fix:** Gap removed for correct column width.
- `2.0.0` | `2025-02-28`
    - **New:** Flexbox-based grid system for modern, responsive layouts.
    - **New:** Added Tailwind Preflight (based on `modern-normalize`) for consistent cross-browser styling.
    - **New:** Shorter column class names (e.g., `col-1-3` instead of `col_1_of_3`).
    - **New:** `sub-section` class for easier sub-columns without extra nesting.
    - **New:** Apply `box` or `hero-box` directly to sections for cleaner code.
    - **Optimized:** Removed redundant full-width classes; use `col-1-1` for full-width columns.
    - **Optimized:** Added CSS variables for easier customization.
    - **Optimized:** Mobile-first design with min-width media queries.
- `1.1.3` | `2023-01-13`
    - Set just one font alongside `sans-serif` alias
    - Removing old `zoom: 1` fallback for IE 6/7
    - Fix grid percentages errors _(from a non-used case of grid with spaces)_
- `1.1.2` | `2018-03-17` - Remove `body` tag from example
- `1.1.1` | `2016-08-16` - Fix for SVG classes
- `1.1.0` | `2016-07-21` - 12 columns
- `1.0.0` | `2016-03-30` - First release
