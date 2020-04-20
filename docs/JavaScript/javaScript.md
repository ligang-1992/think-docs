##### 1、秒转换为时间

```
<script type="text/javascript">
	function formatSeconds(value) {
		var secondTime = parseInt(value); // 秒
		var minuteTime = 0; // 分
		var hourTime = 0; // 小时
		if (secondTime > 60) { //如果秒数大于60，将秒数转换成整数
			//获取分钟，除以60取整数，得到整数分钟
			minuteTime = parseInt(secondTime / 60);
			//获取秒数，秒数取佘，得到整数秒数
			secondTime = parseInt(secondTime % 60);
			//如果分钟大于60，将分钟转换成小时
			if (minuteTime > 60) {
				//获取小时，获取分钟除以60，得到整数小时
				hourTime = parseInt(minuteTime / 60);
				//获取小时后取佘的分，获取分钟除以60取佘的分
				minuteTime = parseInt(minuteTime % 60);
			}
		}
		var result = "" + parseInt(secondTime) + "秒";

		if (minuteTime > 0) {
			result = "" + parseInt(minuteTime) + "分" + result;
		}
		if (hourTime > 0) {
			result = "" + parseInt(hourTime) + "小时" + result;
		}
		return result;
	}
</script>
```

2、回车键绑定事件

```
// 回车事件绑定
$('#search_input').bind('keyup', function(event) {
    if (event.keyCode == "13") {
        //回车执行查询
        $('#search_button').click();
    }
});

// JS监听某个DIV区域
$("#queryTable").bind("keydown",function(e){
        // 兼容FF和IE和Opera    
    var theEvent = e || window.event;    
    var code = theEvent.keyCode || theEvent.which || theEvent.charCode;    
    if (code == 13) {    
        //回车执行查询
            $("#queryButton").click();
        }    
});

//回车事件  JS监听body区域
document.onkeydown = function (event) {
    var e = event || window.event;
    if (e && e.keyCode == 13) { //回车键的键值为13
        $("#login").click(); //调用登录按钮的登录事件
    }
};
```

##### 3、日期字符串转换为时间戳
```
var date = '2015-03-05 17:59:00.0';
date = date.substring(0,19);    
date = date.replace(/-/g,'/'); 
var timestamp = new Date(date).getTime();
document.write(timestamp);
```
##### 4、时间戳转换为所需格式的时间字符串
```
    var dateFormat = function(timestamp){
        var time = newDate(timestamp)    //先将时间戳转为Date对象，然后才能使用Date的方法
        var year = time.getFullYear(),
            month = time.getMonth() + 1 ,  //月份是从0开始的
            day = time.getDate(),
            hour = time.getHours(),
            minute = time.getMinutes(),
            second = time.getSeconds()
            //add0()方法在后面定义
        return  year+'-'+this.add0(month)+'-'+ this.add0(day)+''+this.add0(hour)+':'+this.add0(minute)+':'+this.add0(second)  
     }
     
     var add0 = function(m){
        return m < 10 ? '0' + m: m
     }
```


