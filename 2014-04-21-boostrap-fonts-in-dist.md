## A New Post

Something's screwy with with the way Bootstrap's fonts are handled during `grunt build`. I fixed it thusly:

1. In `main.scss`, make the `$icon-font-path:` relative:
  
  ```
  $icon-font-path: "../bower_components/bootstrap-sass-official/vendor/assets/fonts/bootstrap/";
  ```

2. In `.gitgnore`, change `bower_components` to `/bower_components`

2014-05-05 update:

When using `yo-webapp` you need to manually copy bootstrap/s font files to `styles/fonts` - they can be found at ``
