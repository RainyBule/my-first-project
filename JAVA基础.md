# JAVA基础

## 入门篇

### 注释

单行注释//          快捷键为ctrl+/

多行注释/*   */   快捷键为ctrl+shift+/

注释的颜色字体可在setting中修改

不要注释嵌套

### 关键字

特点：字母全部小写、单词高亮显示

public class+类名{

​	类的范围

}

- C 语言视角：C 语言是面向过程的，只有函数；而 Java 是面向对象的，**一切皆类**。
- 强制规则：
  - 一个 `.java` 文件里只能有一个 `public` 类。
  - 文件名必须和这个 `public` 类名一模一样（大小写敏感）。
  - 这就像 C 语言里，头文件通常要和里面的主要结构体或函数对应一样，但 Java 管得更严

```java
package com.zlj.test;
// package： 表示当前的类定义在哪个包下
// 这段代码不需要我们自己写，是IDEA自动生成的

//表示定义一个类
//class：表示定义一个类，类是java项目中最基本的组成单元
//HelloWorld：类名，类名必须与文件名一致
public class HelloWorld {
    static void main() {
        System.out.println("Hello World");//输出语句
    }
}

```

### 主方法

**主方法 (**`public static void main(String[] args)`**)**

快捷缩写**psvm**

这是你最需要注意的地方，也是 Java 最死板的地方。

在 Java 中，`public` 的意思是“公开的”。
如果一个类被声明为 `public`，就意味着它是**给外界看的**，是给其他程序调用的。

- **`public`**：公开的。因为 JVM（Java 虚拟机）是从外面调用这个方法的，所以它必须公开。

- **`static`**：静态的。**这和 C 语言里的 `static` 有点像**，意味着它属于类本身，不需要 `new` 一个对象就能运行。JVM 启动时还没创建任何对象，所以入口必须是 `static` 的。

- **`void`**：没有返回值。

- **`main`**：方法名，JVM 只认准这个名字。

- `String[] args`

  。这是命令行参数。

  - 在 C 语言里，`main` 函数通常写成 `int main(int argc, char *argv[])`。
  - 在 Java 里，它把参数封装成了一个字符串数组 `String[] args`。哪怕你不用参数，这个格式也必须写上，否则 JVM 会认为“找不到入口”，直接报错。

  但public对于Java25来说是多余的，新版通常直接写成

  ```java
  static void main() {
  
  }
  ```

## 语法篇

### 字面量

![image-20260504162714309](../assets/image-20260504162714309.png)

练习  输出恐龙的信息：年龄 体重 性别

![image-20260504164039440](../assets/image-20260504164039440.png)

### 变量

变量是存储数据的小空间，而不是数据

定义格式如下

![6e60956334501437dd69eaa19894d54c](../assets/6e60956334501437dd69eaa19894d54c.png)

变量定义及数据类型与C语言一样的

练习 输出余额

![8b35c36a04aa7b2f929989c73f713cf4](../assets/8b35c36a04aa7b2f929989c73f713cf4.png)

变量的注意事项

- 只能存一个值
- 变量名不允许重复定义
- 变量在使用之前一定要进行赋值（变量a没有存数据时不能输出a，无意义）
- 一条语句可以定义多个变量，也可以连续赋值（a=b=c=d=10）

### 计算机存储规则

在计算机中，任意数据都是以二进制的形式来存储的

在计算机中，不同类型的数据有不同的存储单元

字节是最小的存储单元，1字节=8bit

在Java中，int类型占4个字节/32个bit位

### 数据类型

| 整数  | 取值范围                         | 内存（字节） |
| ----- | -------------------------------- | ------------ |
| byte  | -128~127                         | 1            |
| short | -32768~32767                     | 2            |
| int   | -2147483648~2147483647（10位数） | 4            |
| long  | 19位数                           | 8            |

在计算机表示56

若为byte类型，则是00111000

若为short类型，则是00000000 00111000

```java
//1.定义byte类型的变量
byte b=127;
System.out.println(b);

//2.定义short类型的变量
short s=32767;
System.out.println(s);

//3.定义int类型的变量
int i=200;
System.out.println(i);

//4.定义long类型的变量
//long类型数据必须以L或l结尾：`long l=10000000000L;`
long l=10000000000L;  
System.out.println(l);
```



| 浮点数 | 取值范围                     | 内存（字节） |
| ------ | ---------------------------- | ------------ |
| float  | -3.402 *10^38~3.402  *10^38  | 4            |
| double | -1.797 *10^308~1.797 *10^308 | 8            |

```java
//定义float类型的变量
//浮点数类型的变量，必须以f或F结尾，也可以不写
float f=1.1f;
System.out.println(f);

//定义double类型的变量
double d=1.1;
System.out.println(d);
```

字符型：char 二个字节      ‘好’   ‘a’ 

```java
char c='中';
System.out.println(c);
```

**注意：C语言中的char不能存储中文，但是Java里可以**

布尔型：boolean 一个字节   true/false

```java
boolean bb=ture;
System.out.println(bb);//打印出的就是ture，但在C语言中就是1/0
```

string、数组都是引用数据类型，其他是基本数据类型

### 标识符

代码中所有我们自己起的名字。比如类名、变量名、方法名

其命名有以下硬性要求

- 由数字、字母、下划线__、美元符￥组成
- 不能以数字开头
- 不能是关键字
- 区分大小写

驼峰命名法

1. **小驼峰命名法 (lowerCamelCase)**
   - **规则**：第一个单词的首字母小写，后续每个单词的首字母大写。
   - **用途**：在 Java、JavaScript 等语言中，**通常用于变量名和方法名**。
   - **示例**：`userName`, `calculateTotalPrice`, `getStudentInfo`
2. **大驼峰命名法 (UpperCamelCase / PascalCase)**
   - **规则**：每个单词的首字母都大写。
   - **用途**：在 Java 等语言中，**通常用于类名、接口名**。
   - **示例**：`StudentInfo`, `UserService`, `DataProcessor`

### 键盘录入

相当于c语言里的scanf，但Java需要先创建一个Scanner对象

```java
package com.zlj.test;

import java.util.Scanner;

public class demo09 {
    static void main() {
        /*
            键盘录入：
            1. 创建Scanner对象（创建了一个Scanner类型的变量）
            2. 录入数据
            3. 输出数据
            4. 关闭Scanner对象
            就是要找到Scanner这个打工人，然后让它干活
         */

        //Scanner为类名（固定） sc为变量名（自定义）
        //右边的赋值表示“从键盘获取输入”
        Scanner sc = new Scanner(System.in);

        //接收键盘录入的整数
        //.nextInt（）为方法名，读取一个整数，是规定好的功能
        int a = sc.nextInt();
        System.out.println(a);

        //接收键盘录入的double
        double b = sc.nextDouble();
        System.out.println(b);

        //接收键盘录入的字符串
        String c = sc.next();
        System.out.println(c);
    }

}

```

### println输出

```java
//字符串输出
System.out.println("你好，世界！");

//值输出
int Num=100;
System.out.prinln(Num);

//混合输出
int num1 = 10;
int num2 = 20;
System.out.println("第一个数是：" + num1 + "，第二个数是：" + num2);

// 也可以在里面直接做数学运算（记得加括号）
System.out.println("它们的和是：" + (num1 + num2));
```

文字与数字间**的 `+` 号不叫加法，叫“拼接”。** 它的作用是把前后的内容粘成一条长长的字符串。快捷缩写`sout`

### 类型转换

#### 隐式转换

不同类型的数据进行计算，默认采取隐式转换，java自动转换，无需我们写代码

如有byte short类型的数据，先提升为int类型

把取值范围小的提升为取值范围大的，再进行运算

| 变量  | 类型 |
| ----- | ---- |
| a     | byte |
| b     | byte |
| c=a+b | int  |

| 变量  | 类型   |
| ----- | ------ |
| a     | double |
| b     | byte   |
| c=a+b | double |

#### 强制转换

强制转换不会自动触发，需要手动书写代码

书写格式：目标数据类型 变量名=（目标数据类型）被强转的数据;

```java
int a=10;
byte b=(byte)a;
```



不能把大类型变量赋值给小类型

例如

```java
short a=10;
short b=10;
byte c=a+b;
```

a+b会隐形转换为int类型，上面代码试图把int类型变量赋值给byte类型变量，会出现报错，虽然byte足以储存20这个数，但是编译器为了安全起见，认为 `int` 变量**有可能**超出 `byte` 的范围，所以它强制要求你进行**强制类型转换**。必须写成`byte c=(byte)a+b;`

数据类型的范围大小顺序是：`double` > `float` > `long` > **`int`** > **`char`** > `short` > `byte`。

- **从小给大**（比如 `int` 给 `long`）：安全，直接给（自动类型转换）。
- **从大给小**（比如 `int` 给 `char`）：危险，可能会丢数据，必须加 `(char)` 强转（强制类型转换）。

但是强制转换有**弊端：有可能会改变原有数据**。例如：

int类型的300：二进制00000000 00000000 00000001 00101100

把它强制转换为byte，就是去掉前面三个字节  变为00101100  其十进制是44而不是300

所以最好写成**`int c=a+b;`**

### 字符运算

<img src="../assets/image-20260507201232736.png" alt="image-20260507201232736" style="zoom: 50%;" />

大写字母=小写字母-32；

```java
package com.zlj.test;

public class demo16 {
    static void main() {
        //大写字母转换为小写
        char ch = 'A';
        System.out.println((char)(ch + 32));
        //小写字母转换为大写
        char ch1 = 'a';
        System.out.println((char)(ch1 - 32));

    }
}
```

疑惑：char既能表示数字，又能表示ASC码对应的字符，那它到底是数字还是字符

```java
public class CharSummary {
    public static void main(String[] args) {
        
        // --- 1. 存储本质：只存数字 ---
        // 虽然代码写的是 'A'，但计算机内存里实际存储的是整数 65 (ASCII码)。
        // char 类型只占 2 个字节，用来存这个整数。
        char c = 'A'; 

        // --- 2. 显示规则：看类型翻译 ---
        // 当变量类型是 char 时，println 会自动去查表（ASCII/Unicode），
        // 把数字 65 翻译成字符 'A' 打印出来。
        System.out.println(c); // 输出: A

        // --- 3. 运算规则：还原数字身份 ---
        // 一旦 char 参与数学运算（+ - * /），Java 会立即把它当作整数处理。
        // 这里的 c 会被视为 65，而不是 'A'。
        // 且根据规则，char 运算时会自动升级为 int 类型。
        int result = c + 1; // 相当于 65 + 1 = 66
        
        // 因为 result 是 int 类型，println 直接打印数字，不查表。
        System.out.println(result); // 输出: 66

        // --- 4. 赋值规则：大给小需强转 ---
        // c + 1 的结果默认是 int 类型（数字 66）。
        // 试图把 int（大范围）赋值给 char（小范围），编译器会报错。
        // 必须使用 (char) 强制转换，告诉编译器“我知道我在做什么”。
        char nextChar = (char) (c + 1); 

        // 此时 nextChar 存储的是数字 66。
        // 但因为它的类型是 char，打印时又会查表，显示为 'B'。
        System.out.println(nextChar); // 输出: B
    }
}
```

`char` 是最特殊的类型，它既是字符，也是数字。

- **本质**：它底层存的就是一个**数字**（0 到 65535），对应着ASCII 编码表。

- 什么时候是字符？

  - 当你用 `System.out.println(c)` 打印它时，或者赋值给另一个 `char` 时，它显示为**字符**（比如 `'A'`）。也就是打印char类型，无论你写的是char a=65还是char a=‘A’，只要它是char类型都会显示为字符

- 什么时候是数字？

  - 它本质就是数字，当你把它参与运算（`c + 1`）时，或者强制转为 `int` 时，它显示为**数字**（比如 `65`）。

    关于第一种当char c=65时

    如果你写的是char a=c+1会报错。

    如果是char a=(char)(c+1)时，a打印出来就是字符b。

    如果是int a=c+1时，它就变成了数字，不再是字符

    

### 字符串拼接运算

这张图讲清楚了 Java 中字符串（String）与 `+` 号的特殊规则，这也是 Java 和 C 语言最大的区别之一。

**核心原则**

1. **只有加法**：字符串只支持 `+` 操作，不支持 `-`、`*`、`/`。
2. **拼接本质**：只要 `+` 号两边**任意一方是字符串**，它就变成了“连接器”，而不是数学加法。
3. **自动转换**：非字符串数据（如数字）会被自动转成文本形式连接。

**运算顺序（从左到右）**

Java 是严格按照**从左往右**的顺序执行的，这点非常重要：

- 数字在前，字符串在后

  ：先算加法，再拼接。

  - `10 + 8 + "岁"` → 先算 `10+8` 得 `18` → 再拼 `"岁"` → 结果 `"18岁"`

- 字符串在中间

  ：前面的拼完，后面的接着拼。

  - `10 + 8 + "岁" + 1 + 2`
  - 第一步：`18 + "岁"` → `"18岁"`
  - 第二步：`"18岁" + 1` → `"18岁1"`
  - 第三步：`"18岁1" + 2` → `"18岁12"`

### 运算符

#### 算数运算符

\+ - * / %

与C语言一样

整数：整数相除结果还是整数，其他运算跟数学中是一模一样的

小数：小数直接参与计算，结果有可能不精确的

#### 自增自减运算符

与c语言一样的，不想说，略

#### 赋值运算符

其实也不想说，但我表格瘾犯了

| 符号 | 说明     | 举例                  |
| ---- | -------- | --------------------- |
| =    | 直接赋值 | int a=10，将10赋值给a |
| +=   | 加后赋值 | a+=b，将a+b的值给a    |
| -=   | 减后赋值 | a-=b，将a-b的值给a    |
| *=   | 乘后赋值 | a*=b,将a×b的值给a     |
| /=   | 除后赋值 | a/=b，将a÷b的商给a    |
| %=   | 取余赋值 | a%=b，将a÷b的余数给a  |

#### 关系/比较运算符

![image-20260507211626909](../assets/image-20260507211626909.png)

此处与c语言唯一的不同是结果类型**是 `boolean`（布尔值）**true或false，但c语言结果类型是int（整数）1或0

#### 逻辑运算符

![image-20260507212045183](../assets/image-20260507212045183.png)

- **`&&` (短路与)**：如果左边是假（C 是 0，Java 是 false），右边**根本不会执行**。
- **`||` (短路或)**：如果左边是真（C 是 1，Java 是 true），右边**根本不会执行**。

- **`&`（单与）**：不管左边是真还是假，**右边一定会执行**。
- **`|`（单或）**：不管左边是真是假，右边**一定会执行**

基本逻辑和c语言一样，但是操作数的类型要求更严格，java要求必须是boolean类型

C 语言遵循“非 0 即真”的原则。在逻辑运算中，整数可以和逻辑值混用。
1 && 1 → 真 (1)

5 && 0 → 假 (0) （因为 5 非 0，被视为真）

!10 → 假 (0)


Java 的逻辑运算符只能操作 boolean 类型（即 true 或 false）。绝对不允许使用数字（int）代替。
true && true → true

true && false → false

a>=60&&a<=80，当a为70时→ture，当a为55时→false

5 && 0 → 编译报错！ (Type mismatch: 不能将 int 转换为 boolean)

#### 三元运算符

 **基本语法**

三元运算符由三个操作数组成，格式如下：
`条件表达式 ? 值1 : 值2`

 **执行逻辑**

1. 先计算 **条件表达式** 的值（必须是 `boolean` 类型）。
2. 如果为 `true`，则取 **值1**。
3. 如果为 `false`，则取 **值2**。
4. 最终结果就是选中的那个值。

场景：求二个数的最大值

```java
int a = 10;
int b = 20;

// 语法：(条件) ? 真值 : 假值
int max = (a > b) ? a : b;

System.out.println(max); // 输出 20
```

#### 运算符优先级

<img src="../assets/image-20260507214008347.png" alt="image-20260507214008347" style="zoom: 33%;" />

记住小括号优先于所有即可

### 分支/选择结构

#### 判断语句（if）

分为简单if语句、if-else语句、if-else if-else嵌套语句

**1.简单if语句**

这是最基本的形式，当条件为 `true` 时，执行大括号内的代码；如果为 `false`，则直接跳过。

```java
if (条件表达式) {
    // 条件为真时执行的代码
}
```

小细节：（个人觉得K&R风更舒服点）

![image-20260507215751307](../assets/image-20260507215751307.png)

```java
package com.itheima.ifdemo;

public class IfDemo4 {
    public static void main(String[] args) {
        /* 4. 判断布尔类型的变量
           判断布尔类型的变量，直接把变量写在小括号中即可*/

        boolean b = false;

        if(b){
            System.out.println("为真");
        }
    }
}
```

**2.if-else语句**

这是“二选一”的场景。如果条件为 `true`，执行 `if` 块的代码；否则，执行 `else` 块的代码。

```java
if (条件表达式) {
    // 条件为真时执行的代码
} else {
    // 条件为假时执行的代码
}
```

**3.if-else if-else语句**

当需要处理多个互斥的条件时，可以使用这种“多选一”的结构。程序会从上到下依次判断，一旦某个 `if` 或 `else if` 的条件为 `true`，就执行其对应的代码块，然后整个判断结构结束。

```java
if (条件1) {
    // 条件1为真时执行
} else if (条件2) {
    // 条件1为假，且条件2为真时执行
} else if (条件3) {
    // 条件1、2都为假，且条件3为真时执行
} else {
    // 以上所有条件都为假时执行
}
```



#### 选择语句（switch）

`switch` 语句适用于需要根据**单个变量或表达式**的值，从多个固定的选项中进行选择的场景。相比一连串的 `if-else if`，代码结构通常更清晰。

```java
switch (表达式) {
    case 值1:
        // 当表达式的值等于 值1 时执行的代码
        break; // 跳出 switch 结构
    case 值2:
        // 当表达式的值等于 值2 时执行的代码
        break;
    // ... 可以有任意数量的 case
    default:
        // 当表达式的值与所有 case 都不匹配时执行的代码
}
```

 **核心规则**

1. **表达式类型**：`switch` 后面的表达式结果必须是特定类型，例如 `byte`、`short`、`int`、`char`、`String`（Java 7 及以上）或枚举类型。
2. **`break` 关键字**：每个 `case` 语句块末尾的 `break` 非常重要，它的作用是**跳出**整个 `switch` 结构。
3. **`case`穿透：**如果缺少 `break`，程序会继续执行下一个 `case` 的代码，直到遇到 `break` 或 `switch` 结束，这种现象称为“穿透”。
4. **`default` 分支**：`default` 是可写可不写的，类似于 `if-else` 结构中的 `else`，用于处理所有未明确列出的情况。它的位置可以写在switch代码块里的任意位置（开头、中间、结尾）。为了代码的可读性，建议写在最后

**switch新特性**（JDK14+）

- 箭头语法 (`->`)

  用`->`取代case后的冒号： 

  **好处**：代码更简洁，**防止 case 穿透**（不需要写 break）。

  ```java
  //旧特性
  int score = 85;
  String result = ""; // 必须先定义空变量
  switch (score) {
      case 100:
          result = "满分"; 
          break; // 必须写 break，否则会继续执行下面的 case
      case 80, 90: // JDK 12+ 支持逗号合并
          result = "优秀";
          break; 
      case 60:
          result = "及格";
          break;
      default:
          result = "未知等级";
  }
  System.out.println(result);
  
  //新特性
  int score = 85;
  // 直接赋值，不需要预先定义 result
  String result = switch (score) {
      case 100 -> "满分";      // 无需break
      case 80, 90 -> "优秀";   // 逗号分隔多个值
      case 60 -> "及格";
      default -> "未知等级";
  };
  
  System.out.println(result);
  ```

  [哦买噶，字符串也能直接赋值了吗，c不可以的，插个眼]()

- 多值合并

  ```
  case 1, 2, 3 -> ...
  ```

  **好处**：用逗号分隔多个值，替代了旧式的“穿透写法”。

- 返回值 (表达式)

  ```
  int res = switch(...) { ... }
  ```

  **好处**：Switch 可以直接算出一个结果赋值给变量。

- **Yield 关键字**：用于在代码块中返回结果。

![18f7653108ad37066e6f2f2f12fb5c36](../assets/18f7653108ad37066e6f2f2f12fb5c36.png)

![a2ce2887391c26f9e1e569507519c807](../assets/a2ce2887391c26f9e1e569507519c807.png)

```java
import java.util.Scanner; // 1. 导入 Scanner 类

public class SwitchDemo5 {
    public static void main(String[] args) {
        // 2. 创建 Scanner 对象
        Scanner scanner = new Scanner(System.in);

        System.out.println("=== 简易计算器 ===");

        // 3. 获取用户输入的第一个数字
        System.out.print("请输入第一个数字 (a): ");
        int a = scanner.nextInt();

        // 4. 获取用户输入的运算符号
        System.out.print("请输入运算符 (+, -, *, /): ");
        // next() 读取一个字符串，因为我们 switch 用的是 String
        String operator = scanner.next();

        // 5. 获取用户输入的第二个数字
        System.out.print("请输入第二个数字 (b): ");
        int b = scanner.nextInt();

        System.out.println("----------------");

        // 6. Switch 表达式计算
        // 注意：除法这里为了演示保持整数除法，如果需要小数，需将 int 强转为 double
        int result = switch (operator) {
            case "+" -> a + b;
            case "-" -> a - b;
            case "*" -> a * b;
            case "/" -> {
                if (b == 0) {
                    System.out.println("错误：除数不能为0！");
                    yield 0;
                }
                yield a / b;
            }
            default -> {
                System.out.println("错误：不支持的运算符！");
                yield 0;
            }
        };

        // 7. 输出结果
        System.out.println("计算结果: " + a + " " + operator + " " + b + " = " + result);

        // 8. 关闭 scanner，释放资源
        scanner.close();
    }
}
```

### 循环结构

#### for循环

格式：

for（初始化语句;条件判断语句;条件控制语句）{

​	      循环体语句

}

执行流程：
① 执行初始化语句
② 执行条件判断语句，看其结果是否成立
成立：执行循环体语句，然后执行条件控制语句，然后回到② 
不成立：结束循环

```java
// 打印 1 到 5
for (int i = 1; i <= 5; i++) {
    System.out.println("这是第 " + i + " 次");
}

//int i也可以写在for循环外面
int i=1;
for(;i<=5;i++){
    System.out.println("这是第"+i+"次");
}
```

初始化语句、条件判断语句、条件控制语句可以不写，但是之间的分号不能省略

条件判断语句被省略，则为无限循环/死循环，注意在无限循环的下面，不能写任何其他代码，否则会报错

#### while循环

格式：

初始化语句

while(条件判断语句){

​	循环体语句

​	条件控制语句

}

```java
int guess = 0;
int target = 7;
// 只要没猜对，就一直问
while (guess != target) {
    System.out.println("请输入数字：");
    // 这里需要配合 Scanner 获取输入
    // guess = scanner.nextInt(); 
    break; // 暂时用 break 防止死循环
}
```

for和while的区别：

for循环中：知道循环次数或循环的范围

while循环：不知道循环的次数和范围，只知道循环的结束条件

#### do-while循环

格式：

初始化语句;

do{

​	循环体语句;

​	条件控制语句;

}while(条件判断语句);

先执行后判断，循环体至少执行一次，而while是先判断再执行

```java
int choice;
do {
    System.out.println("=== 主菜单 ===");
    System.out.println("1. 登录");
    System.out.println("0. 退出");
    // choice = scanner.nextInt();
    choice = 0; // 模拟退出
} while (choice != 0); // 至少显示一次菜单
```

#### break和continue

 break：直接结束

- 含义：打断、终止。
- 作用：一旦遇到 break，整个循环立刻停止，不再进行下一次判断，直接跳出循环体，执行循环后面的代码。
- 生活案例：你在吃一筐苹果，吃到第 3 个发现是烂的（满足条件），你直接把整筐苹果扔了，剩下的都不吃了。

continue：跳过本次（单次要赖）

- 含义：继续（下一次）
- 作用：一旦遇到 `continue`，本次循环剩下的代码不跑了，直接进入下一次循环（比如去执行 `i++`，然后判断条件）。
- 生活案例：你在吃一筐苹果，吃到第 3 个发现是烂的（满足条件），你把这个烂苹果扔掉，然后继续吃第 4 个。

#### 猜数字游戏

```java
import java.util.Random;
import java.util.Scanner;

public class Test2 {
    public static void main(String[] args) {
        /*
            生成一个1~100之间的随机数，利用键盘录入模拟猜的动作，一直猜，直到猜中为止
         */

        // 1. 生成一个1~100之间的随机数
        Random r = new Random();
        int number = r.nextInt(100) + 1;
        System.out.println(number); // 这一行是为了方便测试，实际游戏中通常会去掉

        while (true) {
            // 2. 键盘录入模拟猜的动作
            Scanner sc = new Scanner(System.in);
            System.out.println("请输入你要猜的数字：");
            int guessNumber = sc.nextInt();

            // 3. 比较
            if (guessNumber > number) {
                System.out.println("你猜的数字太大了");
            } else if (guessNumber < number) {
                System.out.println("你猜的数字太小了");
            } else {
                System.out.println("恭喜你猜对了");
                // 猜中了循环结束
                break;
            }
        }
    }
}
```

随机数生成代码

```java
// 生成 一个[min, max] 之间的随机数
Random r = new Random();
int num = r.nextInt(max - min + 1) + min;
```

#### 打印复杂图形

方法一：找规律

方法二：把复杂图形拆分为长方形和三角形，只要打印长方形和三角形就好

![image-20260508165441185](../assets/image-20260508165441185.png)

![image-20260508165525696](../assets/image-20260508165525696.png)

红色所围区域为要打印的平行四边形，第二种方法就是把这个四边形变成了多个三角形和长方形相加

#### 打印九九乘法表

```c++
package com.itheima.looploop;

public class Test6 {
    public static void main(String[] args) {
        /*
            打印九九乘法表
            1*1=1
            1*2=2 2*2=4
            1*3=3 2*3=6  3*3=9
            1*4=4 2*4=8  3*4=12 4*4=16
            1*5=5 2*5=10 3*5=15 4*5=20 5*5=25
            1*6=6 2*6=12 3*6=18 4*6=24 5*6=30 6*6=36
            1*7=7 2*7=14 3*7=21 4*7=28 5*7=35 6*7=42 7*7=49
            1*8=8 2*8=16 3*8=24 4*8=32 5*8=40 6*8=48 7*8=56 8*8=64
            1*9=9 2*9=18 3*9=27 4*9=36 5*9=45 6*9=54 7*9=63 8*9=72 9*9=81
         */

        // 1. 直角三角形 (9 * 9)
        // 外循环：行数
        for (int i = 1; i <= 9; i++) {
            // 内循环：列数
            for (int j = 1; j <= i; j++) {
                // 打印算式，\t 是制表符，用于对齐
                System.out.print(j + " * " + i + " = " + i * j + "\t");
            }
            // 每一行打印完后换行
            System.out.println();
        }
    }
}
```

#### **制表符\t**

- **简单理解**：

长度可变的大空格，打印表格数据的时候，可以使上下对齐

可以把它直接写在内容后面代替空格，如果一个\t没对齐可以多写几个

- **真正的含义：**

在前面的字符后面补**1~4**个空格，让这个整体（\t前面的内容及它本身）的长度凑成4的整数倍（IDEA）

部分编译器是补1~8个空格，凑成8的整数倍。

### 数组

#### 静态初始化

**完整格式**

数据类型 数组名[] = new 数据类型[]{数据值，数据值...};

int arr[]= new int []{1,2,3};

**简写格式**

数据类型 数组名[]={数据值，数据值...};

int arr[]={1,2,3};



[]可以写在数组名前也可以写在数组名后

**数组特点**：是连续的空间，一旦定义，长度不可变

#### 元素访问

元素的访问都是通过索引进行的

含义：数组的一个编号，也叫作：角标、下标、编号

特点：从0开始的，连续+1，不间断

**获取元素**

变量=数组名[索引]

int num=arr[5];

**修改元素**

数组名[索引]=数据值;

arr[5]=10;

#### 数组遍历

获取数组长度：`int L=arr.length`

```java
for(int i=0;i<arr.length;i++){
	System.out.printlin(arr[i]);
}
```

### 方法

**就等同于 C 语言里的“函数”**。它们都是将一段可重复使用的代码封装起来，完成特定任务。不过，由于 Java 是一门纯粹的面向对象语言，而 C 是面向过程的，所以“方法”在 Java 中有一些独特的规则和特性。

注意：方法不能嵌套，但c语言的函数可以

**Java 允许用局部变量给成员变量赋值**

![image-20260508203143193](../assets/image-20260508203143193.png)

格式：

public static 返回值类型 方法名(参数1，参数2...){

​	方法体;

​	return 返回值;

}

Java21+版本可以不写public

注意点：方法跟方法之间是平级关系，不能相互嵌套，故要写在main外面

```java
package com.zlj.test;

import java.util.Scanner;

public class demo5_1 {
    //方法的定义
    public static int getsum(int a,int b){
        return a+b;
    }
    static void main() {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        int sum = getsum(a, b);//方法的调用
        System.out.println(sum);
    }
}
/*
注意点：
方法跟方法之间是平级关系，不能相互嵌套
方法不会主动运行，需要被调用才可以
小括号中的参数需要一一对应
方法必须放在类（class）里面
 */
```

方法重载

同一个类中，定义了多个同名的方法，这些方法具有类似的功能

每个方法具有不同的参数类型和参数个数，这些同名的方法，就构成了重载关系

简单理解：同一个类，方法名相同，形参【类型、个数、顺序之一或以上】不同的方法构成重载关系，无需看返回值

![image-20260508212911741](../assets/image-20260508212911741.png)

但一般不会写成顺序不同的方式

<img src="../assets/image-20260510113248346.png" alt="image-20260510113248346" style="zoom: 67%;" />

a、b是int型，int会被提升为double，但第三个和第四个顺序不同，二个都可以，Java不知道调用哪个，所以报错了，如果把第二个注释掉，那么又能运行了

## 原理篇

### Java运行机制

**Java程序运行的过程**

HelloWorld.java文件（人类能看懂的源码）通过JDK中的javac编译器编译变为HelloWorld.class字节码文件，然后class文件运行在Java虚拟机（JVM）中而不是在操作系统里。 编译器的作用是把人类能看懂的 `.java` 源码，翻译成**JVM 能看懂的“字节码”**（也就是 `.class` 文件），然后由 JVM 内部的“翻译官”（执行引擎）把它进一步翻译成当前操作系统能听懂的 0 和 1 机器指令。也就是说编译后得到字节码，运行后才变成机器指令

**虚拟机（ VM）**

本质上就是**通过软件模拟出来的“假电脑”**。它是一台运行在你真实电脑（物理机）里的“电脑中的电脑”。这台虚拟出来的电脑拥有自己独立的 CPU、内存、硬盘和网卡，甚至可以安装和运行完全独立的操作系统（比如在你的 Windows 电脑里运行一个完整的 Linux 或 macOS 系统）。

分为系统虚拟机和进程虚拟机。之前用的雷电模拟器模拟手机操作系统，就是系统虚拟机，下载不同版本的虚拟机就能在任意操作系统里运行该软件，这种特性叫跨平台。也就是说手机游戏本身不能跨平台，只能在手机中运行，但它借助于不同版本的虚拟机实现了跨平台

**跨平台好处**：只要一个安装包就能在所有操作系统里运行

JDK里包含我们需要的虚拟机JVM，JVM是进程虚拟机。针对不同操作系统，我们安装不同版本的JDK（Java Development Kit开发者工具包）就可以了，

打开idea你可以看到src文件里是源代码，out里是编译后的代码

### 内存和内存地址

**内存：**

软件在运行时，用来临时存储数据的

把数据保存到内存中，从内存的对应位置（内存地址）把数据取出

**内存地址：**

内存以字节为单位划分，每个字节都有编号，叫做内存地址，用于快速管理内存空间

**内存地址编号规则：**

32位操作系统：内存地址以32位的二进制表示。共2^32个内存地址，最大支持内存：8*2 ^32次方（字节），也就是4096MB约等于4GB

64位的操作系统：内存地址以64位的二进制表示。最大内存地址：2^64     最大支持内存：2^64字节   17592186GB   17179TB

内存地址表示形式：二进制太长了，平常都是每四个二进制为一组转换为16进制来表示，方便阅读

底层存储的是二进制，显示形式是16进制

虽然叫“64位操作系统”，但在目前的实际硬件和系统设计中（如x86-64架构），为了降低硬件复杂度和成本，**真正被用到的地址线通常只有48位**（256TB）

### 变量和方法的内存分配

java虚拟机把内存分为了栈、堆、方法区、本地方法栈、程序计数器

栈跟方法有关系，方法被调用就进栈执行，方法执行完毕就从栈里出去

通过new开辟的空间一定在堆里面，如数组

class文件会加载在方法区内临时存储

![image-20260510125217525](../assets/image-20260510125217525.png)

![image-20260510125430567](../assets/image-20260510125430567.png)

方法被调用就进栈运行

### 数组的内存分配

![image-20260510125839965](../assets/image-20260510125839965.png)

int是基本数据类型，数组是引用数据类型，基本数据类型里存储的是真实的数据，传递的也是真实的数据，引用数据类型存储的数据的地址，传递的也是地址值

## 面向对象

### 类和对象

对象：把相关的数据和方法组织为一个整体来看待

面向对象：利用对象进行软件开发

面向对象的三大特效：**封装、继承、多态**

**类就是一种封装**

定义一个类描述一类事物

```java
public class dog(){
	string name;
	int age;
	string color;
	double weight;
}
```

创建对象，记录单独个体的所有信息

```java
Dog d=new Dog();
d.name="小白";
d.color="白色";
d.weight=5.5;
d.age=2;
```

小细节：

描述一类事物的类叫Javabean类

带有main方法的类叫测试类

Javabean类可以写属性和行为

注意：写在Javabean类里的方法是不加static的

### 封装

#### 数据安全问题(get/set)

防止用户输入错误数据

**private关键字：**

是一个权限修饰符,可以修饰成员变量和成员方法

特点：一旦被private修饰，只能在本类中才能访问，外界无法访问

虽然防止了输入错误数据，但是用了它我们也无法输入正确数据

可以调用set/get方法解决这个问题

**步骤：**

1、私有化成员变量

2、set/get方法（快捷方法alt+insert   或者直接鼠标右键空白处→生成→getter and setter→ctrl+A全选→一个回车）

详见源代码文件com.itheima.ooptest5

#### this关键字

成员变量：定义在方法外面、类里面的变量

局部变量：定义在方法里面或方法形参

就近原则

在方法中使用变量有查找顺序：先找局部变量，如果没有再用所在类的成员变量

```java
pubilc class Dog(){
	private int age;
	
	//set方法(赋值)，不写Static
	public void setAge(int age){
		age=age;
	}
	
	//get方法(获取)
	public int getAge(){
		return age;
	}
}
```

this作用：当变量名相同时，可用于区别成员变量和局部变量

如果想直接使用成员变量，就加this前缀，this.age就是成员变量

```
pubilc class Dog(){
	private int age;
	
	//set方法(赋值)，不写Static
	public void setAge(int age){
		age=age;
	  	System.out.println(this.age);
	}
	
	//get方法(获取)
	public int getAge(){
		return age;
	}
}
```

#### 构造方法/构造器

构造方法也叫构造器、构造函数

**作用：**创建对象的时候，由虚拟机JVM自动调用，给成员变量进行初始化

**特点：**

方法名与类名相同，大小写也要一致

没有返回值类型，连void也没有

没有具体的返回值（不能有return带回结果的数据）

**执行时机：**

创建对象的时候由虚拟机调用，不能手动调用构造方法

每创建一次对象就会调用一次构造方法

**格式：**

修饰符 类名(){

​	方法体;

}

```java
public class Student{
	private	String name;
	private int age;
	public Student(){
		空参构造方法
	}
	public Student(String name,int age){
 		带全部参数构造方法
	}
}
```

![image-20260510222033102](../assets/image-20260510222033102.png)

![image-20260511210729517](../assets/image-20260511210729517.png)

如果没有定义构造方法，系统将给出一个默认的无参数构造方法，如上，不会报错

如果定义了构造方法，系统将不再提供默认的构造方法，如下，没有无参构造，却又调用了，故报错

![image-20260511211331826](../assets/image-20260511211331826.png)

![image-20260511211109590](../assets/image-20260511211109590.png)

带参构造方法和无参数构造方法，二者方法名相同，但是参数不同，这叫做构造方法的重载

建议无论是否使用，都手动书写无参数构造方法，和带全部参数的构造方法

构造方法快捷键：alt+insert   或者直接鼠标右键空白处→生成→构造函数

#### 封装设计要求

合理隐藏，合理暴露

如何合理隐藏？

使用private关键字修饰成员变量，就只能在本类中直接访问，其他任何地方都不能直接访问

如何暴露？

使用public修饰的get（取值）和set（赋值）方法合理暴露

### 实体类

类中成员变量全部私有，并提供public修饰的getter/setter方法

类中需要提供一个无参数构造器，有参数构造器可选

基本作用：创建它的对象，存取数据（封装数据）

实体类的对象只负责数据存取，而数据的业务处理交给其他类完成，实现数据和数据业务处理相分离，也就是一个包建多个类

![image-20260511223054097](../assets/image-20260511223054097.png)

### 原理篇

#### Java中对象的内存分配

![image-20260513155727063](../assets/image-20260513155727063.png)

![image-20260513155741939](../assets/image-20260513155741939.png)

#### 对象在方法中进行传递

把一个对象传递给方法，实际传递的是**对象的内存地址**

当多个变量指向同一个对象的时候，只要有一个变量修改了对象中的属性，其他变量再次访问就是修改之后的结果了

#### this关键字的本质

代表所在方法调用者的内存地址

### static

#### static修饰成员变量

static：表示静态，是Java的修饰符，用来修饰成员变量/成员方法。

**1.静态变量**：被当前类所有的对象共享

​	共享：赋值只要赋值一次。**只要有一个对象修改了静态变量，其他对象再次访问的时候就是修改之后的结果了**

**2.调用方式：**

​	方式一：类名调用（推荐）

​	方法二：对象名调用

```java
public class Student {
    String name;//姓名
    int age;//年龄

    //学生共享一个老师
     static String teacherName;//老师的名字
}


Student.teacherName="小雯";    // 这是类名调用，之后创建的所有对象
Student s2 = new Student();
s2.teacherName="小雯";         //这是对象名调用
```

当前的属性如果是对象独有的则不加static，如果是对象共享的就要加static

详见代码com.itheima.staticvariabletest1

#### 静态变量的内存图

<img src="../assets/image-20260513213354195.png" alt="image-20260513213354195" />静态变量随着类的加载而加载的

第一行加载类，memory.class进到方法区

第二行加载main方法，main方法进栈

第三行用到Student类，故此时该类的字节码文件Student.class加载到方法区，并创造静态变量teacherName（静态区），**静态变量随着类的加载而加载的，会优先于对象出现**。JDK8前静态区在方法区里，之后就挪到了堆里，以后静态变量一律在堆内存。然后对该变量赋值

![image-20260513214130895](../assets/image-20260513214130895.png)第四行有new关键字，此时对象才会在内存出现，等号左边定义变量s1存放在栈内存，等号右边在堆内存开辟小空间，小空间里就是我们创建的对象，存着所有非静态的成员变量（name、age)，默认初始化值null、0  然后把小空间的内存地址赋值给栈内存里的s1，与此同时记录静态区的内存地址

![image-20260513214546057](../assets/image-20260513214546057.png)

第五行第六行给name、age赋值

第七行用s1调用show方法，show方法加载进栈，记录调用者s1的地址。由就近原则，先找show方法里有没有name、age（局部变量），没找到，再去s1地址找name、age（成员变量），打印出小诗诗，23，阿伟老师

![image-20260513214633954](../assets/image-20260513214633954.png)方法执行完毕后直接出栈

第八行创建第二个对象，把操作又重复了一遍，第九行show方法再次进栈

![image-20260513214855770](../assets/image-20260513214855770.png)

到此时show出栈，表示main方法全部执行完，然后main方法出栈，main方法里的变量和对象也会从内存中随之消失，但是静态区变量和方法区字节码信息会永远存在，除非关闭整个虚拟机

![image-20260513215316493](../assets/image-20260513215316493.png)

由此可见static静态变量只有一份，放在静态区中，在该类中被所有对象共享的

![image-20260513215537466](../assets/image-20260513215537466.png)



#### static修饰成员方法

特点：

static修饰的方法叫做静态方法

该方法多用在测试类和工具类中

Javabean类中很少会用

调用方式：

方式一：类名调用

方式二：对象名调用

工具类：不是用来描述一类事物的，也没有main方法，而是帮我们做一些事情的类。

类名见名知意

私有化构造方法（不让外界创造对象）

方法定义为静态 （类名调用方法）

```java
public class ArrayUtil{
	private ArrUtil(){
	public static int getMax(...){...}
	public static int getMin(...){...}
	public static int getSum(...){...}
	}
}
```



### final

### 枚举

## 疑惑

### 关于构造器

Java里的构造器用来给参数初始化，可是set/get方法也可以，那构造器是否有点多余？

- **构造器**：负责**“生”**。保证对象一出生就是合法的、有初始数据的。
- **Set 方法**：负责**“变”**。用于对象创建之后，根据业务需求修改数据（比如小狗长大了，年龄从 1 岁变成 2 岁）。

所以，它们不是谁替代谁，而是**分工合作**。通常我们写代码是**“构造器初始化 + Set 方法修改”**搭配使用的。

### c与Java的不同

C 语言是面向过程的，只有函数；而 Java 是面向对象的，**一切皆类**。

Java字符串用String类型，而不是c语言的char类型

c语言的bool类型在java里是boolean，且bool返回值为0或1，boolean返回值为ture或false

Java方法里的局部变量可以直接赋值给成员变量，但c语言函数是单独的模块，只能通过指针传地址来改该地址的值，不能直接赋值给函数外的变量

Java里字符串可以通过+号直接拼接，数字与字符串混合输出也是通过+号拼接，但c不行，必须格式化("%d %s",参数，参数)

### 其他

一般方法是public static +返回值类型+方法名(){},但写在Javabean类里的方法是不加static的

