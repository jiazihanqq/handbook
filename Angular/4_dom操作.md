# dom操作

## 用一句话概述
angular中推荐使用renderer2&&elementRef两个方法结合的方式操作dom  
（1）#helloDiv
（2）引用div元素：viewChild('helloDiv')（选择器） 和 elementRef（dom元素的包装类）
（3）引用component模板：viewChild("ImageSliderComponent") 
（4）引用多个：viewChilder("img") querylist<elementref>
（5）renderer2：安全的问题，不允许直接操作dom，防止注入攻击
## 原理

## 实现

## 使用
```
export class DragDirective{
    @Input() dragClass : string;
    constructor(private el:ElementRef, private rd:Renderer2){
        
    }

    if(this.el.nativeElement === ev.target){
        <!-- 添加class -->
        this.rd.addClass(this.el, this.dragClass)
    }
}
```
## 引申
- scrollleft
- 轮播图组件的实现
