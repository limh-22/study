#第二章 JavaScript 数据类型
## 2.1 数据类型的分类
2.1.1 基础数据类型
 
基础数据类型，也可以叫做简单数据类型或原始数据类型。通常表示某种值，对值进行比较。

2.1.2引用数据类型

引用数据类型，也可以叫做 复杂数据类型，是键值对形式出现的，以属性和属性值构成，无需列表集合，在内存中占据独立的空间，任何一个独立的对象都不相等

##2.2 基本数据类型
2.2.1 数字类型
 number，这种类型使用IEEE754格式来标示整数和浮点数。数字类型包括：整数，浮点数，NAN，Infinitiy
数字范围：最小值5e-324，最大为2的53次方

isNAN()方法用来验证值是否为非数字，非数字返回值为true，数字返回值为false

     var a = 10;
     var b = '10';
     alert(isNaN(a + b)) ;//false
     alert(isNaN(a - b)) ;//false
     alert(isNaN(a / b)) ;//false
     alert(isNaN(a * b)) ;//false
     alert(isNaN(NaN)) ;//true

2.2.2 字符串类型
string类型是由引号括起来的一组16位的Unicode字符组成的字符序列，字符串类型通常被用于表达文本数据

        var a = '你好'；
        var b = "你们好"；

字符串中反斜线有着特殊用途，反斜线后面加一个特殊字符，就变为了转义字符，具备一些特殊用途

2.2.3 布尔类型
Boolean类型，只有两个变量值，分别是true和false，并且他们区分大小写，小写的是布尔类型的值。

数据类型中有以下数据类型转换后为false：
(1)false
(2)''空字符串
(3)+0和-0
(4)NaN
(5)null
(6)undefinded

2.2.4 null
  null类型代表空对象，是一个对象。函数的参数，表示该函数不是对象，也可以当做一个空对象使用

2.2.5 undefined
Undefined类型代表未定义，是变量的初始值，也是函数的默认返回值。undefined是关键字，不是对象

       console.log(undefined+1);
        //undefined数字类型转换为NaN 

## 2.3 检验基础数据类型的方式
typeof 运算符把信息当作'字符串'返回，也就是说返回值都是字符串类型，返回值有几种情况：number，string，boolean，undefined，function.null返回的是object，对象不能用typeof检测

        var a = 10;  //number
        var b = 'nihao';//string
        var c = true;//boolean
        var d = false;//boolean
        var e = null;//object
        var f = undefined;//undefined
        var g = ['1',2];//object
        var h = function(){
               alert(1)
        }//function

typeof后面的括号，在进行运算的时候一定要使用，否则返回值可能不正确

## 2.4 数据类型转换
2.4.1 强制转换
  主要指使用Number(),string(),boolean()三个函数，手动将各种类型的值分别转换为：数字类型，字符串类型，布尔类型

Number()转换为数字类型

        console.log(Number ('325'));//325
        console.log(Number ('nihao'));//NaN
        console.log(Number (''));//0 
        console.log(Number (true));//1
        console.log(Number (false));//0

String（）转换为字符串类型

       console.log(String(222))//222
       console.log(String(trie))//true
       console.log(String(false))//false、

Boolean（）转换为布尔类型

       console.log(Boolean(222))//true
       console.log(Boolean('nihao'))//true
       console.log(Boolean(''))//false
       console.log(Boolean(0))//false
       console.log(Boolean(NaN))//false

2.4.2 paresInt()和paresFloat()

paresInt()函数可以将数据转换成数字类型，并取整数部分，浮点数部分不取，如先遇见非数字、则显示NaN
praseFloat（）函数可以将数据类型转换为数字类型，且整数和浮点数都取

        var a = 10.67;//10
        var b = '4.466';//4
        var c = '12e';//12
        var d = 'nihao';//NaN
        var d = 'nihao123';//NaN
       /********************/
        var a = 10.67;//10.67
        var b = '4.466';//4466
        var c = '12.4e';//12.4
2.4.3 自动转换

变量的数据类型不确定，但各种运算对数据都有要求，如果运算符发现运算的数据类型与预期的不一样，就会进行自动运算。