When running `gulp`, the relative paths no longer work in the css file saved to `dist`.

Here's the solution I came up with:

In `gulfile.js`:

1. add `var replace = require('gulp-replace');` under `load plugins`

2. add a replace step to the `html` task:

```javascript
    return gulp.src('app/*.html')
        // yada yada yada
        // yada yada yada
        .pipe(replace('bower_components/bootstrap-sass-official/vendor/assets/fonts/bootstrap/', 'fonts/'))
        .pipe(gulp.dest('dist'))
        // yada yada yada
});
```

Now when I run `gulp`, the relative paths are changed before the css file is saved to `dist`