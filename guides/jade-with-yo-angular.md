#adding jade to yo angular
```
npm install --save-dev grunt-contrib-jade
```
*Gruntfile.js*  
add jade task
```javascript
        jade: {
          compile: {
            options: {
              data: {
                debug: false 
              }
            },
            files: [{
              expand: true,
              cwd: '<%= yeoman.app %>',
              src: [
                '{,**/}*.jade'
              ],
              dest: '.tmp',
              ext: '.html'
            }]
          }
        },
```
add watch task
```javascript
      jade: {
        files: [
          '<%= yeoman.app %>/{,*/}*.jade'
        ],
        tasks: ['jade']
      },
```
add the jade task to all three *concurrent* build tasks
```javascript
        concurrent: {
            server: [
                'jade',
                'compass:server'
            ],
            test: [
                'jade',
                'compass'
            ],
            dist: [
                'jade',
                'compass:dist',
                'imagemin',
                'svgmin'
            ]
        },
```
if you aren't using grunt-angular-templates then add an option to *htmlmin*
```javascript
    htmlmin: {
      dist: {
        options: {
          collapseWhitespace: true,
          conservativeCollapse: true,
          collapseBooleanAttributes: true,
          removeCommentsFromCDATA: true,
          removeOptionalTags: true
        },
        files: [{
          expand: true,
          cwd: '<%= yeoman.dist %>',
          src: ['*.html', 'views/{,**/}*.html'],
          dest: '<%= yeoman.dist %>'
        },{
          expand: true,
          cwd: '.tmp',
          src: ['views/{,**/}*.html'],
          dest: '<%= yeoman.dist %>'
        }]
      }
    },
```
