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
mkdir server                            //create a directory for the server to live in
echo web: node server/app.js>Procfile   //this makes the command heroku uses to start your app
```
* set up angular server

```dos
npm install --save express              //a modular web server
npm install --save gzippo               //compresses files to save bandwidth
npm install --save compression          //used by gzippo  
```
+/server/app.js
```javascript
'use strict';
var express = require('express'),
    gzippo = require('gzippo'),
    compression = require('compression');
var app = express();

app.set('port', process.env.PORT || 3000);
app.use(compression());

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
heroku login                    //you may need to mess about with sha keys at this point
heroku create appname           //make your app on heroku
grunt build                     //build client-side ready for deployment
git add --all                   //make git aware of any changes
git commit -m "first commit"    //commit your changes
git push origin master          //push to github
git push heroku master          //push to heroku
heroku ps:scale web=1           //starts your heroku app
heroku open                     //opens it in your browser
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