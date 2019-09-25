# webpack性能优化

## 打包速度
### 跟上技术的迭代 
node版本，webpack的版本
### 尽可能少的应用loader
### 使用 exclude 和 include 约定打包范围
exclude '/node_modules/'
include path.resolve(__dirname, '../dist')
### 尽可能少的使用plugin
在使用plugin的时候，尽量使用官方推荐的库，另外想好这个插件是开发时候用的，还是生产环境用的
### 合理的使用resolve参数
resolve参数中的extensions枚举的文件类型过多，会导致性能问题
```
resolve:{
    extensions:['.css',  '.js', '.jsx']
}
```
### Dllplugin
依赖库文件（node_modules）不要每次打包都要分析，通过dllplugin和dllreferenceplugin插件生成的manifast.json文件做到这一点
```
//webpack.dll.js
将这三个文件打包到dll文件夹中
module.exports = {
    entry:{
        vendors:['react','react-dom','lodash']
    }
    output:{
        filename: '[name].dll.js'
        path: path.resolve(__dirname, '../dll')
        library: '[name]'
        
    }
}
// webpack.common.js引入all-asset-html-webpack-plugin插件
plugins:[
    // 通过此插件，将打包好的文件挂载到html上
    new AddAssetHtmlWebpackPlugin({
        filepath: path.resolve(__dirname, '../dll/venders.dll.js')
    })
    // 到该文件中找第三方模块的映射关系，如果找到了就不用再次打包了
   new webpack.DllReeferencePlugin({
        manifest: path.resolve(__dirname, '../dll/venders.manifast.json')
    })
]
// webpack.dll.js
plugins:[
    new webpack.DllPlugin({
        name:'[name]',
        path: path.resolve(__dirname,'../dll/[name].manifast.json')
    })
]
```
### 控制包的大小
删除冗余的代码，库和包
### 多进程打包
thread-loader,parallel-webpack,happypack
### 合理使用sourcemap
### 结合stats分析打包结果
### 使用webpack-dev-server打包，使用内存打包效率肯定更快
### 合理使用插件