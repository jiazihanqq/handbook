# 标题

## 用一句话概述
- 响应式扩展，优势是在思考维度上加入了时间的考量，把任何变化都要理解想象成一个流，流中涵盖着变化；
- 流被订阅之后，就不需要再次捕捉变化，流会将变化主动推送；
## 原理
- 生成一个流
const height$ = Rx.observabel.formEvent(height, 'keyup')
- 订阅一个事件
height$.subscribe(val => console.long(val))
## 实现

## 使用

## 引申
- 创建类操作符  from（数组） 、 fromEvent、of（针对对象转换成流）

- map 、mapTo（返回固定常量）、 pluck（用于取对象某个键上的值）
- combinelatest 两个流进行合并，并且只要有一个流发生变化，就重新计算；
- zip 两个流合并，并且要两个流都发生改变的情况下重新计算，适用于两个值是相互依赖的；
- obervable三种状态对应subscribe里实现的三个方法：Never 、empty、throw 对应  next error complete
- do 工具类，在当前操作符生效之后，下一个操作符生效之前进行某类操作
- scan reduce(对于无限的流是不会reduce完的) 数组类操作符
- filter take first/last skip 过滤类操作符
- interval timer（延时多久，间隔多久）创建类操作符