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
		Password: <input type = "password" name = "pw

		Please select your colour:
		<select>
			<option>Red</option>
			<option>Green</option>
			<option>Blue</option>
		</select>
		
		<input type = "submit" value = "Click Here!">
		</form>
	</body>
</html>
```