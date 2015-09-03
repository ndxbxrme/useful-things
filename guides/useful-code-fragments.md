# some useful code fragments
### meteor angular routes
* Require a user
```coffeescript
    resolve:
      currentUser: ['$meteor', ($meteor) ->
        $meteor.requireUser()
      ]
```
* Wait for the user object if there is one
```coffeescript
    resolve:
      currentUser: ['$meteor', ($meteor) ->
        $meteor.waitForUser()
      ]
```
* Require a specific type of user
```coffeescript
    resolve:
      currentUser: ['$meteor', ($meteor) ->
        $meteor.requireValidUser (user) ->
          user.roles and user.roles.indexOf('admin') isnt -1
      ]
```
### meteor angular model
* Allow update for doc owner or admin
```coffeescript
  update: (userId, profile, fields, modifier) ->
    profile.userId is userId or Meteor.user().roles.indexOf('admin') isnt -1
```
