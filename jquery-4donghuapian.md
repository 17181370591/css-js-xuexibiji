
jQuery中隐藏元素的hide方法/show方法
	
	1秒钟动画隐藏#al，2s动画显示#al，变化中background渐渐变红，完全变红后变紫色，如果不加参数则直接隐藏
	
	$("button:first").click(function() {
 		$("#a1").hide(1000,function(){
			$(this).show(2000,function(){$(this).css('background','#f0f')});
			$(this).css('background','#f00');
	})

	$("button").click(function() {
        	$("#a1").hide(3000).show(3000)
   	});
