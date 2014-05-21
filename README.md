test-element
====================

A unit testing sampler for Polymer elements using Mocha and Chai.

## Usage

These steps will fetch the dependencies needed for testing & running this sampler:

```
$ git clone git://github.com/PolymerLabs/test-element.git
$ cd test-element
$ bower install
$ cd ..
$ python -m SimpleHTTPServer 9000
```

With the server running, load `http://localhost:9000/runner.html` in a browser to run the tests included. 

### Creating tests

We run entire HTML pages (e.g pages containing elements) as individual tests in a suite. 

To customize the sampler for a new test:

1. Create the test as a new HTML file in the `tests` directory (e.g `my-tabs-basic-test.html`). You can use our [unit test boilerplate](https://raw.githubusercontent.com/PolymerLabs/unit-tests-sampler/master/tests/sample-test.html) as a starting point. It already references the relevant Mocha, Chai and tooling dependencies you'll need.
2. Author your tests in the file you created (e.g in `my-tabs-basic-test.html`). Some [tips](https://gist.github.com/addyosmani/b318ca7618eed38c05e1) are available on how to test attributes and events.

3. `tests/tests.html` takes care of running individual tests. You will want to define a new `htmlSuite()` for a set of tests around a new element and then individual `htmlTest()`s for running each test file. For the `my-tabs` element, this might look as follows:

```
  htmlSuite('my-tabs', function() {
    htmlTest('tests/my-tabs-basic-test.html');
    htmlTest('tests/my-tabs-accessibility-test.html');
  });
```

That's it. You should now be able to run `python -m SimpleHTTPServer 9000`, open up your browser and run your tests from `http://localhost:9000/runner.html`.

### Structure

* runner.html - automates running Mocha with your tests
* tools - helper tools for HTML tests with Mocha and Karma
* tests - sample unit tests
* .bowerrc, .bower.json - Bower config files.

