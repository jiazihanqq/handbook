# 标题

## 用一句话概述
- 状态管理机制，状态就是影响到ui变化的数据。解决碎片化的状态
- 全局的、唯一的、不可改变的内存状态
## 原理
angular中的rxjx状态管理一共有三种模式： store模式、effect模式、entity模式 

- effect模式添加了Effect模块，隔离了副作用，并且生成一个新的无副作用action
- @NgRx/Effects 中提供了一个 @Effect() 装饰器，用来捕捉 Store.dispatch() 出来的特定的 Action（这些 Action 都是包含有副作用的），然后，调用服务后，根据返回值，生成新的 Action （新的 Action 不包含副作用），然后，由 Reducer 将新的 state 返回到store 中
- 由2个文件reducers和actions两个文件拆成3个，各自有分工，actions负责发出消息、effects文件负责处理业务相关数据并返回一个纯净的actions用于通知reducers发生状态改变。


## 实现

## 使用

## 引申

