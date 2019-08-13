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
![avatar](./img/20190807202748.png)  
![avatar](./img/20190807202930.png)  
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
- debounce、debounceTime（300）节流，300毫秒内的输入不触发变化
- destinct（没有重复元素）、distinctUntilChanged（不与前一个相同即可，适用于无尽序列）
- merge、concat（合并到末尾，不适合无尽序列）、startWith（队首插一个值，一般用于默认值）流的合并
- combineLatest、withLatestFrom（分为一个主流，一个辅助流，当主流发生变化，去取辅助流的最新数据）、zip（两个都得是最新的变化，才会生效）
- flatmap（拍扁流中的流 ）、 switchmap（一旦有新的流将抛弃原来的流） 、mergeMap（保留所有的流）
- 表单控件里的valueChanges
![avatar](./img/20190807213807.png)  
