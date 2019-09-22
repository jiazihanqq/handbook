# caching
普通刷新，不会重新下载服务器上的新文件
通过contenthash强制浏览器重新获取文件，
当修改源代码后，会重新生成contenthash编码，库文件一般不会发生变化，业务代码会变化，所以访问时，只需要重新加载业务代码即可
output:[
    filename:'[name].[contenthash].js'
]
## 对于老的webpack版本（低于4.0）
如下配置可以保证，未发生变化的文件名称不会发生变化
还需要一些插件的支持
```
runtimeChunk:{
    name:'runtime'
}
```