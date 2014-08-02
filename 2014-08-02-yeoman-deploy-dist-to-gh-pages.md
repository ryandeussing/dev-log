## deploying `dist` to `gh-pages` within a `gulp-webapp` project

1. npm install --save-dev gulp-subtree

2. create a `deploy` task

```
gulp.task('deploy', ['build'], function () {
    return gulp.src('dist')
        .pipe($.subtree())
        .pipe($.clean());
});
```

3. remove `dist` from `.gitignore`

4. add `CNAME` to the `extras` task (if using custom domain)

```
gulp.task('extras', function () {
  return gulp.src(['app/*.*','app/CNAME', '!app/*.html'], {dot: true})
    .pipe(gulp.dest('dist'));
});
```

5. run `gulp deploy` (builds + deploys!)