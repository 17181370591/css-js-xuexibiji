
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
