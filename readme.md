nodebase
--------
This is my boilerplate for when I start a new ```node.js``` project. I clone this repository and start from there.

You put your code in the ```lib``` folder. I recommend an editor that you can configure to run JSHint for you
while you are editing your JavaScript files. I use WebStorm.

The main advantage of cloning this repository is that it comes with a working test-setup and runs JSHint as well
as all the tests. This can be a pain to set up if you are new to node.

Test setup
----------
- ```mocha``` is the test framework
- ```sinon``` is used for mocks and spies
- ```chai``` is used for assertions
- ```sinon-chai``` is used for better assertions of sinon

Test files
----------
The project it set up to have tests in the ```test``` folder.

There is an example test in ```test/unit/globals.spec.js```.

I usually put my unit tests in ```test/unit``` and my integration tests in ```test/integration```, and create
other folders in ```test/``` for other classes of tests.

BDD style
---------
The tests are set to use BDD-style, and use the dot reporter. These options can be changed in the
file ```test/mocha.opts```

Global variables when testing
-----------------------------
The following global variables are defined for testing:
- ```expect``` for assertions
- ```sinon``` for mocking and spies
- ```_``` the JavaScript helper library underscore
- ```injectr``` for mocking out ```require``` statements
- ```request``` library for making HTTP requests to your API in integration tests

You can alter globals for testing in the file ```test/common.js```

JSHint
------
JSHint is set up to verify all the JavaScript files in the folders ```lib```. ```bin``` and ```test```.

You can add more directories in the ```bin/runTests.js``` file.

You can specify what JSHint options to use in the file ```.jshintrc```

You can specify specific files or directories for JSHint to ignore in the file ```.jshintignore```

Running tests
-------------
After you do ```npm install``` you just run the command

```npm test```

to run all tests.

In the Webstorm editor you can also set up a run configuration and point it at ```bin/runTests.js``` to run tests.

Running a subset of tests
-------------------------
If you want to run a subset of tests, you can modify the file ```tests/mocha.opts``` and add the line
```
--grep myTestFilter
```
At the top, here is the mocha explanation of ```--grep```

The --grep option when specified will trigger mocha to only run tests matching the given pattern which is internally compiled to a RegExp.

Suppose for example you have “api” related tests, as well as “app” related tests, as shown in the following snippet;
One could use ```--grep api``` or ```--grep app``` to run one or the other.
The same goes for any other part of a suite or test-case title, ```--grep users``` would be valid as well,
or even ```--grep GET```.

```
describe('api', function(){
  describe('GET /api/users', function(){
    it('respond with an array of users')
  });
});

describe('app', function(){
  describe('GET /users', function(){
    it('respond with an array of users')
  });
});
```