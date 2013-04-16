# grunt-csscss

[![Build Status](https://secure.travis-ci.org/peterkeating/grunt-csscss.png?branch=master)](http://travis-ci.org/peterkeating/grunt-csscss)

Grunt task that runs [CSSCSS](http://zmoazeni.github.io/csscss/), a CSS redundancy analyzer.

## CSSCSS

CSSCSS runs on Ruby (`v1.9.x` and up), to check Ruby is installed on your machine use `ruby -v`. To install the CSSCSS gem run `gem install csscss` command, this will grab the latest version.

Currently grunt-csscss handles all the features for CSSCSS that are available with version **1.2.0**.

## Getting Started

This plugin requires Grunt `~0.4.0`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-csscss --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-csscss');
```
## Options

### colorize

Type: `Boolean`
Default: `true`

Flag indicating whether the outputted analysis should be colorized.

### compass

Type: `Boolean`
Default: `false`

Enables Compass extensions when parsing Sass.

*[Compass](http://compass-style.org/) must be installed in order to use this option.*

### compassConfig

Type: `String`

Enables Compass extension and specifies path to a config file.

*[Compass](http://compass-style.org/) must be installed in order to use this option.*

### failWhenDuplicates

Type: `Boolean`
Default: `false`

Flag indicating whether the Grunt task should fail when rule sets with duplicate declarations are found by CSSCSS.

### ignoreProperties

Type: `String`

Comma seperated list of CSS properties that should be ignored when finding matches.

### ignoreSelectors

Type: `String`

Comma seperated list of selectors that should be ignored when finding matches.

### minMatch

Type: `Number`
Default: `3`

Only report matches that have at least this many matching rules.

### outputJson

Type: `Boolean`
Default: `false`

Output analysis in JSON format.

### shorthand

Type: `Boolean`
Default: `true`

Whether shorthand CSS declaration should be parsed. Check [here for a great explanation](https://github.com/zmoazeni/csscss/pull/20) of this option.

### showParserErrors

Type: `Boolean`
Default: `false`

Outputs parser errors.

### verbose

Type: `Boolean`
Default: `false`

Displays the CSS properties that have been matched.

## Examples

### Configuration Example

Basic example of a Grunt config containing the CSSCSS task.
```js
grunt.initConfig({
  csscss: {
    dist: {
      src: ['css/style.css']
    }
  }
});

grunt.loadNpmTasks('grunt-csscss');

grunt.registerTask('default', ['csscss']);
```

### Multiple Files

Running CSSCSS against multiple CSS files. All the files specified in the `src` array will be analyzed by CSSCSS.
```js
csscss: {
  dist: {
    src: ['css/style.css', 'css/another.css']
  }
}
```

### Specifying Options

Example of using the [options](https://github.com/peterkeating/grunt-csscss/edit/master/README.md#options).

```js
csscss: {
  options: {
    colorize: false,
    verbose: true,
    outputJson: false,
    minMatch: 2,
    compass: true,
    ignoreProperties: 'padding',
    ignoreSelectors: '.rule-a'
  },
  dist: {
    src: ['css/style.css', 'css/another.css']
  }
}
```

### Analyzing Compass Stylesheet

Example of using CSSCSS to analyze Sass files that are converted using Compass.

```js
csscss: {
  options: {
    compassConfig: 'my/config/file/config.rb'
  },
  dist: {
    src: ['sass/style.scss']
  }
}
```

## Release History

### 0.2.0 (April 13th 2013)

* Added `showParserErrors` option to output parser errors.
* Added `shorthand` option to determined whether shorthand should be parsed.
* Added `compassConfig` option to specify path to Compass config file.

### 0.1.0 (April 12th 2013)

* Initial release supporting all options for CSSCSS v1.0.0.

## Credits

All credit goes to [Zach Moazeni](https://github.com/zmoazeni) for his brilliant work on [CSSCSS](https://github.com/zmoazeni/csscss), great job Zach!
