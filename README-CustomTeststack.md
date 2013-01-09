Setup
-----

folders:

./
- dojo2-core
-- test
--- teststack.js     dojo2's test config
- dojo2-teststack
-- test
--- teststack.js     Seemingly bogus and not used at all
- saucerunner
-- test/
--- teststack.js     Your browser set up configs and your tests to be run

export SAUCE_USERNAME = mrjcleaver;
export SAUCE_ACCESS_KEY = d6eb30b0-57a1-48b3-aa30-90596dadcc9b

or hack  dojo2-teststack/runner.js to hard code them


To run the default dojo tests
-----------------------------

cd dojo2-teststack
node runner.js config=dojo-core/test/teststack.js


To run your own set
-------------------

cd dojo2-teststack
node runner.js config=../saucerunner/test/teststack.js

This will run our teststack.js


Setting up teststack.js
-----------------------

Your
- teststack.js

  // Packages that should be registered with the loader in each testing environment
	packages: [ { name: 'dojo', location: 'dojo2-core' } ],
	// This is the default, as dojo-teststack.js is built for testing dojo-core

	// Non-functional test suite(s) to run in each browser
	suites: [ '../saucerunner/test/all' ],

	or just:

	suites: [ '../saucerunner/test/saucelabs-guinea-pig' ],

	to do a simple multi-browser version of the simplest example on https://saucelabs.com/resources for Node.js

Questions
---------
- How would we embed the Chai assertion tester?

 // says lib/assert - TODO: This assertion library sucks, replace it with a real one
 // says teststack/README.md
 //  The assertion library currently bundled is _not_ recommended and will
 //        be going away. Anything that throws errors will work just fine, so go nuts with [Chai](http://chaijs.com/) or whatever
 //        your preferred AMD-compatible assertion library might be.
 // says # http://net.tutsplus.com/tutorials/javascript-ajax/better-coffeescript-testing-with-mocha/
 //  chai is the assertions library to use with mocha
 // -> chai has not been integrated into dojo2-teststack yet

- If we don't use Chai and instead use the sucky one

- Where do we actually do this:

  browser.get("http://saucelabs.com/test/guinea-pig", function() {
    browser.title(function(err, title) {
      assert.ok(~title.indexOf('I am a page title - Sauce Labs'), 'Wrong title!');

- In particular:
- how do we initialize browser?
- how to avoid deeply nested tests and use mocha/chai style


