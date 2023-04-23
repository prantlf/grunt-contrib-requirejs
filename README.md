# @prantlf/grunt-contrib-requirejs

[![Latest version](https://img.shields.io/npm/v/@prantlf/grunt-contrib-requirejs)
 ![Dependency status](https://img.shields.io/librariesio/release/npm/@prantlf/grunt-contrib-requirejs)
](https://www.npmjs.com/package/@prantlf/grunt-contrib-requirejs)

> Optimize RequireJS projects using r.js. Forked to use a custom r.js module.

Changes made in this fork:

* A new option `requirejs` allows passing a custom build of `r.js` to the task.
* A new option `force` suppresses failures and lets other tasks continue if the current one failes.
* A new option `verbose` enables verbose logging of `r.js` in addition to the command line option.

## Getting Started

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install @prantlf/grunt-contrib-requirejs --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('@prantlf/grunt-contrib-requirejs');
```

*This plugin was designed to work with Grunt 0.4.x. If you're still using grunt v0.3.x it's strongly recommended that [you upgrade](http://gruntjs.com/upgrading-from-0.3-to-0.4), but in case you can't please use [v0.3.3](https://github.com/gruntjs/grunt-contrib-requirejs/tree/grunt-0.3-stable).*

## Requirejs task

_Run this task with the `grunt requirejs` command._

Task targets and options may be specified according to the grunt [Configuring tasks](http://gruntjs.com/configuring-tasks) guide.

# Options

For a full list of possible options, [see the r.js example build file](https://github.com/jrburke/r.js/blob/master/build/example.build.js).

## done(done, build)

The `done` option is an optional hook to receive the `r.js` build output. The first argument is the grunt async callback that you are required to call if you provide the `done` hook. This informs grunt that the task is complete. The second parameter is the build output from `r.js`.

## error(done, error)

The `error` option is an optional hook to receive the `r.js` error. The first argument is the grunt async callback that you are required to call if you provide the `done` hook. This informs grunt that the task is complete. The second parameter is the error instance thrown from `r.js` in case of failure.

## requirejs

The `requirejs` option is an object exported from a module compatible with `r.js`. You can pass an alternative optimizer version to the task by this option. The module `requirejs` is used by `require('requirejs')` by default.

## logLevel

The `logLevel` option is a number to be passed to the `r.js` as the log level. The values can be 0 (tracing), 1 (information), 2 (warning) or 3 (error). The default if 2 (warning).

## verbose

The `verbose` option is a boolean to enable logging at the level 0 (tracing) if set to `true`. The default is `false`.

## force

The `force` option is a boolean, which if set to `true`, forces the grunt running and executing further tasks, although the current task failed. The default is `false`.

### Usage Examples

```js
requirejs: {
  compile: {
    options: {
      baseUrl: 'path/to/base',
      mainConfigFile: 'path/to/config.js',
      name: 'path/to/almond', /* assumes a production build using almond, if you don't use almond, you
                                 need to set the "includes" or "modules" option instead of name */
      include: [ 'src/main.js' ],
      out: 'path/to/optimized.js'
    }
  }
}
```

#### Done

```js
requirejs: {
  compile: {
    options: {
      baseUrl: 'path/to/base',
      mainConfigFile: 'path/to/config.js',
      done: function(done, output) {
        var duplicates = require('rjs-build-analysis').duplicates(output);

        if (Object.keys(duplicates).length) {
          grunt.log.subhead('Duplicates found in requirejs build:');
          grunt.log.warn(duplicates);
          return done(new Error('r.js built duplicate modules, please check the excludes option.'));
        }

        done();
      }
    }
  }
}
```

#### Error

```js
requirejs: {
  compile: {
    options: {
      baseUrl: 'path/to/base',
      mainConfigFile: 'path/to/config.js',
      error: function(done, err) {
        grunt.log.warn(err);
        done();
      }
    }
  }
}
```

#### Requirejs

```js
requirejs: {
  compile: {
    options: {
      requirejs: require('@my/requirejs'),
      baseUrl: 'path/to/base',
      mainConfigFile: 'path/to/config.js',
      include: [ 'src/main.js' ],
      out: 'path/to/optimized.js'
    }
  }
}
```

## License

Copyright (c) 2012-2016 Tyler Kellen, contributors<br>
Copyright (c) 2021-2023 Ferdinand Prantl

Licensed under the MIT license.
