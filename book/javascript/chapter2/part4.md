## 四、流程语句

### 1.if
    
> if (condition) statement1 else statement2

- condition可以是任意表达式，表达式的结果不一定是布尔值
- 会自动调用Boolean()转换函数将表达式转换为布尔值，

推荐的写法
```
if(condition){
    statement1
}else{
    statement2
}
```

### 2.do-while

> 是一种后测试循环语句，在对条件表达式求值之前，循环体内的代码至少执行一次

```
do{
    statement
}while(expression)
```
### 3.while

> 属于前测试循环语句，在循环体内的代码被执行之前，就会对出口条件求值

```
while(expression){
    statement
}

eg:

var i = 0;
while(i < 10){
    i += 2
}
```

### 4.for

> 属于前测试循环语句，具有在循环之前初始化变量，和定义循环后要执行的代码的能力。

```
//和上面的while一样的功能
for(var i = 0; i < 10; i++){
    alert(i)
}
```
- 因为不存在块级作用域，所以for循环内部的变量外部也可以访问的到
- 省略()中的内容只留两个；，就会创建无限循环；

### 5.for-in

> 是一种精准的迭代语句，可以用来枚举对象的属性

```
//显示BOM中window对象的所有属性，
//每次循环都将window对象中的一个属性名赋值给变量propName，
//循环会持续到对象中所有的属性都被枚举一遍。
for(var propName in window){
    document.write(propName);
}
```

- ECMAScript对象的属性没有顺序，所以for-in出来的属性名顺序是不可预测的，因浏览器而异
- 如果要迭代的值是null或undefined，for-in就会抛出错误，ECMAScript更正后，不再抛出错误，只是不执行循环体，为了保持最大程度的兼容，最好先判断对象的值不是null或undefined

### 6.label

定义的label可以在将来break continue语句后引用，加标签的语句一般都要与for语句等循环语句配合使用

```
//label : statement
start: for(var i = 0; i < 10; i++){
    alert(i)
}
```

### 7.break 和 continue

- break : 会立即退出循环，强行继续执行循环后面的语句
- continue：会立即退出循环，但退出循环后会从循环的顶部继续执行


### 8.with

作用是将代码的作用域设置到特定的对象中

> 严格模式下不允许使用with，使用with会导致性能下降，给调试代码也造成困难，所以不建议使用

```
with(location){
    var hostName = hostname;
    var url = href ;  //实际上得到的值是location.href
}
```

### 9.switch

> switch比较的时候使用的是全等操作符，所以不会发生类型转化

- 目的，为了免于编写if  else if else if  这样的代码
- 通过在每个case后面加break，来避免同时执行多个case的情况，假如需要混合，不要忘了在代码加注释，说明是有意省略break
```
switch(i){
    case 1:
        //合并两种情况
    case 2:
        alert("i可能是1也可能是2")
    break;
    default:
        statement
}
```

- case值不一定是常量，也可以是表达式，也可以是变量
```
switch("hello world"){
    case "hello " + "world";
        console.log(321);
    break;
    default:
        console.log("321");
}
```

```
var a = 10;
switch(true){
    case a > 5:
        a += 1
    break;
    case a==11:
        a++
    break;
    default:
        console.log(321)
}
```
