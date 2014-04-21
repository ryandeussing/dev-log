## A New Post

Something's screwy with with the way Bootstrap's fonts are handled during `grunt build`. I fixed it thusly:

1. In `main.scss`, make the `$icon-font-path:` relative:
  
  ```
  $icon-font-path: "../bower_components/bootstrap-sass-official/vendor/assets/fonts/bootstrap/";
  ```

2. In `.gitgnore`, change `bower_components` to `/bower_components`
