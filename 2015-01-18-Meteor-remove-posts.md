```
// server/start.js
// Meteor.call('removeAllPosts') will empty Posts collection
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