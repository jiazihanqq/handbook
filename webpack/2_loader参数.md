# 参数

## mode 
development和production
## entry
entry：{
    main:'./src/index.js'
}
## output
output:{
    filename:"bundle.js",
    path: path.resolve(__dirname,'dist')
}
## loaders
用于定义打版规则，知道对于特定的文件如何打包  
例如：使用file-loader插件打包jpg文件、vue文件  
### 打包静态资源，file-loader和url-loader
```
module:{
    rules:[{
        test: /\.(jpg | png | gif)$/,
        use:{
            // url-loader可以起到和file-loader相似的功能，会把png打包成、   
            // base64编码，小图片就不需要http再去请求了，使用limit参数择  
            // 文件的处理方式，如果大于阈值，则会选择存储图片的源文件   
            loader:"file-loader",
            options:{
                // 文件使用原名，[ext]为占位符，还有[hash]等
                name: '[name]_[hash].[ext]',
                outputPath:'images/',
                limit:2048
            }}
    },{
        test: /\.vue$/,
        use:{loader: "vue-loader"}
    }]
}
```
### 打包修饰类 style-loader 和 css-loader
- css文件 css-loader用于分析css文件的结构，style-loader会将打包的css文件挂载到head中
- sass文件 sass-loader
- postcss-loader 将css语法加上厂商配置（需要autoprefixer插件），需要在postcss.config.js中描述一下

```
module:{
    rules:[{
        test: /\.css$/,
        use: ['style-loader','css-loader']
    }]
}
```
```
module:{
    rules:[{
        // loaders 的执行顺序是从右到左
        test: /\.sass$/,
        use: ['style-loader','options：{
            loader：'css-loader',
            // 这种写法，可以保证sass中引入的sass文件也能被sass-loader和  // postcss-loader处理
            options:{
                importLoaders:2,
                // 采用模块化打包，之后在文件中 import style form ''; //  dom.classlist.add(style.item)
                modules: true
            }
        }','sass-loader','postcss-loader']
    }]
}
```
### 字体文件打包
```
module:{
    rules:[{
        // loaders 的执行顺序是从右到左
        test: /\.(eot| ttf|svg)$/,
        use: {
            loader:'file-loader'
        }
    }]
}
```
## perfoemance 
去掉打包警告