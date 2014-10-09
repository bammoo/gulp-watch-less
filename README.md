# [gulp](http://gulpjs.com)-watch-less [![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Coverage Status][coveralls-image]][coveralls-url] [![Dependency Status][depstat-image]][depstat-url]
> Watch .less files and their @imports using the [gulp-watch][watch] endless stream task

## Install

```sh
$ npm install --save-dev gulp-watch-less
```


## Usage

```js
var gulp = require('gulp');
var watchLess = require('gulp-watch-less');
var less = require('gulp-less');

gulp.task('default', function () {
	return gulp.src('less/file.less')
		.pipe(watchLess('less/file.less'))
		.pipe(less())
		.pipe(gulp.dest('dist'));
});
```

> __Protip:__ until gulpjs 4.0 is released, you can use [gulp-plumber][plumber] to prevent stops on errors.


## API

### GulpWatchLess(glob, [options, callback])

Creates watcher that will spy on files that were matched by glob which can be a [`node-glob`][glob-url] string or array of strings.

**This will also watch all traced `@import` dependencies of the matched files, and re-emit a change event when any of them change**.
In this case, the `file.event` will be equal to `changed:by:import` for easy distinction.

Returns pass-through stream, that will emit vinyl files (with additional `event` property) that corresponds to event on file-system.

#### Callback `function(events, done)`

See documentation on [gulp-watch][watch] task

#### options

See documentation on [gulp-watch][watch] task

##### options.less

Type: `object`  
Default: `{}`

*Optional* options passed through to the [less]().Parser instance.

## License

MIT &copy; [Craig Michael Thompson][profile-url]


[profile-url]: https://github.com/Craga89

[glob-url]: https://github.com/isaacs/node-glob
[less-url]: https://github.com/less/less.js
[watch-url]: https://github.com/floatdrop/gulp-watch
[plumber-url]: https://github.com/floatdrop/gulp-plumber

[npm-url]: https://npmjs.org/package/gulp-watch
[npm-image]: http://img.shields.io/npm/v/gulp-watch.svg?style=flat

[travis-url]: https://travis-ci.org/floatdrop/gulp-watch
[travis-image]: http://img.shields.io/travis/floatdrop/gulp-watch.svg?style=flat

[coveralls-url]: https://coveralls.io/r/floatdrop/gulp-watch
[coveralls-image]: http://img.shields.io/coveralls/floatdrop/gulp-watch.svg?style=flat

[depstat-url]: https://david-dm.org/floatdrop/gulp-watch
[depstat-image]: http://img.shields.io/david/floatdrop/gulp-watch.svg?style=flat