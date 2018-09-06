cookie 
=


- web 浏览器储存的少量数据
	- 最早为服务端设计，作为HTTP协议的扩展实现
	- 会自动在浏览器和服务器之间传输
- 通过读取 cookie 检测是否支持
- 属性
	- 名
	- 值
	- max-age
	- path
	- domain
	- secure
- 有效期
	- 浏览器会话，一旦用户关闭浏览器，数据就丢失
	- 设置 max-age = seconds -> 告诉浏览器有效期
- 作用域
	- 通过**文档源**和**文档路径**确定
	- 通过**path**和**domain**配置
	- web 页面同目录或子目录文档都可以访问
- 保存数据的方法
	- document.cookie 设置一个符合目标的字符串，如下
- 读取 document.cookie 获得 '; ' 分隔的字符串，key=value，解析得到结果
```
document.cookie = 'name=qiu; max-age=9999; path=/; domain=domain; secure';

document.cookie = 'name=aaa; path=/; domain=domain; secure';
// 要改变 cookie 的值，需要使用相同的名字、路径和域，新的值
// 来设置 cookie，同样的方法可以用来改变有效期

// 设置 max-age 为 0 可以删除指定 cookie

//读取 cookie，访问 document.cookie 返回键值对组成的字符串，
//不同键值对之间用 '; ' 分隔。通过解析获得需要的值
```

javascript 定义对象的方法
=
- 对象字面量：```var obj = {};```
- 构造函数：```var obj = new Object();```
- Object.create()：```var obj = Object.create(Object.prototype);```


===运算判断符相等的流程是怎样的
=
- 两个值不是相同类型 -> 不相等
- 都是null或者都是undefined -> 相等
- 都是布尔类型true或者都是false -> 相等
- 其中有一个是**NaN** -> 不相等
- 都是数值型并且数值相等 -> 相等（-0 = 0）
- 都是字符串并且在相同位置包含相同的16位值 -> 相等 --- 如果在长度或者内容上不等 -> 不相等 --- 两个字符串显示结果相同但是编码不同==和===都认为他们不相等
- 如果他们指向相同对象、数组、函数，它们相等 --- 如果指向不同对象，他们不相等

==运算符判断相等的流程是怎样的
=
1. 两个值类型相同 —> 按照 === 比较方法进行比较
1. 类型不同，使用如下规则进行比较
1. 其中一个值是null，另一个是undefined -> 相等
1. 一个值是**数字**另一个是**字符串**，将**字符串转换为数字**进行比较
1. 有布尔类型，将**true转换为1，false转换为0**，然后用==规则继续比较
1. 一个值是对象，另一个是数字或字符串，将对象转换为原始值然后用==规则继续比较
1. **其他所有情况都认为不相等**
