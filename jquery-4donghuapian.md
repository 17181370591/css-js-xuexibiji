
jQuery中隐藏元素的hide方法

  $("button:first").click(function() {
 
              $("#a1").hide(1000,function(){
                $(this).show(2000,function(){$(this).css('background','#f0f')});
                $(this).css('background','#f00');
			  })
