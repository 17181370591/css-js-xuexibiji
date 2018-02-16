
jQuery中隐藏元素的hide方法/show方法
	
	1秒钟动画隐藏#al，2s动画显示#al，变化中background渐渐变红，完全变红后变紫色，如果不加参数则直接隐藏
	
	$("button:first").click(function() {
 		$("#a1").hide(1000,function(){
			$(this).show(2000,function(){$(this).css('background','#f0f')});
			$(this).css('background','#f00');
	})

	 连续点击多下，会重复多次，加上stop后会停止上一次的动画，从当前状态重新hide和show
	
	$("button").click(function() {
        	$("#a1").stop().hide(3000).show(3000)
   	})
	
jQuery中显示与隐藏切换toggle方法

	  $("*").click(function(){ 
		$( ".left" ).stop().slideToggle(333);    	#纵向
		$( ".right" ).stop().toggle(333)});		 #横向
	
	 分开写相当于：
	
	   $("*").click(function(){
		 if ( $( ".left" ).css('display') == 'none' ) {
			  $( ".left" ).show(); 
		} else{
			  $( ".left" ).hide();
		}
	  });

jQuery中下拉动画slideDown/slideUp,jQuery中上卷下拉切换slideToggle


	 slideDown/slideUp是竖直向下show/hide，与slideToggle效果类似。下面的代码$("#a1").toggle(1500)不会
	 等$("#a1").slideDown的回调函数结束，而是500ms秒和回调函数一同执行
	
	$("button:first").click(function(){
        	$("#a1").slideDown(500,function(){
			setTimeout(function(){$("#a1").css("background","#f0f")},555)
						})
		$("#a1").toggle(1500)			
        });
	
	
jQuery中淡出动画fadeOut,fadeIn,fadeTo
	
	淡入淡出效果，通过设置opacity,通过show显示;fadeTo可以自定义透明度最终值
	
    <script type="text/javascript">
	$('#animation').change(function(){
	v=$('#animation>option:selected').val();
	if(v==1){$("p").fadeOut(function(){setTimeout(function(){$("p").fadeIn()},333)})}
	else if(v==2){$("p").fadeOut('slow',function(){setTimeout(function(){$("p").show()},333)})}
	else if(v==3){$("p").fadeOut(3000,function(){setTimeout(function(){$("p").show()},333)})}
	else if(v==4){$("p").fadeOut(1000, "linear" ,function(){setTimeout(function(){$("p").show();alert('complete')},333)})}
	else if(v==5){$("p").fadeOut(function(){setTimeout(function(){$("p").show()},333)})}})
    </script>

	//     显示隐藏           .hide()+.show() = .toggle()
	//     下拉上卷           .slideUp()+.slideDown() = .slideToggle()
	//     淡入淡出           .fadeOut()+.fadeIn() = .fadeToggle()
	
	 <div id="mb" style="border:1px solid ;width:150px;height:50px;margin-top:20px;background:red">测试蒙版效果</div>
    	$("#mb").mouseover(function(){$(this).fadeTo(0,0.1)});
	$("#mb").mouseout(function(){ $(this).fadeTo(0,1)})
	
	
jQuery中动画animate
	
	 y用来判断interval是否运行；f函数用来每0.1秒增加10px宽度；
	
	var y=1;
   	function f() {
		$("#aaron").animate({width:'+=10'},100);
		$("#exec").val($("#aaron").css('width'))}
	$("#exec").click(function(){
		if(y){s=setInterval("f()",100);y=0}
		else{clearInterval(s);y=1};
	})
	
	//width: "toggle"			//设置为左右隐藏
	//height:"toggle"		//设置为上下滑动隐藏
	//opacity:"toggle"		//设置为淡出淡入隐藏  opacity是透明度
	除了定义数值，每个属性能使用'show', 'hide', 和 'toggle'。这些快捷方式允许定制隐藏和显示动画用来控制元素的显示或隐藏
	
	step:fx只返回最后一个动画里改变的属性，now是这个属性的当前值，step的fx和progress的fx不一样;
	$(fx.elem)是被改变对象的jquery对象，可直接用各种jquery方法和属性

	   $aaron.animate({
                height: '50',
		opacity:0.5,
		width:'toggle',
            }, {
                duration :2000,
                //每一个动画都会调用
                step: function(now, fx) {
                   $aaron.text('开始:'+fx.start+'结束:'+fx.end+'属性:'+fx.elem+'当前值:'+now);
		   $aaron.text('开始:'+fx.elem.id+'结束:'+$(fx.elem).prop('class'))
                }
	progress:arguments有3个值，分别是'改变的对象','完成度'和'剩余时间（ms）'
	
	 $aaron.animate({
                height: '50'
            }, {
                duration :2000,
                //每一步动画完成后调用的一个函数，
                //无论动画属性有多少，每个动画元素都执行单独的函数
                progress: function(now, fx) {			
                   $aaron.text('改变的对象:'+arguments[0]+'完成了:'+Math.round(arguments[1]*100)+'%剩余时间:'+arguments[2])

                }
