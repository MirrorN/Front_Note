# 流程控制

流程控制用于控制代码按照何种结构顺序执行代码：

- 顺序结构
- 分支结构
- 循环结构



## 分支结构

根据不同的条件执行不同路径的代码（执行代码多选一）

两种执行语句：

1. if 语句
2. switch 语句

```javascript
if(判断条件){
//判断条件成立的时候执行的代码
} else{
// 判断条件不成立的时候执行的代码
}
```

多分支语句：if - else -if 

```javascript
if(判断条件){
//判断条件一成立时执行
}else if(panud){
//判断条件二成立时候执行
}else{
//判断条件都不成立的时候执行
}

```

### 三元表达式

语法：

``` 
条件表达式？ 表达式1 ：表达式2
```



### switch 语句和 if 语句

switch 语句：也可以实现多分支的选择，一般用于针对变量设置一系列特定值的时候

语法：

```javascript
var num = parseInt(prompt('input a num: '));
switch (num) {
    case 1:
        console.log('1');
        break;
    case 2:
        console.log('2');
        break;
    case 3:
        console.log('3');
        break;
    default:
        console.log('No Match.');
}
```

注意：

1. `switch()`判断条件一般写成变量，方便传入数值；
2. num 和 case 里的值匹配时候是 **全等**，只有数值和数据类型都相等的时候才匹配成功（所以要注意数据类型的转化以及 case 中的值的书写）
3. 不要忘记写 `break`，否则会继续执行下一条`case`



switch 和 if - else if 语句的区别：

1. 一般情况下，两个语句是可以相互替换的
2. switch 语句更多适用于处理 case 比较确定值的情况， if else if语句则是更加灵活，常用于范围判断（大于小于某个范围）
3. switch 语句再进行条件判断之后会直接执行到某个 case 下，效率更高， if else if 语句则是多次判断
4. 分支较少的时候， if else if 语句执行效率更高
5. 分值较多的时候，switch 语句的执行效率更高，结构更清晰。



## 循环结构





