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
          user.roles.indexOf('admin') isnt -1
      ]
```
