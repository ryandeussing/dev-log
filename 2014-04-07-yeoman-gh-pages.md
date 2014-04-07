## old school way (i did this)
- create an `orphan` branch called gh-pages
- start with a fresh clone
- then `git checkout --orphan gh-pages` and `git rm -rf .`
- then add assets for gh-pages and `git push origin gh-pages`

## yeoman way (to try next time)
- deploy only the dist folder using `git subtree` http://yeoman.io/deployment.html