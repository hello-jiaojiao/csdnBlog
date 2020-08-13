# 数据类型

数据类型指的是字面量的类型，在 js 中一共有六种数据类型，分为两类：

- 基本数据类型：

  1. 字符串 (String)：'asd'  '哈哈'  '123'
  2. 数字 (Number)
  3. 布尔 (Boolean)：true  false
  4. 空 (Null) : null 通常指一个空对象
  5. 未定义 (Undefined)：声明未赋值，输出即为 undefined

- 引用数据类型（即对象类型）：

  6. Object

     比如：Object、array、function、data等。

数据类型的声明：

 	var 可以声明各种类型		

```js
var x;			// 	x 为 undefined
var y = 5;		//	y 为 数字
var z = 'Jhon';	//	z 为字符串
```

​	1. 字符串的声明(单引号双引号都可)		

```js
var z = 'Jhon';	
var z = "Jhon";	
```

2. 数字的声明	

   ```js
   var x1 = 33.00;
   var x2 = 33;
   ```

3. 布尔的声明	

   ```js
   var x =  true;
   var y = false;
   ```

4. Undefined 和Null

   ```js
	// undefined 表示变量没有赋值
   // null 表示可以通过将变量的值设置为 null 来清空变量
var persons;	//persons 未赋值
   var car = 'volco';
   var car = null; //null 清空变量
   ```
   
5. object 对象

   ```js
   // 数组
   var cars = new Array();
   cars[0] = 'aaa';
   
   var cars = new Array('saab', 'volvo', 'bmd');
   
   var cars = ['saab', 'volvo', 'bmd'];
   // 对象
   var person = {firstname:'jhon', lastname:'doe', id:9999};
   // 对象  键值对
   var person = {
       firstname:'jhon',
       lastname:'doe',
       id:999
   };
   console.log(person.firstname)
   console.log(person['firstname'])
   ```

**强制类型转换**

- 将其他数据类型转换成 number

  转换方式一（非严格型）：这种方式专门用来对付字符串	

  ​    \- parseInt() 把一个字符串转换为一个整数

  ​    \- parseFloat() 把一个字符串转换为一个浮点数，

  ​							用法跟parseInt() 相同

  ```js
  var obj = new Object();
  console.log(parseInt(5)); //5
  console.log(parseInt(5.4)); //5
  console.log(parseInt(5.6)); //5
  console.log(parseInt('5')); //5
  console.log(parseInt('5.6')); //5
  console.log(parseInt('哈哈')); //NaN (not a number)
  console.log(parseInt('5哈abc哈5')); //5
  console.log(parseInt('5.6哈abc哈5')); //5
  console.log(parseInt('哈5哈5')); //NaN
  console.log(parseInt(''));//NaN
  console.log(parseInt(new Object())); //NaN
  console.log(parseInt(true)); //NaN
  console.log(parseInt(false)); //NaN
  console.log(parseInt(undefined)); //NaN
  console.log(parseInt(null)); //NaN
  ```

  转换方式二（严格型）：使用Number()函数

  ​      \- 字符串 --> 数字

  ​        1.如果是纯数字的字符串，则直接将其转换为数字

  ​        2.如果字符串中有非数字的内容，则转换为NaN

  ​        3.如果字符串是一个空串或者是一个全是空格的字符串，则转换为0

  ​      \- 布尔 --> 数字

  ​        true转成1

  ​        false 转成0

  ​      \- null --> 数字 0

  ​      \- undefined -->数字 NaN 

  ```js
  console.log(Number(5));//5
  console.log(Number(5.6));//5.6
  console.log(Number('5'));//5
  console.log(Number('5.6'));//5.6
  console.log(Number('5.6哈哈'));//NaN
  console.log(Number(' '));//0
  console.log(Number(''));//0
  console.log(Number(true));//1
  console.log(Number(false));//0
  console.log(Number(null));//0
  console.log(Number(new Object()));//NaN
  console.log(Number(undefined));//NaN
  ```

- 将其他数据类型转换为 String

  方法一：

  ​    \- 调用被转换数据类型的toString()方法

  ​    \- 该方法不会影响到原变量，它会将转换的结果返回

  ​    \- 但注意：**null 和 undefined 这两值没有 toString() 方法**，

  如果调用它们的方法会报错

  ```js
  var a=123;
  // 调用a的toString()方法
  // 调用xxx的yyy()方法，就是xxx.yyy()
  a=a.toString(); 
  
  a=true;
  a=a.toString();//后面的值会覆盖掉前面的 
  
  console.log(typeof a);
  console.log(a);
  ```

    方法二：

  ​    \- 调用String()函数,并将被转换的数据作为参数传递给函数

  ​    \- 使用String()函数做强制转换时，

  ​      对于Number和Boolean实际上就是调用toString()方法

  ​      但是对于null和undefined,就不会调用toString()方法

  ​        它会将null直接转换为"null"

  ​        将undefined直接转换为"undefined"

  ```js
  var a=123;
  // 调用String()函数，将a转换为字符串
  a=String(a);
  console.log(typeof a);
  console.log(a);
  ```

- 将其他数据类型转换成 Boolean

   \- 使用Boolean()函数

  ​    \- 数字-->布尔

  ​      	- 除了0和NaN,其余的都是true

  ​    \- 字符串-->布尔

  ​      	- 除了空串，其余的都是true

  ​    \- null和undefined都会转换为false

  ​    \- 对象也会转换为true

  ```js
  console.log(Boolean(true));//true
  console.log(Boolean(5));//true
  console.log(Boolean(5.6));//true
  console.log(Boolean(-5.6));//true
  console.log(Boolean('哈哈'));//true
  console.log(Boolean(new Object()));//true
  console.log(Boolean(' '));//true
  
  console.log(Boolean(false));//false
  console.log(Boolean(''));//false
  console.log(Boolean(0));//false
  console.log(Boolean(undefined));//false
  console.log(Boolean(null));//false
  ```

  