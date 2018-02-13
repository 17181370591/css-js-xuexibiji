https://www.imooc.com/code/9710

jQuery鼠标事件之click与dbclick事件
    
    $(this).get(0).tagName 将jquery对象转成js对象，$(this).index()返回它在所有兄弟节点里的index（即第3个返回2），
    若要找它在同类型节点中的index可用 $('p').index($(this))，此处为p类型,或者用$($(this).get(0).tagName).index($(this))，
    因为此处$(this).get(0).tagName= 'p'，第二行function(i)的i应该是传入$(this)在所有p中的index
    
    $(document).ready(function(){
      $("p").each(function(i){
        $(this).on("dbclick",{a:i},function(event){
          alert($(this).get(0).tagName+"序号：" + $(this).index() + "。段落的数据为: " + event.data.a);
        });
      });
    });
    
    
