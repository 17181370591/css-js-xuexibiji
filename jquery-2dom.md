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
    
    $("#bt1").click(function() {        
        if (!$("p").length) return; 
	//去重，不加if的话连续点两次按钮1，p会被赋值成length=0的object，类似于空集合
        //通过detach方法删除元素  
        //只是页面不可见，但是这个节点还是保存在内存中 
        //数据与事件都不会丢失
    //    p = $("p").detach();
        //数据与事件会丢失
		p = $("p").remove();
		alert(p.length)
    });

    $("#bt2").click(function() {
        //把p元素在添加到页面中
        //事件还是存在
		alert(p.length);
        $("body").append(p);
    });
