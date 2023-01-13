# JavaScript基础

> 了解变量、数据类型、运算符等基础概念，能够实现数据类型的转换，结合四则运算体会如何编程。

- 体会现实世界中的事物与计算机的关系
- 理解什么是数据并知道数据的分类
- 理解变量存储数据的“容器”
- 掌握常见运算符的使用，了解优先级关系
- 知道 JavaScript 数据类型隐式转换的特征

## 一、介绍

### JavaScript的组成

#### ECMAScript

规定了js基础语法核心知识。
比如：变量、分支语句、循环语句、对象等等

#### Web APIs

 DOM 操作文档，比如对页面元素进行移动、大小、添加删除等操作
 BOM 操作浏览器，比如页面弹窗，检测窗口宽度、存储数据到浏览器等等

### 引入方式

> 掌握 JavaScript 的引入方式，初步认识 JavaScript 的作用

JavaScript 程序不能独立运行，它需要被嵌入 HTML 中，然后浏览器才能执行 JavaScript 代码。通过 `script` 标签将 JavaScript 代码引入到 HTML 中，有两种方式：

#### 内部形式

通过 `script` 标签包裹 JavaScript 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 引入方式</title>
</head>
<body>
     <div class="box">
        <script>
              <!--  script 代码可以写到标签内部 -->
            document.write(`你好`)
        </script>
    </div>
   
  <!-- 内联形式：通过 script 标签包裹 JavaScript 代码 -->
  <script>
    alert('嗨，欢迎来传智播学习前端技术！');
  </script>
    
</body>
</html>
```

#### 外部形式

一般将 JavaScript 代码写在独立的以 .js 结尾的文件中，然后通过 `script` 标签的 `src` 属性引入

```javascript
// demo.js
document.write('嗨，欢迎来传智播学习前端技术！');
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 引入方式</title>
</head>
<body>
  <!-- 外部形式：通过 script 的 src 属性引入独立的 .js 文件 -->
  <script src="demo.js"></script>
</body>
</html>
```

如果 script 标签使用 src 属性引入了某 .js 文件，那么 标签的代码会被忽略！！！如下代码所示：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 引入方式</title>
</head>
<body>
  <!-- 外部形式：通过 script 的 src 属性引入独立的 .js 文件 -->
  <script src="demo.js">
    // 此处的代码会被忽略掉！！！！
   alert(666);  
  </script>
</body>
</html>
```

### 注释和结束符

通过注释可以屏蔽代码被执行或者添加备注信息，JavaScript 支持两种形式注释语法：

#### 单行注释

使用 `//` 注释单行代码,快捷键：ctrl + /

```javascript
    // 这种是单行注释的语法
    // 一次只能注释一行
    // 可以重复注释
    document.write('嗨，欢迎来传智播学习前端技术！');
```

#### 多行注释

使用 `/* */` 注释多行代码, 快捷键：shift + alt + A

```javascript

    /* 这种的是多行注释的语法 */
    /*
     更常见的多行注释是这种写法
     在些可以任意换行
     多少行都可以
      */
    document.write('嗨，欢迎学习前端技术！');
```

**注：编辑器中单行注释的快捷键为 `ctrl + /`**

#### 结束符

在 JavaScript 中 `;` 代表一段代码的结束，多数情况下可以省略 `;` 使用回车（enter）替代。

```javascript
    alert(1);
    alert(2);
    alert(1)
    alert(2)
```

JavaScript 跟 HTML 和 CSS 一样，会忽略【一些】空白符，但是换行符（回车）会被识别成结束符 `;`，因此在实际开发中有许多人主张书写 JavaScript 代码时省略结束符 `;`

### 输入输出语法

输出和输入也可理解为人和计算机的交互，用户通过键盘、鼠标等向计算机输入信息，计算机处理后再展示结果给用户，这便是一次输入和输出的过程。

举例说明：如按键盘上的方向键，向上/下键可以滚动页面，按向上/下键这个动作叫作输入，页面发生了滚动了这便叫输出。

#### 输出

JavaScript 可以接收用户的输入，然后再将输入的结果输出：

`alert()`、`document.wirte()`

以数字为例，向 `alert()` 或 `document.write()`输入任意数字，他都会以弹窗形式展示（输出）给用户。

#### 输入

向 `prompt()` 输入任意内容会以弹窗形式出现在浏览器中，一般提示用户输入一些内容。

```javascript
    // 1. 输入的任意数字，都会以弹窗形式展示
    document.write('要输出的内容');
    alert('要输出的内容');

    // 2. 以弹窗形式提示用户输入姓名，注意这里的文字使用英文的引号
    prompt('请输入您的姓名:');

```

## 二、变量

> 理解变量是计算机存储数据的“容器”，掌握变量的声明方式

变量是计算机中用来存储数据的“容器”，它可以让计算机变得有记忆，通俗的理解变量就是使用【某个符号】来代表【某个具体的数值】（数据）

```javascript
  // x 符号代表了 5 这个数值
  x = 5;
  // y 符号代表了 6 这个数值
  y = 6;
    
  //举例： 在 JavaScript 中使用变量可以将某个数据（数值）记录下来！

  // 将用户输入的内容保存在 num 这个变量（容器）中
  num = prompt('请输入一数字!');

  // 通过 num 变量（容器）将用户输入的内容输出出来
  alert(num);
  document.write(num);
```

### 命名与规范

>规则：
 不能用关键字
 关键字：有特殊含义的字符，JavaScript 内置的一些英语词汇。例如：let、var、if、for等
 只能用下划线、字母、数字、$组成，且数字不能开头
 字母严格区分大小写，如 Age 和 age 是不同的变量
>规范：
 起名要有意义
 遵守小驼峰命名法
 第一个单词首字母小写，后面每个单词首字母大写。例：userName

关于变量的名称（标识符）有一系列的规则需要遵守：

1. 只能是字母、数字、下划线、$，且不能能数字开头
2. 字母区分大小写，如 Age 和 age 是不同的变量
3. JavaScript 内部已占用于单词（关键字或保留字）不允许使用
4. 尽量保证变量具有一定的语义，见字知义

注：所谓关键字是指 JavaScript 内部使用的词语，如 `let` 和`var`，保留字是指 JavaScript 内部目前没有使用的词语，但是将来可能会使用词语。

```javascript

    let age = 18; // 正确
    let age1 = 18; // 正确
    let _age = 18; // 正确

    // let 1age = 18; // 错误，不可以数字开头
    let $age = 18; // 正确
    let Age = 24; // 正确，它与小写的 age 是不同的变量
    // let let = 18; // 错误，let 是关键字
    let int = 123; // 不推荐，int 是保留字

```

### 声明和赋值

#### 声明

声明(定义)变量有两部分构成：声明关键字、变量名（标识）

```javascript
    // let 变量名
    // 声明(定义)变量有两部分构成：声明关键字、变量名（标识）
    // let 即关键字，所谓关键字是系统提供的专门用来声明（定义）变量的词语
    // age 即变量的名称，也叫标识符
    let age;
```

关键字是 JavaScript 中内置的一些英文词汇（单词或缩写），它们代表某些特定的含义，如 `let` 的含义是声明变量的，看到 `let`  后就可想到这行代码的意思是在声明变量，如 `let age;`

`let` 和 `var` 都是 JavaScript 中的声明变量的关键字，推荐使用 `let` 声明变量！！！

#### 赋值

声明（定义）变量相当于创造了一个空的“容器”，通过赋值向这个容器中添加数据。

```javascript
    // 声明(定义)变量有两部分构成：声明关键字、变量名（标识）
    // let 即关键字，所谓关键字是系统提供的专门用来声明（定义）变量的词语
    // age 即变量的名称，也叫标识符
    let age;
    // 赋值，将 18 这个数据存入了 age 这个“容器”中
    age = 18;
    // 这样 age 的值就成了 18
    document.write(age);
    
    // 也可以声明和赋值同时进行
    let str = 'hello world!';
    alert(str);
```

### 关键字  

JavaScript 使用专门的关键字 `let` 和 `var` 来声明（定义）变量，在使用时需要注意一些细节：

以下是使用 `let` 时的注意事项：

1. 允许声明和赋值同时进行
2. 不允许重复声明
3. 允许同时声明多个变量并赋值
4. JavaScript 中内置的一些关键字不能被当做变量名

以下是使用 `var` 时的注意事项：

1. 允许声明和赋值同时进行
2. 允许重复声明
3. 允许同时声明多个变量并赋值

大部分情况使用 `let` 和 `var` 区别不大，但是 `let` 相较 `var` 更严谨，因此推荐使用 `let`，后期会更进一步介绍二者间的区别。

### 变量拓展-数组

数组(Array)是一种可以按顺序保存多个数据

数组是按顺序保存，所以每个数据都有自己的编号
计算机中的编号从0开始，所以小明的编号为0，小刚编号为1，以此类推
在数组中，数据的编号也叫索引或下标
数组可以存储任意类型的数

```javascript
// 声明语法
let 数组名 = [数据1, 数据2, 数据3, ...]

let names = ['小明', '小刚', '小李', '小强']
console.log(name[0]) //小明
console.log(name[1]) //小刚
console.log(name.length) //4
```

## 三、数据类型

> 计算机世界中的万事成物都是数据。

计算机程序可以处理大量的数据，为了方便数据的管理，将数据分成了不同的类型：

注：通过 typeof 关键字检测数据类型

```javascript

    // 检测 1 是什么类型数据，结果为 number
    document.write(typeof 1);
```

### 数值类型(Number)

即我们数学中学习到的数字，可以是整数、小数、正数、负数

```javascript

    let score = 100; // 正整数
    let price = 12.345; // 小数
    let temperature = -40; // 负数

    document.write(typeof score); // 结果为 number
    document.write(typeof price); // 结果为 number
    document.write(typeof temperature); // 结果为 number

```

JavaScript 中的数值类型与数学中的数字是一样的，分为正数、负数、小数等。

### 字符串类型(String)

通过单引号（ `''`） 、双引号（ `""`）或反引号包裹的数据都叫字符串，单引号和双引号没有本质上的区别，推荐使用单引号。

注意事项：

1. 无论单引号或是双引号必须成对使用
2. 单引号/双引号可以互相嵌套，但是不以自已嵌套自已
3. 必要时可以使用转义符 `\`，输出单引号或双引号

```javascript
 
    let user_name = '小明'; // 使用单引号
    let gender = "男"; // 使用双引号
    let str = '123'; // 看上去是数字，但是用引号包裹了就成了字符串了
    let str1 = ''; // 这种情况叫空字符串
  
    documeent.write(typeof user_name); // 结果为 string
    documeent.write(typeof gender); // 结果为 string
    documeent.write(typeof str); // 结果为 string
```

模板字符串

1. 作用
拼接字符串和变量
在没有它之前，要拼接变量比较麻烦
2. 符号
 ``
    在英文输入模式下按键盘的tab键上方那个键（1左边那个键）
    内容拼接变量时，用 ${} 包住变量

```javascript
     documeent.write('大家好，我叫' + name + '今年' + age + '岁')
     documeent.write(`大家好，我叫${name}今年${age}岁`)

```

### 布尔类型(boolean)

表示肯定或否定时在计算机中对应的是布尔类型数据，它有两个固定的值 `true` 和 `false`，表示肯定的数据用 `true`，表示否定的数据用 `false`。

```javascript
    //  pink老师帅不帅？回答 是 或 否
    let isCool = true; // 是的，摔死了！
    isCool = false; // 不，套马杆的汉子！

    document.write(typeof isCool); // 结果为 boolean
```

### 未定义(undefined)

未定义是比较特殊的类型，只有一个值 undefined，只声明变量，不赋值的情况下，变量的默认值为 undefined，一般很少【直接】为某个变量赋值为 undefined。

```javascript
    // 只声明了变量，并末赋值
    let tmp;
    document.write(typeof tmp); // 结果为 undefined
```

**注：JavaScript 中变量的值决定了变量的数据类型。**

### 空类型(null)

null 表示值为空

```javascript
let obj = null
```

null 和 undefined 区别：

1. undefined 表示没有赋值
2. null 表示赋值了，但是内容为空
null 开发中的使用场景：
官方解释：把 null 作为尚未创建的对象

## 四、类型转换

JavaScript是弱数据类型： JavaScript也不知道变量到底属于那种数据类型，只有赋值了才清楚。
坑： 使用表单、prompt 获取过来的数据默认是字符串类型的，此时就不能直接简单的进行加法运算，需要转换变量的数据类型。

> 理解弱类型语言的特征，掌握显式类型转换的方法

在 JavaScript 中数据被分成了不同的类型，如数值、字符串、布尔值、undefined，在实际编程的过程中，不同数据类型之间存在着转换的关系。

### 隐式转换

某些运算符被执行时，系统内部自动将数据类型进行转换，这种转换称为隐式转换。

```javascript

    let num = 13; // 数值
    let num2 = '2'; // 字符串

    // 结果为 132
    // 原因是将数值 num 转换成了字符串，相当于 '13'
    // 然后 + 将两个字符串拼接到了一起
    console.log(num + num2);

    // 结果为 11
    // 原因是将字符串 num2 转换成了数值，相当于 2
    // 然后数值 13 减去 数值 2
    console.log(num - num2);

    let a = prompt('请输入一个数字');
    let b = prompt('请再输入一个数字');

    alert(a + b);
```

注：数据类型的隐式转换是 JavaScript 的特征，后续学习中还会遇到，目前先需要理解什么是隐式转换。

补充介绍模板字符串的拼接的使用

### 显式转换

编写程序时过度依靠系统内部的隐式转换是不严禁的，因为隐式转换规律并不清晰，大多是靠经验总结的规律。为了避免因隐式转换带来的问题，通常根逻辑需要对数据进行显示转换。

#### 转数字型

1. `Number()`
2. `String()`
通过 `Number` 显示转换成数值类型，当转换失败时结果为 `NaN`（Not a Number）即不是一个数字。

```javascript

    let t = '12';
    let f = 8;

    // 显式将字符串 12 转换成数值 12
    t = Number(t);

    // 检测转换后的类型
    // console.log(typeof t);
    console.log(t + f); // 结果为 20

    // 并不是所有的值都可以被转成数值类型
    let str = 'hello';
    // 将 hello 转成数值是不现实的，当无法转换成
    // 数值时，得到的结果为 NaN （Not a Number）
    console.log(Number(str));
```

#### 转字符型

1. `parseInt()`保留整数
2. `parseFloat()`可保留小数
3. 变量`.tostring(`转化X进制`)`

## 五、运算符

### 算数运算符

数学运算符也叫算术运算符，主要包括加、减、乘、除、取余（求模）。

 `+`：求和  `-`：求差  `*`：求积  `/`：求商  `%`：取模（取余数,开发中经常作为某个数字是否被整除）

JavaScript中 优先级越高越先被执行，优先级相同时以书从左向右执行。

> 乘、除、取余优先级相同
> 加、减优先级相同
> 乘、除、取余优先级大于加、减
> 使用 () 可以提升优先级
> 总结： 先乘除后加减，有括号先算括号里面的

```javascript
console.log(1 + 2 * 3) // 7
console.log(10 - 8 / 2) // 6
console.log(2 % 5 + 4 * 2) // 10
```

### 赋值运算符

赋值运算符：对变量进行赋值的运算符

`=`将等号右边的值赋予给左边, 要求左边必须是一个容器

`+=`  `-=`  `*=`  `/=` `%=`

```javascript
        // let num = 18
        // num = num + 1

        // num = num + 3
        // num += 3
        // console.log(num)

        // 两个变量的 把i加到 sum 里面去
        let i = 1
        let sum = 0
        // sum = sum + i
        sum += i
```

### 一元运算符

常用于计数来使用

> 自增:   符号：`++`   作用：让变量的值 +1  
>
> 自减：  符号：`--`  作用：让变量的值 -1

```javascript
// 一元运算符
 ++num    //等价于  num += 1

// 前置自增
let i = 1
// 先自加 再使用
console.log(++i + 2)  // 4

// 后置自增
// 先使用 后自加
let i = 1
console.log(i++ + 2) // 3
console.log(i) //2
```

### 比较运算符

作用：比较两个数据大小、是否相等

比较运算符：  

`>`： 左边是否大于右边

`<`： 左边是否小于右边  

`>=`： 左边是否大于或等于右边  

`<=`： 左边是否小于或等于右边  

`==`： 左右两边是否相等  

`===`： 左右两边是否类型和值都相等  

`!==`： 左右两边是否不全等  

比较结果为boolean类型，即只会得到true或false

> 比较运算符的细节:
>
> 字符串比较，是比较的字符对应的ASCII码  
>
> 从左往右依次比较  如果第一位一样再比较第二位，以此类推
>
> NaN不等于任何值，包括它本身
>
> 尽量不要比较小数，因为小数有精度问题

> 不同类型之间比较会发生隐式转换  
>
> 最终把数据隐式转换转成number类型再比较  
>
> 所以开发中，如果进行准确的比较我们更喜欢 === 或者 !==

```javascript
console.log(3 > 5) // false
        console.log(5 >= 5) //  true
        // console.log(5 = 5)
        console.log(5 == 5)//  true
        // == 只要值一样就是true  不管数据类型
        console.log(5 == '5')// true
        console.log(5 == 'pink')// false
        // === 以后判断要用  ===  开发常用   要求值和数据类型都一样
        console.log(5 === 5) // true
        console.log(5 === '5')// false
        // 特殊情况
        console.log('pink' > 'red')// false
        console.log('pink' > 'pin')// true
        console.log(1 === NaN)// false
        console.log(NaN === NaN)// false
        console.log(0.1 + 0.2 === 0.3)// false
        console.log(0.1 + 0.2) //0.30000000000000004

        console.log(3 > '2') // true
```

**= 和 == 和 === 区别**

`=` 是赋值  

`==` 是判断 只要求值相等，不要求数据类型一样即可返回true  

`===` 是全等 要求值和数据类型都一样返回的才是true 【常用】

### 逻辑运算符

| 符号 |  名称  | 读法 |             特点              |      口诀      |
| :--: | :----: | :--: | :---------------------------: | :------------: |
|  &&  | 逻辑与 | 并且 | 符号两边都为true 结果才为true |    一假则假    |
| \|\| | 逻辑或 | 或者 |  符号两边有一个true就为true   |    一真则真    |
|  !   | 逻辑非 | 取反 |    true变false false变true    | 真变假，假变真 |

<font color=red>有5个值是当 false 来看的</font>

`false`  `数字0`  `‘’`  `undefined`  `null`

**逻辑运算符的短路**

短路：只存在于 && 和 || 中，当满足一定条件会让右边代码不执行

原因：通过左边能得到整个式子的结果，因此没必要再判断右边

运算结果：无论 && 还是 || ，运算结果都是最后被执行的表达式值，一般用在变量赋值

| 符号 |     短路条件      |
| :--: | :---------------: |
|  &&  | 左边为false就短路 |
| \|\| | 左边为true就短路  |

```javascript
        // 逻辑与 一假则假
         console.log(true && true) //true
         console.log(false && true) //false
        // 逻辑或  一真则真
         console.log(false || true) //true
         console.log(false || false) //false
        // 逻辑非  取反
         console.log(!true) //false
         console.log(!false) //true

         function fun(x, y) {
  // 实参为空时，设置默认值
             x = x || 0
             y = y || 0

             x + y
         }
         fun() // 0
```

### 运算符优先级

| 优先级 | 运算符     | 顺序              |
| ------ | ---------- | ----------------- |
| 1      | 小括号     | ( )               |
| 2      | 一元运算符 | ++  --  !         |
| 3      | 算数运算符 | 先 * / % 后 + -   |
| 4      | 关系运算符 | >  >=  <  <=      |
| 5      | 相等运算符 | ==  !=  ===  !=== |
| 6      | 逻辑运算符 | 先 && 后 \|\|     |
| 7      | 赋值运算符 | =                 |
| 8      | 逗号运算符 | ,                 |

## 六、语句

### 表达式和语句

表达式：表达式是一组代码的集合，JavaScript解释器会将其计算出一个结果

语句： js整句或命令，js语句是以分号结束（可以省略） 比如： if语句 for 循环语句

区别： 表达式计算出一个值，但语句用来自行以使某件事发生(做什么事)  

 表达式 `3 + 4`

 语句 `alert()` 弹出对话框

 其实某些情况，也可以把表达式理解为语句，因为它是在计算结果，也是做事

### 分支语句

分支语句可以让我们有选择性的执行想要的代码

#### If分支语句

if语句有三种使用：单分支、双分支、多分支

单分支使用语法

```javascript
单分支if语法
//if (条件) 满足条件要执行的代码

        if (条件) {
                    满足条件要执行的代码
        }
//括号内的条件为true时，进入大括号里执行代码
//小括号内的结果若不是布尔类型时，会发生隐式转换转为布尔类型

双分支if语法
        if (条件) {
                满足条件要执行的代码
        } else {
            不满足条件要执行的代码
        }

多分支if语法
        if (条件1) {
                代码1
        } else if (条件2){
            代码2
        } else if (条件3){
            代码3
        } else {
               代码n
        }
//先判断条件1，若满足条件1就执行代码1，其他不执行
//若不满足则向下判断条件2，满足条件2执行代码2，其他不执行
//若依然不满足继续往下判断，依次类推
//若以上条件都不满足，执行else里的代码n
//注：可以写N个条件

```

#### 三元运算符

其实是比 if 双分支 更简单的写法，有时候也叫做三元表达式  

符号：`?` 与 `:` 配合使用

`条件 ？ 满足条件执行的代码 : 不满足条件执行的代码`

```js
  let num1 = 40
        let num2 = 30
        // num1 > num2 ? console.log(num1) : console.log(num2)
        // let re = num1 > num2 ? num1 : num2
        let re = num1 > num2 ? num1 : num2
        console.log(re) //40

   // 1. 用户输入数字
        let num = prompt('请您输入一个数字')
        // 2. 判断条件是 小于 10  则数字前面 + '0'   01 否则 不补
        // let t = num >= 10 ? num : '0' + num
        let t = num < 10 ? '0' + num : num
        document.write(t)
```

#### switch 语句

找到跟小括号里数据全等的case值，并执行里面对应的代码  

若没有全等 `===` 的则执行`default`里的代码  例：数据若跟值2全等，则执行代码2

> 1. switch case语句一般用于等值判断,不适合于区间判断
> 2. switch case一般需要配合break关键字使用 没有break会造成case穿透

```js
       switch (数据) {
            case 值1:
                代码1
                break
            case 值2:
               代码2
                break
            default:
               代码n
               break
        }

例：简单计算器
 // 1. 用户输入数字   还有一次 运算符
        let num1 = +prompt('请您输入第一个数:')
        let num2 = +prompt('请您输入第二个数:')
        let sp = prompt('请您输入+ - * / 运算')
        // 2. 根据不同的运算符计算不同的结果 switch
        switch (sp) {
            case '+':
                alert(`您选择的是加法，结果是: ${num1 + num2}`)
                break
            case '-':
                alert(`您选择的是减法，结果是: ${num1 - num2}`)
                break
            case '*':
                alert(`您选择的是乘法，结果是: ${num1 * num2}`)
                break
            case '/':
                alert(`您选择的是除法，结果是: ${num1 / num2}`)
                break
            default:
                alert(`你输了啥？ 请输入+ - * / `)
        }
```

### 循环语句

#### 断点调试

作用：学习时可以帮助更好的理解代码运行，工作时可以更快找到bug  

浏览器打开调试界面

1. 按F12打开开发者工具
2. 点到sources一栏
3. 选择代码文件

断点：在某句代码上加的标记就叫断点，当程序执行到这句有标记的代码时会暂停下来

#### while 循环

目标：掌握while循环语法，能重复执行某段代码

循环：重复执行某段代码， while : 在…. 期间

释义：跟if语句很像，都要满足小括号里的条件为true才会进入执行代码  

while大括号里代码执行完毕后不会跳出，而是继续回到小括号里判断条件是否满足，若满足又执行大括号里的代码，然后再回到小括号判断条件，直到括号内条件不满足，即跳出

```js
 while (循环条件) {
        要重复执行的代码(循环体)
    }

 // 循环必须有3要素
        // 变量的起始值
        let i = 1
        // 终止条件（没有终止条件，循环会一直执行，造成死循环）
        while (i <= 3) {
            document.write(`月薪过万 <br>`)
            // 变量变化量
            i++
        }

 // 求 1~100 之间的偶数累加和
        let i = 1
        let sum = 0
        while (i <= 100) {
            if (i % 2 === 0) {
                // 此时 i 一定是偶数
                sum = sum + i
            }
            // 不管你是偶数还是奇数我都要++
            i++
        }
        console.log(sum)
```

#### for 循环

也是重复执行代码  

好处：把声明起始值、循环条件、变化值写到一起，让人一目了然

```js
for (起始条件; 退出条件; 变化量) {
            循环语句
 }
 //  循环的最大价值就是遍历数组
        let arr = ['马超', '赵云', '张飞', '关羽', '黄忠', 'pink老师']
        // console.log(arr)
        // document.write(arr)
        // document.write(arr[0])
        // document.write(arr[1])
        // document.write(arr[2])
        // document.write(arr[3])
        // document.write(arr[4])
        // 利用循环的方式
        document.write(arr.length)
        // 2. arr.length  数组的长度  通过他可以告诉我们数组里面有几个元素
        for (let i = 0; i < arr.length; i++) {
            document.write(`名字是: ${arr[i]} <br>`)
        }
```

for循环嵌套

```js
 // 循环嵌套
        for (let i = 1; i < 6; i++) {
            for (let j = 1; j < 6; j++) {
                document.write('🔅')
            }
        }
        // 外面循环执行一次，里面循环执行全部（5次）
```

#### 循环退出

`continue`：结束本次循环，继续下次循环

`break`：跳出所在的循环

```js
  // 我们要打印吃包子
        let i = 1
        while (i <= 6) {
            if (i === 3) {
                i++
                // continue 结束本次循环 继续下一次循环
                // continue
                // 退出循环
                break
            }
            document.write(`我要吃第${i}个包子 <br>`)
            i++
        }

 for (let i = 1; i < 6; i++) {
            if (i === 2) {
                // continue  // 1345 继续 退出本次循环，继续下一次循环
                break  // 结束循环 退出整个循环
            }
            document.write(i)
        }
```

### 数组

数组(Array)是一种可以按顺序保存数据的数据类型

> 数组是按顺序保存，所以每个数据都有自己的编号  `let 数组名 = [元素1，元素2，...，元素n]`
>
> 数组中元素的编号从0开始，以此类推  `arr[0]`
>
> 在数组中，数据的编号也叫索引或下标 `数组名[下标]`
>
> 数组可以存储任意类型的数据

```js
 // 数组求和案例
        let arr = [2, 6, 1, 7, 4]
        // 求和变量
        let sum = 0
        // 求平均值变量
        let average = 0
        // 遍历数组
        for (let i = 0; i < arr.length; i++) {
             console.log(arr[i]) // arr[i] 就是数组里面的每个值 比如 2， 6
            sum += arr[i] // sum = sum + arr[i]
        }
        average = sum / arr.length
        document.write(`这个同学的总分是: ${sum}, 平均分是:${average}`)
```

#### 操作数组

查询数组数据：`数组[下标]`

重新赋值：`数组[下标] = 新值`

数组添加新的数据：`arr.push(新增的内容)`  `arr.unshift(新增的内容)`

> `数组.push()` 方法将一个或多个元素添加到数组的末尾，并返回该数组的新长度 (重点)
>
> `数组.unshift(新增的内容)` 方法将一个或多个元素添加到数组的开头，并返回该数组的新长度

删除数组中数据： `arr.pop()`  `arr.shift()`  `arr.splice(操作的下标,删除的个数)`

> `数组. pop()` 方法从数组中删除最后一个元素，并返回该元素的值
>
> `数组. shift()` 方法从数组中删除第一个元素，并返回该元素的值
>
> `数组. splice(start, deleteCount)` 方法 删除指定元素
>
>  `start`：起始位置，指定修改的开始位置（从0计数）  
>
>  `deleteCount`：表示要移除的数组元素的个数(可选)。 如果省略则默认从指定的起始位置删除到最后。

```js
 let arr = ['red', 'green']
        // 把 blue 放到 arr 的后面
         arr.push('blue')
        console.log(arr) //['red', 'green', 'blue']

 let arr = ['red', 'green']
       arr.unshift('pink', 'blue')
 console.log(arr) //['pink', 'blue', 'red', 'green']

   let arr = ['red', 'green', 'blue']
        // 删除最后一个元素
        // arr.pop()
         console.log(arr.pop()) // 看我删了一个， 删的是 最后一个 blue
         console.log(arr.shift()) // 看我删了一个， 删的是 第一个 red
        // shift是删除     unshift比shift 加了一个 un 表示加
        // console.log(arr)

        // 重点删除  arr.splice(从哪里开始删， 删几个)
        let arr = ['red', 'green', 'blue']
        //  我就想把green 删掉
        // 第一个1 是从索引号是1的位置开始删
        // 第二1 是删除几个
        // arr.splice(1, 1)
        // arr.splice(1) //从第一个删到最后
        console.log(arr)
```

#### 冒泡排序

```js
let arr = [2, 6, 4, 3, 5, 1]
        // 1. 外层循环控制  趟数   循环 4次   arr.length - 1
        for (let i = 0; i < arr.length - 1; i++) {
            // 2. 里层的循环 控制 一趟交换几次  arr.length - i - 1 次序
            for (let j = 0; j < arr.length - i - 1; j++) {
                // 交换两个变量
                // arr[j]   arr[j + 1]
                if (arr[j] > arr[j + 1]) {
                    let temp = arr[j]
                    arr[j] = arr[j + 1]
                    arr[j + 1] = temp
                }
            }
        }
        console.log(arr)
```

## 七、函数

函数： function，是被设计为执行特定任务的代码块

函数可以把具有相同或相似逻辑的代码“包裹”起来，通过函数调用执行这些被“包裹”的代码逻辑，这么做的优势 是有利于精简代码方便复用

### 函数使用

函数名命名规范和变量命名基本一致  

尽量小驼峰式命名法  

前缀应该为动词  

命名建议：<font color=Salmon>常用动词约定</font>

| 动词 | 含义                   |
| ---- | ---------------------- |
| can  | 判断是否可执行某个动作 |
| has  | 判断是否含有某个值     |
| is   | 判断是否为某个值       |
| get  | 获取某个值             |
| set  | 设置某个值             |
| load | 加载某些数据           |

```js
function 函数名() {
    函数体
}

// 1. 函数的声明，函数不调用自己不执行
        function sayHi() {
            document.write(`你好~~~`)
        }
// 2. 函数调用，可多次调用，每调用一次执行一次
        sayHi()
```

### 函数传参

若函数完成功能需要调用者传入数据，那么就需要用有参数的函数，这样可以极大提高函数的灵活性

> **形参**：声明函数时写在函数名右边小括号里的叫形参（形式上的参数）
>
>  形参可以理解为是在这个函数内声明的变量（比如 num1 = 10）
>
> **实参**：调用函数时写在函数名右边小括号里的叫实参（实际上的参数）  
>
>  实参可以理解为是给这个变量赋值  
>
> 开发中尽量保持形参和实参个数一致  
>
> 我们曾经使用过的 `alert('打印')`, `parseInt('11')`, `Number('11')` 本质上都是函数调用的传参

```js
 // 带有参数的函数
        function getSum(形参1,形参2...) {

        }
       getSum(实参1,实参2...)

  // 声明
        function getSum(num1, num2) { // 声明这个函数需要传入几个数据
            document.write(num1 + num2)
        }
        // 调用
        getSum(1, 2) // 多个数据用逗号隔开
       
        function getSum(x, y) {
            // x = 1 
            // document.write(x)
            // document.write(x + y)
            // 我们想要：如果调用的时候，我们没有传递实参，则默认为 0
            x = x || 0
            y = y || 0
            document.write(x + y)
        }
        // 调用
        // getSum(1, 2)
        getSum() // 0
        getSum(1, 2)  //3
```

**函数的参数个数**

```js
 // function fn(x, y) {
        //     // x = 1 
        //     // y = undefined
        //     // 1 + undefined  =  NaN
        //     console.log(x + y)
        // }
        // fn(1, 2)

        // 1. 实参个数少于形参   返回的结果 NaN
        // fn(1)
        // 2. 实参个数大于形参   非诚勿扰,多的剩下

        function fn() {
            // arguments 函数内有效   表现形式 伪数组 
            // 伪数组 比真数组 少了一些 pop()  push()  等方法 
            console.log(arguments) //  [1,2,3]
            let sum = 0
            for (let i = 0; i < arguments.length; i++) {
                sum += arguments[i]
            }
            console.log(sum)
        }

        fn(1, 2, 3)
```

技巧(实参默认值)

```js
    function fn(x, y) {
             x = x || 0
             y = y || 0
             console.log(x + y)
         }
         fn(1, 2) //3
         fn() //0
        // x 和 y 可以看做是 函数内部的局部变量
        // 调用的时候会有个内部判断是否有参数传递过来
        // 没有参数 则 执行 x = 0
        // 有参数，则执行 实参赋值
        function fn(x = 0, y = 0) {
            console.log(x + y)
        }
        fn()
        fn(3, 5)
```

### 函数返回值

函数是被设计为执行特定任务的代码块

执行完特定任务之后，然后把任务的结果返回给我们

**用`return`返回数据**

> 在函数体中使用 return 关键字能将内部的执行结果交给函数外部使用  
>
> 函数内部只能出现 1 次 return，并且 return 后面代码不会再被执行，所以 return 后面的数据不要换行写 return会立即结束当前函数  
>
> 函数可以没有 return，这种情况函数默认返回值为 undefined

````js
function fn() {
        return 20
}
fn()
console.log(fn()); //20
// return 相当于 执行了一句话   fn() = 20

 function fn() {
             // 退出函数的作用  return 后面的代码不在执行
            return
             alert(11) X
             return X
         }
         fn()

//return返回多个值
function fn(x, y) {
            let jia = x + y
            let jian = x - y
            // return jia, jian 结果值返回了 jian 因为return只能返回一个值
            return [jia, jian]
        }
        let re = fn(1, 2)   //  [3, -1]
        document.write(`相加之后的结果是：${re[0]},相减之后的结果是: ${re[1]} `)
````

### 作用域

通常来说，一段程序代码中所用到的名字并不总是有效和可用的，而限定这个名字的`可用性的代码范围`就是这 个名字的`作用域`。作用域的使用提高了程序逻辑的局部性，增强了程序的可靠性，减少了名字冲突。

> 全局作用域【全局有效】
>
> 作用于所有代码执行的 环境(整个 script 标签 内部)或者一个独立的 js 文件

> 局部作用域【局部有效】
>
> 作用于函数内的代码环 境，就是局部作用域。 因为跟函数有关系，所 以也称为函数作用域。

> 块级作用域【{}内有效】
>
> 块作用域由 { } 包括,if语 句和for语句里面的{ }等

#### 变量的作用域

> 全局变量 【函数外部let 的变量】
>
> 全局变量在任何区域都可以访问和修改

> 局部变量【函数内部let的变量】
>
> 局部变量只能在当前函数内部访问和修改

> 块级变量【{}内部的let变量】
>
> let定义的变量,只能在 块作用域里访问,不能跨 块访问,也不能跨函数访 问

<font color=Red>如果函数内部或者块级作用域内部，变量没有声明，直接赋值，也当全局变量看，但是强烈不推荐。</font>

<font color=RosyBrown>但是有一种情况，函数内部的形参可以看做是局部变量。</font>

#### 作用域链

变量访问原则-作用域链

只要是代码，就至少有一个作用域  

写在函数内部的局部作用域  

如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域  

根据在内部函数可以访问外部函数变量的这种机制，用链式查找决定哪些数据能被内部函数访问，就称作作用域链

**作用域链**：采取``就近原则``的方式来查找变量最终的值

### 匿名函数

#### 函数表达式

将匿名函数赋值给一个变量，并且通过变量名称进行调用 我们将这个称为函数表达式

```javascript
 // 函数表达式
        let fn = function () {
            console.log(111)
        }
        fn()

 let btn = document.querySelector('button')
        // btn.onclick = function () {
        //     alert('月薪过万')
        // }
        btn.addEventListener('click', function () {
            alert('月薪过10万')
        })
```

#### 立即执行函数

避免全局变量之间的污染

<font color=OrangeRed>注意： 多个立即执行函数要用 ; 隔开，要不然会报错</font>

```js
 //方式1
 (function () {
            console.log(111)
        })();
        
 // 防止结束符；写漏，常写开头
        ; (function () {
                console.log(222)
        })()

 //方式2
 (function () {
             console.log(111)
        }());
```

## 八、对象

对象（`object`）：JavaScript里的**一种数据类型**

可以理解为是一种**无序的数据集合**

> **对象有属性和方法组成**  
>
> 属性：信息或叫特征（名词）。 比如 手机尺寸、颜色、重量等…  
>
> 方法：功能或叫行为（动词）。 比如 手机打电话、发短信、玩游戏…

#### 属性

1. 属性都是成 对出现的，包括属性名和值，它们之间使用英文 `:` 分隔  

2. 多个属性之间使用英文 `,` 分隔  

3. 属性就是依附在对象上的变量（外面是变量，对象内是属性）  

4. 属性名可以使用 `""` 或 `''`，一般情况下省略，除非名称遇到特殊符号如空格、中横线等

```js
 // 声明人对象
        let person = {
            uname: '刘德华',
            age: 18,
            sex: '男',
            // 方法名：function(){}
            sayHi: function () {
                console.log('hi~~~')
            },
            mtv: function (s) {
                console.log(s)
            }
        }
        // 1. 访问属性  得到值   对象.属性名
        console.log(person.uname)
        console.log(person.age)
        // 2. 访问属性  得到值   对象['属性名']
        console.log(person['sex']) //等价console.log(person.sex)
        // 调用方法 对象.方法名()
        person.sayHi()
        person.mtv('无间道')
```

#### 方法

数据行为性的信息称为方法，如跑步、唱歌等，一般是动词性的，其本质是函数。

1. 方法是由方法名和函数两部分构成，它们之间使用 `:` 分隔
2. 多个属性之间使用英文 `,` 分隔
3. 方法是依附在对象中的函数
4. 方法名可以使用 `""` 或 `''`，一般情况下省略，除非名称遇到特殊符号如空格、中横线等

声明对象，并添加了若干方法后，可以使用 `.` 调用对象中函数，称之为方法调用。

```js
// 对象是有属性和方法组成的，那么属性和方法都要写在对象里面
        let ldh = {
            // 属性
            uname: '刘德华',
            // 方法   方法名: function(){}
            sing: function () {
                console.log('唱歌')
            },
            dance: function (s) {
                console.log(s)
            }
        }

        // 外部使用   对象.方法名()
        ldh.sing()
 //对象方法也可以传参，与函数使用方法基本一致
        ldh.dance('恭喜发财') 
```

<font color=SeaGreen>注意： 千万别忘了给方法名后面加小括号</font>

#### 操作对象

> **查询对象**
>
>  对象.属性 或者 对象[‘属性’]
>
>  对象.方法()

> **重新赋值**
>
>  对象.属性 = 值
>
>  对象.方法 = function() {}

> **添加数据**
>
>  对象名.新属性名 = 新值

> **删除属性**
>
>  delete 对象名.属性名

```js
   let obj = {
            uname: '小明',
            age: 18

        }
        console.log(obj.age)
        // 修改  对象.属性 =  新值
        obj.age = 81
        console.log(obj)
        // 新增一个属性  js 可以非常方便的动态新增属性或者方法
        obj.sex = '男'
        // 会去对象里面找是否有 sex这个属性，如果有则更新值修改
        // 会去对象里面找是否有 sex这个属性，如果没有则新增这个属性
        obj.sing = function () {
            console.log('hi')
        }
        console.dir(obj)

        // 删除 (了解)
        delete obj.uname
        console.dir(obj)
```

#### 遍历对象

对象没有像数组一样的length属性,所以无法确定长度

对象里面是无序的键值对, 没有规律. 不像数组里面有规律的下标

`k` 是获得对象的`属性名`， `对象名[k]` 是获得 `属性值`

```js
        let obj = {
            uname: '小明',
            age: 18,
            sex: '男'
        }
        // for  in  循环语句
        // for (let k in 对象名) {}  重点
        // k 变量   k  或者  key    value  
        for (let k in obj) {
            console.log(k)  // 属性名
            // console.log(obj.k)  // obj.k 意思是 obj里面的k属性,而这里的k是变量 undefined
            // console.log(obj['k']) //undefined
            console.log(obj[k])  // 属性值 

            // 为什么这么写？
            // k  ===  'uname'   === 'age'  === 'sex'
            // // obj.k
            // // obj['uname']
            // obj['sex']  === 18
        }
```

#### 内置对象

JavaScript内部提供的对象，包含各种属性和方法给开发者调用

如：`document.write()`  `console.log()`

**内置对象`Math`**

`Math`对象是JavaScript提供的一个“数学高手”对象  提供了一系列做`数学运算`的方法

方法有：  

`random()`：生成0-1之间的随机数（包含0不包括1）  

`ceil()`：向上取整  `floor()`：向下取整  

`max()`：找最大数  `min()`：找最小数  

`pow()`：幂运算  `abs()`：绝对值

```js
        console.log(Math.PI)  //  圆周率    π  
        console.log(Math.random())  //  随机数  随机抽奖  随机点名
        // 返回的是小数  但是能得到 0  得不到 1
        // 向上取整  返回的整数
        console.log(Math.ceil(1.1))  // ceil  2
        console.log(Math.ceil(1.5))  // ceil  2
        console.log(Math.ceil(1.9))  // ceil  2
        // 向下取整  返回的整数  floor  
        console.log(Math.floor(1.1))  // floor  1
        console.log(Math.floor(1.5))  // floor  1
        console.log(Math.floor(1.9))  // floor  1
        console.log('-------------------------------')
        // round 就近取整( .5往大取证)  返回的整数   
        console.log(Math.round(1.1))  // round  1
        console.log(Math.round(1.5))  // round  2
        console.log(Math.round(1.9))  // round  2
        console.log('-------------------------------')
        console.log(Math.round(-1.1))  // round  -1
        console.log(Math.round(-1.5))  // round  -1
        console.log(Math.round(-1.9))  // round  -2

        // 最大值和最小值
        console.log(Math.max(1, 5, 9, 45))
        console.log(Math.min(1, 5, 9, 45))
```

**生成任意范围随机数**

0~10：`Math.floor(Math.random() * (10 + 1))`

5~10：`Math.floor(Math.random() * (5 + 1)) + 5`

n~m：<font color=oyalBlue>Math.floor(Math.random() * (M - N + 1)) + N</font>

```js
   // 求得 N - M 之间的一个随机数公式
        // let random = Math.floor(Math.random() * (10 - 1 + 1)) + 1
        // console.log(random)
        // 封装一个随机数函数  min 到  max  
        function getRandom(min, max) {
            return Math.floor(Math.random() * (max - min + 1)) + min
        }
        let random = getRandom(1, 10)
        console.log(random)
        let random1 = getRandom(1, 50)
        console.log(random1)
```

## 九、拓展

### 术语解释

| 术语           | 解释                                                         | 举例                                               |
| -------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| 关键字         | 在JavaScript中有特殊意义的词汇                               | let、var、function、if、else、 switch、case、break |
| 保留字         | 在目前的JavaScript中没意义，但未来可能会具有特殊意义的词汇   | int、short、long、char                             |
| 标识（标识符） | 变量名、函数名的另一种叫法                                   | 无                                                 |
| 表达式         | 能产生值的代码，一般配合运算符出现                           | 10 + 3、age >= 18                                  |
| 语句           | 一句代码也称之为一条语句，一般按 用途还会分类：输出语句、声明语句、 分支语句 | 无                                                 |

### 数据类型的存放

`简单类型`又叫做基本数据类型或者`值类型`，`复杂类型`又叫做`引用类型`。

> **值类型**：简单数据类型/基本数据类型，在存储时变量中存储的是值本身，因此叫做值类型
>
> `string` ，`number`，`boolean`，`undefined`，`null`  

> **引用类型**：复杂数据类型，在存储时变量中存储的仅仅是地址（引用），因此叫做引用数据类型
>
> 通过 `new` 关键字创建的对象（系统对象、自定义对象），如 Object、Array、Date等
>
> 引用类型变量（栈空间）里存放的是地址，真正的对象实例存放在堆空间中

**堆栈空间分配区别：**

![image-20230113173412367](JavaScript%E5%9F%BA%E7%A1%80.assets/image-20230113173412367.png)

1、栈（操作系统）：由操作系统自动分配释放存放函数的参数值、局部变量的值等。其操作方式类似于数据结构中的栈；

<font color=Tomato>简单数据类型存放到栈里面 </font>

![image-20230113173716075](JavaScript%E5%9F%BA%E7%A1%80.assets/image-20230113173716075.png)

2、堆（操作系统）：存储复杂类型(对象)，一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收。

 <font color=Tomato>引用数据类型存放到堆里面</font>

![image-20230113173953482](JavaScript%E5%9F%BA%E7%A1%80.assets/image-20230113173953482.png)
