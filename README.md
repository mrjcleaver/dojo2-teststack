# The Dojo Test Stack

The Dojo Test Stack is a collection of JavaScript modules designed to work together to help you write consistent,
high-quality test cases for your JavaScript libraries and applications.


## This repository

This repository is an experimental repository for the next major version of the Dojo Toolkit. However, at this point
it is extremely likely that this project *will* be finalised and maintained, so please feel free to start using it
as long as you can put up with some API churn until it reaches alpha.


## Features

* 100% [AMD](https://github.com/amdjs/amdjs-api/wiki/AMD), 100% Promises/A-based API
* Instant one-off test execution in the browser or Node.js
* Full statement, branch, function, and line code coverage reporting with
  [Istanbul](https://github.com/gotwarlost/istanbul)
* Functional testing using the standard [WebDriver API](http://www.w3.org/TR/webdriver/) with promises-wrapped
  [WD.js](https://github.com/admc/wd)
* Integration with [Sauce Labs](http://saucelabs.com/) for super simple continuous integration
* Tested with [Travis CI](http://travis-ci.org/)
* Extensible interfaces (comes with TDD, BDD, and objects)
* Extensible reporters (comes with basic console and WebDriver reporters, lcov and tap output planned)


## How to write tests

dojo2-teststack currently comes with support for 3 different test interface: TDD, BDD, and object-oriented. There will
be more instructions here soon; for now, https://github.com/csnover/dojo2-core/blob/master/test/cookie.js demonstrates
writing both synchronous and asynchronous tests. The assertion library currently bundled is _not_ recommended and will
be going away. Anything that throws errors will work just fine, so go nuts with [Chai](http://chaijs.com/) or whatever
your preferred AMD-compatible assertion library might be.


## How to run

First:

1. `git clone --recursive https://github.com/csnover/dojo2-teststack.git` as a sibling directory of the package you
   want to test

Then, for a stand-alone browser client:

1. Navigate to `http://path/to/dojo2-teststack/client.html?suites=mid/of/testsuite&suites=mid/of/othersuite`
1. View console
1. Fix bugs

Or, for a stand-alone Node.js client:

1. Run `node client.js suites=mid/of/testsuite suites=mid/of/othersuite`
1. View console
1. Fix bugs

Or, as an amazing fully-featured automated test runner:

1. Create a teststack configuration file describing your desired test environment, like the one at
   https://github.com/csnover/dojo2-core/blob/master/test/teststack.js
1. `cd dojo2-teststack`
1. `node runner.js config=mid/of/teststack/config`
1. View console
1. Fix bugs

…plus CI support:

1. Create a `.travis.yml` like the one at https://github.com/csnover/dojo2-core/blob/master/.travis.yml
2. Enable Travis-CI for your GitHub account
3. That’s it! Easy continuous integration is easy.


## License

New BSD License © 2012 Colin Snover http://zetafleet.com. Released under
[Dojo Foundation CLA](http://dojofoundation.org/about/cla).