## old school way
- create an `orphan` branch called gh-pages
- start with a fresh clone
- then `git checkout --orphan gh-pages` and `git rm -rf .`
- then add assets for gh-pages and `git push origin gh-pages`

## yeoman way 
`grunt build` and if you get errors see this: https://github.com/Modernizr/grunt-modernizr/issues/48

deploy only the `dist` folder using `git subtree` http://yeoman.io/deployment.html

- remove the dist directory from the .gitignore file
- `git add dist && git commit -m "Initial dist subtree commit"`
- deploy the subtree to a different branch - specify a relative path to your dist directory with `--prefix`
```
git subtree push --prefix dist origin gh-pages
``` 
- commit regular dev changes to `master`, and re-use the above command when you want to push `dist` to `gh-pages` **no need to switch branches**

now a snippet: `gh-preview`