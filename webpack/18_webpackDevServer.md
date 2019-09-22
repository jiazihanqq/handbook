# webpackDevServer
## proxy属性的配置
```
// webpack.config.js
devServer:{
    proxy:{
        // 当请求此接口时，将地址转发到下面的地址
        '/react/api':'http://www/dell-lee.com'
         // 去demo.json去请求数据，要求返回的是demo.json数据
        '/react/api':{
            // 多个api接口放在context中
            context:[],
            target: 'http://www/dell-lee.com'，
            // 拦截
            bypass: function(){
                
            }
            pathRewrite:{
                'header.json': demo.json
            }
            // 突破origin的限制
            changeOrigin: true
            headers:{
                host：
                cookie：
            }
        }
    }
}
```
## 实现前端路由的配置（只在开发时期有效，发布时需要在服务器上设置Apache）
当后端没有此地址的时候，会自动返回index.js页面，走前端的路由配置，实现了前端的路由  

historyapifallback
```
// webpack.config.js
devServer:{
    historyApiFallback:true
}
```
甚至可以实现一个重写规则  
```
// webpack.config.js
devServer:{
    historyApiFallback:{
        rewrite:[{
            from: /abc.html/,
            to: /list.html/,
        }]
    }
}
```
或者一套重定向规则
```
// webpack.config.js
devServer:{
    historyApiFallback:{
        rewrite:[{
            from: /abc.html/,
            to: function(){
                return ....
            },
        }]
    }
}
```
