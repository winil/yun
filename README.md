有时后台传到前台的数据包括了一些实体，如<就是&lt;，这时可以用一个函数deentityify把它转为html的格式，当然，这个函数我也是百度知道的。
<script>
		Function.prototype.method=function(name,fun){
    if(!this.prototype[name])
        this.prototype[name]=fun;
}

String.method('deentityify',function(){
    var entity={
        quot:'"',
        lt:'<',
        gt:'>'
    }
    console.log(1);
    return function(){
        return this.replace(/&([^&;]+);/g,function(a,b){
            var ret=entity[b];
            return typeof ret==='string'?ret:a
        })
    }
}());
var str='&lt;p&gt;&lt;img src=&quot;/ueditor/php/upload/image/20170426/1493199621873071.png&quot; title=&quot;1493199621873071.png&quot; alt=&quot;ka-2.png&quot;/&gt;&lt;/p&gt;'
console.log(str);
str.deentityify(); //转为html
console.log(str.deentityify());
	</script>
