JQuery介绍：JQuery是一个js库

- 优点：轻量级；链式编程；隐式迭代；跨浏览器兼容；样式动画支持，大大简化了DOM操作；支持插件扩展开发，有丰富的第三方插件；免费开源

- 入口函数

- ```JavaScript
  $(function () {
  //代码
  });
  
  $(document).ready(funciton {});
  ```

- 等着DOM结构渲染完毕即可执行内部代码，不必等到所有外部资源加载完成JQuery帮我们完成了封装

- 引入JQuery：<script src='jquery.min.js'></script>

- JQuery顶级对象：$

  - DOM对象转换为JQuery对象：$(DOM对象)；
  - JQuery对象转换为DOM对象：$('div').get(index)    $     ('div')[index] 

- JQuery修改样式：$('div').css('background','green');

- 基本选择器：

  - $('#id')指定id元素
  - $('.class')指定类元素
  - $('div,p,li')获取多个元素
  - $('ul>li')子代
  - $('*')所有元素
  - $('div')根据标签获取元素
  - $('li.class')交集获取
  - $('ul li')后代

- 隐式迭代：遍历内部DOM元素（伪数组形式存储）的过程就叫做隐式迭代

- 筛选选择器：

  - $('li:first'):第一个元素
  - $('li:last')最后一个元素
  - $('li:eq(2)')索引为2的元素
  - **$('li:odd')索引为奇数的所有元素**
  - **$('li:even')索引为偶数的所有元素**

- **JQuery筛选方法**

  - $('li').parent()删选亲父级元素
  - $('li').parents('div')筛选祖先元素div
  - $('ul').children('li')筛选子集，如果不加参数，获取所有的，如果添加指定的元素按照指定的找
    - $('ul').children();
  - $('ul').find('li')筛选后代，不一定是亲儿子
  - $('li').siblings('li')筛选兄弟
  - $('li').nextAll()获取后面的所有元素
  - $('li').prevAll()获取前面的

- 判断是否具有某个类名：$('div').hasClass('son');

- 指定索引方法：$('div').eq(index);

- 获取当前索引值：index();

- ```JavaScript
  //当点击li的时候获取下标
  $('li').click(function () {
     	var i = $(this).index();
      console.log(i);
  });
  ```

- （打印对象的属性和方法：console.dir(li);）

- 添加事件：（下拉菜单）,show,hide,toggle;

- 添加事件：$(document).click(function () {})

- JQuery样式操作

  - 参数只写属性名，则是返回属性值：$(this).css('color')

  - 参数是属性名，属性值：$(this).css('color','green');

  - 参数可以使对象形式，方便设置多组样式：$(this).css({color:'white',fontSize:'20px'});

  - ```javascript
    $('input').click(function () {
        $('div').css({
            width : 300,
            height : 300,
            background : 'blue',
            fontSize : '66px'
        });
    });
    ```

    

- 设置类样式方法，等同于原生JS的classList，可以操作类样式

  - 添加类：$('div').addclass('current');
  - 移除类：$('div').removeclass('current');
  - 切换类：$('div').toggleclass('current');
  - 原生JS中的className会覆盖元素原先的类名，JQuery里类操作只是对指定类进行操作，不影响原先类名

- JQuery效果(当有动画效果的时候，一定要加上stop，防止动画同时出现的效果)

  - 显示隐藏效果：
    - show(速度，swing/linear,效果结束之后的执行函数);
    - hide()
    - toggle()
  - 滑动效果(参数与显示隐藏效果的一样)：
    - slideDown(),slideUp(),slideToggle();
  - 事件切换：hover([over],out);
  - 淡入淡出效果：
    - fadeIn:淡入（渐显，渐明）
    - fadeOut:淡出
    - fadeToggel:切换
    - fadeTo(speed,opacity):到达某个位置即停止(opacity透明度，范围为：0-1，必须写)；
  - 自定义动画：(speed:slow,normal,fast)**只能给元素添加**
    - animate(params,[speed],[easing],[fn]);
    - params:想要更改的样式的属性，以对象形式传递，必须写，符合参数用驼峰命名法，其余参数可省略
    - 

- JQuery属性操作：

  - 固有属性的获取和设置：prop();    prop('属性','属性值')；
  - 自定义属性的设置与获取：attr('属性');    attr('属性'，'属性值');

- 事件：

  - 改变即触发事件：change

  - 输入即触发事件：oninput

  - 滚动即触发事件：scroll（滚动时完成某些事情）

  - ```javascript
    $(window).scroll(function () {
        console.log(123);
        console.log(Math.random());
    });
    ```

    

- 数据缓存：data() ，当做变量存储**(自定义属性)**

  - 附加数据语法：data('name','value');//向被选中元素添加数据

  - 获取数据语法：data('name');//向被选中元素获取数据

  - ```javascript
    //data()可以在指定的元素上存储数据，并不会修改DOM元素结构，所以元素上无法查看，一旦页面刷新，之前数据被移除
    $('input').click(funciton () {
          //将index = '666'这个属性添加给img标签
          $('img').data('index',666);
    	 console.log( $('img').data('index') );
    });
    ```

    

- JQuery内容文本值：

  - 普通元素内容：html();获取元素内容；  html('内容');设置元素内容
  - 普通元素文本内容：text();获取文本内容； text('文本内容');设置文本内容
  - 表单的值：val();获取表单的值；

- 给小数点保留2位小数：toFixed(2)

- 获取祖先元素：parents（'div'）;

- JQuery元素操作

  - 遍历元素：
    - JQuery隐式迭代是对于同一类元素做了同样的操作，如果想要给同一类元素不同操作就遍历(使用此方法要转换对象类型)
      - 遍历元素：$('div').each(function (index,domElm)) {xxx;})
      - **遍历数据：$.each(object,function(index,element)(xxx;))**
    - 创建元素：
    - $('<li></li>');
    - 添加元素：
      - element.append('内容')  //把内容放在匹配元素内部最后面（父子）
      - element.appendTo('内容')   //（子->父）
      - element.prepend('内容')   //把内容放入目标元素前面（兄弟）
      - element.prepentTo('内容')   //（子->父）
      - element.before('内容')  //把内容放在目标元素前面（外部添加）
      - element.after('内容')   //把内容放在目标元素后面（外部添加）
    - 删除元素
      - element.remove()   //删除匹配的元素（本身）
      - element.empty()    //删除匹配的元素集合中所有的子节点
      - element.html()    //清空匹配的元素内容
      - 第二个和第三个作用等价，都可以删除元素里的内容，不过html()还可以设置内容

- JQuery尺寸：（获取的Number类型，可直接运算）

  - width(),height()     //只算宽高
  - innerWidth(),innerHeight()    //包含padding+width
  - outerWidth(),outerHeight()  //包含padding+border+width
  - outerWidth(true),outerHeight(true)   //包含padding+border+margin+width
  - 以上参数为空则为获取，返回的是数字型，如果参数为数字，则是修改相应值，参数可不必写单位

- JQuery位置

  - offset() :被选元素相对于**文档**的偏移坐标，跟父级没有关系（top ，left）

    - 例如：offset().top    //用户获取距离文档顶部的距离；offset({top:10,left:30})    //设置元素偏移；

  - position():被选元素相对于带有定位的父级偏移坐标，如果父级都没有定位，则以文档为准

    - 例如：position().top   //用于获取距**定位父级**顶部的距离，该方法只能获取

  - scrollTop(),scrollLeft()    //设置或获取元素被卷去的头部和左侧，不限参数是获取，参数为不带单位的数字则是设置被卷去的头部

  - scroll事件：谁有滚动条加给谁，当整个浏览器都有滚动条，该事件加给**window**

  - ```javascript
    //设置点击按钮返回顶部
    $('div').click(function () {
        $('div').animate({
            scrollTop : 0
        },1000);
    });
    //在滚动过程中打印距离顶部的距离
    $('div').scroll(function () {
        console.log($('div').scrollTop());
    });
    ```

- JQuery事件

  - 注册：element.事件(function () {});

  - 事件处理：on()绑定事件：on()方法在匹配元素上绑定一个或多个事件的事件处理函数

    - element.on(events,[selector],fn)
    - events:一个或多个用空格分隔的事件类型，如click或keydown
    - selector:元素的子元素选择器

  - on()方法优势：

  - ```javascript
    //优势一：可以绑定多个事件，多个处理程序
    $('div').on({
        mouseover : function () {},
        mouseout : function () {},
        click : function () {}
    });
    
    
    //优势二：可以事件委派操作（子元素的事件绑定在父元素身上）
    //在此之前bind(),live(),delegate()等方法来处理事件绑定或事件委派，最新版的用on代替
    //动态创建li
    $('ul').on('click','li',function () {
    	console.log($(this).html());
    });
    //给动态创建的元素li添加点击事件
    $('li').on('click',function () {
        console.log($(this).html());
    });
    $('<li>yuan</li>').appendTo('ul');
    
    
    //优势三：可以给动态生成的元素绑定事件解绑
    $('ul').off('click','li');
    
    ```

    

  - 事件处理off()解绑事件：

    - $('p').off       //解绑p元素所有事件处理程序
    - $('p').off('click')        //解绑p元素上面的点击事件
    - $('p').off('click','li')        //解绑事件委托

  - 如果有的事件只想触发一次，可以使用one()来绑定事件

  - 自动触发事件：trigger()【会触发默认行为】

    - element.click()     //第一种简写模式
    - element.trigger('type')       //第二种自动触发模式
    - element.triggerHandler(type)        //第三种自动触发模式【默认效果不会触发，例如：input获取焦点有光标】

  - oninput:边输入边执行事件处理程序；

  - change：当输入完成之后确定发生改变执行事件处理程序；

- JQuery事件对象：事件被触发就会有事件对象的产生     event

  - element.on(events,[selector],function(event){})
  - 阻止默认行为：event.preventDefault();或者  return  false;
  - 阻止冒泡：event.stopPropagation();    var  ev = e || window.event;

- JQuery插件

  - 引入插件必须放在所有标签之后，</body>之前
  - 图片懒加载：图片使用延迟加载可提高网页下载速度，它也能帮助减轻服务器负载，当我们页面滑动到可视区域再显示图片（使用JQuery插件库EasyLazyLoad，注意此时的js引入文件和js调用必须写到DOM元素《图片》最后面）

- 普通函数（自调用函数，命名函数，定时器函数）里面，this指向window

- 构造函数里，this指向实例对象

- 对象中this指向当前对象，事件处理函数中this指向事件源

















































































