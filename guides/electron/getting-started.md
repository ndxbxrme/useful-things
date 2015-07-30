#Getting Started with Electron
Install electron
```bash
npm install electron-prebuilt -g
```
make a directory for your project and NPM initialize it
```bash
mkdir getting-started && cd getting-started
npm init
```
answer the questions however you like except `entry point` which you should set to `main.js`  
make a simple HTML file called `index.html`
```html
<html>
  <head>
    <title>Getting Started</title>
  </head>
  <body>
    <h1>I got up</h1>
  </body>
</html>
```
i'm going to use coffeescript in these guides since i love it!  
so make sure you have it installed then start it watching the directory (you might want to do this in a new terminal tab)
```bash
npm install -g coffee-script
coffee -cw .
```
make a new file called `main.coffee`
```coffeescript
app = require 'app'
BrowserWindow = require 'browser-window'

mainWindow = null

app.on 'window-all-closed', ->
  if process.platform isnt 'darwin'
    app.quit()
    
app.on 'ready', ->
  mainWindow = new BrowserWindow
    width: 800
    height: 600
  mainWindow.loadUrl 'file://' + __dirname + '/index.html'
  mainWindow.on 'closed', ->
    mainWindow = null
```
now all you have to do is type
```bash
electron .
```
and you're off!
