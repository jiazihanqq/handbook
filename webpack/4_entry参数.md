# 
## entry
打版的入口文件，打包两次
```
entry:{
    main:'./src/index.js'
    sub:'./src/index.js'
}
```

## output
打包的输出文件，两次打包，按照各自的名字命名

```
output:{
    // 所有的输出js带一个公共地址，比如cdn地址
    publicpath:'http://cdn.com.cn'
    filename:'[name].js',
    path:path.resolve(__dirname,"dist")
}
```