# altiva-css
Altiva CSS micro-library for rapid and responsive front-end interface development

## Install and Quick Start

### Step 1

 1. Create a `css` folder inside your project.
 2. Create a new file `design.css` inside the `css` folder.
 2. [Download](https://raw.githubusercontent.com/Altiva/altiva-css/master/altiva.min.css) Altiva CSS in the same folder and include these files in your html project:

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Your Incredible Website</title>
	<link rel="stylesheet" href="css/altiva.min.css">
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
