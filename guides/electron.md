# electron bits & pieces

## build and publish with auto update (for windows)

* make an app  
  don't use /build as your output directory, use something safe like /app
* `npm install --save-dev electron builder`
* `npm install --save electron-updater`
* edit `package.json`  
  ```json
    "main": "app/main.js",
    "scripts": {
      "start": "electron .",
      "pack": "build --win -p always"
    },
    "build": {
      "appId": "com.companyname.productname",
      "productName": "productname"
    }
  ```
* edit your main.coffee file (or .js file if you aren't using coffeescript)
  ```coffeescript
  {autoUpdater} = require 'electron-updater'
  ...
  app.on 'ready', ->
    autoUpdater.checkForUpdatesAndNotify() 
* if you don't already have one get a github token with repo access from https://github.com/settings/tokens/new and set it as the environment variable `GH_TOKEN` on your local machine
* update version number, push to github and publish a draft release
  ```bash
    npm version patch --no-git-tag-version
    git add --all
    git commit -m "my release"
    git push origin master
    npm run pack
  ```
* go to the releases section near the top of your github repo mainpage and publish the draft that has been created
* you are done, go home and schleeeep weeeeell
