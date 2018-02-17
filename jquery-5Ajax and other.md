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

使用getScript()方法异步加载并执行js文件

         <script type="text/javascript">
                $("#btnShow").bind("click", function () {
                    var $this = $(this);
                    jQuery.getScript('https://www.imooc.com/data/sport_f.js',function(){
                        $this.attr("disabled", "true");
                        for(i=0;i<data.length;i++){alert(data[i].name)} 
                    });
                })
        </script>

使用get()方法以GET方式从服务器获取数据

          get的第三个参数json表示数据格式，会返回object（类似字典），不填json会alert undefined，因为返回文本
  
            $(function () {
                $("#btnShow").on("click", function () {
                    var $this = $(this);
                    $.get('https://www.imooc.com/data/info_f.php',function(data){alert(data);
                        $this.attr("disabled", "true");
                        $("ul").append("<li>我的名字叫：" + data.name + "</li>");
                        $("ul").append("<li>男朋友对我说：" + data.say + "</li>");
                    },'json');
                })
            });
            
 使用post()方法以POST方式从服务器发送数据
           
                $("#btnCheck").bind("click", function () {
                    $.post('https://www.imooc.com/data/check_f.php',
                    {num:$("#txtNumber").val()},
                    function (data) {
                        $("ul").append("<li>你输入的<b>  "
                        + $("#txtNumber").val() + " </b>是<b> "
                        + data + " </b></li>");
                    });
                })
            
            
使用serialize()方法序列化表单元素值

       使用serialize()方法可以将表单中有name属性的元素值进行序列化，生成标准URL编码文本字符串，直接可用于ajax请求
       下面的alert内容是"Text1=%E5%95%8A&Text=10&Checkbox1=on"
           
        <form action="">
            <ul>
                <li>姓名：<input name="Text1" type="text" size="12" /></li>
                <li>
                    <select name="Text">
                        <option value="10">男</option>
                        <option value="1">女</option>
                    </select>
                </li>
                <li><input name="Checkbox1" type="checkbox" />资料是否可见 </li>
                <li id="litest"></li>
            </ul>            
        </form>                   
        <script type="text/javascript">
                $("#btnAction").bind("click", function () {                    
                    alert($('form').serialize())                      
                })</script>

使用ajax()方法加载服务器数据

           type类型是post，data是 post的数据，  success 是请求 成功时调用的函数
          
                $("#btnCheck").bind("click", function () {
                    $.ajax({
                        url:'https://www.imooc.com/data/check.php',
                        type:'post',
                    data: { num: $("#txtNumber").val()},
                            success: function (data) {
                            $("ul").append("<li>你输入的<b>  "
                            + $("#txtNumber").val() + " </b>是<b> "
                            + data + " </b></li>"+data.responseTex);
                        }
                    });
                })