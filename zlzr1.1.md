##### jQuery判断对象是否为空
```javascript
let obj = {foo:'bar'};
$.isEmptyObject(obj);
// 结果为false 
//用于检测对象是否为空，不包含任何属性
```
##### jQuery一个对象绑定多个事件
```javascript
//第一种
$('#btn').on({
    click:function() {
      console.log('点击事件')
    },
    monseout:function() {
      console.log('移出事件');
    }
})
//第二种
$('#btn').bind({
    click:function() {
       console.log('点击事件');
    },
    mouseout:function() {
      console.log('鼠标移出事件');
    }
})
//移出所有事件绑定
$('#btn').off()
//移出一种事件绑定
$('#btn').off('click')
//移出事件绑定的第二种办法,移出所有的事件
$('#btn').unbind()
//移出单个事件绑定
$('#btn').unbind('click')
```
##### 事件冒泡、事件捕获、事件委托的关系
一、事件冒泡和事件委托是浏览器执行事件的不同阶段。

二、事件委托是利用事件冒泡阶段运行机制来实现的。

##### 事件冒泡和事件捕获的运行条件
当一个事件发生在具有父元素的的元素上时，现代浏览器根据事件添加时的设置来执行（冒泡或者捕获）。简单的来说就是几个元素层叠关系，
执行事件的时候，子元素会触发父元素的事件，父元素也会触发子元素事件。这种情况下通过addEventListener()的第三个参数来决定事件是
事件冒泡注册的还是事件捕获注册的。如果事件是从外向里（从大到小，从祖辈的小辈）就是事件捕获，此时addEventListener的第三个参数
是true,如果事件是从里向外（从小到大，从小辈到祖辈）就是事件冒泡，此时addEventListener的第三个参数设置的应该是false，默认的也
false。
##### 阻止事件冒泡和事件捕获
event.stopPropagation();
##### 事件冒泡和事件捕获的区别
执行事件的顺序不同；事件捕获:从外到里；事件冒泡：从里到外。
##### 事件委托
什么是事件委托？onclick等就是事件。委托就是把交给别人来做。事件本身是应该加在某些元素自身的，可以交给其他元素来做。通常这种叫做
事件委托。
举个栗子：有三个同事周一会有三个快递到来。那么为了签收快递，我们只有两种办法。三个人在前台等，或者委托前台MM代收，然后再分发下去，
在现实生活中，肯定不会三个人都傻傻的站在前台等。只能请前台MM，就是来了更多快递，前台MM也会替我们收了快递，分发给更多人。
##### 事件委托原理
就是利用事件冒泡原理，把事件加到父级上，触发执行效果。
##### 作用
- 性能好
- 可以给动态创建的元素绑定事件，达到想要的效果。
##### 事件源
跟this作用一样(他不用看指向问题，谁操作的就是谁),event对象下的。
##### 使用情景
- 有很多DOM元素要绑定相同的事件。
- 动态生成的DOM元素需要利用事件委托来注册事件。因为元素不存在的情况下，是不能给该元素绑定任何事件的。
##### 语法
```javascript
 $('#father').on('click','#son',function(){
          console.log('通过事件委托来给子元素绑定事件');
       })
```
##### 获取异步操作的结果
```javascript
//获取异步操作结果
function getData(callback) {
  setTimeout(function() {
    var data = 'hello data';
    callback(data)
  },4000)
}

function callback(info) {
  console.log(info);
}

getData(callback);
```

