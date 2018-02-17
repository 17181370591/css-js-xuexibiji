https://www.imooc.com/learn/762
使用getJSON()方法异步加载JSON格式数据

        点击按钮getJSON从第一个参数获取json数据，点击后禁用按钮，json数据被遍历添加到ul里做li

        <div id="divtest">
            <div class="title">
                <span class="fl">我最喜欢的一项运动</span> 
                <span class="fr">
                    <input id="btnShow" type="button" value="加载" />
                </span>
            </div>
            <ul></ul>
        </div>
        
        <script type="text/javascript">
        //$('#btnShow').on('click',function(){
   	$('#btnShow').click(function(){
   	        $.getJSON('https://www.imooc.com/data/sport.json',function(data){
       		$('#btnShow').prop('disabled',true);
                $('ul').css('border','1px solid #f00')
                for(i=0;i<data.length;i++){
                        $('ul').append('<li>'+data[i].name+'</li>')}
                })
        })</script>
        
        
