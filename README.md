# alumna-css
Alumna CSS is a micro-library for rapid and responsive front-end interface development.

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

## Changelog

- `2.1.0` | `2026-05-01`
    - **New:** Gap-aware grid. Every `.section` and `.sub-section` now supports `--gap` (defaults to `0rem`). Column widths automatically subtract the gap, so `col-1-3` stays one-third even with spacing.
    - **Changed:** Column classes now use CSS variables (`--p`) for proportional widths, enabling clean `calc()` support for gaps.
    - **Improved:** `.col` defaults to `flex: 1 1 0%` for better equal distribution with gaps.
- `2.0.1` | `2025-12-29`
    - **Fix:** Gap removed for correct column width
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
