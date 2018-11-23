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
touch webpack.config.js
npm i path --save-dev

let path = require('path');

module.export ={
    entry: './src/index.js',
    output: {
        path: path.resolve(__dirname, './dist'),
        filename: 'main.js',
        publicPath: '/dist'
    }
}

```
