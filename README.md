<p align="center">
	<a href="http://standardjs.com/"><img src="https://img.shields.io/badge/code%20style-standard-brightgreen.svg" alt="JavaScript Style Guide" /></a>
	<a href="https://travis-ci.org/Automotivated/vroom"><img src="https://travis-ci.org/Automotivated/vroom.svg?branch=master" alt="Build Status" /></a>
	<a href="https://www.bithound.io/github/Automotivated/vroom"><img src="https://www.bithound.io/github/Automotivated/vroom/badges/score.svg" alt="bitHound Overall Score"></a>
	<a href="https://codeclimate.com/github/Automotivated/vroom"><img src="https://codeclimate.com/github/Automotivated/vroom/badges/gpa.svg" /></a>
	<a href='https://coveralls.io/github/Automotivated/vroom?branch=master'><img src='https://coveralls.io/repos/github/Automotivated/vroom/badge.svg?branch=master' alt='Coverage Status' /></a>
</p>

# Automotivated.vroom()
Automotivated.vroom( ) is an innovative application to show inventory based on search queries of the visitor. It's build on top of [Vue](http://vuejs.org/) and [Vuex](http://vuex.vuejs.org/en/index.html)

## v0.0.1 EOL
Because of several reasons, the development of vroom v0.0.1 has been discontinued. The previous development repository has been deleted and the project has gain a complete reboot.

## v1.0.0
Starting fresh, starting something awesome! We're expecting the same output, so don't worry! The project is started this time with [vue-cli](https://github.com/vuejs/vue-cli)
> Thanks to [Dezzign](http://www.dezzign.nl/) we won't rely anymore on a default design (materialize) but are getting our own brandnew look and feel. Customizable to your own needs!

## Before we begin
Put on some nice [Electro Swing](https://www.youtube.com/watch?v=aUn2HvekSZY) and make sure you got the following applications installed:

- [Node v4.5.0+](https://nodejs.org/en/)

> **&lt;code like a pro&gt;**<br>
 Here is a little list off applications I use for development. Not required to run the application, but are always nice to have and will definitely make your life a little less frustrating
 - [Sublime](https://www.sublimetext.com) *the best editor there is!*
	- [Package Control](https://packagecontrol.io/)
	- [Material Theme](https://packagecontrol.io/packages/Material%20Theme)<br />
	*choose `Darker` and switch back to `Monokai` from sublime (default theme in Sublime 3)<br />
	tweak the settings with `Material Theme Config`*
	- [Vue Syntax Highlighter](https://github.com/vuejs/vue-syntax-highlight)
	- [Sass](https://packagecontrol.io/packages/Sass)
	- [Git](https://packagecontrol.io/packages/Git)
	- [Markdown Preview](https://packagecontrol.io/packages/Markdown%20Preview)
	- [ES6 Syntax](https://packagecontrol.io/packages/JavaScriptNext%20-%20ES6%20Syntax)
	- [GitGutter](https://packagecontrol.io/packages/GitGutter) *what's changed since last commit*
 - [BeardedSpice](https://beardedspice.github.io/) *don't worry, nobody will hear your music except you!*
 - [Spectacle](https://www.spectacleapp.com/) *shortcuts to get the windows where you want them!*

> **&lt;/code like a pro&gt;**<br>

## [Hey Ho, Let's Go!](https://www.youtube.com/watch?v=ZDXdBx6UaLI) (installation)
Open your favorite ([fish](https://fishshell.com/) || [zsh](http://www.zsh.org/)) flavoured ([oh-my-fish](https://github.com/oh-my-fish/oh-my-fish) || [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)) terminal ([iterm](https://www.iterm2.com/)) and go to your projects folder and clone this repo!

> **&lt;code like a pro&gt;**<br>
 I'm using fish with oh-my-fish and my own [feest](https://github.com/FKobus/theme-feest) theme. Install is super easy and can be done with one command: `omf install https://github.com/FKobus/theme-feest`<br>
 **&lt;/code like a pro&gt;**<br>

Start with cloning the project to your own development machine

```sh
git clone https://github.com/Automotivated/vroom.git
```
Go to the root of your clone and install all dependencies
```sh
npm install
```

## [Compilation](https://www.youtube.com/watch?v=KWJEM5Vcxmk)
We're using [webpack](https://webpack.github.io/) with [hot module replacement](https://webpack.github.io/docs/hot-module-replacement.html) for active development. Run the following command in the project root and it will start a webserver at [http://localhost:8080/](http://localhost:8080/).
```sh
npm run dev
```
When you're ready with making everything possible, run the build command to minify and some more stuff I really don't want to talk about.
```sh
npm run build
```

## [Testing](https://www.youtube.com/watch?v=b8Lol5ce-e0)
The whole app is and should be testable via unit test. New added code must be added to a test. Unit tests are run by Karma with Sinon and Chai.<br>
The following command will run all tests in tests/unit
```sh
npm run test
```

## Integration
Start with adding the vroom minified library to your project (best place should be in the footer somewhere). It's hosted on [surge.sh](http://surge.sh) but available via the vroom subdomain:
```html
<script src="//vroom.automotivated.nl/js/vroom.min.js"></script>
```
Include the style package in the `<head>`
```html
<link rel="stylesheet" href="//vroom.automotivated.nl/css/vroom.min.css">
```
After that, just bind Automotivated.vroom to any valid html element you like. Best practice would be a div.
```html
<div id="vroom"></div>
```

You can bind the app in Javascript by element selector or pass the element.
```js
Automotivated.vroom('#vroom')
// or
Automotivated.vroom(document.querySelector('#vroom'))
```

Before we can show some data, we need to establish a connection to the api server. You can offcourse build you own API. See the [Automotivated.engine( )](https://github.com/Automotivated/engine) docs for formatting.
```html
<div id="vroom"></div>
<script>
	Automotivated.vroom('#vroom', {
		api: {
			endpoint: 'http://engine.automotivated.nl/api',
			version: 'v1',
			key: 'YOUR_UNIQUE_KEY'
		}
	});
</script>
```

#### Options
`api.endpoint` is the api to talk to<br>
`api.version` is the version of the api<br>
`api.key` is the key that's used for authentication<br>
`overviewCount` is the amount of hits per page<br>
`overviewRendering` is what we default want to start with (`rows` or `grid`)<br>
`debounce` wait with calling the api when this little timer is finished<br>
`availableFilters` orders and enables filters<br>
`language` set the language of the application<br>

A typical integration will look something like this
```html
<div id="vroom"></div>
<script>
	document.addEventListener('DOMContentLoaded', function () {
		if (typeof window.Automotivated.vroom == 'function') {
			Automotivated.vroom('#vroom', {
				api: {
					endpoint: 'http://engine.automotivated.nl/api',
					version: 'v1',
					key: 'YOUR_UNIQUE_KEY'
				},
				overviewCount: 24,
				overviewRendering: 'grid',
				debounce: 400,
				availableFilters: ['keyword', 'fuel', 'price', 'year', 'body', ...],
				language: 'nl'
			});
		}
	});
</script>
```

## [Roadmap](https://www.youtube.com/watch?v=gEPmA3USJdI)
Because we rebooted the project, this list will grow and grow before release. Then we will add a feature list for upcoming releases.
##### v1.0.0
- [x] Setting up the 1.0.0 environment
- [x] Setup CI (travis)
- [x] Setup CD (surge)
- [x] Setup Coveralls
- [x] Setup Code Coverage
- [ ] Start working on documentation
- [ ] Setup gitbook
- [ ] Autodeploy gitbook to surge?
- [x] Get a design from Dezzign
- [ ] Get test coverage as high as necessary
- [x] Internationalization
- [x] History state
- [ ] Add an API [Automotivated.engine( )](https://github.com/Automotivated/engine)
- [x] Create a store module for the app
  - [x] options
  - [x] api
  - [x] global app states
- [ ] Create a store module for the filters
  - [x] Masterdata
  - [x] Active filters
  - [x] Reset filters
  - [ ] Parsing
- [ ] Create a store module for the results
  - [ ] Dummy content
- [ ] Create a store module for the stats
  - [ ] Display (grid/rows)
  - [ ] Size (results per page)
  - [ ] Ordering (asc/desc)
  - [ ] Pagination/offset
-[ ] Components
	- [ ] Mobile
		- [x] Mobile menu
		- [x] Sidebar toggle
		- [ ] Improved media queries
	- [x] Active filters
	- [ ] Filters
	  - [x] Search filter
	  - [x] Multi filter
	  - [ ] Multi-search filter
	  - [x] Range filter
	  - [x] Energylabel filter
	  - [x] Color filter
	- [x] Loading
	- [ ] Modal
		- [ ] Error notifications
	- [ ] Pagination
	- [ ] Grid results
	- [ ] Row results
	- [ ] Sorting
	- [ ] Switch overview rendering
	- [ ] Switch overview count
	- [ ] Detail page

## Resources
- http://vuejs.org/
- http://vuex.vuejs.org/en/intro.html

### For later readings
- http://baymard.com/blog/how-to-design-applied-filters
