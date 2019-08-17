改变函数执行时的上下文，再具体一点就是改变函数运行时的this指向


我们拿别人的方法，并动态改变其上下文帮自己输出了信息，说到底就是实现了复用

（1）求数组的最值
需要把Math穿进去
Math.min.call(Math, 34,5,3,6,54,6,-67,5,7,6,-8,687);
（2）将伪数组转化为数组
将带有length字面量，转换成一个数组  
var arrayLike = {
  0: 'qianlong',
  1: 'ziqi',
  2: 'qianduan',
  length: 3
}
var arr = Array.prototype.slice.call(arrayLike);
（3）利用call做继承

### 实现call和bind 
（1）改变this的指向
（2）给定参数执行函数
（3）this不传的时候相当于指向window

https://www.jianshu.com/p/af3f41d8ef99



### 实现柯里化


