# alumna-css
Alumna CSS micro-library for rapid and responsive front-end interface development

## Install and Quick Start

### Step 1

 1. Create a `css` folder inside your project.
 2. Create a new file `design.css` inside the `css` folder.
 2. [Download](https://raw.githubusercontent.com/alumna/alumna-css/master/alumna.min.css) Alumna CSS in the same folder and include these files in your html project:

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

### Step 2

 1. Create a section group
 2. (Optional) Create a box to contain your columns without touching the screen limits
 3. Define the desired column numbers

```html
...
<div class="section group">
	<div class="box"> <!-- This is optional -->
		
		<div class="col col_1_of_3">
			<!-- First column of three -->
		</div>

		<div class="col col_1_of_3">
			<!-- Second column of three -->
		</div>

		<div class="col col_1_of_3">
			<!-- Third column of three -->
		</div>


	</div>
</div>
...
```

## Changelog

- `1.0.0` | `2016-03-30` - First release
- `1.1.0` | `2016-07-21` - 12 columns
- `1.1.1` | `2016-08-16` - Fix for SVG classes
- `1.1.2` | `2018-03-17` - Remove `body` tag from example
- `1.1.3` | `2023-01-13`
    - Set just one font alongside `sans-serif` alias
    - Removing old `zoom: 1` fallback for IE 6/7
    - Fix grid percentages errors _(from a non-used case of grid with spaces)_

