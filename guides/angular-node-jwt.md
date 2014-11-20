#angular & node.js & JWT & sequelize
---
start with a folder
```
git init
yo angular originem	
mkdir server
npm install --save express
npm install --save-dev grunt-connect-proxy
npm install --save-dev grunt-develop
```
make a basic api server.  
_+/server/app.js_
```javascript
'use strict';

var express = require('express');

var app = express();

app.get('/api', function(req, res){
    res.send('Welcome to originum');
});
console.log('API Server running on port ' + (process.env.PORT || 3000));
app.listen(process.env.PORT || 3000);
```
add proxy and node runner (develop) to _gruntfile.js_
```javascript
//10 - before module.exports = function (grunt) {
var proxy = require('grunt-connect-proxy/lib/utils').proxyRequest;
//32 - after yeoman: appConfig
develop: {
	server: {
		file: 'server/app.js'
	}
},
// - after watch: {
nodejs: {
  files: [
      'server/**/*.js',
      'server/*.js'
  ],
  tasks: ['env:test','develop'],
  options: { nospawn: true }
},
//75 - after connect: {
proxies: [
	{
		context: '/api',
		host: 'localhost',
		port: 3000,
		https: false,
		changeOrigin: false
	}
],
//95 - at the beggining of the return [ array
proxy,
//111 - same as last one
proxy,
//415 - add to grunt.task.run([ array
'configureProxies',
'develop'
```
clean out boilerplate code from angular project
```
remove extraneous code from app/index.html
add <base href="/" /> to app/index.html <head>
empty app/styles/main.scss
empty app/views/main.html
```
.  
##ENVIRONMENT VARIABLES
ensure env file is ignored by git and install the required module
```
echo local.env.js >> .gitignore
npm install --save-dev grunt-env
```
configure _gruntfile.js_
```javascript
//gruntfile, before grunt.initConfig({
var localConfig;
try {
	localConfig = require('./server/config/local.env');
}catch(e){
	localConfig = {};
}
//gruntfile, inside grunt.initConfig({
env: {
	test: { NODE_ENV: 'test' },
	prod: { NODE_ENV: 'production' },
	all: localConfig
},
//gruntfile, at the beggining of grunt.task.run([
'env:all',
```
add a server folder for configuration files
```
mkdir server/config
```
make an environment variables file.  
_+/server/config/local.env.js_
```javascript
'use strict';

module.exports = {
	SECRET: 'my secret'
};
```
test your new environment variable by modifying _/server/app.js_
```javascript
console.log(process.env.SECRET);
```
.  
##MODREWRITE FOR PROPER ADDRESS HANDLING
this changes addresses from http://host/#/something into http://host/something.

add required module
```
npm install --save-dev connect-modrewrite
```
modify gruntfile
```javascript
//gruntfile.js before grunt.initConfig({
var modRewrite = require('connect-modrewrite');
//gruntfile.js add to initConfig.connect.proxies.livereload.options.middleware.return, after proxy,
modRewrite(['!\\.html|\\.js|\\.svg|\\.css|\\.png|\\.gif|\\.jpg$ /index.html [L]']),
//same for the other middleware return object
```
alter how angular handles routing
```
//inject $locationProvider into app/scripts/app.js->.config()
//add $locationProvider.html5Mode(true); to the same config function
```
.  
##ADDING JWT AND SEQUELIZE
add required modules
```
npm install --save body-parser
npm install --save compression
npm install --save express-jwt
npm install --save glob
npm install --save gzippo
npm install --save jsonwebtoken
npm install --save lodash
npm install --save method-override
npm install --save morgan
npm install --save pg
npm install --save sequelize
```
make a route for login and an interceptor service
```
yo angular:factory authInterceptor
yo angular:route login
```
make server directories
```
mkdir server\controllers
mkdir server\models
```
make a postgres database called originum-development
and change a few variables to match
```
add DATABASE_URL and JWT_SECRET to /server/config/local.env.js
add extra routes to gruntfile.js->connect.proxies
context: ['/api','/authenticate','/signup'],
```
modify app.js to configure express server and setup our database.  
_*/server/app.js_
```javascript
'use strict';

var express = require('express'),
    db = require('./models'),
    http = require('http');

var app = express();

require('./config/express')(app);

db
.sequelize
.sync({force:false})
.complete(function(err){
  if(err){
    throw err[0]; 
  } else {
    http.createServer(app).listen(app.get('port'), function(){
      console.log('Server listening on port ' + app.get('port'));
    });
  }
});
```
main express configuration file, includes a .dist server for angular.  
_+/server/config/express.js_
```javascript
var express = require('express'),
    glob = require('glob'),
    gzippo = require('gzippo'),
    logger = require('morgan'),
    bodyParser = require('body-parser'),
    compress = require('compression'),
    methodOverride = require('method-override'),
    path = require('path'),
    expressJwt = require('express-jwt');


module.exports = function(app, config){
  app.set('port', process.env.PORT || 3000);
  app.use('/api', expressJwt({secret:process.env.JWT_SECRET}));
  app.use(logger('dev'));
  app.use(bodyParser.json());
  app.use(bodyParser.urlencoded({
    extended: true
  }));
  app.use(compress());
  app.use(methodOverride());
  
  var controllers = glob.sync(path.normalize(__dirname + '/..') + '/controllers/*.js');
  controllers.forEach(function(controller){
    require(controller)(app);
  });

  //angular distribution server
  app.use('/scripts', gzippo.staticGzip(__dirname + '/../../dist/scripts'));
  app.use('/images', gzippo.staticGzip(__dirname + '/../../dist/images'));
  app.use('/styles', gzippo.staticGzip(__dirname + '/../../dist/styles'));
  app.use('/views', gzippo.staticGzip(__dirname + '/../../dist/views'));
  app.all('/*', function(req, res) {
    res.sendFile('index.html', {root: __dirname + '/../../dist'});
  });  
  
  app.use(function (req, res, next) {
    var err = new Error('Not Found');
    err.status = 404;
    next(err);
  });

  if(app.get('env') === 'development'){
    app.use(function (err, req, res) {
      res.status(err.status || 500);
      res.render('error', {
        message: err.message,
        error: err,
        title: 'error'
      });
    });
  }

  app.use(function (err, req, res) {
    res.status(err.status || 500);
    res.render('error', {
      message: err.message,
      error: {},
      title: 'error'
    });
  });
};
```
a basic server controller that is protected by JWT.  
_+/server/controllers/api.js_
```javascript
'use strict';

var express = require('express'),
    router = express.Router();

module.exports = function(app){
  app.use('/', router);
};

router.get('/api', function(req, res) {
  res.send('welcome to api ' + JSON.stringify(req.user.id));
});
```
server controller to authenticate a user (ie Log in.)  
_+/server/controllers/authenticate.js_
```javascript
'use strict';

var express = require('express'),
    router = express.Router(),
    db = require('../models'),
    jwt = require('jsonwebtoken');

module.exports = function(app){
  app.use('/', router);
};

router.post('/authenticate', function(req, res) {
  db.User.find({where: {username: req.body.username, password: req.body.password}})
  .then(function(user){
    if(user) {
      var token = jwt.sign(user, process.env.JWT_SECRET, {expiresInMinutes:60*5});
      res.json({token:token});   
    }
    else {
      res.status(401).json({success:false, message:'user not found'}); 
    }
  },
  function(err){
    res.status(401).send(err);
  });
});
```
server controller to sign up a user.  
_+/server/controllers/signup.js_
```javascript
'use strict';

var express = require('express'),
    jwt = require('jsonwebtoken'),
    db = require('../models'),
    router = express.Router();

module.exports = function(app){
  app.use('/', router);
};

router.post('/signup', function(req, res) {
  db.User.find({where: {username: req.body.username}})
  .then(function(user)
    {
      if(user) {
        res.status(401).json({success:false, message:'username taken'});
      }
      else {
        db.User.create({username: req.body.username, password: req.body.password})
        .then(function(user){
          var token = jwt.sign(user, process.env.JWT_SECRET, {expiresInMinutes:60*5});
          res.json({token:token});
        });      
      }
    },function(err)
    {
      res.status(401).send(err);
    });
});
```
the main model file which ties all the others together.   
_+/server/models/index.js_
```javascript
var fs = require('fs'),
  path = require('path'),
  Sequelize = require('sequelize'),
  lodash = require('lodash'),
  db = {};

var sequelize = new Sequelize(process.env.DATABASE_URL, {
    debug: false,
    logging: false
});

fs.readdirSync(__dirname).filter(function (file) {
  return (file.indexOf('.') !== 0) && (file !== 'index.js');
}).forEach(function (file) {
  var model = sequelize.import(path.join(__dirname, file));
  db[model.name] = model;
});

Object.keys(db).forEach(function (modelName) {
  if ('associate' in db[modelName]) {
    db[modelName].associate(db);
  }
});

module.exports = lodash.extend({
  sequelize: sequelize,
  Sequelize: Sequelize
}, db);
```
_+/server/models/user.js_
```javascript
module.exports = function(sequelize, DataTypes) {
  var User = sequelize.define('User', {
    username: DataTypes.STRING,
    password: DataTypes.BIGINT,
    data: DataTypes.TEXT
  }, {
    classMethods: {
      associate: function(models) {    
      }
    }
  });
  return User;
};
```
_*/app/scripts/controllers/login.js_
```javascript
'use strict';

angular.module('originemApp')
.controller('LoginCtrl', function($scope, $http, $window, $location) {
    $scope.message = '';  
  
    var doHash = function(str){
        var hash = 0;
        for(var i=0; i<str.length; i++) {
            var char = str.charCodeAt(i);
            hash = ((hash<<5)-hash)+char;
        }
        return hash;
    };
  
    $scope.submit = function() {
        $http.post('/authenticate', angular.extend($scope.user, {password:doHash($scope.user.password)}))
        .success(function(data) {
            $window.sessionStorage.token = data.token;
            $location.path('/');
        })
        .error(function(error){
            delete $window.sessionStorage.token;
            $scope.message = error;
        });
    };
  
    $scope.signup = function() {
        if($scope.myForm.$valid)
        {
          $http.post('/signup', angular.extend($scope.user, {password:doHash($scope.user.password)}))
          .success(function(data) {
              $window.sessionStorage.token = data.token;
              $location.path('/');
          })
          .error(function(error){
              delete $window.sessionStorage.token;
              $scope.message = error;
          });   
        }
    };
});
```
basic login page markup.  
_*/app/views/login.html_
```javascript
<form name="myForm" ng-submit="submit()">
    <div>
        {{message}}
        <label>Username
            <input ng-model="user.username" type="text" name="user" required placeholder="Username" />
        </label>
        <label>Password
            <input ng-model="user.password" type="password" name="pass" required placeholder="Password" />
        </label>
    </div>
    <div>
        <input class="button" type="submit" value="Login" />
        <input class="button signup" type="button" ng-click="signup()" value="Sign Up" />
    </div>
</form>
```
a service that redirects to /login when we recieve a 401 from the server.  
_*/app/scripts/services/authinterceptor.js_
```javascript
'use strict';
angular.module('originemApp')
.factory('authInterceptor', function($rootScope, $q, $window, $location) {
    return {
        request: function(config) {
            config.headers = config.headers || {};
            if($window.sessionStorage.token) {
                config.headers.Authorization = 'Bearer ' + $window.sessionStorage.token;
            }
            return config;
        },
        response: function(response) {
            if(response.status === 401) {
                $location.path('/login');
            }
            return response || $q.when(response);
        },
        responseError: function(response) {
            if(response.status === 401) {
                $location.path('/login');
            }
            return response || $q.when(response);
        }
    };
})
.config(function($httpProvider) {
    $httpProvider.interceptors.push('authInterceptor');
});
```

