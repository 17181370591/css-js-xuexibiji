# css-js-xuexibiji(慕课网https://www.imooc.com/code/8342）
学习css/js/jq的笔记：
jquery：
jQuery对象转化成DOM对象
		var $div = $('div'); //jQuery对象
		var div=$div.get(0);  //这里div是dom对象
    
DOM对象转化成jQuery对象  
    var div = document.getElementsByTagName('div'); //dom对象
    $div =  $(div);         //这里div是jQuery对象
    
Query选择器之层级选择器    
    > （大于号）紧跟父子关系 如$("div > p")表示选择div下的直接层是p的节点。

    + （加号）  紧跟兄弟关系 如$("div + p")表示选择div同层的后面的相邻的p节点。

    ~ （波浪线）任意距离兄弟关系 如$("div + p")表示选择div同层的后面的p节点。

    (空格)    任意层父子关系 如$("div p")表示选择div下的p节点（不管中间隔多少层）。

    ,(逗号)   表示选择器组合，如$("div p, span p")表示div下p节点和span下p节点。
    
jQuery选择器之基本筛选选择器
    - 匹配第一个元素：`$(":first")`，如`$("div:first").css('color', 'red');`

    - 匹配最后一个元素：`$(":last")`

    - 匹配索引为index的元素：`$(":eq(index)")`

    - 匹配索引大于index的元素：`$(":gt(index)")`   //greater than

    - 匹配索引小于index的元素：`$(":lt(index)")`      //littler than

    - 匹配索引为偶数的元素：`$(":even")`

    - 匹配索引为奇数的元素：`$(":odd")`
    
    $('div:not(has(p)')         #含有不是p标签的任何其他标签的div，也可以含有p标签，p两边可以加引号可以不加
    
    $('div:contains(:not("asd")')     #内部任何文本不含有asd的div，asd两边可以加引号可以不加
    
   
