```
// in server/start.js

if (Meteor.isServer) {
  Meteor.startup(function() {
    return Meteor.methods({
      removeAllPosts: function() {
        return Posts.remove({});
      }
    });
  });
}
```


`Meteor.call('removeAllPosts')`