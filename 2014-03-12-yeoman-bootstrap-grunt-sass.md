## the goal here is to use yeoman + bootstrap to create a SiteLeaf theme

- re-installed yeoman (perhaps `npm update` would have worked)
- used the updated `yo webapp` generator, chose `bootstrap` but not `sass/compass`
- installed `grunt-sass` and added `grunt.loadNpmTasks('grunt-sass');` to my gruntfile

So now I'm not using Compass and can't lean on its functions, but I never really did.

## note: https://github.com/yeoman/generator-webapp/issues/302

Next: I'll see how I can set things up for a SiteLeaf theme within this Yeoman app.

Actually, that's not going to work. I'll need to take steps:
1. design statically using 'grunt-serve' which is crazy-fast
2. then decide which elements map to SiteLeaf assets
3. then recreate the site as a SiteLeaf theme, using assets
4. from then on, use `site-leaf-gem` and `pow` to work on site



