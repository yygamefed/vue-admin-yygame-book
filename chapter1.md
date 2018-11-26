# ES6常用的新语法

## 箭头函数
保持this指向不变
```javascript

var a= ()=>{
}
``` 

------------------
## 简洁的function写法
即 arrow function

例如：

```javascript

var s={
    a:function(){
        alert(1);
    }
}

``` 

可以简写成
```javascript

var s={
    a(){
        alert(1);
    }
}
```
------------------

## 对象

### 解构

```javascript
var s={
    name:1,
    value:2
}
var name = s.name;
var value = s.value;
```
可以简写成

```javascript
var s={
    name:1,
    value:2
}
var {name,value}=s;
```


