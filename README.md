## Demo group


### 1. entry file


此时的配置文件

```js
module.exports = {
  entry: './main.js', // 入口文件
  output:{
    filename: 'bundle.js', // 打包文件
  }
};
```

### 2. Multi-entry files


此时的配置文件

```js
module.exports = {
  entry: {
    'bundle1': './main1.js',
    'bundle2': './main2.js'
  },
  output:{
    filename: '[name].js',
  }
};
```

### 3. babel-loader

此时的配置文件

```js
module.exports = {
  entry: {
    'bundle': './main.jsx' // 入口文件
  },
  output:{
    filename: '[name].js', // 打包生成的文件
  },
  module: {
    rules: [ // 打包规则
      {
        test: /\.jsx?$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['es2015','react']
          }
        }
      }
    ]
  }
};
```

### 4. css-loader

配置文件 

```js
module.exports = {
  entry: {
    'bundle': './main.js'
  },
  output:{
    filename: '[name].js',
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader','css-loader']
      }
    ]
  }
};
```

### 5. image-loader

配置文件

```js
module.exports = {
  entry: {
    'bundle': './main.js'
  },
  output:{
    filename: '[name].js',
  },
  module: {
    rules: [
      {
        test: /\.(png|jpg)$/,
        use: [
          {
            loader:'url-loader',
            options: {
              limit: 8192
            }
          }
        ]
      }
    ]
  }
};
```

### Reference

[github](https://github.com/ruanyf/webpack-demos#demo01-entry-file-source)