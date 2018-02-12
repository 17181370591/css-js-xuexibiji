#https://www.imooc.com/code/10369

jQuery节点创建与属性的处理/DOM内部插入append()与appendTo()

    $(body).append($('<input type="text" value="hehe">asd'))  #$('<div></div>'))用来产生div对象，用append添加
    append()和appendTo()似乎作用一样，只是攻受关系颠倒
    
DOM内部插入prepend()与prependTo()
    用法与append和appendTo一样，作为子元素，在父元素最前面插入，append是最后面

DOM外部插入after()与before()

    $(".test1").after($('<div>asd</div>'),$('<div>ddd</div>'))
    $(".test2").before('<p style="color:red">before</p>', '<p>多参数</p>')
    before与after都是用来对相对选中元素外部增加相邻的兄弟节点
    2个方法都支持多个参数传递after(div1,div2,....) 可以参考右边案例代码
    after向元素的后边添加html代码，如果元素后面有元素了，那将后面的元素后移，然后将html代码插入
    before向元素的前边添加html代码，如果元素前面有元素了，那将前面的元素前移，然后将html代码插
    
DOM外部插入insertAfter()与insertBefore()
    insertAfter与after的关系和append()与appendTo()关系一样；
    所以insertAfter()，insertBefore()，appendTo()，prependTo()这四个东西根本没用
    
    
DOM节点删除之empty()的基本用法
    
    $("#test").empty();
    empty 顾名思义，清空方法，但是与删除又有点不一样，因为它只移除了 指定元素中的所有子节点。
    这个方法不仅移除子元素（和其他后代元素），同样移除元素里的文本。因为，根据说明，元素里任何文本字符串都被看做是该元素的子节点。

 DOM节点删除之remove()的有参用法和无参用法
 
        $("p:contains(1)").remove()         无参数。remove移除本身，empty删除自身内部所有东西，匹配:empty
        $("p").remove(":contains('1')")         有参数，效果和上一行一样
        如果不通过remove方法删除这个节点其实也很简单，但是同时需要把事件给销毁掉，这里是为了防止"内存泄漏"，
        所以前端开发者一定要注意，绑了多少事件，不用的时候一定要记得销毁
        
DOM节点删除之保留数据的删除操作detach()

    detach可以删除节点，类似remove，但remove后的节点重新添加事件已经被销毁掉，detach会保留
    $("p").detach()这一句会移除对象，仅仅是显示效果没有了。但是内存中还是存在的。当你append之后，又重新回到了文档流中。就又显示出来了。
    
    $("#bt1").click(function(){        
        if(!$("p").length){return} 	//去重，不加if的话连续点两次按钮1，p会被赋值成length=0的object，类似于空集合
        //通过detach方法删除元素  
        //只是页面不可见，但是这个节点还是保存在内存中         
    	p = $("p").detach();	//数据与事件都不会丢失
	//p = $("p").remove();  //数据与事件会丢失
	alert(p.length)});

    $("#bt2").click(function() {
        //把p元素在添加到页面中
        //事件还是存在
		alert(p.length);
        $("body").append(p);
    });

DOM拷贝clone()

	clone方法比较简单就是克隆节点，但是需要注意，如果节点有事件或者数据之类的其他处理,我们需要通过clone(true)传递一个布尔值true用来指定，
	这样不仅仅只是克隆单纯的节点结构，还要把附带的事件与数据给一并克隆了，arron2的克隆会克隆事件，所有点新生成的节点也会出发arron2
	 点击事件继续生成新节点
	
    <script type="text/javascript"> 
        //只克隆节点
    	//不克隆事件
	    $(".aaron1").on('click', function() {  
	        $(".left").append( $(this).clone().css('color','red') )
	    })
    	//克隆节点
    	//克隆事件
	    $(".aaron2").on('click', function() {
	        $(".left").append( $(this).clone(true).css('color','yellow') )
	    })
    </script>
    
DOM替换replaceWith()和replaceAll()
	
	$("p:eq(1)").replaceWith('<a style="color:red">替换第二段的内容</a>')
	#将第二个p替换成'<a style="color:red">替换第二段的内容</a>'，下一行作用一样。replaceWith()和replaceAll()也是攻受关系颠倒
	$('<a style="color:red">替换第二段的内容</a>').replaceAll('p:eq(1)')
	
DOM包裹wrap()方法

	 给匹配的元素包裹指定标签，wrap('<div></div>')和wrap(function(){return '<div></div>';}),效果一样
	 wrap('<div>')/wrap('<div/>')/wrap('<div></div>')三种写法都可以,
	但若写成$('p').wrap('div')，它就会复制文档中的第一个div元素作为包裹元素
	
	$('.aaron1').on('click',function(){$('p').wrap($('<div></div>').css('padding','5px'))});
	$('.aaron2').on('click',function(){$('a').wrap(function(){return '<div></div>'})})
	
DOM包裹wrapAll()方法
	
	 给所有有元素添加同一个父元素a（父元素a包裹所有子元素）。所有元素的父元素会被全部清空，
	 元素间的其他元素会被移动到父元素a外（后面）。参数为函数时会分开包裹，切勿使用
	$('p').wrapAll('<div></div>')
	
DOM包裹wrapInner()方法
	
	 为选定元素的所有子元素加一个wrap.如果子元素只有文本元素也添加
	 $('div').wrapInner('<p></p>')
	 $('div').wrapInner(function() {return '<p></p>'; })
	
DOM包裹unwrap()方法
	
	 把父元素删除，unwrap()括号里输入任何参数都无效
	$(".aaron1").click(function(){$('p:first').unwrap()})

jQuery遍历之children()方法
	
	 childeren只找子元素，不找其他后代元素，参数是进一步筛选
	$("div").children().children()
	$("div").children(".selected")

jQuery遍历之find()方法

	find()方法可以查找后代元素，children是父子关系查找，find是后代关系（包含父子关系),必须加参数。
	find()相当于空格，children相当于>
	
jQuery遍历之parents()方法
	
	parents()方法可以查找祖先元素，类似find与children的区别，parent只会查找一级，parents则会往上一直查到查找到祖先节点
	

jQuery遍历之closest()方法（从自己开始找祖先）

	$("div").closet("li');
	起始位置不同：.closest开始于当前元素 .parents开始于父元素(如果起始位置本身满足条件closet就返回本身）
	遍历的目标不同：.closest要找到指定的目标，.parents遍历到文档根元素，closest向上查找，
	直到找到一个匹配的就停止查找，parents一直查找到根元素，并将匹配的元素加入集合
	结果不同：.closest返回的是包含零个或一个元素的jquery对象，parents返回的是包含零个或一个或多个元素的jquery对象
	
jQuery遍历之next()方法和prev方法
	
	next()方法查找指定元素集合中每一个元素紧邻的后面同辈元素的元素集合
	 下行表示class=item的相邻的属性z含有文本asd的兄弟节点，更改其css
	$('.item').next('[z*=asd]').css('color','#f00')
	
	 下行表示class=item的相邻的前一个兄弟节点，然后去掉第一个元素，更改css
	$('.item').prev(':gt(0)').css('border', '1px solid blue');

jQuery遍历之siblings()
	
	 下行表示class=item的所有兄弟节点（不选取自己）里class=item-1的元素，更改css
	$('.item').siblings('.item-1').css('border', '2px solid blue')
	 下行表示class=item的所有兄弟节点（不选取自己），然后取最后一个元素，更改css
	$('.item').siblings(':last').css('border', '2px solid blue')
	
	
	
	
