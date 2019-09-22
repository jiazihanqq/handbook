# pwa
## 使用http-server插件在指定文件夹下启动服务器
```
script:{
    start: "http-server --dist"
}
```
## pwa实现的效果
当服务器挂掉，在本例利用缓存重新构建页面
workbox-webpack-plugin， 会生成precatch-manifest和service-worker两个文件支持pwa功能，

```
// webpack.prod.js
plugins:[
    new WorkboxPlugin.GenerateSW({
        clientsClain: true,
        skipWaiting: true
    })
]
```
```
// 在业务代码中，注册使用
 navigator.serviceWorker.register('./service-worker').then(

 ).catch(

 )
```