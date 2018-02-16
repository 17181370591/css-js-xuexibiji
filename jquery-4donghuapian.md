
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
	
	
jQuery中淡出动画fadeOut
	
	淡入淡出效果，通过设置opacity,通过show显示
	
    <script type="text/javascript">
	$('#animation').change(function(){
	v=$('#animation>option:selected').val();
	if(v==1){$("p").fadeOut(function(){setTimeout(function(){$("p").show()},333)})}
	else if(v==2){$("p").fadeOut('slow',function(){setTimeout(function(){$("p").show()},333)})}
	else if(v==3){$("p").fadeOut(3000,function(){setTimeout(function(){$("p").show()},333)})}
	else if(v==4){$("p").fadeOut(1000, "linear" ,function(){setTimeout(function(){$("p").show();alert('complete')},333)})}
	else if(v==5){$("p").fadeOut(function(){setTimeout(function(){$("p").show()},333)})}})
    </script>
