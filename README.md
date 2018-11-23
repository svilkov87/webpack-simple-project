# webpack-simple-project

## creating package.json with dependenses

```
npm init
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack"
  },
  
```

## install webpack localy

```
npm i webpack --save-dev

```

## install webpack cli

```
npm i webpack-cli --save-dev

```

## create index js file
```
touch index.html
mkdir src
cd src
touch index.js
ls


npm run build - will create a new dist directory after that
```
##  libs install

```
npm i jquery --save
npm install vue
npm install vue-loader

index.js:

import $ from 'jquery';
import Vue from 'vue';

$('.title').html('some text');

console.log('1');

```

##  dev-server install

```
npm i webpack-dev-server --save-dev

  "scripts": {
    "build": "webpack --mode production",
    "dev": "webpack-dev-server --mode development --open"
  },

```

##  create webpack config

```
!perhaps, need apdate versions of babel

touch webpack.config.js
npm i path --save-dev
npm i babel-cli --save-dev
npm i babel-preset-latest --save-dev
npm i babel-core babel-loader babel-preset babel-preset-env babel-preset-stage-3 --save-dev
npm i style-loader --save-dev
npm i css-loader --save-dev
npm i node-sass --save-dev
npm i extract-text-webpack-plugin@next --save-dev



const path = require('path');
const ExtractTextPlugin = require('extract-text-webpack-plugin');

let conf = {
    entry: './src/index.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        publicPath: '/dist/',
        filename: 'main.js'
    },
    devServer: {
        overlay: true
    },
    module: {
        rules: [
            {
                test: /\.js$/,
                loader: 'babel-loader'
                // exclude: '/node_modules/'
            },
            {
                test: /\.css$/,
                use: [
                    'style-loader',
                    'css-loader'
                ]
            },
            {
                test: /\.scss$/,
                use: ExtractTextPlugin.extract( {
                    fallback: 'style-loader',
                    use: [
                        'css-loader',
                         'sass-loader'
                        ]
                } )
            }
        ]
    },
    plugins: [
        new ExtractTextPlugin('style.css')
    ]
}

module.exports = ( env, options ) => {

    let production = options.mode === 'production';
    conf.devtool = production
                        // ? 'sourcemap'
                        ? false
                        : 'eval-sourcemap';
    return conf;

}


```
