#heroku & node.js & angular

* sign up for a heroku account
* make a new github repository

```dos
git clone https://github.com/username/appname.git
cd appname
yo angular

```

* clean out boilerplate angular code

```dos
mkdir server
echo #>server\app.js
echo web: node server/app.js>Procfile
```
* set up angular server

```dos
npm install --save express
npm install --save gzippo
npm install --save compression
npm install --save method-override
npm install --save logger
```
~/server/app.js
```javascript
'use strict';
var express = require('express'),
    gzippo = require('gzippo'),
    compression = require('compression'),
    methodOverride = require('method-override'),
    logger = require('logger');
var app = express();

app.set('port', process.env.PORT || 3000);
app.use(compression());
app.use(methodOverride());

app.use('/scripts', gzippo.staticGzip(__dirname + '/../dist/scripts'));
app.use('/images', gzippo.staticGzip(__dirname + '/../dist/images'));
app.use('/styles', gzippo.staticGzip(__dirname + '/../dist/styles'));
app.use('/views', gzippo.staticGzip(__dirname + '/../dist/views'));
app.all('/*', function(req, res) {
  res.sendFile('index.html', {root: __dirname + '/../dist'});
});  

app.listen(app.get('port'));
console.log('server listening on ' + app.get('port'));
```
* remove `dist` from .gitignore
* download and install the heroku toolbelt which can be found on the first page of the heroku nodejs tutorial [here](https://devcenter.heroku.com/articles/getting-started-with-nodejs#set-up)

```dos
heroku login
heroku create appname
grunt build
git add --all
git commit -m "first commit"
git push origin master
git push heroku master
heroku ps:scale web=1
heroku open
```
* you should now see your shiny new app

###add a domain
* add a CNAME record with your domain registrar pointing to appname.herokuapp.com
```dos
heroku domains:add www.mydomain.com
```

###view your logs
```dos
heroku logs --tail
```