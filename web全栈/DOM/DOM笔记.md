#第六章 DOM
##6.1 DOM的概念
6.1.1DOM的概念

DOM是文档对象模型，DOM对象不仅仅是一个普通的内置对象，他还是一个巨大的API的核心对象，它将对象的内容呈现在JS面前，并赋予了JS操作文档的能力。

6.1.2DOM和JavaScript的关系

一个web页面是一个文档，这种文档可以在浏览器窗口或者作为html源代码显示出来，但上述两种情况都是同一个文档，DOM提供了对同一份文档的另一种表现，存储和操作的方式，DOM能够使用JavaScript脚本语言进行修改。

6.1.3 DOM节点

加载html页面，web浏览器生成一个橡树一样的结构，用来表示页面的内部结构，DOM将这种结构理解为节点，根据w3c的htmlDOM标准，html文档找的所有内容都是节点。

> 整个文档是一个文档节点
> 每个html元素是元素节点
> html元素内的文本是文本节点
> 每个html属性都是属性节点
> 注释也是节点，叫注释节点

6.1.4 DOM树

DOM树体现着html页面的层级结构，而DOM树有DOM文档树和DOM元素树两种。DOM元素树包含的只有元素节点，而DOM文档树则包括DOM文档中的所有内容。

##6.2 获取元素
6.2.1 用ID获取元素
getElementsById()的方法，接受一个参数：获取元素的ID，如果没有找到相应元素，则返回该元素，否则返回Null
  
        //用变量  在文档中  找  元素  用ID  id
        var d = document.getElementById('d');

6.2.2 用标签名获取元素

document.getElementByTAgName()可以获取该元素名称下所有的元素，返回一个伪数组，或者说是一个节点列表

           var lis = document.getElementByTAgName('li')
           //伪数组
           console.log(lis);

在某一个元素中，并不是在全局文档中利用标签获取元素，这样更加精准

           var ul = document.getElementById('ul');
           var list = ul.getElementsByTagName('list');
           console.log(list)

当元素只有一个的时候,返回的也依然是一个列表,而不是一个元素.可以通过数组的下标找到该元素.

        var div = document.getElementsByTagName('div');
        console.log(div[0]);

6.2.3用类名获取元素

          var a = document.getElementsByClassName('a');
          console.log(a); 

6.2.4 用选择器获取元素

querySelector()和querySelectorAll()可以依靠选择器找到元素,但是前者只能找到元素列表的第一个元素,而后者可以全部找到.注意,该方法性能没有直接利用标签寻找.

        var ul = document.getElementById('ul')
        var x = document.querySelector('#div>div a');
        var lis = ul.querySelectorAll('li');
        console.log(lis);

##6.3 获取元素中的其他信息
6.3.1 获取元素名 

当我们使用id获取元素的时候，元素的名称会和整个元素一起显示出来，如果想要拿到该元素的元素名，也就是标签名则需要用tagName属性。该属性只能获取，不能设置。

         var div = document.getElementById('mydiv');
         console.log(div.tagName);

6.3.2获取元素节点里的内容

当获取了元素之后，如果我们需要拿到元素中的内容（所有东西），则需要用另一种方法得到。元素里的内容可能包括：文本和元素。需要用innerHTML属性：

        var div = document.getElementById('mydiv');
        console.log(div.innerHTML);
          
        div.innerHTML = '你好';

6.3.3  获取元素节点中的文本

利用innerText属性获取的只是文本节点，不能是其他，当然innerText属性除了获取，也可以设置元素中的文本

        var div = document.getElementById('mydiv');
        console.log(div.innerText);
          
        div.innerText = '你好';

6.3.4获取元素的其他信息

利用className属性获取元素的类名,以字符串的形式返回.同时可以设置新的class类名,需要注意的是,返回值是一个字符串,如果更换其中一个类,则需要考虑该字符串中其他类是否应该一起设置.
 
        var div = document.getElementById('mydiv');
        console.log(div.className)

6.3.5 获取属性样式

style属性可以获取元素内联样式的所有属性，当然如果继续在style中找属性名，如backgroundColor，就可以得到该属性的值，以字符串的形式返回同时也可以设置该属性,从而达到增加或更改样式,需要注意的是,以JS形式增加的样式优先级大于CSS.


       <div style="background-color: blue"></div>

        var div = document.getElementsByTagName('div');
        //js拿到和获取的是内联
        console.log(div[0]);

##练习
需求1：更改粗体：

       var div = document.getElementById('div');
         console.log(div.tagName);

         //方法一:
         //那些标签是加粗的 b,strong,h1~h6
         //H1||H2||H3||H4||H5||H6||B||STRONG
        if(div.tagName == 'H1'|| div.tagName == 'H2'||div.tagName == 'H3'||div.tagName == 'H4'||div.tagName == 'H5'||div.tagName == 'H6'||div.tagName == 'B'||div.tagName == 'STRONG'){
            div.style.fontWeight = 200 ;
        }

        //方法二：
        //不管是不是粗体，统一变为细体
        div.style.fontWeight = 200 ;

        //方法三
        var arr = ['H1','H2','H3','H4','H5','H6','B','STRONG'];
        //console.log(arr.indexof('DIV'));
        //检测数组里是否有粗体的标签名，返回-1以外的都是粗体
        var isTrue = arr.indexof(div.tagName);
        console.log(isTure);
        //判断如是粗体标签名  就改变样式
        if(isTrue != -1){
            div.style.fontWeight = 200;
            div.style.color = 'red';
        }


需求2：

......

需求三：
