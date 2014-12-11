Not sure why this isn't part of Bootstrap, but here it is:

    @mixin breakpoint($min: 0, $max: 0) {
      $type: type-of($min);
      @if $type == string {
        @if $min == xxs {
          @media (min-width: 1px) { @content; }
        }
        @else if $min == xs {
          @media (min-width: 480px) { @content; }
        }
        @else if $min == sm {
          @media (min-width: 768px) { @content; }
        }
        @else if $min == md {
          @media (min-width: 992px) { @content; }
        }
        @else if $min == lg {
          @media (min-width: 1200px) { @content; }
        }
        @else {
          @warn "Breakpoint mixin supports: xs, sm, md, lg";
        }
      }
      @else if $type == number {
        $query: "all" !default;
        @if $min != 0 and $max != 0 {
          $query: "(min-width: #{$min}) and (max-width: #{$max})";
        }
        @else if $min != 0 and $max == 0 {
          $query: "(min-width: #{$min})";
        }
        @else if $min == 0 and $max != 0 {
          $query: "(max-width: #{$max})";
        }
        @media #{$query} {
          @content;
        }
      }
    }
    
Now you can do this to test it out:

    body {
      @include breakpoint(xxs) {
        background-color: red;
      }
      @include breakpoint(xs) {
        background-color: blue;
      }
      @include breakpoint(sm) {
        background-color: orange;
      }
      @include breakpoint(lg) {
        background-color: yellow;
      }
    }