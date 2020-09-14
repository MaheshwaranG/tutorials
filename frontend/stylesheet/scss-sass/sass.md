## SASS

Syntactically Awesome Stylesheet is a css pre-processor. which helps to reduce repetition with css. it is a super set of CSS and is based on javascript.
you can write a sass code and save it as .scss extension. once you run the file by,
sass --watch filename.scss
then it will create two file as a name of
filename.css
filename.css.map
whenever you change SCSS file, the style.css fill will be updated automatically. So Don't directly change compiled css file.

**Two Type of Syntaxes :**

1. SCSS - Sassy CSS
   SCSS is a extension of CSS so every valid CSS is a valid SCSS as well.
2. Indented Syntax
   This is older syntax. it use .sass extension

**Environment Setup for react sass:**
npm init
npm install --save-dev react react-dom webpack webpack-dev-server
npm install --save-dev babel-core babel-loader babel-preset-es2015 babel-preset-react

./node_modules/webpack/bin/webpack.js -p

**Simple Ref:**
https://github.com/marharyta/webpack-boilerplate/blob/master/webpack-basic-setup/webpack.config.js
