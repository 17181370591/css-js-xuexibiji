https://www.imooc.com/learn/762

使用load()方法异步请求数据

        $("#btnShow").bind("click", function () {
            var $this = $(this);
            $("ul").load('https://www.imooc.com/data/fruit_part.html',function(){$this.attr("disabled", "true"); 
            });
        })
        
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
                    jQuery.getScript('https://www.imooc.com/data/sport_f.js',function(data){
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
                
使用ajaxSetup()方法设置全局Ajax默认选项

                $('body').append('<div class="a"></div>');
                $.ajaxSetup({type:'post',success:function(data){
                       $('.a').empty(); $('.a').append(data)
                }});                 
                $("#btnShow_1").bind("click", function () {
                    $.ajax({
                        data: { num: $("#txtNumber").val() },
                        url: "https://www.imooc.com/data/check.php"
                    });
                })
                $("#btnShow_2").bind("click", function () {
                    $.ajax({
                        data: { num: $("#txtNumber").val() },
                        url: "https://www.imooc.com/data/check_f.php"
                    });
                })
                
使用ajaxStart()和ajaxStop()方法

        ajaxStart()和ajaxStop()方法是绑定Ajax事件。
        ajaxStart()方法用于在Ajax请求发出前触发函数，ajaxStop()方法用于在Ajax请求完成后触发函数。它们的调用格式为：
        $(selector).ajaxStart(function())和$(selector).ajaxStop(function())
        其中，两个方法中括号都是绑定的函数，当发送Ajax请求前执行ajaxStart()方法绑定的函数，请求成功后，执行ajaxStop ()方法绑定的函数。                  
          <div id="divtest">
            <div class="title">
                <span class="fl">加载一段文字</span> 
                <span class="fr">
                    <input id="btnShow" type="button" value="加载" />
                </span>
            </div>
            <ul> 
               <li id="divload"></li>
            </ul>
        </div> 
        
        <script type="text/javascript">
            $("#divload").ajaxStart(       //请求 成功前显示
                function () { 
                    $(this).html("正在请求数据...");
                } 
                );
              $("#divload").ajaxStop(function(){    ///请求 完成后显示
                   $(this).html("数据请求完成！");
                }); 
                
                $("#btnShow").bind("click", function () { 
                    var $this = $(this); 
                    $.ajax({
                        url: "https://www.imooc.com/data/info_f.php", 
                        dataType: "json",
                        success: function (data) {
                        //    $this.attr("disabled", "true");
                        $("ul").append("<li>我的名字叫：" + data.name + "</li>");
                        $("ul").append("<li>男朋友对我说：" + data.say + "</li>");
                        }
                    });
                })
        </script> 
        
表单验证插件——validate 
           
       <form id="frmV" method="get" action="#">
            <div id="divtest">
                <div class="title">
                    <span class="fl">表单验证插件</span>  
                    <span class="fr">
                        <input id="btnSubmit" type="submit" value="提交" />
                    </span> 
                </div>
                <div class="content">
                    <span class="fl">邮箱：</span><br />
                    <input id="email3" name="email" type="text" /><br />
                    <span class="tip">1<br></span>
                       <span class="f2">shouji：</span><br />
                    <input id="email23" name="email2" type="text" /><br />
                    <span class="tip2">2</span>
                </div> 
            </div>
        </form>
        
        $('form').validate，rules是对各个输入框的name添加规则，errorPlacement设置错误显示在哪个地方,
        messages自己定义报错信息。 下面是validate的插件和不设置messages时用中文报错的插件
        <script type="text/javascript" src="https://www.imooc.com/data/jquery.validate.js"></script>
        <script type="text/javascript" src="https://www.imooc.com/data/jquery.validate.messages_cn.js"></script>
       
        <script type="text/javascript">
        $('#frmV').validate({
            rules:{
                email:{
                    required:true,email:true
                    
                },email2:{
                    required:true,rangelength:[3,6],max:1
                    
                }
                
            },
             messages:{
                   email:{
                   required:'请输入email',email:'email格式错误'                    
                },email2:{
                    required:'请输入2b',rangelength:'3到5谢谢',max:'小鱼1'                    
                }                
            },
            errorPlacement:function(e,el){
                n=el.prop('name');
                if(n=='email'){
                    $('.tip').append(e)
                    
                }
                else if(n=='email2'){
                    $('.tip2').append(e)
                    
                }
                
            }
        })</script>
        
 表单插件——form
        
        form插件：<script type="text/javascript" src="http://www.imooc.com/data/jquery.form.js"></script>
        
        <form id="frmV" method="post" action="#">
            <div id="divtest">
                <div class="title">
                    <span class="fl">个人信息页</span> 
                    <span class="fr">
                        <input id="btnSubmit" type="submit" value="提交" />
                    </span>
                </div>
                <div class="tip"></div>
                <div class="content">
                    <span class="fl">用户名：</span><br />
                    <input id="user" name="user" type="text" /><br />
                    <span class="fl">昵称：</span><br />
                    <input id="nick" name="nick" type="text" />
                    <div class='e'></div>
                </div>
            </div>
        </form>
        
        option 里写了type：post，form的html代码没有method：post也会以post方式提交。target似乎是ajax数据展示的target
        
        <script type="text/javascript">
            $(function () {
                var options = {
                    url: "https://www.imooc.com/data/form_f.php",  
                    target: ".tip",
                    type:'post' 
                } 
                $('#frmV').ajaxForm(options)
            })</script>
