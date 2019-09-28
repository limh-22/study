#第六章 DOM
##6.1 DOM的概念
#####6.1.1DOM的概念

DOM是文档对象模型，DOM对象不仅仅是一个普通的内置对象，他还是一个巨大的API的核心对象，它将对象的内容呈现在JS面前，并赋予了JS操作文档的能力。

#####6.1.2DOM和JavaScript的关系

一个web页面是一个文档，这种文档可以在浏览器窗口或者作为html源代码显示出来，但上述两种情况都是同一个文档，DOM提供了对同一份文档的另一种表现，存储和操作的方式，DOM能够使用JavaScript脚本语言进行修改。

#####6.1.3 DOM节点

加载html页面，web浏览器生成一个橡树一样的结构，用来表示页面的内部结构，DOM将这种结构理解为节点，根据w3c的htmlDOM标准，html文档找的所有内容都是节点。

> 整个文档是一个文档节点
> 每个html元素是元素节点
> html元素内的文本是文本节点
> 每个html属性都是属性节点
> 注释也是节点，叫注释节点

#####6.1.4 DOM树

DOM树体现着html页面的层级结构，而DOM树有DOM文档树和DOM元素树两种。DOM元素树包含的只有元素节点，而DOM文档树则包括DOM文档中的所有内容。

##6.2 获取元素
#####6.2.1 用ID获取元素
getElementsById()的方法，接受一个参数：获取元素的ID，如果没有找到相应元素，则返回该元素，否则返回Null
  
        //用变量  在文档中  找  元素  用ID  id
        var d = document.getElementById('d');

#####6.2.2 用标签名获取元素

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

#####6.2.3用类名获取元素

          var a = document.getElementsByClassName('a');
          console.log(a); 

#####6.2.4 用name属性值获取元素
getElementsByName()方法可以获取相同名称的name元素,返回一个伪数组对象.

        <input type="radio" name="sex" value="0">男 
        <input type="radio" name="sex" value="1">女
    
        var sex = document.getElementsByName('sex');
        console.log(sex);

#####6.2.4 用选择器获取元素

querySelector()和querySelectorAll()可以依靠选择器找到元素,但是前者只能找到元素列表的第一个元素,而后者可以全部找到.注意,该方法性能没有直接利用标签寻找.

        var ul = document.getElementById('ul')
        var x = document.querySelector('#div>div a');
        var lis = ul.querySelectorAll('li');
        console.log(lis);



##6.3 获取和设置元素中的其他信息
#####6.3.1 获取元素名 

当我们使用id获取元素的时候，元素的名称会和整个元素一起显示出来，如果想要拿到该元素的元素名，也就是标签名则需要用tagName属性。该属性只能获取，不能设置。

         var div = document.getElementById('mydiv');
         console.log(div.tagName);

#####6.3.2获取元素节点里的内容

当获取了元素之后，如果我们需要拿到元素中的内容（所有东西），则需要用另一种方法得到。元素里的内容可能包括：文本和元素。需要用innerHTML属性：

        var div = document.getElementById('mydiv');
        console.log(div.innerHTML);
          
        div.innerHTML = '你好';

#####6.3.3  获取元素节点中的文本

利用innerText属性获取的只是文本节点，不能是其他，当然innerText属性除了获取，也可以设置元素中的文本

        var div = document.getElementById('mydiv');
        console.log(div.innerText);
          
        div.innerText = '你好';

#####6.3.4获取元素的其他信息

利用className属性获取元素的类名,以字符串的形式返回.同时可以设置新的class类名,需要注意的是,返回值是一个字符串,如果更换其中一个类,则需要考虑该字符串中其他类是否应该一起设置.
 
        var div = document.getElementById('mydiv');
        console.log(div.className)

#####6.3.5 获取属性样式

style属性可以获取元素内联样式的所有属性，当然如果继续在style中找属性名，如backgroundColor，就可以得到该属性的值，以字符串的形式返回同时也可以设置该属性,从而达到增加或更改样式,需要注意的是,以JS形式增加的样式优先级大于CSS.


       <div style="background-color: blue"></div>

        var div = document.getElementsByTagName('div');
        //js拿到和获取的是内联
        console.log(div[0]);

#####6.3.6 获取元素的属性
div.getAttribute('')可以获取某个元素的属性值，要将属性名称放在括号中记得要用括号引起来，返回值就是字符串形式的属性值。

        var div = document.getElementById('mydiv');
        var a = document.getElementsByTagName('a');

        console.log(div.getAttribute('data-ww'));
        console.log(a.getAttribute('href'));

#####6.3.7 设置元素属性
setAttribute('')可以设置元素的某个属性，以一个是参数名，第二个参数是属性值，都需要用引号括起来以逗号分隔

         var div = document.getElementsByTagName('div');         
         var a = document.getElementsByTagName('a');         
            
         div[0].setAttribute('id','mydiv');
         a[0].setAttribute('href','http://baidu.com');

#####6.3.8 删除元素属性
使用removeAttribute(),可以删除某个元素的某个属性，括号中放入需要删除的属性名，用括号包括。

        var div = document.getElementById('mydiv');
        div.removeAttribute('div');

##6.4  增加元素
#####6.4.1创建元素节点
利用js创建一个元素的方法是，先在文档中创建一个标签document.createElement()括号中写一个标签名，当然要用字符串形式。创建之后不是就存在了，而是需要将这个已经创建的元素放到你想放到的元素（父元素）中去。


        //用一个变量承接在文档中‘创建’的一个元素
        var div = document.createElement('div');
        //将已经创建的元素放到想放的位置
        document.body.appendChild(div);
#####6.4.2创建文本节点
利用js创建文本节点，先在文档中创建文本document.createTextNode('')在括号中将要创建的字符串放入，最后插入到需要的元素中

        var p = document.getElementById('p');
        var text = document.createTextNode('一段文字');
        p.appendChild(text);

#####6.4.3 css样式赋予
style.cssText是一个css的样式集和，它可以把css层叠样式表中的css样式直接放在该属性后，就不需要一条一条的去赋予样式了，可以一次性赋予样式

       div.style.cssText =
      'width:100px;height:100px;background-color:blue;';

#####6.4.4 在某元素前插入创建的新元素
inserBefore（）这个函数和appendChild（）用法基本一致，都是向父级中插入一个子元素，但区别是
inserBefore（）是可以选择插入的位置，他要插入到哪一个子元素之前的位置，因此需要那个子元素inserBefore（）

    <ul id="ul">
        <li id="pg">苹果</li>
        <li id="jz">桔子</li>
        <li id="xj">香蕉</li>
    </ul>
    <script>
        var ul = document.getElementById('ul');
        //获取苹果
        var pg = document.createElement('pg');
        //获取桔子
        var li = document.createElement('li');
        //在父级中插入一个元素（插入元素，再谁前面）
        ul.insertBefore(li,jz);
        var t = document.createTextNode('火龙果');
        li.appendChild(t);
    </script>

## 6.5 删除和替换元素
##### 6.5.1  元素的替换
元素的替换是在父元素中的子元素需要被一个新的子元素替代，使用replaceChild（）方法，该方法有两个参数，第一个参数是将要替换的新元素，第二个是被替换的旧元素，中间用逗号分隔。

        var mydiv = document.getElementById('mydiv');
        var pyo = document.createElement('p');
        //在父元素中替换子元素，第一个是新的，第二个是旧的
        document.body.replaceChild(pyo,mydiv);

######6.5.2  元素的删除
元素的删除是在父元素的其中一个子元素需要删除，使用removeChild（）方法，将需要删除的元素放到括号中。

        var mydiv = document.getElementById('mydiv');
        document.body.removeChild(mydiv);

## 6.6 查找节点（node）
节点是在DOM树上的每一个节点，其中包括：元素，文本，属性，注释等等，常用的有三个，元素，文本，属性，

#####6.6.1 节点的属性
 
        var mydiv = document.getElementById('mydiv');
        document.body.nodeName();
        document.body.nodeValue();
        document.body.nodeType();

#####6.6.2 层次节点
节点可以分为父节点和子节点，兄弟节点两种，当我们知道其中之一的时候，可以用一些方法找到另一个

#####6.6.3获取所有子节点
使用childNodes属性拿到的是该元素下的所有节点，包含所有节点类型，不单单是元素
   
     <ul id="myul">
        <li>111</li>
        <li>222</li>
        <li>333</li>
    </ul>
    <script>
        var myul = document.getElementById('myul');
        //childNodes是所有节点
        console.log(myul.childNodes);
    </script>

#####6.6.4 获取第一个和最后一个子节点
用firstChild（）和lastChild()可以拿到该负元素的第一个和最后一个子节点,注意不一定是元素节点、

       <ul id="myul"><li>111</li><li>222</li><li>333</li></ul>
        <script>
            var myul = document.getElementById('myul');
            console.log(myul.firstChild);
            console.log(myul.lastChild);
        </script>

#####6.6.5  获取父节点
使用parentNode属性可以拿到该元素的父节点注意父节点只有一个

     <body>
        <ul id="myul"><li>111</li><li>222</li><li>333</li></ul>
        <script>
            var myul = document.getElementById('myul');
            console.log(myul.parentNode);
        </script>
     </body>

#####6.6.6 获取兄弟节点
使用 和 可以获得该元素的前一个和后一个兄弟节点，只能获取一个。

    <h2>h2</h2><div id="mydiv"></div><p>p</p>
    <script>
        var mydiv = document.getElementById('mydiv')
        console.log(mydiv.previousSibling)
        console.log(mydiv.nextSibling)
    </script>

##6.6.7 元素的宽高属性
#####6.7.1  offsetWidth和offsetHeight
需要获取一个元素的宽度和高度，使用style是无法获取的，所以我们选择使用offsetWidth和offsetHeight属性，该属性可以获取元素的占位宽高，它也包含了内边距和边框
   
        var mydiv = document.getElementById('mydiv');
        console.log(mydiv.style);//这种方式只能拿到内联样式
        console.log(mydiv.offsetWidth);

        
#####6.7.2clientWidth和clientHeight
clientWidth和clientHeight属性也可以获取元素的宽高，但与offsetWidth不同的是不包含边框

      console.log(mydiv.clientWidth);

##6.8  子元素与父元素的距离

offsetLeft和offsetTop是距离body左边界和上边界的距离，但如果改子元素使用了定位属性则offsetLeft和offsetTop参照的就不再是body而是距离他最近的父级元素

    <div id="a">
        <div id="b"></div>
    </div>
    <script>
        var b = document.getElementById('b');
        console.log(b.offsetLeft);
        console.log(b.offsetTop);
    </script>

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


