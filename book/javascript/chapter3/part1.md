﻿### 1.基本类型嗯和引用类型的值

> 基本类型的值：简单的数据段；引用类型的值：由多个值构成的对象。

> 基本类型的值：Undefined、Null、Boolean、Number、String

> 引用类型的值：是保存在内存中的对象，js不允许直接访问内存中的位置，也就是说不能直接操作对象的内存空间，操作对象时，实际上是在操作对象的引用而不是实际对象，引用类型的值是按引用访问的

### 1、动态的属性

- 创建基本类型的值
    
```
var a = "3";
```

- 创建引用类型的值
> 可以添加属性和方法，也可以改变和删除其属性和方法

```
var person = new Object();
person.name = "果果的对象"；
```

### 2、复制变量值

- 基本类型的值复制：下例中，创建一个a的副本，两个值互不影响
    ```
    var a = 2;
    var b = a;
    ```
- 引用类型的值复制：同样是将储存在变量对象中的值复制一份放在新的变量分配空间上，只不过复制的是指针；这个指针指向存储在堆中的一个对象，两个变量实际上引用同一个对象，所以，改变其中一个变量，就会影响另一个变量

### 3、传递参数

> ECMAScript中所有函数的参数都是按值传递的，也就是说，把外部的值复制给函数内部的参数，就和把值从一个值复制到另一个值一样。

> 基础类型的值传递和基础类型的值复制是一样的，引用类型的值传递和引用类型的值是一样的。

- 基本类型的值：被传递的值会被复制给一个局部变量（即命名参数，用ECMAScript概念说，就是arguments对象中的一个元素）
- 引用类型的值：会把这个值在内存中的地址复制给局部变量，所以局部变量的变化会反映到函数的外部。


### 4、检测类型

- typeof()操作符： undefined、string、number、boolean、object(null也是object)
- intanceof操作符：
```
console.log(arr intanceof Array) //arr 是不是Array
```