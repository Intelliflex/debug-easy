<h1>debug-easy</h1>

Debug-easy makes it easy to log colorful and meaningful debug messages to your browser console, without the residual mess associated with console.log. Debug messages may be enabled or disabled for individual modules that you are working on. Debug messages may also be disabled globally, to negate console messages in production builds using a single command.

Debug-easy has been enhanced from it's preliminary release making it easy to use and supporting multiple arguments and now using only a single first argument, which may be a comma delimited string or an object with keys. The commands debug.info(), debug.warn(), debug.error(), debug.success() and debug.highlight() are the same as debug.log, but have preset colors.

![Screenshot](https://raw.githubusercontent.com/Intelliflex/debug-easy/master/screenshot.jpg)

<b>SYNTAX</b>
<b>debug.log</b> ('Heading,Module,Color,Background-color,space', var1, var2, var3 .....)
<i>You may include as many or as few options or variables as you like, so debug.log('Test,testVal) is valid. The word space may be used to print a spacer after the output. The spacer may be customised by using debug.spacer('<---my spacer---?')</i>

<b>debug.heading</b> ('Your Heading Title,module,color,background-color, 2nd gradient color, force)

Apart from beautifying console output, making it easier to debug your applications, or provide meaningful data for advanced users, debugging can be turned off with a single command, <b>debug.off()</b> or can be disabled for individual modules.

<b>INSTALLATION</b>
npm install --save debug-easy

<b>Usage Examples:-</b>
<i>Note: This example can be tested easily by typing <b>debug.sample()</b>

<pre>
	let a = 10
	let b = 5
	let obj1 = [
		{ a: 'aaa', b: 'bbb' },
		{ a: 'ccc', b: 'ddd' },
		{ a: 'eee', b: 'fff' }
	]
	let obj2 = [{ a: 1 }, { b: 2 }, { c: 3 }, { d: 4 }]
	let obj3 = {
		error: 'There was an error',
		status: 400,
		details: 'Not found'
	}

	Debug.heading('This is a General Heading')
	Debug.error('This is an error')
	Debug.warn('This is a warning')
	Debug.info('This is Info')
	Debug.highlight('This is highlighted')
	Debug.success('This is Successs')
	Debug.heading('Heading for Module1,module1,black,yellow,orange')
	Debug.info('Multiple Objects,module1', obj1, 'a', a, 'b', b, 'a+b=', a + b)
	Debug.highlight('This is a highlight in module1, module1')
	Debug.warn('This is a warning in module 2,module2')
	Debug.heading('Heading for Module 2,module2,white,green,black')
	//HEADINGS FOR EACH MODULE WILL NOT BE SHOWN MORE THAN ONCE
	Debug.heading('Heading not shown,module2,white,green,black')
	Debug.heading(
		'2nd Heading will be shown if Forced,module2,blue, white, cyan,force'
	)
	Debug.off('module1,module2')
	//THE NEXT LINE WILL NOT BE SHOWN AS DEBUG IS OFF
	Debug.log('This will not be shown,module1')
	Debug.on('module1')
	Debug.log('This will be shown as debug turned back on for module1,module1')
	Debug.log(
		'This will not be shown as debug is still off for module2,module2'
	)
	Debug.on('module2')
	Debug.log(
		{
			title: 'Using Named Properties',
			module: 'my Module',
			color: 'fuchsia',
			bg: 'lavender',
			spacer: '<===== Unique Spacer =====>',
			space: true
		},
		obj3
	)
	Debug.highlight('This is highlighted with spacer,module2,space')
	Debug.success('This is Successs,module2')
	Debug.spacer('<----- Custom Spacer ----->')
	Debug.error('Error with new custom spacer,,space', obj1)
	Debug.info('Here is an Array', obj2)
	Debug.table('Object can be shown as Table,module2,blue,lavender', obj1)
	Debug.history()
		
</pre>
