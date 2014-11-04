Getting this fun error:

```
/Users/ryandeussing/code/test/node_modules/gulp/node_modules/vinyl-fs/node_modules/vinyl/index.js:153
    if (!this.path) throw new Error('No path specified! Can not get relative.'
                          ^
Error: No path specified! Can not get relative.
    at File.Object.defineProperty.get (/Users/ryandeussing/code/test/node_modules/gulp/node_modules/vinyl-fs/node_modules/vinyl/index.js:153:27)
...
...
```

Turns out it's an error in the `images` task, this is what I did in my `gulpfile.js` (added line with file types):

```
gulp.task('images', function () {
  return gulp.src('app/images/**/*')
    .pipe($.filter('*.{jpg,jpeg,svg,gif,png}'))
    .pipe($.cache($.imagemin({
      progressive: true,
      interlaced: true
    })))
    .pipe(gulp.dest('dist/images'));
});
```