节点
=

1. 创建新节点
	1. createDocumentFragment() //创建一个DOM片段
	1. createElement() //创建一个具体的元素
	1. createTextNode() //创建一个文本节点
1. 添加、移除、替换、插入
	1. appendChild() //添加
	1. removeChild() //移除
	1. replaceChild() //替换
	1. insertBefore() //插入
1. 查找
	1. getElementsByTagName() //通过标签名称
	1. getElementsByName() //通过元素的Name属性的值
	1. getElementById() //通过元素Id，唯一性


typeof & instanceof
=

相同点：判断一个变量是否为空，或者是什么类型的
typeof 定义：**返回值是一个字符串，用来说明变量的数据类型**

1. typeof 一般只能返回如下几个结果：number,boolean,string,function,object,undefined
1. typeof 来获取一个变量是否存在，if(typeof a!="undefined"){alert("ok")}，而不要去使用 if(a) 因为如果 a 不存在（未声明）则会出错
1. 对于 Array,Null 等特殊对象使用 typeof 一律返回 object，这正是 typeof 的局限性

Instanceof 定义：**instanceof 用于判断一个变量是否属于某个对象的实例**
实例：a instanceof b?alert("true"):alert("false"); //a是b的实例？真:假
```
var a = new Array(); 
alert(a instanceof Array);  // true
alert(a instanceof Object)  // true

function test(){};
var a = new test();
alert(a instanceof test)   // true
```
如下，得到的结果为‘N’,这里的 instanceof 测试的 object 是指 js 语法中的 object，不是指 dom 模型对象
```
if (window instanceof Object){ alert('Y')} else {  alert('N');}  // 'N'
```
闭包
=

1. 定义用法：当一个函数的返回值是另外一个函数，而返回的那个函数如果调用了其父函数内部的其它变量，如果返回的这个函数在外部被执行，就产生了闭包
1. 表现形式：使函数外部能够调用函数内部定义的变量
1. 变量的作用域
	1. 变量的作用域分类：全局变量和局部变量。
	1. 特点
		1. 函数内部可以读取函数外部的全局变量；在函数外部无法读取函数内的局部变量
		1. 函数内部声明变量的时候，一定要使用 var 命令。如果不用的话，你实际上声明了一个全局变量
1. 注意点
	1. 滥用闭包，会造成内存泄漏：由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除
	1. 会改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值


算法
=

#### 冒泡排序

原理：从第一个元素开始，往后比较，遇到比自己小的元素就交换位置

特点：交换的次数最多，所以它的性能是最差的


#### 插入排序

原理：插入排序的基本操作就是将一个数据插入到已经排好序的有序数据中，从而得到一个新的、个数加一的有序数据

特点：插入算法把要排序的数组分成两部分：

第一部分包含了这个数组的所有元素，但将第一个元素除外（让数组多一个空间才有插入的位置）.

第二部分就只包含这一个元素（即待插入元素）。在第一部分排序完成后，再将这个最后元素插入到已排好序的第一部分中

比冒泡排序快一点


#### 希尔排序

原理：希尔排序也叫 递减增量排序算法，是插入排序的一种神龟进化版。什么叫递减增量呢，就是定义一个间隔序列，例如是5，3，1。第一次处理，会处理所有间隔为5的，下一次会处理间隔为3的，最后一次处理间隔为1的元素。也就是相邻元素执行标准插入排序。

特点：由于多次插入排序，我们知道一次插入排序是稳定的，不会改变相同元素的相对顺序，但在不同的插入排序过程中，

  相同的元素可能在各自的插入排序中移动，最后其稳定性就会被打乱，所以shell排序是不稳定的。

　打个比方，我原来的数组是[5,4,3,2,1]的，这样一打乱就全部重新排了。


#### 归并排序

原理：归并排序法是将两个（或两个以上）有序表合并成一个新的有序表，即把待排序序列分为若干个子序列，每个子序列是有序的。然后再把有序子序列合并为整体有序序列。

特点：速度仅次于快速排序，为稳定排序算法，一般用于对总体无序，但是各子项相对有序的数列.

属于分治思想，递归归并


#### 快速排序

原理：
1、在数据集之中，选择一个元素作为"基准"（pivot）。比如选择下面数字45
![](https://files.jb51.net/file_images/article/201701/2017011109535710.png)

2、所有小于"基准"的元素，都移到"基准"的左边；所有大于"基准"的元素，都移到"基准"的右边。
![](https://files.jb51.net/file_images/article/201701/2017011109535811.png)

3、对"基准"左边和右边的两个子集，不断重复第一步和第二步，直到所有子集只剩下一个元素为止。

特点：速度最快。和归并排序不同的是，归并排序是先分为两组再继续排，而快速排序是边分边排


#### 选择排序

原理：在要排序的一组数中，选出最小的一个数与第一个位置的数交换，然后剩下的数当中找出最小的与第二个位置的数交换，如此循环直到倒数第二个数和最后一个数为止。

特点：可以说是冒泡排序的衍生品，效率比较一般般


#### 奇偶排序

原理：

选取所有奇数列的元素与其右侧相邻的元素进行比较，将较小的元素排序在前面；

选取所有偶数列的元素与其右侧相邻的元素进行比较，将较小的元素排序在前面；

重复前面两步，直到所有序列有序为止。

特点：奇数和偶数序列交替比较
