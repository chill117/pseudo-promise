# pseudo-promise

A custom promise implementation for Node


## Installation

Add `pseudo-promise` to your project's `package.json` file:
```
{
  "name": "Your App",
  "dependencies": {
    "pseudo-promise": "latest"
  }
}
```
*It is recommended that you specify a hard-coded version number instead of `latest`*

*See https://npmjs.org/package/pseudo-promise for the latest release version*


Then install it by running the following:
```
npm install
```


## Usage

Given an asynchronous function:
```
var Promise = require('pseudo-promise')

function asynchronousFunction() {

	var promise = new Promise()

	setTimeout(function() {

		// Uncomment the following line to simulate an error:
		// prommise.reject('An error occurred!')

		promise.resolve({name: 'A result!'})

	}, 500)

	return promise
	
}
```

Listen for either an error or a result:
```
asynchronousFunction().complete(function(error, result) {

	if (error)
		return console.log(error)

	// Do stuff with the result.
	console.log('result:')
	console.log(result)

})
```

Or, listen for the result only:
```
asynchronousFunction().success(function(result) {

	// Do stuff with the result.
	console.log('result:')
	console.log(result)

})
```

Or, listen for the error only:
```
asynchronousFunction().error(function(error) {

	console.log(error)

})
```

Chaining works too:
```
asynchronousFunction()
	.error(function(error) {

		console.log(error)

	})
	.success(function(result) {

		// Do stuff with the result.
		console.log('result:')
		console.log(result)

	})
```


## How to Run Tests

From your project's base directory:
```
mocha
```
*You may need to run `npm install` locally to get the dev dependencies.*