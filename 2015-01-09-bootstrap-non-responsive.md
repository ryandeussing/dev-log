## Stripping responsive behavior for draft site

1. comment out `<meta name="viewport" content="width=device-width">` 
2. change these vars:

```
$screen-xs:                  1px;
$screen-sm:                  2px;
$screen-md:                  3px;
$screen-lg:                  9999px;
```

sample: 

```
// Extra small screen / phone
// Note: Deprecated $screen-xs and $screen-phone as of v3.0.1
$screen-xs:                  1px;
$screen-xs-min:              $screen-xs !default;
$screen-phone:               $screen-xs-min !default;

// Small screen / tablet
// Note: Deprecated $screen-sm and $screen-tablet as of v3.0.1
$screen-sm:                  2px;
$screen-sm-min:              $screen-sm !default;
$screen-tablet:              $screen-sm-min !default;

// Medium screen / desktop
// Note: Deprecated $screen-md and $screen-desktop as of v3.0.1
$screen-md:                  3px;
$screen-md-min:              $screen-md !default;
$screen-desktop:             $screen-md-min !default;

// Large screen / wide desktop
// Note: Deprecated $screen-lg and $screen-lg-desktop as of v3.0.1
$screen-lg:                  9999px;
$screen-lg-min:              $screen-lg !default;
$screen-lg-desktop:          $screen-lg-min !default;

// So media queries don't overlap when required, provide a maximum
$screen-xs-max:              ($screen-sm-min - 1) !default;
$screen-sm-max:              ($screen-md-min - 1) !default;
$screen-md-max:              ($screen-lg-min - 1) !default;
```

3. in html, use only `col-xs` classes