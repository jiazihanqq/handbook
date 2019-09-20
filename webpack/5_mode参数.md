# mode
## 文件的划分
### 两个打版文件 
- webpack.dev.js
- webpack.prod.js
缺点：两个文件中会有大量重复的代码
### 三个文件
- webpack.dev.js
- webpack.prod.js
- webpack.common.js
webpack.common.js用来记录重复的代码
使用webpack-merge合并打包代码
```
const commonConfig = reqiure("./webpack.common.js")
const devConfig = {}
module.exports = merge(commonConfig, devConfig)
```
## devtool
使用devtool配置sourcemap的策略

```
mode: "development "
devtool: "none"
// 通过eval运行映射关系
devtool: "eval"
// 生成一个vlq的编码集合
devtool: "source-map"
// 将映射关系写到打版后的文件中，在出错时，将出错行号和列号都输出，耗费性能
devtool: "inline-source-map"
// 仅告诉哪一行代码出了错
devtool: "cheap-inline-source-map"
// 如果引用的第三方库出现了bug，也要一并输出
devtool: "cheap-module-inline-source-map"
```
## 重要结论
- development模式，推荐使用：
devtool: "cheap-module-eval-source-map"
- production模式，推荐使用：
devtool: "cheap-module-source-map"

## sourcemap原理

https://segmentfault.com/a/1190000008315937
https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/
http://www.ruanyifeng.com/blog/2013/01/javascript_source_map.html
https://www.youtube.com/watch?v=NkVes0UMe9Y