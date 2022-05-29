# 作用域

作用域：变量名在某个范围内起作用，提高程序的可靠性减小命名冲突

es6之前，两种作用域：

1. 全局作用域：整个js文件或者整个 script 标签之间
2. 局部作用域：函数内部

根据定义的作用域不同，变量的区别：

- 全局变量

  - 全局作用域下声明（var 定义）
  - **在函数内不使用var定义的变量也是全局变量**（不建议使用）
  - **注意：只有在浏览器关闭的时候才会被销毁，因此比较占内存**

- 局部变量

  - 在函数内部定义的变量
  - 只在函数内部使用，当所在的代码块被执行的时候，会被初始化，代码块运行结束后就会销毁，更节省内存空间
  - 现阶段没有块级作用域

  


 作用域链：内部函数访问外部函数定义的某个变量值，采用的是链式查找的方式（就近原则）：

```javascript
var num = 10;
function fun1() {
    var num = 20;
    function fun2() {
        console.log(num);   // 输出的结果为20
    }
    fun2();
}
fun1();
```





# 预解析

JS引擎运行JS代码分为两步：

1. 预解析
   1. 变量预解析（变量提升）：将所有变量声明提升到当前作用域最前面，不提升赋值操作
   2. 函数预解析（函数提升）：将所有的函数声明提升到当前作用域最前面，不调用
2. 代码执行 ：按照代码执行顺序从上往下执行

其中预解析会**将所有的 var 变量声明 和 function 提升到当前作用域的最前面**，例如：

```javascript
console.log(num);
var num = 3;
```

其运行的结果为 `undefined`，实际上代码运行的顺序是：

```javascript
var num;
console.log(num);
num = 3
```

对于匿名函数也是如此：

```javascript
fun();
var fun = function () {
    console.log('hi');
}

/*
        通过匿名函数方式等同于声明变量方式，因此上述代码执行步骤实际上是：
        var fun;
        fun();
        fun = function(){...}
        因此会报错
        */
```

由于函数提升：

```javascript
func();
function func() {
    console.log('hi');
}

```

代码运行正常

## 预解析案例

### 案例一

```javascript
var num = 10;
fun();
function fun() {
    console.log(num);
    var num = 20;
}
```

输出结果为`undefined`，代码执行顺序等价于：

```javascript
var num;
function fun(){
    var num;
    console.log(num);
    num = 20;
}
num = 10;
fun();
```

注意两种情况：

```javascript
var num = 10;
fun();
function fun() {
    console.log(num);    // 10
}

var num = 10;
fun();
function fun() {
    var num;
    console.log(num);  // undefined
}
```



### 案例二

```javascript
var num = 10;
function fn() {
    console.log(num);
    var num = 20;
    console.log(num);
}
fn();
```

输出结果为`undefined`和`20`，代码执行顺序为：

```javascript
var num;
function fn(){
	var num;
    console.log(num);
    num = 20;
    console.log(num);
}
num = 10;
fn();
```

注意是将变量声明和函数声明提升到**本作用域**的最前面。

### 案例三

```javascript
f1();
console.log(c);
console.log(b);
console.log(a);
function f1() {
    var a = b = c = 9;
    console.log(a);
    console.log(b);
    console.log(c);
}
```

实际执行的代码为：

```javascript
function f1() {
    /*
            var a=b=c=9 相当于 var a=9; b=9; c=9; 因此 b，c都是全局变量
            abc全部声明为局部的方式为 : var a=9,b=9,c=9;
            */
    var a;
    a = 9;
    b = 9;
    c = 9;
    console.log(a);
    console.log(b);
    console.log(c);
}
f1();
console.log(c);
console.log(b);
console.log(a);
```

所以输出的结果为：

```
9 9 9 9（全局变量c） 9（全局变量b） 报错（a不是全局变量，未定义）
```



# 对象

JS对象：一组无序的属性和方法的集合

创建对象的方法：

1. 字面量（`{}`）
2. 使用new object
3. 使用构造函数



## 字面量方式

定义案例：

```javascript
var obj = {
    name: '可可',
    type: '阿拉斯加',
    age: 5,
    color: 'brown',
    bark: function () {
        console.log('wang wang wnag');
    },
    showFilm: function () {
        console.log('show film.');
    }
}

console.log(obj['name']);
console.log(obj.color);
obj.bark();
obj.showFilm();
```

注意点：

- 要使用 var 定义
- 属性和方法定义都采用 键值对 的形式
- 不同属性和方法之间使用 `,`隔开
- 方法的定义采用的是匿名函数的方式

对象调用：

- 对象.属性名
- 对象[‘属性名’]，属性名必须加引号
- 对象.方法名()，调用方法要加括号



## new Object方式

案例：

```javascript
var obj = new Object();
obj.uname = 'name';
obj.age = 18;
obj.sayHi = function () {
    console.log('Hi');
}

// 调用
console.log(obj.uname);
console.log(obj['age']);
obj.sayHi();
```

利用等号赋值的方式添加对象属性，每个属性和方法之间使用`;`隔开。



## 构造函数方式

构造函数：将对象里一些相同的属性和方法封装到函数中

案例：

```javascript
function People(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
    this.func1 = function () {
        console.log('hi.');
    }
}

var people1 = new People('name1', '18', 'man');
console.log(typeof (people1));  // object 类型
console.log(people1.name);
console.log(people1.sex);
people1.func1();
```

注意点：

- **构造函数名一定要大写**
- 构造函数不需要 return 就可以返回结果
- 调用构造函数必须使用 new
- 注意 `this`
- 通过 new 关键字生成对象也成为对象实例化

New 关键字的执行过程：

1. 首先在内存中创建一个新的空的对象
2. 让 this 指向这个空对象
3. 执行构造函数里的代码，给这个新对象添加属性和方法
4. 返回这个新对象

### 遍历对象

使用 for-in 语句可以遍历数组或者对象（推荐用来遍历对象）

案例：

```javascript
var obj1 = new Object();
obj1.name = 'uname';
obj1.sec = 'man';
obj1.age = 18;
obj1.func = function () {
    console.log('say hi');
}

for (k in obj1) {  // 一般都会使用 k 或者 key
    console.log(k);  // k 表示的是对象中的属性名
    console.log(obj1[k]);  // obj[k]可以得到对象的某个属性值 注意不加引号
}
```





