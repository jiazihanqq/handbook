# css文件的代码分割（或者叫合并好一些？）
默认会把import的css文件打包进js文件中
## 使用minicssextractplugin插件替换掉style-loader插件
需要解决treeShaking的问题，不对css代码作用
```
// package.json
sideEffects:[
    "*.css"
]
同时 optimization中
配置usedExports:true
```
## css文件的合并、压缩
在用一个页面import进来的css文件会被默认打包为一个文件，但不会合并
使用 optimize-css-assets-webpack-plugin插件实现css代码的合并和压缩
## css文件的拆分
通过cachegroups写匹配完成代码文件的拆分
