https://www.imooc.com/code/9710

jQuery鼠标事件之click与dbclick事件    
    $(this).get(0).tagName 将jquery对象转成js对象，$(this).index()返回它在所有兄弟节点里的index（即第3个返回2），
    若要找它在同类型节点中的index可用 $('p').index($(this))，此处为p类型,或者用$($(this).get(0).tagName).index($(this))，
    因为此处$(this).get(0).tagName(也可以用prop('tagName')获取tagname)= 'p'，第二行function(i)的i应该是传入$(this)在所有p中的index
    
    $(document).ready(function(){
      $("p").each(function(i){
        $(this).on("click",{a:i},function(event){
          alert($(this).get(0).tagName+"序号：" + $(this).index() + "。段落的数据为: " + event.data.a);
        });
      });
    });
    
jQuery鼠标事件之mousedown与mouseup事件（鼠标按下和松开，合在一起构成click）
jQuery鼠标事件之mousemove事件（光标移动）
jQuery鼠标事件之mouseover与mouseout事件
jQuery鼠标事件之mouseenter与mouseleave事件

    mouseenter只监听当前元素，不监听子元素，mouseover会监听子元素
    mouseenter监听 父元素，光标进入子元素不触发。mouseover监听 父元素，光标进入子元素会触发mouseout
    mouseleave mouseenter只会在当前绑定元素执行，不会冒泡执行父元素的事件;mouseover mouseout冒泡执行父元素事件
    
jQuery鼠标事件之hover事件
    
    第一个函数是mouseenter ，第二个是mouseleave
    $("p").hover(
        function() {
            $(this).css("background", 'red')
        },
		      function() {
            $(this).css("background", 'yellow')
        }  
    ); 
    
jQuery鼠标事件之focusin事件(输入框等获得焦点)

jQuery鼠标事件之focusout事件(输入框等失去焦点)

jQuery表单事件之blur与focus事件

	blur与focus只对当前元素有效，不会冒泡；
	 第1段.aaron是div，无法blur和focus，而且focus不冒泡，所以没有效果；
	 第2段inupt获取光标后会加border；
	 第3段.aaron是div，无法blur和focus，但focusin冒泡，所以div的子元素input被focusin后，val会改变，
	 在点input的时候会一级一级的往上面查父元素，如果父元素有事件就执行了，所以看到了效果。这叫事件冒泡
	$(".aaron").focus(function() {
        	$(this).css('border', '2px solid red')
    	})   ;
	$(".aaron").find('input').focus(function() {
        	$(this).css('border', '2px solid red')
   	 });
    	$(".aaron1").focusin(function() {
       	 	$(this).find('input').val('冒泡捕获了focusin事件')
    	})

	 
jQuery表单事件之change事件(冒泡)	 
	 
	  change在form元素有改变时调用，下几行表示被改变时s赋值为input父元素下的checked的合集，将val按顺序拼接后赋值v
	 $(".aaron1>input").change(function(e) {
		var v='';var s=$(this).parent().find(':checked');
		for(i=0;i<s.length;i++){v=v+s.eq(i).val();}
        	$("#result").html(v);
    	})

jQuery表单事件之select事件

	select事件只能用于<input>元素与<textarea>元素

jQuery键盘事件之keydown()与keyup()事件

    $('.target1').keypress(function(e) {
        $("em:first").text(e.target.value)
    });

    //监听键盘按键
    //获取输入的值
    $('.target2').keyup(function(e) {
        $("em:last").text(e.target.value)
    });
    
jQuery键盘事件之keypress()事件
	keypress事件与keydown和keyup的主要区别:
	只能捕获单个字符，不能捕获组合键
	无法响应系统功能键（如delete，backspace）
	不区分小键盘和主键盘的数字字符
	
