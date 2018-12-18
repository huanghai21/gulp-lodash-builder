# gulp-lodash-builder-fix  
> A tool to create a customised version of lodash 
This is a folk version of [gulp-lodash-builder](https://github.com/OneLittleRobot/gulp-lodash-builder);
Fixed 2 issues:
 1. `lodash` script not work properly with the `execFile` way.
 2. remove the build.option `compat`. It's a invalid argument for lodash-cli.

## Usage

Install `gulp-lodash-builder-fix` as a development dependency:

```shell
$ npm install --save-dev gulp-lodash-builder-fix
```

Then, add it to your `gulpfile.js`:

### Gulp Example
```javascript
var gulp = require('gulp');
var lodashBuilder = require('gulp-lodash-builder-fix');

var options = {
  target: "/assets/javascript/vendor/lodash.custom.js",
  settings: {}
};
gulp.task('lodash', function (cb) {
  return gulp.src("/assets/javascript/src/**", {buffer: false})
    .pipe(lodashBuilder(options))
    .on('error', function (err) {
      console.log('err: ', err)
    })
});
```

## Options

### target

`String` - Where to output the custom build lodash file.

### build

`String` - Which custom lodash build to use. Build types: `compat`, `modern`, `strict`, `modularize`. See [Lodash Custom Builds](https://lodash.com/custom-builds) for details on build options.

### settings

`Object` - Sent to Lodash CLI as `settings` for precompiling templates. See [Lodash Custom Builds](https://lodash.com/custom-builds) for more details.
