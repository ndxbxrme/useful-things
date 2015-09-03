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
### directives
* Validate a UK postcode
```coffeescript
.directive 'postcode', ->
    restrict: 'EA'
    require: 'ngModel'
    link: (scope, elem, attrs, ngModel) ->
      ngModel.$parsers.unshift (val) ->
        if val
          m = val.match(/^(([gG][iI][rR] {0,}0[aA]{2})|((([a-pr-uwyzA-PR-UWYZ][a-hk-yA-HK-Y]?[0-9][0-9]?)|(([a-pr-uwyzA-PR-UWYZ][0-9][a-hjkstuwA-HJKSTUW])|([a-pr-uwyzA-PR-UWYZ][a-hk-yA-HK-Y][0-9][abehmnprv-yABEHMNPRV-Y]))) {0,}[0-9][abd-hjlnp-uw-zABD-HJLNP-UW-Z]{2}))$/gi)
          ngModel.$setValidity 'postcode', m?.length > 0
        val
```
