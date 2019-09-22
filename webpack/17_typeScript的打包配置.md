# TypeScript 
规范代码，适用于大型项目
## ts代码的编译
使用ts-loader插件进行打包
```
module:{
    rules:[{
        test:/\.tsx?$/,
        use:'ts-loader',
        exclude: /node_modules/
    }]
}
```
## tsconfig.json文件
```
{
    "compilerOptions":{
        "outDir":'./dist',
        // 使用import的模式使用
        "module":"es6",
        // 打包成es5
        "target":"es5"
        // 允许再引入js文件的插件
        "allowsJs":true 
    }
}
```
## 规范依赖的库的使用
安装库的同时，需要安装类型文件，如下所示
www.microsoft.github.io/TypeSearch/ 上去查找对应的类型文件
```
npm install @type/lodash --save-dev

```