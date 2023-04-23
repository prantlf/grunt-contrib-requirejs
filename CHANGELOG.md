## [2.0.1](https://github.com/prantlf/grunt-contrib-requirejs/compare/v2.0.0...v2.0.1) (2023-04-23)


### Bug Fixes

* Upgrade dependencies ([35855ee](https://github.com/prantlf/grunt-contrib-requirejs/commit/35855ee3a981125c2eb871d1017129d5221f9158))

# [2.0.0](https://github.com/prantlf/grunt-contrib-requirejs/compare/v1.1.0...v2.0.0) (2023-04-23)


### Features

* Replace requirejs with @prantlf/requirejs ([8445751](https://github.com/prantlf/grunt-contrib-requirejs/commit/844575154d4191a9e417572b972f2ab2d5a57f78))


### BREAKING CHANGES

* The package @prantlf/requirejs with a modern JvaScript parser and source map support is used by default now. Although it supports all features of requirejs and the existing scenarios should not be broken, the parser replacement might have some side-effects. You should test that everything works after the upgrade.

## [1.1.0](https://github.com/prantlf/grunt-contrib-requirejs/compare/v1.0.0...v1.1.0) (2022-01-03)

### Features

* Do not append the .js extension to module names relative to the current path ([8f93a0e](https://github.com/prantlf/requirejs-babel/commit/8f93a0e60f2eb96cd16aafd4a46de90a409f0b1b))
* Do not transpile source files already in the AMD format ([919a891](https://github.com/prantlf/requirejs-babel/commit/919a89195d7019cfddebc18b4580a3f3b71a0a16))
* Propagate errors from loading missing files ([d69c42d](https://github.com/prantlf/requirejs-babel/commit/d69c42d2d45e0c3b8e1441485bd2b5669f0a84da))


This is the first release after forking the project.

## 1.0.0

    v1.0.0:
      date: 2016-03-04
      changes:
        - Update usage example to show a working usage.
        - Remove peerDep and point to main task.
        - rjs-build-analysis returns an object not an array.
        - Made clear that usage of almond is not required.
        - Added error option to handle r.js errors.
    v0.4.4:
      date: 2014-04-25
      changes:
        - Reduce logging verbosity unless `--verbose` flag is used.
    v0.4.3:
      date: 2014-02-26
      changes:
        - Remove "Gruntfile.js" as package.json main.
    v0.4.2:
      date: 2014-02-26
      changes:
        - Catch exceptions in `done`.
    v0.4.1:
      date: 2013-05-16
      changes:
        - Add `done` option.
    v0.4.0:
      date: 2013-02-15
      changes:
        - First official release for Grunt 0.4.0.
    v0.4.0rc7:
      date: 2013-01-23
      changes:
        - Updating to work with grunt v0.4.0rc7.
    v0.4.0rc5:
      date: 2013-01-09
      changes:
        - Updating to work with grunt v0.4.0rc5.
    v0.3.3:
      date: 2012-10-12
      changes:
        - Rename grunt-contrib-lib dep to grunt-lib-contrib.
    v0.3.1:
      date: 2012-10-09
      changes:
        - Bump to RequireJS 2.1.x.
        - Run optimizer async.
    v0.3.0:
      date: 2012-09-23
      changes:
        - Options no longer accepted from global config key.
    v0.2.0:
      date: 2012-09-10
      changes:
        - Refactored from grunt-contrib into individual repo.
