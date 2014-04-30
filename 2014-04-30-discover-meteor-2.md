## Templates

Templates go in a `views` directory for organization's sake, but Meteor will actually find files anywhere in the `client` directory - templates, css, js, etc.

`main.html` will include a `postsList` template:

```
    <div id="main" class="row-fluid">
      {{> postsList}}
    </div>
```

the `postsList` template (in `views`) will look like this:

```
<template name="postsList">
  <div class="posts">
    {{#each posts}}
      {{> postItem}}
    {{/each}}
  </div>
</template>
```
note: the `posts` object will come from a `template manager` (`posts_list.js`)

and the `postItem` template will look like this:

```
<template name="postItem">
  <div class="post">
    <div class="post-content">
      <h3><a href="{{url}}">{{title}}</a><span>{{domain}}</span></h3>
    </div>
  </div>
</template>
```

note: `domain` is a helper method, while `url` and `title` are properties

## Template Managers & Helpers

Not quite a controller, but does similar work: provides data for the view.

`client/views/posts/posts_list.js`:

```
var postsData = [
  {
    title: 'Introducing Telescope',
    author: 'Sacha Greif',
    url: 'http://sachagreif.com/introducing-telescope/'
  }, 
  {
    title: 'Meteor',
    author: 'Tom Coleman',
    url: 'http://meteor.com'
  }, 
  {
    title: 'The Meteor Book',
    author: 'Tom Coleman',
    url: 'http://themeteorbook.com'
  }
];
Template.postsList.helpers({
  posts: postsData
});
```

The last part is what makes the `posts` data available in the `postsList` view. It defines a *template helper* called `posts` (that just returns our array of placeholder data).

`Template.myTemplate.helpers()` is a Meteor function that allows you to create template-specific helpers.

Note: within each iteration of an `{{#each}}` block, the value of `this` is assigned to the current object being iterated. That's true for code in the template manager and template helpers:

```
Template.postItem.helpers({
  domain: function() {
    var a = document.createElement('a');
    a.href = this.url; // the current post
    return a.hostname;
  }
});
```