## Updating NPM with permission errors

1 -  Reset `/usr/local` permissions ala [this post](http://www.daigo.org/2013/11/installing-npm-on-mavericks-macbook-pro/):

```
This is a permissions issue and the fix, courtesy of Tim Schaub, is to recursively change the owner of the files in your /usr/local folder to the current user:

sudo chown -R $USER /usr/local
```
2 -  Downloaded & reinstalled node.js

3 - Uninstalled hombrew node.js, repeat 2 above

4 - Bower was mysteriously not installed by Yeoman, so I manually installed it `npm install bower -g`

5 - re-ran `yo webapp` and all good