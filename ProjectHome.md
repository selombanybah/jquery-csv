# jquery-csv 0.7 (Beta) #

# Summary #

Javascript is growing up and HTML is finally maturing the point where webapps are being built to completely displace desktop applications. It's about time that the supporting libraries grow up too.

Looking for a complete, end-to-end, battle tested, performance optimized CSV parser that's available in the familiar jQuery syntax style? Welcome...

This library is a different creature, featuring a slim Chomsky - Type III parser implementation. Full (that means 100%) [IETF RFC 4180](http://tools.ietf.org/html/rfc4180) compliance. Including coverage for a few edge cases that even the spec fails to cover.

Enough with the wind-up...

Want to see it in action? Check out the [Basic Usage Demo](http://jquery-csv.googlecode.com/git/examples/basic-usage.html). Want more? The [Use Cases](http://code.google.com/p/jquery-csv/#Use_Cases) section below has what you need.

_Aside: To the script kiddies... Don't be sad, we bet there are still plenty of people who would like to hear you outline the merits of str.split()._

# Features #
  * Convert a CSV String to an array
  * Convert a multi-line CSV string to a 2D array
  * Convert a multi-line CSV string to an array of objects (ie header:value pairs)
  * Convert an array of values to CSV (_under development_)
  * Convert an array of objects to CSV (_under development_)
  * [Hooks/Callbacks](HooksAndCallbacks.md) to extend the default parsing process
  * Customizable delimiter (default: ") and separator (default: ,) characters
  * Node.js support (ie CommonJS importing and async callback support)


# Syntax #

### Importing ###

**Client-Side:** (ie browser) - import via the script element.
```
<script src="jquery-csv.js"></script>
```

**Server-Side:** (ie Node.js) - Import via the standard CommonJS approach.
```
var $ = jQuery = require('jquery');
require('./jquery.csv.js');
```

### Usage ###

Each one of the methods can be called with the following form:
```
$.csv.function(csv, {options}, callback);
```

| **csv** | required | The csv data to be transformed. |
|:--------|:---------|:--------------------------------|
| **options** | optional | An object containing user-defined overrides for the default options. |
| **callback**| optional | Used for Node.js-style async callbacks. Uses the form function(err, data). |

### Methods ###

**toArray**
  * Parse a single entry string to an array
```
$.csv.toArray(csv);
```
_Documented under [API#$.csv.toArray()](API#$.csv.toArray().md)._

**toArrays**
  * Parse a multi-line CSV string to a 2D array
```
$.csv.toArrays(csv);
```
_Documented under [API#$.csv.toArrays()](API#$.csv.toArrays().md)._

**toObjects**
  * Parse a multi-line CSV string to an array of objects
```
$.csv.toObjects(csv);
```
_Documented under [API#$.csv.toObjects()](API#$.csv.toObjects().md)._

**fromArrays (not implemented)**
  * Convert array data to a CSV string
```
$.csv.fromArrays(arrays); // planned
```

**fromObjects (not implemented)**
  * Convert an array of objects to a CSV string
```
$.csv.fromObjects(objects); // planned
```

# Use Cases #

What fun is having a shiny new library without examples to play with?

No fun that's what... That is coming from a guy who has spent entirely too much time mucking through API documentation when he'd much rather be out at the beach, surfing, or chasing girls.

Instead of the typical useless contrived example code, I have provided a handful of simple yet powerful demos. Not only are they fun to play with but a quick peak at the source will show you how simple and easy they were to implement.

Who knows... maybe this whole 'having fun' concept may spread to some of the other Open Source libraries as a result. One can dream...

## Basic Usage ##

Want to play with the parser and maybe validate your CSV data without all the frills? No need to download the source first, there's a demo for that...

[jQuery-CSV - Basic Usage Demonstration](http://jquery-csv.googlecode.com/git/examples/basic-usage.html)

### Client-Side File Handling ###

Yes, you read that right. It's now possible to open local files in the browser without firing a single request to the server.

The functionality is still pretty new so not all browsers support it (I'm looking @ you IE). If that's not an issue I highly suggest you try it. It's much easier than the traditional client/server approach.

[jQuery-CSV - File Handling Demonstration](http://jquery-csv.googlecode.com/git/examples/file-handling.html)

### jQuery-CSV + Flot ###

Hands down, the most exciting addition to the demo collection so far...

You can input the data set using either the text area provided or via uploading CSV data files.

Want to plot 5 data sets on the same grid, no problem; Just upload 5 files containing one dataset each. The jQuery-CSV will handle the plumbing while Flot will make it all look pretty.

[jQuery-CSV - Flot Demonstration](http://jquery-csv.googlecode.com/git/examples/flot.html)

### jQuery-CSV + Google Visualization API ###

OK, I lied. This one is even cooler than Flot. Hike up your fancy pants because these things look slick.

Don't want to draw a line graph, no problem you can tap into the massive collection of different graph types available. Embedded is a fully configurable dashboard.

**Warning: You may experience multiple spontaneous 'oh my got that's soo awesome' fits of excitement. Maybe even get [stoked](http://www.youtube.com/watch?v=QgXObaM9i2Q). Happens to the best us...**

[jQuery-CSV - Google Visualization API Demonstration](http://jquery-csv.googlecode.com/git/examples/google-visualization.html)

### jQuery-CSV + Node.js ###

What's better than a powerful JavaScript platform in the browser. A second, even more powerful JavaScript platform on the server.

And... jQuery-CSV fully supports it. There is not online demo because it requires a Node.js server to run but a stub is provided to help get you started.

Dependencies:

To make this example work, you'll also need to install jQuery via the [NPM](http://en.wikipedia.org/wiki/Npm_(software)).
```
npm install jquery
```

The link to the stub:

[node-usage.js](http://jquery-csv.googlecode.com/git/examples/node-usage.js)

### Client-Side Database Import ###

Wait... what? Don't databases require a server-side API? Not if the data access layer implements a REST API that accepts JSON POST updates.

When it comes to databases, CSV is still a favored format for data dumps because it's simple, lightweight, and platform agnostic. It's possible to expose a server-side SaaS service to handle the data conversion but that would involve more web requests, more bandwidth, more CPU time, and more unnecessary strain on the webserver.

I hear web browsers are becoming more powerful, lets use those...

It will require [jQuery-JSON](http://code.google.com/p/jquery-json/) to handle the data (de)serialization but the chain from a CSV file to an AJAX POST request is very simple.

Open a .csv file Locally (HTML5 File API) -> jQuery-CSV -> jQuery.JSON -> jQuery.POST

(planned HTML example needs to be added to the repository)

# Long-Term Development #

1.0 will be the first long-term support release. The design will freeze and focus will shift away from rapid development.

No detail will be overlooked. If you want code that stands the test of time be patient, it's coming.

# Short-Term Development #

0.7 Finally, all of the core parser bugs are resolved. Time to add some new functionality. The parsers are finished, how about we get those formatters working now.

**0.7 changes from the last version:**

The close of the 0.6 (ie bugfix) release series marks a significant milestone. Finally, the parser is 100% compliant.

The 0.6 release series included:
  * a huge number of bigfixes
  * accurate CSV tracebacks for malformed data
  * internal state tracking
  * parser hooks for inlining additional user-definied processing steps
  * 3 completely new parsers to replace the old mega-monolithic parser
  * the castToScalar hook to auto-cast numerical data
  * a new test runner to check for strict RFC compliance
  * greatly improved test coverage
  * document updates
  * a lot of new demos
  * support for node.js style callbacks

In short, the external API is nearly identical to previous but there were a TON of internal changes. All targeted to make this library stable, consistent, cross-compatible, and free of side-effects.

_Note: Want to know where this project is headed, check out the [Roadmap](Roadmap.md)._

# How You Can Help #

**Run the test runner:**
Just run the tests (http://jquery-csv.googlecode.com/git/test/test.html) in your particular brand of browser and report any failures.

**We need performance tests:**
Performance tests in javascript would add a lot of value to the project. If that's your forte, don't be shy.

**Provide feedback:**
If you have a good suggestion, a useful use case, or just want to share your experience, don't hesitate to get involved. Check out the [Feedback](Feedback.md) wiki and share your thoughts.

Without your contributions and the contributions of the community, this would be just another half-baked CSV to add to the pile of literally thousands of broken/incomplete implementations. The quality of projects like these is a direct result of a greater community that is willing to suggest improvements and test the code.


---


**jQuery-CSV** coding style is inherited from the [JQuery Core Style Guidelines](http://docs.jquery.com/JQuery_Core_Style_Guidelines)

by **Evan Plaice**