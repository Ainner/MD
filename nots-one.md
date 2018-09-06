下面这段代码要循环延时输出 0、1、2、3、4
=
- 错误
	- 错误原因：循环中setTimeout接受的参数函数通过闭包访问变量i
```
for (var i = 0; i < 5; ++i) {
  setTimeout(function () {
    console.log(i + ' ');
  }, 100);
}
```
- 正确
	- 修改方法：将setTimeout放在函数立即调用表达式中，将i值作为参数传递给包裹函数，创建新闭包
```
for (var i = 0; i < 5; ++i) {
  (function (i) {
    setTimeout(function () {
      console.log(i + ' ');
    }, 100);
  }(i));
}
```

输出日期
=
```
var days = ['日','一','二','三','四','五','六'];
var date = new Date();

console.log('今天是星期' + days[date.getDay()]);
```
三种实现继承的优缺点
=
```
function Shape() {}

function Rect() {}

// case1
Rect.prototype = new Shape();

// case2
Rect.prototype = Shape.prototype;

// case3
Rect.prototype = Object.create(Shape.prototype);

Rect.prototype.area = function () {
  // do something
};
```
- case1
	- 优点一：正确设置原型链实现继承
	- 优点二：父类实例属性得到继承，原型链查找效率提高，也能为一些属性提供合理的默认值
	- 缺点一：父类实例属性为引用类型时，不恰当地修改会导致所有子类被修改
	- 缺点二：创建父类实例作为子类原型时，可能无法确定构造函数需要的合理参数，这样提供的参数继承给子类没有实际意义，当子类需要这些参数时应该在构造函数中进行初始化和设置
	- 总结：继承应该是继承方法而不是属性，为子类设置父类实例属性应该是通过在子类构造函数中调用父类构造函数进行初始化

- case2
	- 优点一：正确设置原型链实现继承
	- 缺点一：父类构造函数原型与子类相同。修改子类原型添加方法会修改父类

- case3
	- 优点一：正确设置原型链且避免方法1.2中的缺点
	- 缺点一：ES5方法需要注意兼容性

- 改进
```
1. 所有三种方法应该在子类构造函数中调用父类构造函数实现实例属性初始化
function Rect() {
    Shape.call(this);
}
2. 用新创建的对象替代子类默认原型，设置`Rect.prototype.constructor = Rect;保证一致性
3. 第三种方法的polyfill：
function create(obj) {
    if (Object.create) {
        return Object.create(obj);
    }

    function f() {};
    f.prototype = obj;
    return new f();
}
```
