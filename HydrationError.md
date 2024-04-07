# The guide to avoid NextJS hydraion errors.

## Causes

- Conditional handling in the component return which only accessed after the first rendered frame.
- Accessing window or localStorage object inside the JSX.

**Solution:** <br> 
We can use ``useClient`` custom hook to perform the logic only if it is on the client side which will prevent nextJs from trying to evaluate the condition before it's parts are initialized.

- ```<p>``` nested in another ```<p>``` tag
- ```<div>``` nested in a ```<p>``` tag
- ```<ul>``` or ```<ol>``` nested in a ```<p>``` tag
- Interactive Content
cannot be nested (```<a>``` nested in a ```<a>``` tag, ```<button>``` nested in a ```<button>``` tag, etc.)

**Solution:** <br>
Only avoiding the practicies above should do the trick.

## Procedure

Unfortunately NextJs errors does not always give away the part that caused the error which makes it our mission.
The followed approach is pretty simple but a bit time consuming and it is just to comment out everything in the page and start uncommenting it one by one until the error is thrown. Now we know what component is causing the error.
We follow the same approach inside the component until we eventually get to the root cause and given the two methods above we should be able to handle it.
