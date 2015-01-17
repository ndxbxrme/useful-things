##cloud9 angular with proxied api server
```
npm install -g yo
npm install -g generator-angular
yo angular
npm install
npm install imagemin-gifsicle
npm install imagemin-pngquant
npm install imagemin-optipng
npm install imagemin-jpegtran
npm install --save-dev grunt-connect-proxy
npm install --save-dev connect-modrewrite
```
//make file called mongodc
```
mongod --nojournal --bind_ip=0.0.0.0 --dbpath=data --rest
```
```
chmod a+a mongodc
mkdir data
```
gruntfile

//require extra stuff - line 12
```
var proxy = require('grunt-connect-proxy/lib/utils').proxyRequest;
var modRewrite = require('connect-modrewrite');
```
//change watch so it isn't so wasteful - line 33
```
watch: {
  options: {
    livereload: true
  },
  scripts: {
    files: ['<%= yeoman.app %>/scripts/{,*/}*.js'],
    tasks: ['newer:jshint:all']
  },
  css: {
    files: ['<%= yeoman.app %>/styles/{,*/}*.{scss,sass}'],
    tasks: ['compass:server', 'autoprefixer']
  },
},  
```
//add proxy config to the connect object
```
proxies: [{
  context: ['/api', '/socket.io'],
  host: 'localhost',
  port: 23232,
  https: false,
  changeOrigin: false
}],
options: {
  port: process ? process.env.PORT : 9000,
  hostname: process ? process.env.IP : 'localhost'
},
```
//we are going to use 'test' config, so remove the port property and add these to the top of the middleware return object
```
proxy,
modRewrite(['!\\.html|\\.js|\\.svg|\\.css|\\.png|\\.gif|\\.jpg|\\.ttf|\\.woff|\\.otf|\\.swf$ /index.html [L]']),
```              
              
//in copy, change {webp} to *    - line 330         
```
'images/{,*/}*.*'
```
//disable imagemin - 356
```
dist: [
  'compass:dist',
  //'imagemin',
  //'svgmin'
]
      
```
//add proxy config to the start of grunt serve registerTask - line 379
```
grunt.task.run([
'configureProxies',
```      
//change from livereload server to test server - line 398     
```
'connect:test',
```   
//make 3 cloud9 run configurations
```
grunt - grunt serve
mongo - ./mongodc
api - ./server/app.js
```