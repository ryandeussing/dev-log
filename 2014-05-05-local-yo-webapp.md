## Every time I want to use `yo-webapp` I need to do this

`cd generator-webapp`

`git pull origin master`

Why? Because I did this when I needed a pre-release version:

```
$ git clone https://github.com/yeoman/generator-webapp
$ cd generator-webapp
$ npm link
```

Now yo webapp will use the latest version, i.e. from the `generator-webapp` directory.