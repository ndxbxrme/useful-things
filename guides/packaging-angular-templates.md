#packaging angular templates
packages all your angular views into the scripts.js file which is cool for a whole bunch of reasons.  
should play nicely with [jade angular](https://github.com/ndxbxrme/useful-things/blob/newmain/guides/jade-with-yo-angular.md)
```
npm install --save-dev grunt-angular-templates
```
add task
```javascript
        ngtemplates: {
          options: {
            module: 'mspApp',
            htmlmin: {
              collapseBooleanAttributes: true,
              collapseWhitespace: true,
              removeAttributeQuotes: false,
              removeEmptyAttributes: true,
              removeRedundantAttributes: false,
              removeScriptTypeAttributes: true,
              removeStyleLinkTypeAttributes: true
            },
            usemin: 'scripts.js'
          },
          main: {
            cwd: '.tmp',
            src: ['views/*.html', 'views/partials/*.html'],
            dest: '.tmp/tmp-templates.js'
          }
        },  
```
add a copy task
```
,
            templates: {
                expand: true,
                cwd: '<%= yeoman.app %>/views',
                dest: '.tmp/views',
                src: '**/*.html'
            }
```
if you have image references in your templates then add scripts.js to usemin
```javascript
        usemin: {
            html: ['<%= yeoman.dist %>/{,*/}*.html','<%= yeoman.dist %>/scripts/*.js'],
            css: ['<%= yeoman.dist %>/styles/{,*/}*.css'],
            options: {
                assetsDirs: ['<%= yeoman.dist %>', '<%= yeoman.dist %>/images']
            }
        },
```
add *ngtemplates* and *copy:templates* to *dist* build list
```javascript
    grunt.registerTask('build', [
        'clean:dist',
        'wiredep',
        'useminPrepare',
        'concurrent:dist',
        'autoprefixer',
        'copy:templates',
        'ngtemplates',
        'concat',
        'ngmin',
        'copy:dist',
        'cdnify',
        'cssmin',
        'uglify',
        'filerev',
        'usemin',
        'htmlmin'
    ]);
```
