## grunt indent

to change 4-spaces to 2-spaces after scaffolding with `yo webapp`:

- `npm install grunt-indent --save-dev`
- `grunt.loadNpmTasks('grunt-indent');` in `Gruntfile`
- add `indent` to `grunt.registerTask` function in `Gruntfile`

- add this to `gruntInitConfig` function:

```
indent: {
          scripts: {
            src: [
              'app/scripts/*.js', 'app/styles/*.scss', '*app/*.html'
            ],
            dest: 'dist/',
            options: {
              style: 'space',
              size: 2,
              change: -1
            }
          }
        },
```
- run `grunt indent`
- maunally tweak/move files

Actually I bet I should register the `indent` task separately, so it's not run on every `grunt build`!

## mixins for breakpoint content-blocks

```
// ----- MIXINS WITH CONTENT BLOCKS  -----

@mixin phone {
  @media (max-width : $screen-xs-max) {
    @content;
  }
}

@mixin tablet {
  @media (min-width : $screen-sm) and (max-width : $screen-sm-max) {
    @content;
  }
}

@mixin tablet-and-up {
  @media (min-width : $screen-sm) {
    @content;
  }
}

@mixin desktop {
  @media (min-width : $screen-md) and (max-width : $screen-md-max) {
    @content;
  }
}

@mixin desktop-and-up {
  @media (min-width : $screen-md) {
    @content;
  }
}

@mixin widescreen {
  @media (min-width : $screen-lg) {
    @content;
  }
}
```

## add `_vars.scss` partial to override Bootstrap vars as needed
