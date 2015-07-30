#Packaging your app
starting with an electron app eg. the one from getting-started  
install [electron-packager](https://github.com/maxogden/electron-packager)
```bash
npm install -g electron-packager
```
find out your version of electron by running
```bash
electron -v
```
and use that version number in the next command (also replace `AppName` with your app's name)
```bash
electron-packager ./ getting-started --platform=all --arch=all --version=0.30.1 --out=release
```
now you will have a bunch of packaged apps in the folder `/release`
