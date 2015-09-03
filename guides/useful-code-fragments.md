# some useful code fragments
### meteor angular routes
* Require a user
```coffeescript
    resolve:
      currentUser: ['$meteor', ($meteor) ->
        $meteor.requireUser()
      ]
```
