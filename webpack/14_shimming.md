# 解决兼容性问题
##polyfill解决浏览器高低版本的问题
解决浏览器不支持新的方法，而使用的插件，
例如在低版本浏览器中，自动编写一个模拟promise方法的函数。
## 引用模块之间的引用
当发现模块中（如node_modules引入的模块总）存在$符号，就会自动的把jquery模块引入到该包中
再例如，在模块中使用_join代表lodash中的join方法，就可以做如下定义
new webpack.ProvidePlugin({
    $:'jquery',
    _join:['lodash',"join"]
})