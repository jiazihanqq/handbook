# code-splitting
将业务逻辑代码和第三方库剥离开，打包文件太大，加载时间太长
比如maim.js 依赖lodash库
## cleanWebpackPlugin
分为build、dist、src三个文件夹
- build 存储webpack打包配置
- dist 存储打包后生成的文件
- src 存储源代码
在打包之前，清除dist文件夹中的打包文件
```
new CleanWebpackPlugin(['dist',{
    root:path.resolve(__dirname,'../')
}])
```
## 代码分割
### 方法一，手动代码分割
同时加载2个1mb的代码，比加载1个2mb的文件要快很多，当业务代码发生变化时，用户只需要加载main.js即可。
将lodash文件挂载到全局对象上
```
// lodash.js
import _ from 'lodash'  
window._ = _;

```
同时修改入口文件
```
entry:{
    lodash:'./src/lodash.js',
    main:'./src/index.js'
}
```
### 方法二，webpack自带的插件
#### 同步加载文件：webpack-splitChunks-plugin插件
- 样例
```
optimization:{
    splitChunks:{
        chunks:'all'
    }
}
```
- 属性
chunks:"async"/"all"/"synch"
cacheGroups:{  // 缓存组，将符合条件的代码放到一起
    vendor:{
        // 如果在node_moduels文件夹下，
        test:/[\\/]node_modules[\\/]/,
        priority:-10,
        fileName:'vendors.js'
    },
    default:{
        // 如果上一个判断不生效的时候，
        minChunks:2,
        priority:-20,
        // 重复引入的代码不再重新分割打包
        reuseExistingChunk:true,
        filename:"common.js"
    }
}
minSize:30000// 大于此阈值的文件，才会做代码分割
maxSize: 50000// 大于此阈值的文件，将会被拆分多个50kb的文件
minChunks:2// 至少用到两次以上，才会分割成独立文件  
#### 异步加载文件：babel-plugin-dynamic-import-webpack或者babel/plugin-syntax-dynamic-import
第一种插件的缺点： 不能将文件智慧命名，例如下面的代码，将文件重命名为lodash
```
(function(){
    import (/*webpackChunkName:"lodash"*/"lodash").then(({default: _}) =>{
        var element = document.createElement("div");
        element.innerHTML = _.join(['Dell', "lee"], '-');
        return element;
    })
})()
```
```
//.babelrc
plugins:["dynamic-import-webpack"]
```
```
optimization:{
    splitChunks:{
        chunks:'all',
        catchGroups:{
            vendor:false,
            default:false
        }
    }
}
```