## 二、数据类型

> 6种基本数据类型：Undefind、Null、Boolean、Number、String、Object

### 1.typeof() 
检测给定变量的数据类型，这是一个操作符而不是函数，所以括号不是必须的；

- 特殊的：
    ```
    typeof(null)//object  因为null是空对象指针
    ```
### 2.Undefined

- 只有一个值：undefined
- 使用var但是没有给变量赋值，变量的值就是undefined
```
var name;
console.log(name)//undefined
```
- 显示初始化定义变量，但是没有意义
```
var name = undefined;
console.log(name == undefined); // true
```

- 包含undefined和定义未定义不同
```
var name ;
//var age;
console.log(name);//undefined
console.log(age);//报错 
```
- 特例 typeof不一样，声明没声明都显示undefined

### 3.Null

- 只有一个值 null
- 逻辑上表示一个空对象指针，所以typeof(null)是object
- 如果这个变量以后要存对象，那初始值就定义为null
- undefined 是派生自 null，==操作符会做相应的转换，所以 undefined == null //true , 

### 4.Boolean
- 两个值：true、false
- Boolean()转型函数，转型规则

数据类型  | true | false
---|---|---
string | 任何非空字符串|""空字符串
Number | 任何非0包括无穷大|0和NaN
Object | 任何对象 | null
Unndfined |不适用 |undefined
- if(name){} // 这里就会按照上面的规则转换

### 5.Number

- 十进制：10
- 八进制：0开头，数字序列0~7， 
- 十六进制：0x开头，后面跟0~9、A ~ F 或 a ~ f
- 注意：如果八进制、二进制、十六进制输入错误，默认会按十进制读

  ##### 1.浮点数
  
  - 数值中包含小数点，如果小数点后面是0000，就会被看成整数
  
  - 0.1可以写成 .1 但是不推荐
  
  - 注意，保存浮点数的内存是保存整数的内存的两倍
  - e表示法：3.125e7  //31250000
  - 精度：最高精度是17位小数，所以0.1+0.2不等于0.3
  - 数值范围 ：
  
        (最小数值) Number.MIN_VALUE
        (最大数值) Number.MAX_VALUE

  - Infinity(正无穷)  -Infinity(负无穷)
        
  ##### 2.NaN

    > 是非数值，not a number 是一个特殊的数值，用来表示一个本来要返回数值的操作数为返回数值的情况
    
    - 任何涉及NaN的操作都会返回 NaN
    
    - NaN不等于任何值，包括自己 NaN == NaN   // false
    
    - isNaN() : 参数可以是任何值，接受到参数后会尝试转化为数值，如果不能转换才会返回true，比如：isNaN("10"); //false

    - isNaN()参数是对象的话，会先调用对象的valueOf()方法，看看该方法返回的值是否为数值，如果不是，再调用toString()方法，再测试返回值，这过程也是ECMAScript内置函数和操作符的一般执行流程
    
  ##### 3.数值转换
  
  - Number()
  
    + boolean true  1  /  false  0

    + null 0
    
    + undefined NaN
    
    + String： 
    
    【只包含数字】："123" 变 123 ，"123ww" 变 123 ，"011" 变 11；
    
    【浮点数】："1.123" 变 1.123 ；
    
    【16进制】"0xf" 变为对应十进制;
    
    【空】 0
    
    【除以上外】NaN
    
    【对象】 先valueOf()，如果是NaN，在调用toString(),然后再走上面的规则
    
  - parseInt()
  
    + 空字符串  NaN  （Number()对空字符串是0）
    + 浮点数 直接转化为整数
    + ECMScript定义的进制转化有点不一样，所以可以为函数提供第二个函数，转换进制，默认10进制，例如：parseInt('0xA',16) 
    
  - parseFloat()
  
    + 1.232.14  转换为 1.232
    + 16进制的数始终被转换为0
    + 只解析10进制，

### 6.String
  
  > 表示由0或多个16位Unicode字符组成的字符序列，用 ' 或 " 表示
  
- 字符字面量：也叫转义序列，用来表示非打印字符，或者其他用途的字符

  /n 换行
  
  /t 制表
  
  /b 退格
  
  /r 回车
  
  \\\ 斜杠
  
  \\' 单引号
  
  \\" 双引号
  
- 字符串特点：一旦创建，值就无法改变，要改变变量保存的字符串，首先要销毁原来的字符串，然后再用另一个字符串包含新值的字符串填充该变量；

- 转换字符串

  toString()：所有数据类型都有这个方法，只有null 和 undefined没有，参数可以是16、8表示16进制 8进制、
 
  如果不知道值是null 和 undefined ，可以使用转型函数 String()，如果有toString()方法返回正常的值，如果是null则返回"null",undefined 返回 "undefined"
      
### 7.Object
   
 > 对象其实是一组数据和功能的集合
    
- 创建方式

var obj = new Object();  //括号可以省略，但是不推荐

var obj = {};

- 每个对象都有的属性和方法

+ constructor： 用于保存创建当前对象的函数，例如构造函数，上例中，也就是Object()
+ hasOwnProperty(propertyName) ：检查给定的属性在当前实例中（而不是在原型中）是否存在，参数必须是字符串 

+ isPrototypeof(obj) ：检查传入的对象是否是当前对象的原型；

+ propertyIsEnumerable(propertyName) ： 检测给的属性能不能用for in来枚举，参数必须是字符串

+ toLocaleString() 返回对象的字符串表示，这个字符串与执行环境的地区对应

+ toString() : 返回对象的字符串表示

+ valueOf() : 返回对象的字符串、数值、或布尔值表示，和toString()返回值相同

