# redux


## 用一句话概述
状态就是影响到ui变化的数据，（全局、唯一、每次都会返回新的状态）
redux 一般在coremodule中import  
好处：   
（1）不会直接操作状态，避免多人协作造成的混乱    
（2）把对内存数据的修改，从组件中剥离开  
![avatar](./img/20190819222221.png)  

Effect角色是对reducer的补充，
reducer用来专门处理内部的数据变化，effects用来处理外部的数据变化
![avatar](./img/20190819233231.png)  

## 原理
reducer 
- 初始状态 
```
 const initialState State = {
     quota: {
         id: 1
         name: "zhangsan"
         params: "zs"
     };
 }
```
- 每一个状态
```
 export ingerface State{
     quota:{
         id:
         name:
         params:
     };
 }
```
action（举个例子，有三个动作：发送http请求，http成功返回，http返回失败）
- type
- payload 
store
- index.ts中描述各个reducer
```
    export interface State = {
        quote: Quote.state
    }
    const initialState: State = {
        quote: Quote.initialState
    }
    const reducers = {
        quote: Quote.reducer
    }
    const productionReducers = combineReducers(reducers);
    ……
    storeModule.provideStore(reducer),
    RouterStoreModule.connnectRouter(),
```
- 调用
```
 quote$: Observable<Quote>;
 <!-- 得到最新的状态 -->
 this.quote$ = this.store$.select(state => state.quote.quote);
 this.quoteService$.getQuote().subscribe(
     q=> {
         <!-- 传递消息 -->
         this.store$.dipatch({type:actions.SUCCESS, payload: q})
     }
 )
```

- effects的实现
```
    <!-- 通过ofType捕捉LOAD的action，在得到之后要做一些操作 -->
    quote$: observable<Action> = this.action$.ofType(action.LOAD)
    .map(toPayLoad)
```
## 实现

## 使用

## 引申
reselect软件包，使用缓存记录状态
![avatar](./img/20190819222221.png)