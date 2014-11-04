Was getting weird permission errors when tryign to `npm install && npm link` yeoman `generator` and `generator-gulp-webapp` repos.

solution: `sudo chown -R $USER /usr/local`