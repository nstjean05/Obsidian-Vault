## Tables
- Arrange data in rows and columns
- 
```HTML
<!DOCTYPE html>
<html>
	<head>
		<title> Our First Webpage!</title>
	</head>
	<body>
		<table>
			<tr rowspan="2"><th>Names</th></tr>
			<tr><th>First Name</th><th>Last Name</th>
			<tr>Noah<td></td><td>St. Jean</td></tr>
		</table>
	</body>
</html>
```
## Form
- Use to collect user input
- `<form>` contains form input elements
	- Each element must have a name attribute
- Action attribute defines what to do when the user clicks on the submit button
- Can't functionally take an input using only HTML, backend knowledge is also required.
```HTML
<!DOCTYPE html>
<html>
	<head>
		<title> Our First Webpage!</title>
	</head>
	<body>
		<form action="/action_page.php">
		User Name: <input type = "text" name = "username" value "value">
		Password: <input type = "password" name = "pw">

		Please select your colour:
		<select>
			<option>Red</option>
			<option>Green</option>
			<option>Blue</option>
		</select>

		<br>Please select your colour again:
		<br><input type = "radio" name = "colour" value = "red">Red
		<br><input type = "radio" name = "colour" value = "green">Green
		<br><input type = "radio" name = "colour" value = "blue">Blue
		
		<input type = "submit" value = "Click Here!">
		<!-- This is where the backend comes into play, clicking here will simply cause an error. -->		
		</form>
	</body>
</html>
```

## SVG
- Scalable Vector Graphics (SVG)
	- Defines vector-based graphics in the XML format
	- Are contained in the `<svg>` element
	- Can draw:
		- Paths
		- Boxes
		- Circles
		- Text
		- Graphic Images
- This allows images to be scaled indefinitely using polygons
- SVG images begin with an `<svg>` element.
	- Has the properties of height and width (in pixels)
	- 