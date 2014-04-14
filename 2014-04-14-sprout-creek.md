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

