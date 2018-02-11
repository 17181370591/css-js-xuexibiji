#https://www.imooc.com/code/10369

jQuery节点创建与属性的处理/DOM内部插入append()与appendTo()

    $(body).append($('<input type="text" value="hehe">asd'))  #$('<div></div>'))用来产生div对象，用append添加
    append()和appendTo()似乎作用一样，只是攻受关系颠倒

DOM外部插入after()与before()

    $(".test1").after($('<div>asd</div>'),$('<div>ddd</div>'))
    $(".test2").before('<p style="color:red">before</p>', '<p>多参数</p>')
    before与after都是用来对相对选中元素外部增加相邻的兄弟节点
    2个方法都支持多个参数传递after(div1,div2,....) 可以参考右边案例代码
    after向元素的后边添加html代码，如果元素后面有元素了，那将后面的元素后移，然后将html代码插入
    before向元素的前边添加html代码，如果元素前面有元素了，那将前面的元素前移，然后将html代码插

