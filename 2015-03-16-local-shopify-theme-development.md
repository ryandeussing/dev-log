## it sucks

• `gem install shopify_theme`

requires ruby 1.9

`theme watch` will upload changed/added assets to the live site, like it's 1996

tip: use the theme id of an inacitve theme, and watch changes in the `preview theme` windoe

• `npm install gulp-cssimport`

use this if you want to `@import` files from different directories locally

instructions here: http://shopify.github.io/shopify-css-import/

use the gulpfile below for scss:

```
// https://github.com/unlight/gulp-cssimport
var gulp = require('gulp');
var cssimport = require("gulp-cssimport");

var globalConfig = {
  src: 'app/styles' // your dev stylesheet directory. No trailing slash
};

// Process CSS
gulp.task('styles', function(){
  return gulp.src(globalConfig.src + '/**/*.*')
    .pipe(cssimport())
    .pipe(gulp.dest('assets/'));
})

// Watch files
gulp.task('watch', function () {
  gulp.watch(globalConfig.src + '/**/*.*', ['styles']);
});

// Default task
gulp.task('default', ['watch']);
```