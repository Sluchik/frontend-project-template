# Frontend Project Template

A small framework-agnostic project template for front-end web apps and sites.


## Contents

### Main folders

* `/dist`  The build folder
* `/docs`  Documentation
* `/src`   Unminified source files
* `/tasks` Individual build tasks
* `/test`  Unit Test specifications

### Directory Structure

```
├── dist
├── docs
├── src
│   ├── components
│   ├── styles
│   │   ├── fonts
│   │   ├── elements.css
│   │   ├── fonts.css
│   │   ├── media.css
│   │   ├── props.css
│   │   ├── sections.css
│   │   └── utils.css
│   ├── utils
│   │   └── modernizr
│   │       └── modernizr.js
│   ├── views
│   ├── favicon.ico
│   ├── index.css
│   ├── index.html
│   ├── index.js
│   └── robots.txt
├── tasks
│   ├── helpers
│   │   ├── is-production.js
│   │   └── logError.js
│   ├── audio.js
│   ├── connect.js
│   ├── html.js
│   ├── images.js
│   ├── scripts.js
│   ├── static.js
│   └── styles.js
├── test
│   └── test.spec.js
├── .editorconfig
├── .eslintrc
├── .gitattributes
├── .gitignore
├── .stylelintrc
├── gulpfile.js
├── karma.conf.js
├── package.json
└── README.md
```

`.gitignore` files are used to include some otherwise empty directories in the repository in order to define a reusable project structure.


## Set up

### Prerequisites

* [Node](http://nodejs.org/)
* [Gulp](http://gulpjs.com/)
* [Browserify](http://browserify.org/)
* [Karma](http://karma-runner.github.io/)

### Getting started

From a terminal or command prompt at the project root run:

```shell
$ npm install
```

### HTML

Only an index page is included in the default HTML structure, in `src/index.html`. By default, `lodash` template variables are used to configure a static index page which is written to `dist/index.html`.

### CSS

The default CSS structure and build is based on [SUIT CSS](https://github.com/suitcss/) conventions. [Normalize](http://necolas.github.io/normalize.css/) and [SUIT base](https://github.com/suitcss/base/) are included as a basis for the project CSS.

Base styles and utilities are included in `src/styles/`. All other CSS files are in their respective component folders.

[PostCSS](https://github.com/postcss/postcss) transpiles the CSS to support future syntax and vendor prefixes.

### JS

Polyfills and utilities are included in `src/utils/`. All other JS files are in their respective component folders.

#### Babel

[Babel](https://babeljs.io/) is included to transpile es6/7. The default presets are es2015 and stage-0.

#### vendor.js

A separate `vendor.js` file can be built by configuring the vendor section in `package.json`. For example:

```shell
"vendor": {
    "lodash": "lodash",
    "threejs": "./src/vendor/threejs/three.js"
}
```

#### Modernizr

A [simple modernizr version](http://modernizr.com/download?-touchevents-addtest-setclasses-testprop-dontmin-cssclassprefix:Modernizr-) is included in the project in `src/utils/modernizr/`. It includes the standard HTML5 shim/shiv, CSSClasses, testProp and addTest. It also includes `touchevents` to exclude hover states from mobile devices. Modernizr CSS classNames are prefixed with `Modernizr-` to make them easy to recognise.

#### Lodash

[Lodash](https://lodash.com/) is included by default and is used for basic configuration of the `index.html` page.

### Assets

Static assets such as icons are included in their respective component folder in `src/components`. They are optimised and copied into folders in `dist/img` as part of the build process.

## Usage

### Building

Gulp is used to run the build tasks for the project. The tasks are all defined in `gulpfile.js`, while the corresponding functions are in the `tasks` directory. Paths/globs for `gulp.src` and `gulp.dest` are defined in `package.json`.

Starts the connect, build and watch tasks:

```shell
$ gulp
```

Processes assets and builds CSS and JS bundles, uglified and cleaned of debug logs and sourcemaps:

```shell
$ gulp build --min
or
$ gulp build --prod
```
Individual tasks:

```shell
# Builds the JS, CSS, static files and images to `dist` then exits:
$ gulp build

# Starts a simple web server that reloads when changes are made:
$ gulp connect

# Rebuilds bundles automatically when changes are made:
$ gulp watch

# Builds CSS bundle to `dist/css/styles.css`:
$ gulp css

# Builds JS bundle to `dist/js/bundle.js`:
$ gulp js

# Builds vendor JS bundle to `dist/js/vendor.js`:
$ gulp vendor

# Copies modernizr.js to `dist/js`:
$ gulp modernizr

# Renders HTML templates and copies to `dist`:
$ gulp html

# Copies static files to `dist`:
$ gulp static

# Minifies and copies images to `dist/img`, creating WebP versions:
$ gulp images

# Converts and copies audio files to `dist/audio`:
$ gulp audio

```

### Linting

[ESLint](http://eslint.org/) and [stylelint](http://stylelint.io/) are setup to lint the working files in `src/`. Rules can be configured by editing the `.eslintrc` and `.stylelintrc` files in the project root.

```shell
$ gulp lint
$ gulp js:lint
$ gulp css:lint
```

A detailed report highlighting any problems will be output to the console.

### Testing

A testing set up is included, utilising the [Karma](https://github.com/karma-runner/karma) test runner, [Mocha](http://visionmedia.github.io/mocha/) framework and [Chai](http://chaijs.com/) assertion library.

```shell
$ npm install -g karma-cli
$ karma start
```
A report highlighting any failed test will be output to the console. Karma will keep running until the task is terminated and will rerun the tests when files are saved.
