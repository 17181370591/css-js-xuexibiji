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
    
    $('div:not(has(.pa)')         #含有不是p标签的任何其他标签的div，也可以含有.pa(class=pa)，.pa两边可以加引号可以不加
    
    $('div:contains(:not("asd")')     #内部任何文本不含有asd的div，asd两边可以加引号可以不加
    
   
jQuery选择器之内容筛选选择器
	$(':contains(text)')  			查找指定标签内字符串，文本含有text（后代元素含有也行）

	$(':parent')				查找有内容的标签,也可以是文本（包括空格），似乎等于:not(:empty)

	$(':empty')				查找内容为空的标签，不能含有任何标签和文本，似乎等于:not(:parent)

	$('has:(selector)')			查找指定标签，内部含有selector（后代元素含有也行）
	
	
jQuery选择器之属性筛选选择器
	
	$("div[name]") 匹配含有name属性的div元素

	$("div[name='test']") 匹配name值为test的div元素
	
	$("div[name|='test']") 匹配name值内部含有test的div元素,如name=aatestaa

	$("div[name!='test']") 匹配name值不为test的div元素,name=test a的元素也能匹配,没有name属性也能匹配

	$("div[name*='test']") 匹配name值包含test的div元素

	$("div[name^='test']") 匹配name值开头为test的div元素

	$("div[name$='test']") 匹配name值结尾为test的div元素

	$("div[id][name^='test']") 匹配有id属性且name值开头为test的div元素
	
	$("*[name]")和$("[name]") 匹配有name属性的所有标签
	
jQuery选择器之子元素筛选选择器

	$(".first-div a:first-child")查找class="first-div"下所有的a元素，且该a元素是它父元素下第一个子元素（父元素不需要满足.first-div）

	$(".first-div a:last-child")与first-child类似

	$(".first-div a:only-child")查找class="first-div"下所有的a元素，且该a元素是它父元素下唯一的子元素（父元素不需要满足.first-div，且不算文本元素）

	$(".last-div a:nth-child(2)")查找class="last-div"下的第二个a元素，条件同上

	$(".last-div a:nth-last-child(2)")查找class="last-div"下的倒数第二个a元素，条件同上

