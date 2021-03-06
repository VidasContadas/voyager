# Voyager

[![Build Status](https://travis-ci.org/vega/voyager.svg)](https://travis-ci.org/vega/voyager)

Voyager is a visualization browser for data analysis, building on top of [Vega-Lite](https://github.com/vega/vega-lite).
Try our [online demo](http://vega.github.io/voyager/). Also, be sure to check out [related projects](https://vega.github.io/).

**This project is an [alpha](http://en.wikipedia.org/wiki/Software_release_life_cycle#Alpha) software.
We are working on improving its code and documentation.**

If you are using Voyager for your project(s), please let us know what are you using it for by emailing us at [Vega-Lite \[at\] cs.washington.edu](mailto:vega-lite@cs.washington.edu).  Feedbacks are also welcomed.
If you find a bug or have a feature request, please take a look a [the issue tracker](https://github.com/vega/voyager/issues/) and [create an issue](https://github.com/vega/voyager/issues/new) if there is no existing issue.

## Setup Instruction

First clone this repository by running

```
git clone https://github.com/vega/voyager
```

### Install Dependencies

Make sure you have node.js. (We recommend using [homebrew](http://brew.sh) and simply run `brew install node`.)

Then, `cd` into your local clone of this repository, and install all the dependencies (bower dependencies will auto-install once the npm install completes):

```sh
cd voyager
npm install
```

Now you should have all dependencies and should be ready to work.

Note: Bower is used in this project to manage client-side dependencies. The necessary bower packages will auto-install when `npm install` completes. To manage bower dependencies, install bower globally as detailed in the [Dependencies development guide](#dependencies) below.

### Running

You can run `npm start`, which serves the site as well as running tests in the background.
If you edit any file, our gulp task runner should automatically refresh the browser and re-run tests.

## Development Guide

### Folder Structure

We try to follow [Google's Angular Best Practice for Angular App Structure](https://docs.google.com/document/d/1XXMvReO8-Awi1EZXAXS4PzDzdNvV6pGcuaF4Q9821Es/pub) and use [generator-gulp-angular](https://github.com/Swiip/generator-gulp-angular) to setup the project.

All source code are under `src/`

- `src/app/` contains our main classes
- `src/components` contains our other components
- `src/assets/images/` contains relevant images
- `src/data/` contains all data that we use in the application
- `src/vendor` contains

@kanitw has created [`gulp/gen.js`](gulp/gen.js) for help generating angular components.
For example, you can run `gulp gen -d directiveName` (requires gulp to be installed globally) and this would create all relevant files including the javascript file, the template file, the stylesheet file and the test spec.

#### Coding Style

We use jshint as our linter for coding in the project.

#### Stylesheets

We use [sass](http://sass-lang.com) as it is a better syntax for css.

#### Dependencies

Managing front-end dependencies with [Bower](http://bower.io) requires the `bower` package to be globally installed:
```sh
npm install -g bower
```

This project depends on [Datalib](https://github.com/vega/datalib) for data processing, [Vega-Lite](https://github.com/vega/vega-lite) as a formal model for visualization, and [Vega-Lite-ui](https://github.com/vega/vega-lite-ui), which contains shared components between Polestar and Voyager.

If you plan to make changes to these dependencies and observe the changes without publishing / copying compiled libraries all the time, use [`bower link`](https://oncletom.io/2013/live-development-bower-component/).

In each of your dependency repositories, run

```sh
cd path/to/dependency-repo
bower link
```

Then go to your this project's directory and run

```sh
bower link datalib
bower link vega-lite
bower link vega-lite-ui
bower link viscompass
```

Now all the local changes you make in each repo will be reflected in Voyager automatically.

Since bower uses the compiled main file, make sure that each linked repo is compiled everytime you run `npm start`.
Otherwise, you will get errors for missing libraries or undefined globals.

### Releasing / Github Pages

`gh-pages` branch is for releasing a stable version.
`gh-pages` should only contain the dist folder.

Use `publish.sh` to:

1. publish the current version to npm
2. deploy the current branch to gh-pages and
3. create a release tag for github and bower.

## Acknowledgement

Voyager's development is led by Kanit Wongsuphasawat, Dominik Moritz, and Jeffrey Heer at the University of Washington [Interactive Data Lab](http://idl.cs.washington.edu), in collaboration with [UW eScience Institute](http://escience.washington.edu/), [Tableau Research](http://research.tableau.com) and [Bocoup](https://bocoup.com/). 

We used [generator-gulp-angular](https://github.com/Swiip/generator-gulp-angular) for bootstrapping our project.

