### 2014-04-06
- removed `generator-webapp` manually, b/c I had copied in code from github last time to get the latest before it was released
    
    git clone https://github.com/yeoman/generator-webapp
    cd generator-webapp
    npm link

Now `yo webapp` will use the latest version, i.e. from the generator-webapp directory. Then each time you want to update the generator, just navigate to generator-webapp, git pull origin master.

### 2014-03-31
- was getting weird npm errors, including on `npm update`, so I removed npm files and reintalled node using the installer. fixed.

### 2014-03-25
- reinstalled yo-webapp from scratch, using ruby compass gem for now...

### 2014-03-24
- turns out .scss files are not compiling, and that I prob want to use grunt-contrib-sass (libsass is not ready for primetime)
- there's a PR for using SASS without compass, gotta wait for it to be accepted...

### the goal here is to use yeoman + bootstrap to create a SiteLeaf theme

- re-installed yeoman (perhaps `npm update` would have worked)
- used the updated `yo webapp` generator, chose `bootstrap` but not `sass/compass`
- installed `grunt-sass` and added `grunt.loadNpmTasks('grunt-sass');` to my gruntfile

So now I'm not using Compass and can't lean on its functions, but I never really did.

### note: https://github.com/yeoman/generator-webapp/issues/302

Next: I'll see how I can set things up for a SiteLeaf theme within this Yeoman app.

Actually, that's not going to work. I'll need to take steps:
1. design statically using 'grunt-serve' which is crazy-fast
2. then decide which elements map to SiteLeaf assets
3. then recreate the site as a SiteLeaf theme, using assets
4. from then on, use `site-leaf-gem` and `pow` to work on site


