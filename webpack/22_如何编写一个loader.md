# 如何编写一个loader
就是一个函数

```
// 接受到源码参数
module.exports = function(source){

    // this.query参数内容，指的是webpack.config.js文件中配置的option中的参数
    this.query 
    // 将变动的源码返回回去
    return source.replace('dell', 'delllee')
}
```
```
modules:{
    rules:[{
        test: /\.js/
        use: [path.resolve(__dirname, './loder/loader.js')]
    }]
    
}
```
## loader-utils
