# 标题

## 用一句话概述
- @click 等事件
- v-if、v-for、v-show等指令
- :value 绑定数据
- v-model 双向数据绑定
## 原理

## 实现

## 使用

## 引申
- vuex状态管理
（1）解决的问题，不同组件之间共享一个状态，导致状态的混乱，同时也可以让view state action之间松耦合  
（2）效果相当于ng的redux，也是把和业务相关的状态保存到store中，不直接修改  
（3）

- vue-router路由和组件间的对应关系
通过router-vue引入路由，其他使用方式和ng基本相同，
（1）嵌套子路由的时候，需要在子模块中引入router-vue视图    
（2）如果是根路由或者是重定向路由，需要加redirect重定向    
（3）动态路由（根据id展现对应的商品），通过route.params.id获取路由中的id，获取到id后做一次网络请求即可   4
（4）参数路由，通过route.query.message对象获取
（5）编程式路由：this.$route.push()
（6）不需要回退的路由： this.$route.replace()
（7）路由的回退： this.$route.go(-1)


![avatar](./img/20190805213129.png)