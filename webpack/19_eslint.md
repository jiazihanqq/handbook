# eslint
解决团队代码的维护性和一致性
## 生成配置文件 
执行npx eslint --init命令
会生成 .eslintrc.js 文件
## 开始检测src路径下的文件
npx eslint src
## babel-eslint 用于react
```
//.eslintrc.js
moduel.exports = {
    extends: airbnb
    parser: babel-eslint
    // 打破airbnb公司的要求，自定义一个rules
    rules:[{
        "react/prefer-stateless-function":0
    }]
    // 配置一个document全局对象，且不允许覆盖
    globals:{
        document:false
    }
}
```
## 使用vscode安装eslint插件
## 用webpack中集成eslint
npm install eslint-loader --save-dev
```
rules:[{
    test:
    exclude:/node_module/
    use:['babel-loader','eslint-loader']
}]
```
通过如下配置，会打开一个浏览器，实时的更新修改情况
```
webpack.config.js
dv-server{
    overlay: true
}
```
## eslint自动修复代码
```
rules:[{
    loader:'eslint-loader',
    options:{
        fix:true
    }
}]
```

## 最佳使用eslint的时候，是git提交代码的时候
运行 npx eslint src