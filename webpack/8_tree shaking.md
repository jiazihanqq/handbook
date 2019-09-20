# Tree shaking
将引入的模块中，所有没有使用到的方法过滤掉（只支持esmodule的引入，即静态引入），在production模式下会起到作用。

```
// webpack.config.js
modules:{
    optimization:{
        usedExports:true
    }
}
```
```
// package.json
// 防止一个import的模块，由于其没有exports任何东西，而被打包忽略掉
sideEffects:false
sideEffects:[*.css]
```
