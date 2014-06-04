When using gulp...you can use [this](https://github.com/yeoman/generator-gulp-webapp/blob/master/docs/recipes/gh-pages.md)

1. `npm install --save-dev gulp-subtree`

2. create a `deploy` task:

```
gulp.task('deploy', ['build'], function () {
    return gulp.src('dist')
        .pipe($.subtree())
        .pipe($.clean());
});
```

3. remove `dist` from `.gitignore`


Voila! Now you just run `gulp deploy` to push `dist` to `gh-pages`

