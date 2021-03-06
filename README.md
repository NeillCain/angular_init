# angular_init 0.3.0

## Quick Start

ngi creates AngularJS templates for you from the command line.

**Get up and running in seconds:**

[![Gem Version](https://badge.fury.io/rb/ngi.svg)](http://badge.fury.io/rb/ngi)

```shell
$ gem install ngi
$ cd ~/MyAwesomeApp # => go to your app
$ ngi controller # => creates a new AngularJS controller
```

## Know everything

<a href="http://joshbeam.github.io/angular_init">Website</a>

**Having issues?** Email me (Josh) at <a href="mailto:frontendcollisionblog@gmail.com">frontendcollisionblog@gmail.com</a>. I'll usually respond within an hour or so. You can also report a bug by opening a new issue through GitHub, or if you want to add a feature yourself, just fork and submit a pull request!

**What's new in 0.3.x?**

*This version is backwards-compatible with 0.2.x*
- Use custom template files (see the [tutorial][tutorial])

## In simple terms:

This tool (`ngi`) can make (for example) an AngularJS controller template file for you (`.js`), so that **whenever you want to make a new controller for your app, you don't have to type the same starting code over and over again** (by the way, this tool doesn't only create controllers. It does directives, filters... almost anything).

## Why use `ngi` (and not something else)?

**`ngi` has one task, and one task only, which makes it lightweight and specialized**. Most AngularJS developers are probably using the command line already (Gulp, Bower, npm, Git, etc.), so why not use the command line to streamline your code-writing too?

Type less, write more AngularJS! Use `ngi`, the simple template generator.

![Example](https://github.com/joshbeam/angular_init/blob/master/ngi_example.gif "Example")

# Table of Contents

- [Sample Usage][sample-usage]
- [Features][features]
- [Install in 1 step][install]
- [How to use it (docs)][commands]
- [FAQ][faq]
- [Technical Info][tech-info]

# Sample Usage

After you [do the 1-step installation][install] of `ngi` (the short-name for the shell script of `angular_init`), go to where your site is at (in this case, `~/MyAwesomeApp`). When you're in your site's project directory, just type `ngi <component>` to create a new JavaScript file for you!

## Command line

```shell
~/MyAwesomeApp $ ngi controller # this will create a controller!

# you'll be prompted for some quick info
[?] New file name: myAwesome.controller.js
[?] Module name: myModule
[?] Controller name: MyAwesomeController
[?] Inject (already injected $scope): $route

# all done!
```

## Output (new boilerplate code)

```javascript
// ~/MyAwesomeApp/myAwesome.controller.js

;(function(app) {

	'use strict';

	app.controller('MyAwesomeController',MyAwesomeController);

	MyAwesomeController.$inject = ['$route', '$scope'];

	function MyAwesomeController($route, $scope) {
	
	}

})(angular.module('myModule'));
```

By the way, the output of this little tool is meant to follow [John Papa's AngularJS Style Guide][style-guide].

# Features

## Current features

- Create a module, directive, controller, filter, run, config, "routes" config, constant, service, factory, or index HTML page by saying `ngi <component>`, where `<component>` is any of the above types (module, directive, etc.)
- Current languages that have default templates: CoffeeScript, ECMAScript5 (choose your language with `ngi --config (or -c)`)
- Use custom templates

## Coming soon

- Possible Node.js version

Feel free to fork the project or get <a href="http://frontendcollisionblog.com/about">in touch with Josh (me)</a> with any feature requests!

# Installation (in 1 step)

**Dependencies** [Ruby 2.1.0][ruby] and [RubyGems][rubygems] (optional [Bundler][bundler])

Add this line to your application's Gemfile:

    gem 'ngi'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install ngi

# Commands

```shell
~/MyAwesomeApp $ ngi controller # => controller
~/MyAwesomeApp $ ngi directive # => directive
~/MyAwesomeApp $ ngi factory # => factory
~/MyAwesomeApp $ ngi service # => service (same as factory)
~/MyAwesomeApp $ ngi constant # => constant
~/MyAwesomeApp $ ngi run # => a run block
~/MyAwesomeApp $ ngi config # => a config block
~/MyAwesomeApp $ ngi routes # => a config block with $routeProvider injected
~/MyAwesomeApp $ ngi module # => module (you can inject dependencies too)
~/MyAwesomeApp $ ngi filter # => filter

# or

~/MyAwesomeApp $ ngi index # => an index page in HTML

# or

# use either --options or -o
~/MyAwesomeApp $ ngi --options # => choose your language to use (CoffeeScript or ECMAScript5)
```

# FAQ

**1. Can you explain why the module name is passed as the argument to the IIFE (in the default template)?**

- If you're using a JSHint plug-in, it will only say 'angular is not defined' in one place
- Eliminates the clutter of declaring something like `var app = angular.module('myModule')`
- Something like `angular.module('myModule')` cannot be minified, but the argument `app` can (only an issue if the full module getter happens multiple time)
- Streamlines the pattern across all of the templates

**2. Why are you using `$inject`?**

Check out [John Papa's Style Guide][style-guide].

**3. Why are you following the snake-case convention (`angular_init`) and not camelCase (`angularInit`) if this is a JavaScript project?**

The command line tool itself is written in <a href="https://www.ruby-lang.org/en/">Ruby</a>, and the <a href="https://github.com/bbatsov/ruby-style-guide#snake-case-files">convention</a> is to use snake-case for class file naming.

*For other questions and comments, check out this <a href="http://www.reddit.com/r/angularjs/comments/30ydha/command_line_tool_to_create_angularjs_controllers/">Reddit discussion</a> about `ngi` (feel free to post your own question too). Or, open a new issue on GitHub.*

# Technical Information

Uses <a href="http://semver.org/">Semantic Versioning</a>

**Language** Ruby

**Requirements** Only tested with `ruby 2.1.0p0 (2013-12-25 revision 44422) [x86_64-darwin13.0]`. Compatibility with previous versions of Ruby cannot be guaranteed.

<hr>

**Disclaimer**

`angular_init` and `ngi` and the author (Joshua Beam) are not directly associated with <a href="http://angularjs.org">AngularJS</a>.

**Copyright (c) 2015 Joshua Beam** &mdash; <a href="http://frontendcollisionblog.com">Front End Collision</a>

MIT License

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

[install]: #installation-in-1-step
[sample-usage]: #sample-usage
[features]: #features
[commands]: #commands
[faq]: #faq
[tech-info]: #technical-information
[style-guide]: https://github.com/johnpapa/angular-styleguide
[rubygems]: https://rubygems.org/pages/download
[ruby]: https://www.ruby-lang.org/en/downloads/
[bundler]: http://bundler.io/
[tutorial]: https://github.com/joshbeam/angular_init/blob/master/TUTORIAL.md