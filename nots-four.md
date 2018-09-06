javascript
===

1. js 如何检测一个变量是一个 String 类型？
```
typeof(obj) === "string"
typeof obj === "string"
obj.constructor === String
```
1. 如何用 js 去除字符串空格？
	1. 方法一：使用replace正则匹配的方法
		1. 去除所有空格: str = str.replace(/\s*/g,"")
		1. 去除两头空格: str = str.replace(/^\s*|\s*$/g,"")
		1. 去除左空格： str = str.replace( /^\s*/, “”)
		1. 去除右空格： str = str.replace(/(\s*$)/g, "")
```
var str = " 23 23 "; 
var str2 = str.replace(/\s*/g,"");
console.log(str2); // 2323

```
	1. 方法二：使用 str.trim() 方法  --- (局限性，无法去除中间空格)
```
var str = " hei hei "; 
var str2 = str.trim();
console.log(str2); //hei hei
```
1. 如何获取 URL 中字符串中的参数？
实例：http://www.runoob.com/jquery/misc-trim.html?channelid=12333&name=xiaoming&age=23
```
function showWindowHref(){
 	var sHref = window.location.href;
 	var args = sHref.split('?');
 	if(args[0] == sHref){
		return "";
    }
	var arr = args[1].split('&');
	var obj = {};
	for(var i = 0;i< arr.length;i++){
		var arg = arr[i].split('=');
        obj[arg[0]] = arg[1];
    }
	return obj;
}
var href = showWindowHref(); // obj
console.log(href['name']); // xiaoming
```

js 字符串操作函数
=
1. concat() – 将两个或多个字符的文本组合起来，返回一个新的字符串
1. indexOf() – 返回字符串中一个子串第一处出现的索引。如果没有匹配项，返回 -1
1. charAt() – 返回指定位置的字符
1. lastIndexOf() – 返回字符串中一个子串最后一处出现的索引，如果没有匹配项，返回 -1
1. match() – 检查一个字符串是否匹配一个正则表达式
1. substr() 函数 -- 返回从string的startPos位置，长度为length的字符串
1. substring() – 返回字符串的一个子串。传入参数是起始位置和结束位置
1. slice() – 提取字符串的一部分，并返回一个新字符串
1. replace() – 用来查找匹配一个正则表达式的字符串，然后使用新字符串代替匹配的字符串
1. search() – 执行一个正则表达式匹配查找。如果查找成功，返回字符串中匹配的索引值。否则返回 -1
1. split() – 通过将字符串划分成子串，将一个字符串做成一个字符串数组
1. length – 返回字符串的长度，所谓字符串的长度是指其包含的字符的个数
1. toLowerCase() – 将整个字符串转成小写字母
1. toUpperCase() – 将整个字符串转成大写字母
