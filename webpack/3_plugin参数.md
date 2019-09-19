# plugin参数
在webpack运行到某个时刻的时候，协助做一些事情，比如生成html文件、删除某些文件。

## htmlWebpackPlugins
自动生成首页html，并将js的入口文件引入进来
```
const HtmlWebpackPlugin = require('html-webpack-plugin')
module.exports = {
    ...
    plugins:[
        new HtmlWebpackPlugin({
            // 使用模板来生成html的dom元素部分
            template:"src/index.html"
        })
    ]
    ...
}
```
## cleanwebpackplugin
```
plugins:[
      new HtmlWebpackPlugin({
            // 使用模板来生成html的dom元素部分
            template:"src/index.html"
        }),
        // 清除dist文件夹下的文件
        new CleanWebpackPlugin(['dist'])
]
```