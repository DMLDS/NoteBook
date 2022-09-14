## 1.Java基础

### 1.常用命令行操作

dir  	:列出当前目录下的文件以及文件夹
md 	:创建目录
rd  	:删除**目录**
cd	:进入指定目录
cd.. 	: 退回到上一级目录
cd/	:退回到根目录
del 	:删除**文件**（del  *.txt可以删除全部txt文件，以此类推）
exit 	: 退出dos 命令行
补充：echo javase>1.doc(创建文件1.doc，并向其中写入javase)
常用快捷键
← →：移动光标
↑↓：调阅历史操作命令
Delete和Backspace：删除字符
注意：在输入dos命令时，要是用英文输入，所有标点符号都是英文。

### 2.开发环境

- **JDK = JRE + 开发工具集（例如Javac编译工具等）**
- **JRE = JVM + Java SE标准类库**

### 3.注释

Java中的注释类型：

单行注释

格式：//注释文字

多行注释

格式：/* 注释文字*/
注：对于单行和多行注释，被注释的文字，不会被JVM（java虚拟机）解释执行。
多行注释里面不允许有多行注释嵌套

文档注释(java特有)

格式：

/**

@author  指定java程序的作者

@version  指定源文件的版本
*/

注释内容可以被JDK提供的工具javadoc所解析，生成一套以网页文件形式体现的该程序的说明文档。

解析注释内容命令：

​    javadoc -d  xxxx(文档名)  -author -version  xxxx(源代码名)

### 4.第一章小结

Java源文件以“java”为扩展名。源文件的基本组成部分是类（class），如本例中的HelloWorld类。
Java应用程序的执行入口是main()方法。它有固定的书写格式：
**public static void main(String[] args) {…}**
Java语言严格区分大小写。
Java方法由一条条语句构成，每个语句以“;”结束。
大括号都是成对出现的，缺一不可。
一个源文件中最多只能有一个public类。其它类的个数不限，如果源文件包含一个public类，则文件名必须按该类名命名。有多个类时，编译会生成多个字节码文件。

输出命令：System.out.println()

​                    System.out.print()   



##  2.变量、标识符、保留字、进制

### 1.标识符

#### 1.定义法则

1.**由 26 个英文字母大小写，0-9，_或$ 组成**

2.**数字不可以开头。**

3.**标识符不能包含空格。**

4.**不可以使用关键字和保留字，但能包含关键字和保留字。**

5.**Java 中严格区分大小写，长度无限制。**

####  2.标识符规范

​	1.包名：多单词组成时所有字母都小写：xxxyyyzz
​	2.类名、接口名：多单词组成时，所有单词的首字母大写：XxxYyyZzz
​	3.变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写：xxxYyyZzz
​	4.常量名：所有字母都大写。多单词时每个单词用下划线连接：XXX_YYY_ZZZ

#### 3.注意点

- 注意 1：在起名字时，为了提高阅读性，要尽量有意义，“见名知意”。
- 注意 2：java 采用 unicode 字符集，因此标识符也可以使用汉字声明，但是不建议使用。

### 2.变量

####  1.种类

   * 基本数据类型： 
     * 整型：byte \ short \ int \ long （long声明变量后面要加上l或L)	
     * 浮点型：float （float声明的变量后面要加上f或F）\ double 	
     * 字符型：char 	
       * 布尔型：boolean 	

* 引用数据类型： 	
  * 类：class 	
  * 接口：interface 	
  * 数组：array

#### 2.整型

**整型常量默认为int型**

| 类型  | **占用存储空间** | 表数范围               |
| ----- | ---------------- | ---------------------- |
| byte  | 1字节=8bit位     | -128 ~ 127             |
| short | 2字节            | -2^15~ 2^15-1          |
| int   | 4字节            | -2^31~ 2^31-1 (约21亿) |
| long  | 8字节            | -2^63~ 2^63-1          |

#### 3.浮点型

* 与整数类型类似，Java 浮点类型也有固定的表数范围和字段长度，不受具体操作系统的影响。

* 浮点型常量有两种表示形式：
  十进制数形式：如：5.12 512.0f .512 (必须有小数点）
  科学计数法形式:如：5.12e2 512E2 100E-2

* float:单精度，尾数可以精确到7位有效数字。很多情况下，精度很难满足需求。
  double:双精度，精度是float的两倍。通常采用此类型。
* **Java 的浮点型常量默认为double型，声明float型常量，须后加‘f’或‘F’。**

| 类型         | 占用存储空间 | 表数范围               |
| ------------ | ------------ | ---------------------- |
| 单精度float  | 4字节        | -3.403E38 ~ 3.403E38   |
| 双精度double | 8字节        | -1.798E308 ~ 1.798E308 |

* **注意** 

  虽然float变量只有4字节，少于long的8字节，但是float的4字节中每个bit位不全是0和1，一部分是0和1，另一部分表示的是10的幂，而long的8字节每个bit位全为0和1，所以float的表数范围远大于long

  

#### 4.字符型

* char 型数据用来表示通常意义上“字符”(**2字节**)
* Java中的所有字符都使用Unicode编码，故一个字符可以存储一个字母，一个汉字，或其他书面语的一个字符。
  字符型变量的三种表现形式：
  字符常量是用单引号(‘ ’)括起来的单个字符。例如：char c1 = ‘a’; char c2 = ‘中’; char c3 = ‘9’;
* Java中还允许使用转义字符‘\’来将其后的字符转变为特殊字符型常量。例如：char c3 = ‘\n’; //’\n’表示换行符
* 直接使用Unicode值来表示字符型常量：‘\uXXXX’。其中，XXXX代表一个十六进制整数。如：\u000a 表示\n。
  char类型是可以进行运算的。因为它都对应有Unicode码。

#####      ASCLL码

* 在计算机内部，所有数据都使用二进制表示。每一个二进制位（bit）有0 和1 两种状态，因此8个二进制位就可以组合出256 种状态，这被称为一个字节（byte）。一个字节一共可以用来表示256 种不同的状态，每一个状态对应一个符号，就是256 个符号，从0000000 到11111111。

* ASCII码：上个世纪60年代，美国制定了一套字符编码，对英语字符与二进制位之间的关系，做了统一规定。这被称为ASCII码。ASCII码一共规定了128个字符的编码，比如空格“SPACE”是32（二进制00100000），大写的字母A是65（二进制01000001）。这128个符号（包括32个不能打印出来的控制符号），只占用了一个字节的后面7位，最前面的1位统一规定为0。

* 缺点：
  不能表示所有字符。

  相同的编码表示的字符不一样：比如，130在法语编码中代表了é，在希伯来语编码中却代表了字母Gimel(ג)。

##### Unicode码 

* 乱码：世界上存在着多种编码方式，同一个二进制数字可以被解释成不同的符号。因此，要想打开一个文本文件，就必须知道它的编码方式，否则用错误的编码方式解读，就会出现乱码。

* Unicode：一种编码，将世界上所有的符号都纳入其中。每一个符号都给予一个独一无二的编码，使用Unicode 没有乱码的问题。

* Unicode 的缺点：Unicode 只规定了符号的二进制代码，却没有规定这个二进制代码应该如何存储：无法区别Unicode 和ASCII：计算机无法区分三个字节表示一个符号还是分别表示三个符号。

* 另外，我们知道，英文字母只用一个字节表示就够了，如果unicode统一规定，每个符号用三个或四个字节表示，那么每个英文字母前都必然有二到三个字节是0，这对于存储空间来说是极大的浪费。

##### UTF-8

* UTF-8 是在互联网上使用最广的一种Unicode 的实现方式。

* UTF-8 是一种变长的编码方式。它可以使用1-6 个字节表示一个符号，根据不同的符号而变化字节长度。

* UTF-8的编码规则：
  对于单字节的UTF-8编码，该字节的最高位为0，其余7位用来对字符进行编码（等同于ASCII码）。
  对于多字节的UTF-8编码，如果编码包含n 个字节，那么第一个字节的前n位为1，第一个字节的第n+1 位为0，该字节的剩余各位用来对字符进行编码。在第一个字节之后的所有的字节，都是最高两位为"10"，其余6位用来对字符进行编码。

#### 5.布尔类型

* boolean 类型用来判断逻辑条件，一般用于程序流程控制：
  - if条件控制语句；
  - while循环控制语句；
  - do-while循环控制语句；
  - for循环控制语句；

* boolean类型数据只允许取值true和false，无null。
  * **不可以使用0或非0 的整数替代false和true，这点和C语言不同。**
  * Java虚拟机中没有任何供boolean值专用的字节码指令，Java语言表达所操作的boolean值，在编译之后都使用java虚拟机中的int数据类型来代替：true用1表示，false用0表示。———《java虚拟机规范8版》

###   3.基本数据类型转换

#### 1.自动类型提升

* **当容量小的数据类型的变量和容量大的数据类型的变量做运算时，结果自动提升为容量大的数据类型。**

  **char、byte、short-->int-->long-->float-->double **

* **特别的：当byte、char、short三种类型的变量做运算时，结果为int类型**

  ```java
  class VariableTest2{
  	public static void main(String[] args) {
  		byte b1 = 2;
  		int i1 = 129;
  		
  		//编译不通过
  //		byte b2 = b1 + i1;
  		int i2 = b1 + i1;
  		long l1 = b1 + i1;
  		System.out.println(i2);
  		System.out.println(l1);
  
  		float f = b1 + i1;
  		System.out.println(f);
  		//***************特别的**************************
  		char c1 = 'a';	//97
  		int i3 = 10;
  		int i4 = c1 + i3;
  		System.out.println(i4);
  
  		short s2 = 10;
  		//编译错误
  //		char c3 = c1 + s2;
  		
  		byte b2 = 10;
  //		char c3 = c1 + b2;	//编译不通过
  
  //		short s3 = b2 + s2;	//编译不通过
  		
  //		short s4 = b1 + b2;	//编译不通过
  	}
  }
  class VariableTest4{
  	public static void main(String[] args){
  		//1. 编码情况
  		long l = 123456;
  		System.out.println(l);
  		//编译失败：过大的整数
  		//long l1 = 452367894586235;
  		long l1 = 452367894586235L;
  
  		//**************************
  		//编译失败
  //		float f1 = 12.3;
  		
  		//2. 编码情况2:
  		//整型变量，默认类型为int型
  		//浮点型变量，默认类型为double型
  		byte b = 12;
  	//	byte b1 = b + 1;	//编译失败
  		
  	//	float f1 = b + 12.3;	//编译失败
  	}
  }
  
  ```

  **整型变量，默认类型为int型**
  **浮点型变量，默认类型为double型**

#### 2.强制类型转换

* 自动类型转换的逆过程，将容量大的数据类型转换为容量小的数据类型。使用时要加上强制转换符：()，但可能造成精度降低或溢出,格外要注意。（**说明：此时容量大小指的是，表示数的范围的大和小。比如：float容量要大于long的容量**）
* 通常，字符串不能直接转换为基本类型，但通过基本类型对应的包装类则可以实现把字符串转换成基本类型。
* 如：String a = “43”; inti= Integer.parseInt(a);
* **boolean类型不可以转换为其它的数据类型。**

```java
short s = 5;
s = s-2; //判断：no
byte b = 3;
b = b + 4;//判断：no
b = (byte)(b+4);//判断：yes
char c = ‘a’;
int i = 5;
float d = .314F;
double result = c+i+d; //判断：yes
byte b = 5;
short s = 3;
short t = s + b;//判断：no

```

### 4.字符串类型：String

- **String不是基本数据类型，属于引用数据类型**
- 使用方式与基本数据类型一致。例如：String str= “abcd”;
- String类型变量的使用
  1. String属于引用数据类型
  2. 声明String类型变量时，使用一对""
  3. String可以和8种基本数据类型变量做运算，且运算只能是**连接运算；+**
  4. **运算的结果仍然是String类型**

- 一个字符串可以串接另一个字符串，也可以直接串接其他类型的数据。例如：

```java
class StringTest{
	public static void main(String[] args){

		String s1 = "Good Moon!";

		System.out.println(s1);

		String s2 = "a";
		String s3 = "";

//		char c = '';	//编译不通过
		//char类型必须不能空，String类型里面从空到无限长均可以
		//*******************************
		int number = 1001;
		String numberStr = "学号:";
		String info = numberStr + number;	//连接运算
		boolean b1 = true;
		String info1 = info + true;
		System.out.println(info1);
	}
}

```

```java
String str1 = 4; //判断对错：no
String str2 = 3.5f + “”; //判断str2对错：yes
System.out.println(str2); //输出：”3.5”
System.out.println(3+4+“Hello!”); //输出：7Hello!
System.out.println(“Hello!”+3+4); //输出：Hello!34
System.out.println(‘a’+1+“Hello!”); //输出：98Hello!
System.out.println(“Hello”+‘a’+1); //输出：Helloa1
```

### 5.进制转换

* 所有数字在计算机底层都以二进制形式存在。

* 对于整数，有四种表示方式：

* 二进制(binary)：0,1 ，满2进1.以0b或0B开头。

* 十进制(decimal)：0-9 ，满10进1。

* 八进制(octal)：0-7 ，满8进1. 以数字0开头表示。

* 十六进制(hex)：0-9及A-F，满16进1. 以0x或0X开头表示。此处的A-F不区分大小写。如：0x21AF +1= 0X21B0

#### 1.二进制！！！

* Java整数常量默认是int类型，当用二进制定义整数时，其第32位是符号位；当是long类型时，二进制默认占64位，第64位是符号位

* 二进制的整数有如下三种形式：

* **原码：直接将一个数值换成二进制数。最高位是符号位**

* **负数的反码：是对原码按位取反，只是最高位（符号位）确定为1。**

* **负数的补码：其反码加1。计算机以二进制补码的形式保存所有的整数。**

* **正数的原码、反码、补码都相同，负数的补码是其反码+1**

  ![img](https://img-blog.csdnimg.cn/img_convert/c2d9860f3b822dbeabac4b4ff6e0c7c5.png)

**原码与反码是帮助推导出补码而存在的！！！**

![img](https://img-blog.csdnimg.cn/img_convert/a200a439100aaa2c2721deb5c8664693.png)

- **计算机底层都是使用二进制表示的数值。**
- **计算机底层都是使用的数值的`补码`保存数据的。**

**所以说原码与补码没用，只是辅助记忆，计算机只认补码！**

#### 2.进制的转化

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/img_convert/050e3f2cd04de75da6e70a074670260d.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/img_convert/b3386e2cd8b7990a222895f6b0472d33.png#pic_center)

## 3.运算符

**自增自减与赋值运算符不改变数据类型！**

### 1.算术运算符

![img](https://img-blog.csdnimg.cn/img_convert/f7d0e93c6d24a078945d60f9a37a9518.png)

```java
class Day3Test{
	public static void main(String[] args) {

		//除号：/
		int num1 = 12;
		int num2 = 5;
		int resule1 = num1 / num2;
		System.out.println(resule1);	//2

		int result2 = num1 / num2 * num2;
		System.out.println(result2);

		double result3 = num1 / num2;
		System.out.println(result3);	//2.0

		double result4 = num1 / num2 + 0.0;	//2.0
		double result5 = num1 / (num2 + 0.0);	//2.4
		double result6 = (double)num1 / num2;	//2.4
		double result7 = (double)(num1 / num2);	//2.0
		System.out.println(result5);
		System.out.println(result6);

		// %：取余运算
		//结果的符号与被模数的符号相同
		int m1 = 12;
		int n1 = 5;
		System.out.println("m1 % n1 = " + m1 % n1);

		int m2 = -12;
		int n2 = 5;
		System.out.println("m2 % n2 = " + m2 % n2);

		int m3 = 12;
		int n3 = -5;
		System.out.println("m3 % n3 = " + m3 % n3);

		int m4 = -12;
		int n4 = -5;
		System.out.println("m4 % n4 = " + m4 % n4);

		//(前)++ : 先自增1，后运算
		//(后)++ ：先运算，后自增1
		int a1 = 10;
		int b1 = ++a1;
		System.out.println("a1 = " + a1 + ",b1 = " + b1);

        int a2 = 10;
		int b2 = a2++;
		System.out.println("a2 = " + a2 + ",b2 = " + b2);

		int a3 = 10;
		a3++;	//a3++;
		int b3 = a3;

		//注意点：
		short s1 = 10;
		//s1 = s1 + 1;	//编译失败
//		s1 = (short)(s1 + 1);	//正确的
		s1++;	//自增1不会改变本身变量的数据类型
		System.out.println(s1);

		//问题：
		byte bb1 = 127;
		bb1++;
		System.out.println("bb1 = " + bb1);

		//(前)-- :先自减1，后运算
		//(后)-- ：先运算，后自减1

		int a4 = 10;
		int b4 = a4--;	//int b4 = --a4;
		System.out.println("a4 = " + a4 + ",b4 = " + b4);
	}
}

```

**注意**

* **如果对负数取模，可以把模数负号忽略不记**，如：5%-2=1。但被模数是负数则不可忽略。此外，**取模运算的结果不一定总是整数。**

* 对于除号“/”，它的整数除和小数除是有区别的：整数之间做除法时，只保留整数部分而舍弃小数部分。例如：intx=3510;x=x/1000*1000; x的结果是？

* **“+”除字符串相加功能外，还能把非字符串转换成字符串**.例如：System.out.println(“5+5=”+5+5); //打印结果是？5+5=55 ?

* **取余运算结果的符号与被模数的符号相同

* **自增自减不改变数据类型**

### 2.赋值运算符

- 符号：
  - **当“=”两侧数据类型不一致时，可以使用自动类型转换或使用强制类型转换原则进行处理。**
  - 支持连续赋值。
- 扩展赋值运算符：`+=, -=, *=, /=, %=`
- **赋值运算符不改变数据类型**

```java
class MkFan{
	public static void main(String[] args) {
		//练习1：
		int i = 1;
		i *= 0.1;
		System.out.println(i);//输出0
		i++;
		System.out.println(i);//输出1

		//练习2：
		int m = 2;
		int n1 = 3;
		n1 *= m++; 
		System.out.println("m=" + m);	//3
		System.out.println("n1=" + n1);	//6

		//练习3：
		int n = 10;
		n += (n++) + (++n);
		System.out.println(n);	//32
	}
}

```

### 3.比较运算符

![img](https://img-blog.csdnimg.cn/img_convert/4c0e1372e661757c6da2ed97b586317f.png)

- 比较运算符的结果都是`boolean`型，也就是要么是true，要么是false。

- 比较运算符“`==`”不能误写成“=” 。

### 4.逻辑运算符

- `&`—逻辑与
- `|`—逻辑或
- `！`—逻辑非
- `&&` —短路与
- `||`—短路或
- `^` —逻辑异或

![img](https://img-blog.csdnimg.cn/img_convert/4add9a396703648c91b94525fafad732.png)

* 逻辑运算符用于连接布尔型表达式，在Java中不可以写成3<x<6，应该写成x>3 & x<6 。

* “&”和“&&”的区别：

* 单&时，左边无论真假，右边都进行运算；

* 双&时，如果左边为真，右边参与运算，如果左边为假，那么右边不参与运算。

* “|”和“||”的区别同理，||表示：当左边为真，右边不参与运算。

* 异或(^)与或( | )的不同之处是：当左右都为true时，结果为false。理解：异或，追求的是“异”!，异为true，同为false

### 5.位运算符

![img](https://img-blog.csdnimg.cn/img_convert/994544c74839171dbc3a8f12514c7ddc.png)

**注意：无<<<**

**后四种都是把两个数字的二进制写下来，然后相应位之间进行运算**

```java
/*
运算符之五：位运算符(了解)

结论：
1.位运算符操作的都是整型的数据变量
2.<< : 在一定范围内，每向左移一位，相当于 * 2
  >> : 在一定范围内，每向右移一位，相当于 / 2

面试题：最高效的计算2 * 8 ？	2 << 3 或 8 << 1
*/
class BitTest{
	public static void main(String[] args){
		int i = 21;
//		i = -21;
		System.out.println("i << 2 :" + (i << 2));
		System.out.println("i << 3 :" + (i << 3));
		System.out.println("i << 20 :" + (i << 20));
		System.out.println("i << 27 :" + (i << 27));
		int m = 12;
		int n = 5;
		System.out.println("m & n :" + (m & n));
		System.out.println("m & n :" + (m | n));
		System.out.println("m & n :" + (m ^ n));
		//练习：交换两个变量的值
		int num1 = 10;
		int num2 = 20;

		//方式一：
	//	int tent = num1;
	//	num1 = num2;
	//	num2 = tent;

		//方式二：
		//好处：不用定义临时变量
		//弊端：①相加可能超出存储范围 ② 有局限性：只适用于数值类型
//		num1 = num1 + num2;
//		num2 = num1 - num2;
//		num1 = num1 - num2;

		//方式三：使用位运算
		num1 = num1 ^ num2;
		num2 = num1 ^ num2;
		num1 = num1 ^ num2;

		System.out.println("num1 = " + num1 + ",num2 = " + num2);
	}
}

```

![img](https://img-blog.csdnimg.cn/img_convert/06975540d7771681c5bc64c58e4ebd2d.png)

### 6.三元运算符

**从右向左运算**

* 运算符之六：三元运算符
  1.结构：(条件表达式)？表达式1 : 表达式2

* 说明
  ① 条件表达式的结果为boolean类型
  ② 根据条件表达式真或假，决定执行表达式1，还是表达式2.
    如果表达式为true,则执行表达式1
    如果表达式为false,则执行表达式2
  ③ **表达式1 和表达式2类型要求是一致的，**

  **即如果两个表达式类型不统一，可能会有自动类型提升**

  ④ 三元运算符是可以嵌套的

* 凡是可以使用三元运算的地方，都是可以改写if-else。
  反之，则不一定成立！！！

### 7.运算符的优先级

- 运算符有不同的优先级，所谓优先级就是表达式运算中的运算顺序。如右表，上一行运算符总优先于下一行。
- 只有单目运算符、三元运算符、赋值运算符是从右向左运算的。

![img](https://img-blog.csdnimg.cn/img_convert/5909431ec9e6d00239b7ade5433e881d.png)

### 8.注意！！！

**byte char short之间运算后类型为int**

**连加连减，赋值运算（+=，-=等）不改变数据原类型**

## 4.程序流程控制

### 1.概述

  流程控制语句是用来控制程序中各语句执行顺序的语句，可以把语句组合成能完成一定功能的小逻辑模块。

其流程控制方式采用结构化程序设计中规定的三种基本流程结构，即：

*  顺序结构

- 分支结构

- 循环结构

  

* 1、顺序结构

  程序从上到下逐行地执行，中间没有任何判断和跳转。

* 2、分支结构

  根据条件，选择性地执行某段代码。
  有if…else和switch-case两种分支语句。

* 3、循环结构

  根据循环条件，重复性的执行某段代码。
  有while、do…while、for三种循环语句。
  注：JDK1.5提供了foreach循环，方便的遍历集合、数组元素。

### 2.顺序结构

Java中定义成员变量时采用合法的前向引用。如：

![img](https://img-blog.csdnimg.cn/img_convert/a8d98801448dd4e103449c9a21bc17e2.png)

### 3.分支语句

#### 1.if-else结构

![img](https://img-blog.csdnimg.cn/img_convert/98582479c99fc827cd6bcffcf9c2519b.png)

![img](https://img-blog.csdnimg.cn/img_convert/fa96e57b19acf19576a892ed142df686.png)

**使用说明：**

* 条件表达式必须是布尔表达式（关系表达式或逻辑表达式）、布尔变量；
* 语句块只有一条执行语句时，一对{}可以省略，但建议保留；
* if-else语句结构，根据需要可以嵌套使用；
* 当if-else结构是“多选一”时，最后的else是可选的，根据需要可以省略；
* 当多个条件是“互斥”关系时，条件判断语句及执行语句间顺序无所谓当多个条件是“包含”关系时，“小上大下/ 子上父下”。



#### 2.switch-case语句

**注意： switch结构中的表达式，只能是如下的六种数据类型之一：byte 、short、char、int、枚举类型(JDK5.0)、String类型(JDK7.0)**

**不能是：long，float，double，boolean**

**注意**

​		1.根据switch表达式中的值，依次匹配各个case中的常量。一旦匹		配成功，进入相应case结构中，执行相关语句。
 		 当调用完执行语句后，则仍然继续向下执行其他case语句，直到		遇到break关键字或末尾结束为止。

​		2.break, 可以使用switch-case结构中，表示一旦执行到此关键		字，就跳出switch-case结构。

​		3.switch结构中的表达式，只能是如下的六种数据类型之一：	byte、short、char、int、枚举类型(JDK5.0)、String类型(JDK7.0)
​		4.case 之后之能声明常量。不能声明范围。

​		5.break关键字是可选的。

​		6.default：相当于if-else结构中的else。
​		default 结构是可选的，而且位置是灵活的。

**若有多个相同的case执行语句，则可以对case进行合并**

​     **如 case 1 :  case 2 : case 3 :    System.out,print();break;**

```java
/*
编写程序：从键盘上输入2020年的“month”和“day”，
要求通过程序输出输入的日期为2019年的第几天。
2 15 : 31 + 15

5 7: 31 + 28 +31 +30 + 7
...
说明：break在switch-case中是可选的。
*/
import java.util.Scanner;
class DayTest{
	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		System.out.println("请输入2020年的month");
		int month = scan.nextInt();
		System.out.println("请输入2020年的day");
		int day = scan.nextInt();

		//定义一个变量来保存天数
		int sumDays = 0;
		switch(month){
		case 12:
			sumDays += 30;
		case 11:
			sumDays += 31;
		case 10:
			sumDays += 30;
		case 9:
			sumDays += 31;
		case 8:
			sumDays += 31;
		case 7:
			sumDays += 30;
		case 6:
			sumDays += 31;
		case 5:
			sumDays += 30;
		case 4:
			sumDays += 31;
		case 3:
			sumDays += 29;
		case 2:
			sumDays += 31;
		case 1:
			sumDays += day;
		}

		System.out.println("2020年" + month + "月" + day + "日是当年的第" + sumDays + "天");
	}
}
```

### 4.输入语句

**具体步骤：
1.导包：import java.util.Scanner;
2.Scanner的实例化;
3.调用Scanner类的相关方法，来获取指定的变量。**

**注意： scanner类相关方法里面没有读char型变量的方法，用读String类型的代替**

```java
import java.util.Scanner;

class IFTest{
	public static void main(String[] args){
		//声明一个Scanner
		Scanner scan = new Scanner(System.in);

		int num = scan.nextInt();

		System.out.println(num);
	}
}

```

###  5.循环结构

#### 1.for循环

**语法格式**
**for(①初始化部分;②循环条件部分;④迭代部分)｛**
            **③循环体部分;**
**｝**

**执行过程：①-②-③-④-②-③-④-②-③-④-.....-②**

**说明：**
**②循环条件部分为boolean类型表达式，当值为false时，退出循环**
**①初始化部分可以声明多个变量，但必须是同一个类型，用逗号分隔**
**④可以有多个变量更新，用逗号分隔**

#### 2.while循环

```java
①初始化部分
while(②循环条件部分)｛
    ③循环体部分;
    ④迭代部分;
}
12345
```

**执行过程：①-②-③-④-②-③-④-②-③-④-…-②**

#### 3.do-while循环

**do-while循环结构的使用**
**一、循环结构的四个要素**
**① 初始化条件**
**② 循环条件 --->是boolean类型**
**③ 循环体**
**④ 迭代条件**

**二、do-while循环的结构**
**①**
**do{**
	**③;**
	**④;**
**}while(②);**

**执行过程：① - ③ - ④ - ② -  ③ - ④ - ... - ②**

#### 4.嵌套循环结构

* **将一个循环放在另一个循环体内，就形成了嵌套循环。其中，for ,while ,do…while均可以作为外层循环或内层循环。**
* **实质上，嵌套循环就是把内层循环当成外层循环的循环体。当只有内层循环的循环条件为false时，才会完全跳出内层循环，才可结束外层的当次循环，开始下一次的循环。**
* **设外层循环次数为m次，内层为n次，则内层循环体实际上需要执行m*n次。**

```java
/*
100000以内的所有质数
质数：素数，只能被1和它本身整除的自然数。

最小的质数是：2
*/

class PrimeNuberTest{
	public static void main(String[] args){
		boolean isFlag = true;	//标识是否被除尽，一旦除尽，修改其值。
		int count = 0;	//记录质数的个数

		//获取当前时间举例1970-01-01 00:00:00 的毫秒数
		long start = System.currentTimeMillis();

		for(int i = 2;i <= 100000;i++){	//遍历100以内的自然数
			//优化2：对本身是质数的自然数有效 5447---> 11
		//	for(int j =2;j < i;j++){	//j:被i去除
			for(int j =2;j <= Math.sqrt(i);j++){	//j:被i去除
				if(i % j == 0){	//i被j除尽
					isFlag = false;
					break;	//优化一：只对本身非质数的自然数是有效的。
				}
			}
			if(isFlag == true){
			//	System.out.println(i);
				count++;
			}

			//重置isFlag
			isFlag = true;
		}

		//获取当前时间举例1970-01-01 00:00:00 的毫秒数
		long end = System.currentTimeMillis();


		System.out.println("质数的个数:" + count);
		System.out.println("所花费的时间为:" + (end - start));	//16843 --> 5447	优化一
	}
}

```

#### 5.break，continue的使用

##### 1.break

​	**break语句用于终止某个语句块的执行**

**{    
	......**
	**break;**
	**......**
**}**
**1**
**2**
**3**
**4**
**5**





* **break语句出现在多层嵌套的语句块中时，可以通过标签指明要终止的是哪一层语句块**

**label1:	{	......**
**label2:		{	......**
**label3:			{	......**
					**break label2;**
					**......**
				**}**
			**}**
		**}**



##### 2.contuinue

- continue 语句
  - continue只能使用在循环结构中
  - continue语句用于跳过其所在循环语句块的一次执行，继续下一次循环
  - **continue语句出现在多层嵌套的循环语句体中时，可以通过标签指明要跳过的是哪一层循环**

##### 3.return

- return：并非专门用于结束循环的，它的功能是结束一个方法。当一个方法执行到一个return语句时，这个方法将被结束。
- 与break和continue不同的是，return直接结束整个方法，不管这个return处于多少层循环之内。

##### 4.特殊流程控制语句

* **break只能用于switch语句和循环语句中。**
* **continue 只能用于循环语句中。**
* **二者功能类似，但continue是终止本次循环，break是终止本层循环。**
* **break、continue之后不能有其他的语句，因为程序永远不会执行其后的语句。**
* **标号语句必须紧接在循环的头部。标号语句不能用在非循环语句的前面。**
* **很多语言都有goto语句，goto语句可以随意将控制转移到程序中的任意一条语句上，然后执行它。但使程序容易出错。Java中的break和continue是不同于goto的。**

### 6.注意！！！

**break 与continue通过lable定向跳出循环要注意是终止循环还是结束本次循环！！！**

## 5.数组

### 1.数组的概述

 * **一、数组的概述**

 * **1.数组的理解：数组(Array)，是多个相同类型数据按一定顺序排列的集合，**

 * **并使用一个名字命名，并通过编号的方式对这些数据进行统一管理。**

 * 

 * **2.数组的相关概念：**

 * >**数组名**

 * >**元素**

 * >**角标、下标、索引**

 * >**数组的长度：元素的个数**

 * 

 * **3.数组的特点：**

 * **1)数组属于引用类型的变量。数组的元素，既可以是基本数据类型，也可以是引用数据类型。**

 * **2)创建数组对象会在内存中开辟一整块连续的空间；**

 * **3)数组的长度一旦确定，就不能修改;**

 * **4)数组是有序排列的。**

 * 

 * **4.数组的分类：**

 * **① 按照维数：一维数组、二维数组、三维数组……**

 * **② 按照数组元素类型：基本数据类型元素的数组、引用类型元素的数组**

### 2.一维数组

**1一维数组的声明和初始化**

**2如何调用数组的指定位置的元素  **

**3 如何获取数组的长度 **

**4 如何遍历数组 **

**5数组元素的默认初始化值：见ArrayTest1.java**

**6 数组的内存解析：见ArrayTest1.java**

​    

```java
public class ArrayTest {
	public static void main(String[] args) {
		
		//1. 一维数组的声明和初始化
		int num;	//声明
		num = 10;	//初始化
		int id = 1001;	//声明 + 初始化
		
		int[] ids;	//声明
		//1.1静态初始化:数组的初始化和数组元素的赋值操作同时进行
		ids = new int[]{1001,1002,1003,1004};	
		//1.2动态初始化:数组的初始化和数组元素的赋值操作分开进行
		String[] names = new String[5]; 
		
		//错误的写法：
//		int[] arr1 = new int[];	//未赋值、未指明长度
//		int[5] arr2 = new int[5];
//		int[] arr3 = new int[3]{1,2,3};
		
		//也是正确的写法：
		int[] arr7 = {1,2,3,5,4};//类型推断
		
		/*总结：数组一旦初始化完成，其长度就确定了。
		*/
		
		//2.如何调用数组的指定位置的元素：通过角标的方式调用。
		//数组的角标(或索引)从0开始的，到数组的长度-1结束
		names[0] = "张郃";
		names[1] = "王陵";
		names[2] = "张学良";
		names[3] = "王传志";	//charAt(0)
		names[4] = "李峰";
//		names[5] = "周礼";	//如果数组超过角标会通过编译，运行失败。
		
		//3.如何获取数组的长度
		//属性：length
		System.out.println(names.length);	//5
		System.out.println(ids.length);	//4
		
		//4.如何遍历数组
//		System.out.println(names[0]);
//		System.out.println(names[1]);
//		System.out.println(names[2]);
//		System.out.println(names[3]);
//		System.out.println(names[4]);
		
		for(int i = 0;i < names.length;i++){
			System.out.println(names[i]);
		}
		
	}
}

```

 



数组元素的默认初始化值

 * 	**数组元素是整形：0**
 * 	**数组元素是浮点型：0.0**
 * 	**数组元素是char型：0或'\u0000'，而非'0'（ASCLL码和Unicode码）**
 * 	**数组元素是boolean型:false**
 * 	**数组元素是引用数据类型：null**



```java
public class ArrayTest1 {
	public static void main(String[] args) {
		//5.数组元素的默认初始化值
		int[] arr = new int[4];
		for(int i = 0;i < arr.length;i++){
			System.out.println(arr[i]);
		}
		System.out.println("*****************");
		
		short[] arr1 = new short[4];
		for(int i = 0;i < arr1.length;i++){
			System.out.println(arr1[i]);
		}
		System.out.println("*****************");
		
		float[] arr2 = new float[5]; 
		for(int i = 0;i < arr2.length;i++){
			System.out.println(arr2[i]);
		}
		System.out.println("*****************");
		
		char[] arr3 = new char[5]; 
		for(int i = 0;i < arr3.length;i++){
			System.out.println("----" + arr3[i] + "****");
		}
		
		if(arr3[0] == 0){
			System.out.println("你好！");
		}
		System.out.println("*****************");
		
		boolean[] arr4 = new boolean[5];
		System.out.println(arr4[0]);
		
		System.out.println("*****************");
		String[] arr5 = new String[5];
		System.out.println(arr5[0]);
		//验证
		if(arr5[0] == null){
			System.out.println("北京天气好差！");
		}
		
	}
}

```

​     

#### 1.内存的简化结构

  ![img](https://img-blog.csdnimg.cn/img_convert/c01a07df72a603800e06f07a7f9e9a3b.png)

#### 2.一维数组的内存解析

```java
int[] arr = new int[]{1,2,3};
String[] arr1 = new String[4];
arr1[1] = “刘德华”;
arr1[2] = “张学友”;
arr1 = new String[3];
System.out.println(arr1[1]);//null

```

![img](https://img-blog.csdnimg.cn/img_convert/f75d3027e579de8103c4234856135118.png)

### 3.多维数组的使用

**二维数组的使用**



 * **1.理解**
 * **对于二维数组的理解，我们可以看成是一维数组array1又作为另一个一维数组array2的元素而存在。**
 * **其实，从数组底层的运行机制来看，其实没有多维数组。**
 * 
 * 
 * **2.二维数组的使用：**
 * **① 二维数组的初始化**
 * **② 如何调用数组的指定位置的元素**
 * **③ 如何获取数组的长度**
 * **④ 如何遍历数组**
 * **⑤ 数组元素的默认初始化值:见ArrayTest3.java**
 * **⑥ 数组的内存解析:见ArrayTest3.java**

```java
public class ArrayTest2 {
	public static void main(String[] args) {
		//1.二维数组的声明和初始化
		int[] arr = new int[]{1,2,3};
		//静态初始化
		int[][] arr1 = new int[][]{{1,2,3},{4,5,6},{7,8,9}};
		//动态初始化1
		String[][] arr2 = new String[3][2];
		//动态初始化2
		String[][] arr3 = new String[3][];
		
		//错误的情况
//		String[][] arr4 = new String[][];
//		String[][] arr5 = new String[][4];
//		String[][] arr6 = new String[4][3]{{1,2,3},{4,5,6},{7,8,9}};
		
		//正确的情况：
		int arr4[][] = new int[][]{{1,2,3},{4,5,12,6},{7,8,9}};
		int[] arr5[] = new int[][]{{1,2,3},{4,5,6},{7,8,9}};
		int[][] arr6 = {{1,2,3},{4,5,6},{7,8,9}};		
		
		//2.如何调用数组的指定位置的元素
		System.out.println(arr1[0][1]);	//2
		System.out.println(arr2[1][1]);	//null
		
		arr3[1] = new String[4];	//定义arr3的[1]为长度为4的字符数组
		System.out.println(arr3[1][0]);	//没有上句，会报错
		
		//3.获取数组的长度
		System.out.println(arr4.length);	//3
		System.out.println(arr4[0].length);	//3
		System.out.println(arr4[1].length);	//4
		
		//4.如何遍历二维数组
		for(int i = 0;i < arr4.length;i++){
			for(int j = 0;j < arr4[i].length;j++){
				System.out.print(arr4[i][j] + " ");
			}
			System.out.println();
		}
	}
}
```

**二维数组的使用：**

 * **规定：二维数组分为外层数组的元素，内层数组的元素**

 * **int[][] arr = new int[4][3];** 

 * **外层元素:arr[0],arr[1]等**

 * **内层元素:arr[0][0],arr[1][2]等**

   

 * **⑤ 数组元素的默认初始化值**

 * **针对于初始化方式一：比如：int[][] arr = new int[4][3];**

 * **外层元素的初始化值为：地址值**

 * **内层元素的初始化值为：与一维数组初始化情况相同**

 * 

 * **针对于初始化方式而：比如：int[][] arr = new int[4][];**

 * **外层元素的初始化值为：null**

 * **内层元素的初始化值为：不能调用，否则报错。**

   

 * **⑥ 数组的内存解析**

```java
public class ArrayTest3 {
	public static void main(String[] args) {
		
		int[][] arr = new int[4][3];
		System.out.println(arr[0]);	//[I@15db9742
		System.out.println(arr[0][0]);	//0
		
//		System.out.println(arr);	//ArrayTest3.java
		
		System.out.println("***********************");
		float[][] arr1 = new float[4][3];
		System.out.println(arr1[0]);	//地址值
		System.out.println(arr1[0][0]);	//0.0
		
		System.out.println("***********************");
		
		String[][] arr2 = new String[4][2];
		System.out.println(arr2[1]);	//地址值
		System.out.println(arr2[1][1]);	//null
		
		System.out.println("*********************");
		double[][] arr3 = new double[4][];
		System.out.println(arr3[1]);	//null
//		System.out.println(arr3[1][0]);	//报错
	}
}
```

#### 1.二维数组的内存解析

```java
int[][] arr1 = new int[4][];
arr1[1] = new int[]{1,2,3};
arr1[2] = new int[4];
arr1[2][1] = 30;
```

![img](https://img-blog.csdnimg.cn/img_convert/d4a8ec46ba57eb97884d158f6ea2f53b.png)

```java
int[][] arr4= new int[3][];
System.out.println(arr4[0]);//null
System.out.println(arr4[0][0]);//报错
arr4[0] = new int[3];
arr4[0][1] = 5;
arr4[1] = new int[]{1,2};
```

![img](https://img-blog.csdnimg.cn/img_convert/b1176f460c5c189ca4e7f11d2b75860b.png)

#### 2.练习

![img](https://img-blog.csdnimg.cn/img_convert/07c284ce1d9f3944040e0f97953bae77.png)

杨辉三角

```java
/*
 * 【提示】
 * 1. 第一行有 1 个元素, 第 n 行有 n 个元素
 * 2. 每一行的第一个元素和最后一个元素都是 1
 * 3. 从第三行开始, 对于非第一个元素和最后一个元素的元素。
 * 即：yanghui[i][j] = yanghui[i-1][j-1] + yanghui[i-1][j];
 */
public class ArrayEver2 {
	public static void main(String[] args) {
		//1.声明并初始化二维数组
		int[][] arr = new int[10][];
		
		//2.给数组的元素赋值，遍历二维数组
		for(int i = 0;i < arr.length;i++){
			arr[i] = new int[i+1];
			
			//2.1 给首末元素赋值
			arr[i][0]=arr[i][i]=1;
			//2.2 给每行的非首末元素赋值
		//	if(i > 1){
			for(int j = 1;j < arr[i].length-1;j++){
					arr[i][j] = arr[i-1][j-1] + arr[i-1][j];
				}
		//	}
	
		}
		
	//	3.遍历数组
		for(int i = 0;i < arr.length;i++){
			for(int j = 0;j <arr[i].length;j++){
				System.out.print(arr[i][j] + " ");
			}
			System.out.println();
		}
		
	}
}

```

**创建一个长度为 6 的 int 型数组，要求取值为 1-30，同时元素值各不相同**

```java
public class ArrayEver3 {
	public static void main(String[] args) {
		// 方式一：
//		int[] arr = new int[6];
//		for (int i = 0; i < arr.length; i++) {// [0,1) [0,30) [1,31)
//			arr[i] = (int) (Math.random() * 30) + 1;
//
//			boolean flag = false;
//			while (true) {
//				for (int j = 0; j < i; j++) {
//					if (arr[i] == arr[j]) {
//						flag = true;
//						break;
//					}
//				}
//				if (flag) {
//					arr[i] = (int) (Math.random() * 30) + 1;
//					flag = false;
//					continue;
//				}
//				break;
//			}
//		}
//
//		for (int i = 0; i < arr.length; i++) {
//			System.out.println(arr[i]);
//		}
		// 方式二：
		int[] arr2 = new int[6];
		for (int i = 0; i < arr2.length; i++) {// [0,1) [0,30) [1,31)
			arr2[i] = (int) (Math.random() * 30) + 1;

			for (int j = 0; j < i; j++) {
				if (arr2[i] == arr2[j]) {
					i--;
					break;
				}
			}
		}

		for (int i = 0; i < arr2.length; i++) {
			System.out.println(arr2[i]);
		}
	}
}    
```

### 4.数组中涉及的常见算法

#### 1.数组元素的赋值

```java
import java.util.Scanner;
/*
 * 此题了解！！！
 * 
 * 回形数格式方阵的实现
 * 从键盘输入一个整数（1~20） 
 * 则以该数字为矩阵的大小，把 1,2,3…n*n 的数字按照顺时针螺旋的形式填入其中。例如： 输入数字2，则程序输出： 1 2 
 * 4 3 
 * 输入数字 3，则程序输出：1 2 3 
 * 8 9 4 
 * 7 6 5 
 * 输入数字 4， 则程序输出： 
 * 1   2   3   4
 * 12  13  14  5 
 * 11  16  15  6 
 * 10  9   8   7
 */
public class ArrayTest {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		System.out.println("输入一个数字:");
		int len = scanner.nextInt();
		int[][] arr = new int[len][len];
		int s = len * len;
		/*
		 * k = 1:向右 k = 2:向下 k = 3:向左 k = 4:向上
		 */
		int k = 1;
		int i = 0, j = 0;
		for (int m = 1; m <= s; m++) {
			if (k == 1) {
				if (j < len && arr[i][j] == 0) {
					arr[i][j++] = m;
				} else {
					k = 2;
					i++;
					j--;
					m--;
				}
			} else if (k == 2) {
				if (i < len && arr[i][j] == 0) {
					arr[i++][j] = m;
				} else {
					k = 3;
					i--;
					j--;
					m--;
				}
			} else if (k == 3) {
				if (j >= 0 && arr[i][j] == 0) {
					arr[i][j--] = m;
				} else {
					k = 4;
					i--;
					j++;
					m--;
				}
			} else if (k == 4) {
				if (i >= 0 && arr[i][j] == 0) {
					arr[i--][j] = m;
				} else {
					k = 1;
					i++;
					j++;
					m--;
				}
			}
		}
		// 遍历
		for (int m = 0; m < arr.length; m++) {
			for (int n = 0; n < arr[m].length; n++) {
				System.out.print(arr[m][n] + "\t");
			}
			System.out.println();
		}
	}
}

```

#### 2.数组元素的基本操作

```java
/*
 * 算法的考察：求数值型数组中元素的最大值、最小值、平均数、总和等
 * 
 * 定义一个 int 型的一维数组，包含 10 个元素，分别赋一些随机整数，
 * 然后求出所有元素的最大值，最小值，和值，平均值，并输出出来。
 * 要求：所有随机数都是两位数。
 * 
 * [10,99]
 * 公式：(int)(Math.random() * (99 - 10 + 1) + 10)
 */
public class ArrayTest1 {
	public static void main(String[] args) {
		int[] arr = new int[10];
		//数组赋值
		for(int i = 0;i <arr.length;i++){
			arr[i] = (int)(Math.random() * (99 - 10 + 1) + 10);
		}
		
		//遍历
		for(int i =0;i < arr.length;i++){
			System.out.print(arr[i] + " ");
		}
		System.out.println();
		
		//求数组元素的最大值
		int maxValue = arr[0];
		for(int i = 1;i <arr.length;i++){
			if(maxValue < arr[i]){
				maxValue = arr[i];
			}
		}
		System.out.println("最大值：" + maxValue);
		
		//求数组元素的最小值
		int minValue = arr[0];
		for(int i = 1;i <arr.length;i++){
			if(minValue > arr[i]){
				minValue = arr[i];
			}
		}
		System.out.println("最小值：" + minValue);
		
		//求数组元素的总和
		int sum = 0;
		for(int i = 1;i <arr.length;i++){
			sum += arr[i];
		}
		System.out.println("总和：" + sum);
		
		//求数组元素的平均数
		double avgVales = sum / arr.length;
		System.out.println("平均数：" + avgVales);		
	}
}

```

```java
/*
 * 使用简单数组
 * (1)创建一个名为 ArrayTest 的类，在 main()方法中声明 array1 和 array2 两个变量，他们是 int[]类型的数组。
 * (2)使用大括号{}，把 array1 初始化为 8 个素数：2,3,5,7,11,13,17,19。
 * (3)显示 array1 的内容。
 * (4)赋值 array2 变量等于 array1，修改 array2 中的偶索引元素，使其等于索引值(如 array[0]=0,array[2]=2)。打印出 array1。
 */
public class ArrayTest2 {
	public static void main(String[] args) {
		//声明 array1 和 array2 两个 int[]变量
		int[] array1,array2;
		//array1 初始化
		array1 = new int[]{2,3,5,7,11,13,17,19};
		
		//显示 array1 的内容==遍历。
		for(int i = 0;i < array1.length;i++){
			System.out.print(array1[i] + "\t");
		}
		
		//赋值 array2 变量等于 array1
        //不能称作数组的复制。
		array2 = array1;
		
		//修改 array2 中的偶索引元素，使其等于索引值(如 array[0]=0,array[2]=2)。
		for(int i = 0;i < array2.length;i++){
			if(i % 2 == 0){
				array2[i] = i;
			}
		}
		System.out.println();
		
		//打印出 array1。
		for(int i = 0;i < array1.length;i++){
			System.out.print(array1[i] + "\t");
		}
	}
}

```

![img](https://img-blog.csdnimg.cn/img_convert/1dbdd407ab4eab6dd35163ef5a7b0378.png)

以上仅仅是把array1 这个地址赋给array2，并不叫数组的复制

```java
int[] array1,array2;
array1 = new int[]{2,3,5,7,11,13,17,19};
//数组的复制
array2 = new int[array1.length];
for(int i = 0;i < array2.length;i++){
	array2[i] = array1[i];
}

```

![img](https://img-blog.csdnimg.cn/img_convert/51135a7e4392b848f47caed509ac902f.png)

#### 3.数组的复制，反转，查找

```java
/*
 * 算法的考察：数组的复制、反转、查找(线性查找、二分法查找)
 */
public class ArrayTest3 {
	public static void main(String[] args) {
	
		String[] arr = new String[]{"SS","QQ","YY","XX","TT","KK","EE","GG"};
		
		//数组的复制
		String[] arr1 = new String[arr.length];
		for(int i = 0;i < arr1.length;i++){
			arr1[i] = arr[i];
		}
		
		//数组的反转
		//方法一：
//		for(int i = 0;i < arr.length / 2;i++){
//			String temp = arr[i];
//			arr[i] = arr[arr.length - i - 1];
//			arr[arr.length - i - 1] = temp;
//		}
		
		//方法二：
		for(int i = 0,j = arr.length - 1;i < j;i++,j--){
			String temp = arr[i];
			arr[i] = arr[j];
			arr[j] = temp;
		}
		
		//遍历
		for(int i = 0;i < arr.length;i++){
			System.out.print(arr[i] + "\t");
		}
		System.out.println();
		
		//查找（或搜索）
		//线性查找
		String dest = "BB";	//要查找的元素
		dest = "CC";
		
		boolean isFlag = true;
		
		for(int i = 0;i < arr.length;i++){
			if(dest.equals(arr[i])){
				System.out.println("找到了指定元素，位置为：" + i);
				isFlag = false;
				break;
			}
		}
		if(isFlag){
			System.out.println("很遗憾，没找到！");
		}
		
	}
}

```

##### 1.二分法查找

![img](https://img-blog.csdnimg.cn/img_convert/147a3feee59657d16accdc055c658df3.png)

```java
public class ArrayTest3 {
	public static void main(String[] args) {
		//二分法查找：
		//前提：所要查找的数组必须有序
		int[] arr2 = new int[]{-98,-34,2,34,54,66,79,105,210,333};
		
		int dest1 = -34;
		int head = 0;	//初始的首索引
		int end = arr2.length - 1;	//初始的末索引
		boolean isFlag1 = true;
		while(head <= end){
			int middle = (head + end)/2;
			
			if(dest1 == arr2[middle]){
				System.out.println("找到了指定元素，位置为：" + middle);
				isFlag1 = false;
				break;
			}else if(arr2[middle] > dest1){
				end = middle - 1;
			}else{	//arr2[middle] < dest1
				head = middle + 1;
			}	
		}
		
		if(isFlag1){
			System.out.println("很遗憾，没找到！");
		}		
	}
}

```

#### 4.数组元素的排序算法

* **排序：假设含有 n 个记录的序列为{R1，R2，…,Rn},其相应的关键字序列为{K1，K2，…,Kn}。将这些记录重新排序为{Ri1,Ri2,…,Rin},使得相应的关键字值满足条 Ki1<=Ki2<=…<=Kin,这样的一种操作称为排序。**
* **通常来说，排序的目的是快速查找。**
* **衡量排序算法的优劣：**
* **时间复杂度：分析关键字的比较次数和记录的移动次数
  空间复杂度：分析排序算法中需要多少辅助内存**

* **稳定性：若两个记录 A 和 B 的关键字值相等，但排序后 A、B 的先后次序保持不变，则称这种排序算法是稳定的。**
* **排序算法分类：内部排序和外部排序。
  内部排序：整个排序过程不需要借助于外部存储器（如磁盘等），所有排序操作都在内存中完成。
  外部排序：参与排序的数据非常多，数据量非常大，计算机无法把整个排序过程放在内存中完成，必须借助于外部存储器（如磁盘）。外部排序最常见的是多路归并排序。可以认为外部排序是由多次内部排序组成。**

#### 5.十大内部排序算法

- 选择排序
  - 直接选择排序、堆排序
- 交换排序
  - **冒泡排序、快速排序**
- 插入排序
  - 直接插入排序、折半插入排序、Shell 排序
- 归并排序
- 桶式排序
- 基数排序

#### 6.算法的五大特征

| 输入（Input）                   | 有 0 个或多个输入数据，这些输入必须有清楚的描述和定义        |
| ------------------------------- | ------------------------------------------------------------ |
| 输出（Output）                  | 至少有 1 个或多个输出结果，不可以没有输出结果                |
| 有穷性（有限性，Finiteness）    | 算法在有限的步骤之后会自动结束而不会无限循环，并且每一个步骤可以在可接受的时间内完成 |
| 确定性（明确性，Definiteness）  | 算法中的每一步都有确定的含义，不会出现二义性                 |
| 可行性（有效性，Effectiveness） | 算法的每一步都是清楚且可行的，能让用户用纸笔计算而求出答案   |

**说明：满足确定性的算法也称为：确定性算法。现在人们也关注更广泛的概念，例如考虑各种非确定性的算法，如并行算法、概率算法等。另外，人们也关注并不要求终止的计算描述，这种描述有时被称为过程（procedure）。**

#### 7.冒泡排序

**冒泡排序的基本思想：通过对待排序序列从前向后，依次比较相邻元素的排序码，若发现逆序则交换，使排序码较大的元素逐渐从前部移向后部。**

**因为排序的过程中，各元素不断接近自己的位置，如果一趟比较下来没有进行过交换，就说明序列有序， 因此要在排序过程中设置一个标志swap判断元素是否进行过交换。从而减少不必要的比较。**

![img](https://img-blog.csdnimg.cn/img_convert/1652ba31ff3ee377506665fa442de80d.png)

```java
/*
 * 数组的冒泡排序的实现
 * 
 */
public class BubbleSortTest {
	public static void main(String[] args) {
		
		int[] arr = new int[]{43,32,76,92,-65,85,71,-42};
		
		//冒泡排序
		for(int i = 0;i < arr.length - 1;i++){
			
			for(int j = 0;j < arr.length - 1 - i;j++){
				
				if(arr[j] > arr[j+1]){
					int temp = arr[j];
					arr[j] = arr[j+1];
					arr[j+1] = temp;
				}
			}
		}
		
		for(int i = 0;i < arr.length;i++){
			System.out.print(arr[i] + "\t");
		}
	}
}

```

#### 8.快速排序

**排序思想：**

**从数列中挑出一个元素，称为"基准"（pivot），**
**重新排序数列，所有元素比基准值小的摆放在基准前面，所有元素比基准值大的摆在基准的后面（相同的数可以到任一边）。在这个分区结束之后，该基准就处于数列的中间位置。这个称为分区（partition）操作。**
**递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数列排序。**
**递归的最底部情形，是数列的大小是零或一，也就是永远都已经被排序好了。虽然一直递归下去，但是这个算法总会结束，因为在每次的迭代（iteration）中，它至少会把一个元素摆到它最后的位置去。**

![img](https://img-blog.csdnimg.cn/img_convert/c416b57d8b51b44072a3fa7d7b7aa740.png)

```java
/**
  * 快速排序
  * 通过一趟排序将待排序记录分割成独立的两部分，其中一部分记录的关键字均比另一部分关键字小，
  * 则分别对这两部分继续进行排序，直到整个序列有序。
  *
 */
public class QuickSort {
	private static void swap(int[] data, int i, int j) {
		int temp = data[i];
		data[i] = data[j];
		data[j] = temp;
	}
	private static void subSort(int[] data, int start, int end) {
		if (start < end) {
			int base = data[start];
			int low = start;
			int high = end + 1;
			while (true) {
				while (low < end && data[++low] - base <= 0)
					;
				while (high > start && data[--high] - base >= 0)
					;
				if (low < high) {
					swap(data, low, high);
				} else {
					break;
				}
			}
			swap(data, start, high);
			
			subSort(data, start, high - 1);//递归调用
			subSort(data, high + 1, end);
		}
	}
	public static void quickSort(int[] data){
		subSort(data,0,data.length-1);
	}
	
	public static void main(String[] args) {
		int[] data = { 9, -16, 30, 23, -30, -49, 25, 21, 30 };
		System.out.println("排序之前：\n" + java.util.Arrays.toString(data));
		quickSort(data);
		System.out.println("排序之后：\n" + java.util.Arrays.toString(data));
	}
}

```

#### 9.排序算法性能对比

![img](https://img-blog.csdnimg.cn/img_convert/9d43d5e3a110648c15f953275931755b.png)

**各种内部排序方法性能比较**

* **从平均时间而言：快速排序最佳。但在最坏情况下时间性能不如堆排序和归并排序。**
* **从算法简单性看：由于直接选择排序、直接插入排序和冒泡排序的算法比较简单，将其认为是简单算法。对于Shell排序、堆排序、快速排序和归并排序算法，其算法比较复杂，认为是复杂排序。**
* **从稳定性看：直接插入排序、冒泡排序和归并排序是稳定的；而直接选择排序、快速排序、Shell排序和堆排序是不稳定排序**
* **从待排序的记录数n的大小看，n较小时，宜采用简单排序；而n较大时宜采用改进排序。**

**排序算法的选择**

​	**(1) 若n较小(如n≤50)，可采用直接插入或直接选择排序。当记录规模较小时，直接插入排序较好；否则因为直接选择移动的记录数少于直接插入，应选直接选择排序为宜。**
​	**(2) 若文件初始状态基本有序(指正序)，则应选用直接插入、冒泡或随机的快速排序为宜；**
​	**(3) 若n较大，则应采用时间复杂度为O(nlgn)的排序方法：快速排序、堆排序或归并排序。**

### 5.Arrays工具类的使用

| 1    | boolean equals(int[] a,int[] b)   | 判断两个数组是否相等。                 |
| ---- | --------------------------------- | -------------------------------------- |
| 2    | String toString(int[] a)          | 输出数组信息。                         |
| 3    | void fill(int[] a,int val)        | 将指定值填充到数组之中。               |
| 4    | void sort(int[] a)                | 对数组进行排序。                       |
| 5    | int binarySearch(int[] a,int key) | 对排序后的数组进行二分法检索指定的值。 |

```java
import java.util.Arrays;
/*
 * java.util.Arrays:作数组的工具类，包含了用来操作数组（比如排序和搜索）的各种方法。
 */
public class ArrayTest4 {
	public static void main(String[] args) {
		
		//1.boolean equals(int[] a,int[] b)判断两个数组是否相等。
		int[] arr1 = new int[]{1,2,3,4};
		int[] arr2 = new int[]{1,2,9,3};
		boolean isEquals = Arrays.equals(arr1, arr2);
		System.out.println(isEquals);
		
		//2.String toString(int[] a)输出数组信息。
		System.out.println(Arrays.toString(arr1));		
		
		//3.void fill(int[] a,int val)将指定值填充到数组之中。
		Arrays.fill(arr1, 10);
		System.out.println(Arrays.toString(arr1));		
		
		//4.void sort(int[] a)对数组进行排序。
		Arrays.sort(arr2);
		System.out.println(Arrays.toString(arr2));
		
		//5.int binarySearch(int[] a,int key)对排序后的数组进行二分法检索指定的值。
		int[] arr3 = new int[]{43,32,76,92,-65,85,71,-42}; 
		int index = Arrays.binarySearch(arr3, 210);
		if(index >= 0){
			System.out.println(index);
		}else{
			System.err.println("未找到。");
		}		
	}
}

```

### 6.数组使用中的常见异常

```java
/*
 * 数组中的常见异常：
 * 1.数组角标越界的异常:ArrayIndexOutOfBoundsException
 * 
 * 2.空指针异常:NullPointerException
 * 
 */
public class ArrayExceptionTest {
	public static void main(String[] args) {
		
		//1.数组角标越界的异常:ArrayIndexOutOfBoundsException
		int[] arr = new int[]{1,2,3,4,5,6};
		
		//错误1：
//		for(int i = 0;i <= arr.length;i++){
//			System.out.println(arr[i]);
//		}
		
		//错误2：
//		System.out.println(arr[-2]);
		
		//错误3
//		System.out.println("hello");
		
		//2.空指针异常:NullPointerException
		//情况一:
//		int[] arr2= new int[]{1,2,3};
//		arr2 = null;
//		System.out.println(arr2[0]);
		//情况二:
//		int[][] arr2 = new int[4][];
//		System.out.println(arr2[0][0]);
		
		//情况三:
//		String[] arr3 = new String[]{"AA","QQ","YY","XX","TT","KK"};
//		arr3[0] = null;
//		System.out.println(arr3[0].toString());		
	}
}

```

## 6.面向对象（上）

### 1.面向对象与面向过程

**一、学习面向对象内容的三条主线**

**1.Java 类及类的成员：属性、方法、构造器、代码块、内部类**

**2.面向对象的三大特征：封装、继承、多态性、(抽象性)**

**3.其它关键字：this、super、static、final、abstract、interface、package、import 等**

**二、人把大象装进冰箱**

**1.面向过程:强调的是功能行为，以函数为最小单位，考虑怎么做。**

**① 打开冰箱**

**② 把大象装进冰箱**

**③ 把冰箱门关住** 



**2.面向对象:强调具备了功能的对象，以类/对象为最小单位，考虑来做。**

**人{**

**打开(冰箱){**

**冰箱.开门();**

**}操作(大象){**

**大象.进入(冰箱);**

**}关闭(冰箱){**

**冰箱.关门();**     

**}**

**}**

**冰箱{**

**开门(){**

**}**  

**关门(){**

**}**

**}**

**大象{**

**进入(冰箱){**

**}**

**}**

**程序员从面向过程的执行者转化成了面向对象的指挥者**
**面向对象分析方法分析问题的思路和步骤：**
**根据问题需要，选择问题所针对的现实世界中的实体。**
**从实体中寻找解决问题相关的属性和功能，这些属性和功能就形成了概念世界中的类。**
**把抽象的实体用计算机语言进行描述，形成计算机世界中类的定义。即借助某种程序语言，把类构造成计算机能够识别和处理的数据结构。**
**将类实例化成计算机世界中的对象。对象是计算机世界中解决问题的最终工具。**

### 2.类和对象

 * **三、面向对象的两个要素：**
 * **类:对一类事物的描述，是抽象的、概念上的定义**
 * **对象:是实际存在的该类事物的每个个体，因而也称为实	例(instance)。**
 * **可以理解为：类= 抽象概念的人；对象= 实实在在的某个人**
 * **面向对象程序设计的重点是类的设计；**
 * **设计类，其实就是设计类的成员。**

#### 1.JAVA类及类的成员

- 属性：对应类中的成员变量
- 行为：对应类中的成员方法

#### 2.类与对象的创建和使用

```java
/*
 * 一、设计类、其实就是设计类的成员
 * Field = 属性 = 成员变量 = 域、字段
 * Method = (成员)方法 = 函数 
 * 
 * 创建类 = 类的实例化 = 实例化类
 * 
 * 二.类和对象的使用(面向对象思想落地的实现)
 * 1.创建类，设计类的成员
 * 2.创建类的对象
 * 3.通过“对象.属性”或“对象.方法”调用对象的结构
 * 三、如果创建类一个类的多个对象，则每个对象都独立的拥有一套类的属性。(非 static 的)
 * 	  意味着:如果我们修改一个对象的属性 a，则不影响另外一个对象属性 a 的值。
 */
//测试类
public class PersonTest {
	public static void main(String[] args) {
		//2.创建 Person 类的对象
		//创建对象语法：类名对象名= new 类名();
		Person p1 = new Person();
		//Scanner scan = new Scanner(System.in);
		
		//调用类的结构：属性、方法
		//调用属性:“对象.属性”
		p1.name = "Tom";    
		p1.age = 25;
		p1.isMale = true;
		System.out.println(p1.name);
		
		//调用方法:“对象.方法”
		p1.eat();
		p1.sleep();
		p1.talk("chinese");
		//**********************
		Person p2 = new Person();
		System.out.println(p2.name); //null
		System.out.println(p2.isMale);
		//**********************
		//将 p1 变量保存的对象地址值赋给 p3,导致 p1 和 p3 指向了堆空间中的一个对象实体。
		Person p3 = p1;
		System.out.println(p3.name);
		
		p3.age = 10;
		System.out.println(p1.age); //10
	}
}
/*
 * 类的语法格式：
 * 修饰符 class 类名{
 * 		属性声明;
 * 		方法声明;
 * }
 * 说明：修饰符 public：类可以被任意访问类的正文要用{  }括起来
 */
//1.创建类，设计类的成员
class Person{
	
	//属性:对应类中的成员变量
	String name;
	int age;
	boolean isMale;
	
	//方法:对应类中的成员方法
	public void eat(){
		System.out.println("吃饭");
	}
	
	public void sleep(){
		System.out.println("睡觉");
	}
	
	public void talk(String language){
		System.out.println("人可以说话，使用的是：" + language);
	}
}
```

#### 3.对象的创建和使用：内存解析

![img](https://img-blog.csdnimg.cn/img_convert/fd7a664a69d935533b176a0397576172.png)

* **堆（Heap），此内存区域的唯一目的就是存放对象实例（new出来的结构，数组，对象等），几乎所有的对象实例都在这里分配内存。这一点在 Java 虚拟机规范中的描述是：所有的对象实例以及数组都要在堆上分配。**
* **通常所说的栈（Stack），是指虚拟机栈。虚拟机栈用于存储局部变量等。局部变量表存放了编译期可知长度的各种基本数据类型（boolean、byte、char、short、int、float、long、double）、对象引用（reference 类型，它不等同于对象本身，是对象在堆内存的首地址）。方法执行完，自动释放。**
* **方法区（MethodArea），用于存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。**

```java
Person p1= newPerson();
p1.name = "Tom";
p1.isMale = true;
Person p2 = new Person();
sysout(p2.name);//null
Person p3 = p1;
p3.age = 10;
```

![img](https://img-blog.csdnimg.cn/img_convert/e10710c43389ff33e23d546de2ee864a.png)

### 3.类的成员之一：属性

**局部变量:没有初始化值！！！！**

 * 			**意味着:在调用局部变量之前，一定要显式赋值。**
 * 			**特别地:形参在调用时,赋值即可。例，45 行**

```java
/*
 * 类中属性的使用
 * 
 * 属性(成员变量)	vs	局部变量
 * 1.相同点:
 * 		1.1 定义变量的格式:数据类型 变量名 = 变量值
 * 		1.2 先声明，后使用
 * 		1.3 变量都有其对应的作用域
 * 				
 * 2.不同点:
 * 		2.1 在类中声明的位置不同
 * 		属性:直接定义在类的一对{}内
 * 		局部变量:声明在方法内、方法形参、构造器形参、构造器内部的变量
 * 
 * 		2.2 关于权限修饰符的不同
 * 		属性:可以在声明属性时，指明其权限，使用权限修饰符。
 * 			常用的权限修饰符:private、public、缺省、protected（缺省就是不声明权限修饰符）
 * 			目前声明属性时，都使用缺省即可。
 * 		局部变量:不可以使用权限修饰符。
 * 
 * 		2.3 默认初始化值的情况:
 * 		属性:类的属性，根据其类型，都有默认初始化值。
 * 			整型(byte、short、int、long):0
 * 			浮点型(float、double):0.0
 * 			字符型(char):0(或‘\u0000’)
 * 			布尔型(boolean):false
 * 
 * 			引用数据类型(类、数组、接口):null
 * 
 * 		局部变量:没有初始化值！！！！
 * 			意味着:在调用局部变量之前，一定要显式赋值。
 * 			特别地:形参在调用时,赋值即可。例，45 行
 * 
 * 		2.4 在内存中加载的位置，亦各不相同。
 * 		属性:加载到堆空间中(非 static)
 * 		局部变量:加载到栈空间
 */
public class UserTest {
	public static void main(String[] args) {
		User u1 = new User();
		System.out.println(u1.name);
		System.out.println(u1.age);
		System.out.println(u1.isMale);
		
		u1.talk("俄语");
	}
}
class User{
	//属性(或成员变量)
	String name;	//不加 private 即为缺省
	public int age;	//不加 public 即为缺省
	boolean isMale;
	
	public void talk(String language){//language:形参，也是局部变量
		System.out.println("我们使用" + language + "进行交流。");
	}
	
	public void eat(){
		String food = "石头饼";	//石头饼:局部变量
		System.out.println("北方人喜欢吃:" + food);
	}
}
```

```java
/*
编写教师类和学生类，并通过测试类创建对象进行测试
Student类
属性:
name:String age:int major:String interests:String
方法:say() 返回学生的个人信息
Teacher类
属性:
name:String age:int teachAge:int course:String
方法:say() 输出教师的个人信息
*/
public class School {
	public static void main(String[] args) {
		Student stu = new Student();
        stu.name = "小明";
        stu.age = 16;
		
		Teacher tea = new Teacher();
		tea.name = "王老师";
        tea.age = 27;
        
        tea.say(stu.name,stu.age);
        stu.say(tea.name, tea.age);
	}	
}
class Student{
	String name;
	int age;
	String major;
	String interests;
	
	void say(String name, int age){
		System.out.println("这个学生是："+name+"年龄是："+age);	}
}
class Teacher{
	String name;
	int age;
	String teachAge;
	String course;
	
	void say(String name, int age){
		System.out.println("这个老师是："+name+"年龄是："+age);
	}
}
```

### 4.类的成员之二：方法

#### 1.类中方法的声明与使用

 * **类中方法的声明和使用**
 * 
 * **方法：描述类应该具有的功能。**
 * **比如：Math类：sqrt()\random() \...**
 * **Scanner类：nextXxx() ...**
 * **Arrays类：sort() \ binarySearch() \ toString() \ equals() \ ...**
 * 
 * **1.举例：**
 * **public void eat(){}**
 * **public void sleep(int hour){}**
 * **public String getName(){}**
 * **public String getNation(String nation){}**
 * 
 * 2. **方法的声明：权限修饰符  返回值类型  方法名(形参列表){**
 * **方法体**
 * **}**
 * **注意：static、final、abstract 来修饰的方法，后面再讲。**
 * 
 * 3. **说明：**
 * **3.1 关于权限修饰符：默认方法的权限修饰符先都使用public**
 * **Java规定的4种权限修饰符：private、public、缺省、protected  -->封装性再细说**
 * 
 * **3.2 返回值类型： 有返回值  vs 没有返回值**
 * **3.2.1  如果方法有返回值，则必须在方法声明时，指定返回值的类型。同时，方法中，需要使用**
 * **return关键字来返回指定类型的变量或常量：“return 数据”。**
 * **如果方法没有返回值，则方法声明时，使用void来表示。通常，没有返回值的方法中，就不需要**
 * **使用return.但是，如果使用的话，只能“return;”表示结束此方法的意思。**
 * 
 * **3.2.2 我们定义方法该不该有返回值？**
 * **① 题目要求**
 * **② 凭经验：具体问题具体分析**
 * 
 * **3.3 方法名：属于标识符，遵循标识符的规则和规范，“见名知意”**
 * **3.4 形参列表:方法名可以声明0个、1个，或多个形参。**
 * **3.4.1 格式:数据类型1 形参1，数据类型2 形参2,...**
 * 
 * **3.4.2 我们定义方法时，该不该定义形参？**
 * **① 题目要求**
 * **② 凭经验，具体问题具体分析**
 * **3.5 方法体:方法功能的体现。**
 * 4. **return关键字的使用：**
 * **1.使用范围:使用在方法体中**
 * **2.作业:① 结束方法**
 * **② 针对于有返回值类型的方法，使用"return 数据"方法返回所要的数据。**
 * **3.注意点:return关键字后不可声明执行语句。**
 * 5. **方法的使用中，可以调用当前类的属性或方法。**
 * **特殊的:方法A中又调用了方法A:递归方法。**
 * **方法中不能定义其他方法。**

```java
public class CustomerTest {
	public static void main(String[] args) {
		
		Customer cust1 = new Customer();
		
		cust1.eat();
		
		//测试形参是否需要设置的问题
//		int[] arr = new int[]{3,4,5,2,5};
//		cust1.sort();
		
		cust1.sleep(8);
		
	}
}
//客户类
class Customer{
	
	//属性
	String name;
	int age;
	boolean isMale;
	
	//方法
	public void eat(){
		System.out.println("客户吃饭");
		return;
		//return后不可以声明表达式
//		System.out.println("hello");
	}
	
	public void sleep(int hour){
		System.out.println("休息了" + hour + "个小时");
		
		eat();
//		sleep(10);
	}
	
	public String getName(){
		
		if(age > 18){
			return name;
			
		}else{
			return "Tom";
		}
	}
	
	public String getNation(String nation){
		String info = "我的国籍是：" + nation;
		return info;
	}
	
	//体会形参是否需要设置的问题
//	public void sort(int[] arr){
//		
//	}
//	public void sort(){
//		int[] arr = new int[]{3,4,5,2,5,63,2,5};
//		//。。。。
//	}
	
	public void info(){
		//错误的
//		public void swim(){
//			
//		}
		
	}
}
```

```java
/*
 * 4. 对象数组题目：定义类Student，包含三个属性：
 * 学号number(int)，年级state(int)，成绩score(int)。
 * 创建20个学生对象，学号为1到20，年级和成绩都由随机数确定。
 * 问题一：打印出3年级(state值为3）的学生信息。
 * 问题二：使用冒泡排序按学生成绩排序，并遍历所有学生信息
 * 提示：  1) 生成随机数：Math.random()，返回值类型double;  
 * 		2) 四舍五入取整：Math.round(double d)，返回值类型long。
 * 
 */
public class StudentTest {
	public static void main(String[] args) {
		//声明一个Student类型的数组
		Student[] stu = new Student[20];
		
		for(int i = 0;i <stu.length;i++){
			//给数组元素赋值
            
                
			stu[i] = new Student();
            注意要对每一个数组元素实例化，上面只是声明了数组元素为student类型，每个数组元素为空指针null，要给它们new一个内存！！！！！
            
            
            
			//给Student的对象的属性赋值
			stu[i].number = i + 1;
			//年级:[1,6]
			stu[i].state = (int)(Math.random() * (6 - 1 + 1) + 1);
			//成绩:[0,100]
			stu[i].score = (int)(Math.random() * (100 - 0 + 1));
		}
		
		//遍历学生数组
		for(int i = 0;i < stu.length;i++){
//			System.out.println(stu[i].number + "," + stu[i].state 
//				+  "," + stu[i].score);
			
			System.out.println(stu[i].info());
		}
		System.out.println("*********以下是问题1*********");
		
		//问题一：打印出3年级(state值为3）的学生信息。
		for(int i = 0;i < stu.length;i++){
			if(stu[i].state == 3){
				System.out.println(stu[i].info());
			}
		}
		System.out.println("********以下是问题2**********");
		
		//问题二：使用冒泡排序按学生成绩排序，并遍历所有学生信息。
		for(int i = 0;i < stu.length - 1;i++){
			for(int j = 0;j <stu.length - 1 - i;j++){
				if(stu[j].score >stu[j+1].score){
					//如果需要换序，交换的是数组的元素，Student对象！！！
					Student temp = stu[j];
					stu[j] = stu[j+1];
					stu[j+1] = temp;
				}
			}
		}
		
		//遍历学生数组
		for(int i = 0;i < stu.length;i++){
			System.out.println(stu[i].info());
		}
		
	}
}
class Student{
	int number;	//学号
	int state;	//年级
	int score;	//成绩
	
	//显示学生信息的方法
	public String info(){
		return "学号:" + number + ",年级:" + state + ",成绩:" + score;
	}
}

```

**优化**

 * **4.对象数组题目：定义类Student，包含三个属性：**
 * **学号number(int)，年级state(int)，成绩score(int)。**
 * **创建20个学生对象，学号为1到20，年级和成绩都由随机数确定。**
 * **问题一：打印出3年级(state值为3）的学生信息。**
 * **问题二：使用冒泡排序按学生成绩排序，并遍历所有学生信息**
 * **提示：  1) 生成随机数：Math.random()，返回值类型double;**  
 * 2) **四舍五入取整：Math.round(double d)，返回值类型long。**
 * 
 * **此代码是对StudentTest.java的改进，将操作数组的功能封装到方法中。**

```java
public class StudentTest2 {
	public static void main(String[] args) {
		//声明一个Student类型的数组
		Student2[] stu = new Student2[20];
		
		for(int i = 0;i <stu.length;i++){
			//给数组元素赋值
			stu[i] = new Student2();
			//给Student的对象的属性赋值
			stu[i].number = i + 1;
			//年级:[1,6]
			stu[i].state = (int)(Math.random() * (6 - 1 + 1) + 1);
			//成绩:[0,100]
			stu[i].score = (int)(Math.random() * (100 - 0 + 1));
		}
        
        
		
		StudentTest2 test = new StudentTest2();
        调用同一个类里面的方法需要new一个对象才可以调用
            
        
        
		
		//遍历学生数组
		test.print(stu);
		
		System.out.println("*********以下是问题1*********");
		
		//问题一：打印出3年级(state值为3）的学生信息。
		test.searchState(stu, 3);
		System.out.println("********以下是问题2**********");
		
		//问题二：使用冒泡排序按学生成绩排序，并遍历所有学生信息。
		test.sort(stu);
		
		//遍历学生数组
		for(int i = 0;i < stu.length;i++){
			System.out.println(stu[i].info());
		}
	}
	
	/**
	  * 
	  * @Description 遍历Student[]数组的操作
	 */
	public void print(Student2[] stu){
		for(int i = 0;i < stu.length;i++){	
			System.out.println(stu[i].info());
		}
	}
	
	/**
	  * 
	  * @Description 查找Student数组中指定年级的学习信息
	 */
	public void searchState(Student2[] stu,int state){
		for(int i = 0;i < stu.length;i++){
			if(stu[i].state == state){
				System.out.println(stu[i].info());
			}
		}
	}
	
	/**
	  * 
	  * @Description 给Student数组排序
	 */
	public void sort(Student2[] stu){
		for(int i = 0;i < stu.length - 1;i++){
			for(int j = 0;j <stu.length - 1 - i;j++){
				if(stu[j].score >stu[j+1].score){
					//如果需要换序，交换的是数组的元素，Student对象！！！
					Student2 temp = stu[j];
					stu[j] = stu[j+1];
					stu[j+1] = temp;
				}
			}
		}
	}
}
class Student2{
	int number;	//学号
	int state;	//年级
	int score;	//成绩
	
	//显示学生信息的方法
	public String info(){
		return "学号:" + number + ",年级:" + state + ",成绩:" + score;
	}
}
```

#### 2.理解“万事万物皆对象”

 **1.在Java语言范畴中，我们都将功能、结构等封装到类中，通过类的实例化，来调用具体的功能结构。**

 * 		**》Scanner,String等**
 * 		**》文件：File**
 * 		**》网络资源：URL**
 * 		**2.涉及到Java语言与前端html、后端的数据库交互时，前后端的结构在Java层面交互时，都体现为类、对象。**

#### 3.对象数组的内存解析

**/引用类型的变量，只可能存储量两类值：null或地址值（含变量类型）/**
Student[] stus= newStudent[5];
stus[0] = new Student();
sysout(stus[0].state);//1
sysout(stus[1]);//null
sysout(stus[1].number);//异常
stus[1] = new Student();
sysout(stus[1].number);//0

class Student{
  int number;//学号
  int state = 1;//年级
  int score;//成绩
}

![img](https://img-blog.csdnimg.cn/img_convert/b076c453b52bf6f3643b8cfc66809c25.png)

####  4.匿名对象的使用

**匿名对象的使用** 

**1 理解:我们创建的对象，没有显示的赋值给一个变量名。即为匿名对象。** 

**2 特征：匿名对象只能调用一次。**  

**可以作为实参传递！！！**

**3 使用:如下**

```java
public class InstanceTest {
	public static void main(String[] args) {
		Phone p = new Phone();
//		p = null;
		System.out.println(p);
		
		p.sendEmail();
		p.playGame();
		
		//匿名对象
//		new Phone().sendEmail();
//		new Phone().playGame();
		
		new Phone().price = 1999;
		new Phone().showPrice();	//0.0
		
		//*******************************
		PhoneMall mall = new PhoneMall();
//		mall.show(p);
		//匿名对象的使用
		mall.show(new Phone());	
	}
}

class PhoneMall{
	
	public void show(Phone phone){
		phone.sendEmail();
		phone.playGame();
	}
}

class Phone{
	double price;	//价格
	
	public void sendEmail(){
		System.out.println("发邮件");
	}
	public void playGame(){
		System.out.println("打游戏");
	}
	public void showPrice(){
		System.out.println("手机价格为:" + price);
	}
}
```

#### 5.自定义数组的工具类

工具类：

```java
public class ArrayUtil {

	// 求数组的最大值
	public int getMax(int[] arr) {
		int maxValue = arr[0];
		for (int i = 1; i < arr.length; i++) {
			if (maxValue < arr[i]) {
				maxValue = arr[i];
			}
		}
		return maxValue;
	}

	// 求数组的最小值
	public int getMin(int[] arr) {
		int minValue = arr[0];
		for (int i = 1; i < arr.length; i++) {
			if (minValue > arr[i]) {
				minValue = arr[i];
			}
		}
		return minValue;
	}

	// 求数组总和
	public int getSum(int[] arr) {
		int sum = 0;
		for (int i = 0; i < arr.length; i++) {
			sum += arr[i];
		}
		return sum;
	}

	// 求数组平均值
	public int getAvg(int[] arr) {
		int avgValue = getSum(arr) / arr.length;
		return avgValue;
	}

	// 反转数组
	public void reverse(int[] arr) {
		for (int i = 0; i < arr.length / 2; i++) {
			int temp = arr[i];
			arr[i] = arr[arr.length - i - 1];
			arr[arr.length - i - 1] = temp;
		}
	}

	// 复制数组
	public int[] copy(int[] arr) {
		int[] arr1 = new int[arr.length];
		for (int i = 0; i < arr1.length; i++) {
			arr1[i] = arr[i];
		}
		return arr1;
	}

	// 数组排序
	public void sort(int[] arr) {
		for (int i = 0; i < arr.length - 1; i++) {
			for (int j = 0; j < arr.length - 1 - i; j++) {
				if (arr[j] > arr[j + 1]) {
					int temp = arr[j];
					arr[j] = arr[j + 1];
					arr[j + 1] = temp;
				}
			}
		}
	}

	// 遍历数组
	public void print(int[] arr) {
		System.out.print("[");
		for (int i = 0; i < arr.length; i++) {
			System.out.print(arr[i] + ",");
		}
		System.out.println("]");
	}

	// 查找指定元素
	public int getIndex(int[] arr, int dest) {
		//线性查找
		for (int i = 0; i < arr.length; i++) {
			if (dest==arr[i]) {
				return i;
			}
		}
		return -1;
	}
}
```

测试类：

```JAVA
/**
  * @Description 测试类
  *
 */
public class ArrayUtilTest {


	public static void main(String[] args) {
		ArrayUtil util = new ArrayUtil();
		int[] arr = new int[]{32,5,26,74,0,96,14,-98,25};
		int max = util.getMax(arr);
		System.out.println("最大值为:" + max);
		
//		System.out.print("排序前:");
//		util.print(arr);
//		
//		util.sort(arr);
//		System.out.print("排序后:");
//		util.print(arr);
		
		System.out.println("查找:");
		int index = util.getIndex(arr, 5);
		if(index > 0){
			System.out.println("找到了，索引地址:" + index);
		}else{
			System.out.println("没找到");
		}
	}
}
```

#### 6.方法的重载

 * 方法的重载(overload) loading...

 * 1.定义:在同一个类中，允许存在一个以上的同名方法，只要它们的参数个数或者参数类型不同即可。

 * **“两同一不同”:同一个类、相同方法名**

 * **参数列表不同：参数个数不同，参数类型不同**

 * 2.举例:

 * Arrays类中重载的sort() / binarySearch()

 * 3.判断是否重载

 * **与方法的返回值类型、权限修饰符、形参变量名、方法体都无关。**

 * 4.在通过对象调用方法时，如何确定某一个指定的方法：

   方法名-->参数列表

```java
public class OverLoadTest {
	
	public static void main(String[] args) {
		OverLoadTest test = new OverLoadTest();
		test.getSum(1, 2);	//调用的第一个，输出1
	}

	//如下的四个方法构成了重载
	public void getSum(int i,int j){
		System.out.println("1");
	}
	public void getSum(double d1,double d2){
		System.out.println("2");
	}
	public void getSum(String s,int i){
		System.out.println("3");
	}
	
	public void getSum(int i,String s){
		
	}
	
	//以下3个是错误的重载
//	public int getSum(int i,int j){
//		return 0;
//	}
	
//	public void getSum(int m,int n){
//		
//	}
	
//	private void getSum(int i,int j){
//		
//	}
}
```

举例：

```java
1.判断：与void show(int a,char b,double c){}构成重载的有：
    
a)void show(int x,char y,double z){} // no
b)int show(int a,double c,char b){} // yes
c) void show(int a,double c,char b){} // yes
d) boolean show(int c,char b){} // yes
e) void show(double c){} // yes 
f) double show(int x,char y,double z){} // no
g) void shows(){double c} // no
```

例题：

```java
/*
 * 1.编写程序，定义三个重载方法并调用。方法名为mOL。
 * 三个方法分别接收一个int参数、两个int参数、一个字符串参数。
 * 分别执行平方运算并输出结果，相乘并输出结果，输出字符串信息。
 * 在主类的main ()方法中分别用参数区别调用三个方法。
 * 2.定义三个重载方法max()，
 * 第一个方法求两个int值中的最大值，
 * 第二个方法求两个double值中的最大值，
 * 第三个方法求三个double值中的最大值，并分别调用三个方法。
 * 
 */
public class OverLoadever {
	
	public static void main(String[] args) {
		OverLoadever test = new OverLoadever();
		//1.调用3个方法
		test.mOL(5);
		test.mOL(6, 4);
		test.mOL("fg");
		
		//2.调用3个方法
		int num1 = test.max(18, 452);
		System.out.println(num1);
		double num2 = test.max(5.6, -78.6);
		System.out.println(num2);
		double num3 = test.max(15, 52, 42);
		System.out.println(num3);
	}

	//1.如下三个方法构成重载
	public void mOL(int i){
		System.out.println(i*i);
	}
	public void mOL(int i,int j){
		System.out.println(i*j);
	}
	public void mOL(String s){
		System.out.println(s);
	}
	
	//2.如下三个方法构成重载
	public int max(int i,int j){
		return (i > j) ? i : j;
	}
	public double max(double i,double j){
		return (i > j) ? i : j;
	}
	public double max(double d1,double d2,double d3){
		double max = (d1 > d2) ? d1 : d2;
		return (max > d3) ? max : d3;
	}
}
```

#### 7.可变个数的形参

JavaSE 5.0 中提供了Varargs(variable number of arguments)机制，允许**直接定义能和多个实参相匹配的形参**。从而，可以用一种更简单的方式，来传递个数可变的实参。

可变个数形参的方法：

 * 1.jdk 5.0新增的内容
 * 2.具体使用：
 * 2.1 可变个数形参的格式：数据类型 ... 变量名
 * 2.2 当调用可变个数形参的方法时，传入的参数的个数可以是：0个，1个，2个...
 * 2.3**可变个数形参的方法与本类中方法名相同，形参不同的方法之间构成重载。**
 * 2.4**可变个数形参的方法与本类中方法名相同，形参类型也相同的数组之间不构成重载。即二者不可共存。**
 * 2.5**可变个数形参在方法中的形参中,必须声明在末尾**。
 * 2.6**可变个数形参在方法的形参中，最多只能声明一个可变形参。**
 * **优先调用确定个数形参的方法！**

```java
public class MethodArgs {

	public static void main(String[] args) {
		MethodArgs test = new MethodArgs();
		test.show(12);
		// test.show("hell0");
		// test.show("hello","world");
		// test.show();

		test.show(new String[] { "AA", "BB", "CC" });
	}

	public void show(int i) {

	}

	// public void show(String s){
	// System.out.println("show(String)");
	// }
	public void show(String... strs) {
		System.out.println("show(String ...strs)");


		for (int i = 0; i < strs.length; i++) {
			System.out.println(strs[i]);
		}
	}

	// 此方法与上一方法不可共存
	// public void show(String[] strs){
	//
	// }

	public void show(int i, String... strs) {

	}

	//The variable argument type String of the method show must be the last parameter
//	public void show(String... strs,int i,) {
//
//	}
}
```

#### 8.方法参数的值传递机制（重点！！！）

关于变量的赋值：

**如果变量是基本数据类型，此时赋值的是变量所保存的数据值。**

**如果变量是引用数据类型，此时赋值的是变量所保存的数据的地址值。**

```java
public class ValueTransferTest {

	public static void main(String[] args) {
		
		System.out.println("**********基本数据类型：***********");
		int m = 10;
		int n = m;
		
		System.out.println("m = " + m + ", n = " + n);
		
		n = 20;
		
		System.out.println("m = " + m + ", n = " + n);

		System.out.println("***********引用数据类型:********");
		
		Order o1 = new Order();
		o1.orderId = 1001;
		
		Order o2 = o1;	//赋值后，o1和o2的地址值相同，都指向了堆空间中同一个对象实体
		System.out.println("o1.orderId = " + o1.orderId + ",o2.orderId = " + o2.orderId);
		
		o2.orderId = 1002;
		System.out.println("o1.orderId = " + o1.orderId + ",o2.orderId = " + o2.orderId);
		
	}
}

class Order{
	int orderId;
}
```

##### 1.针对基本数据类型

方法的形参的传递机制：值传递 

1.形参：方法定义时，声明的小括号内的参数 

​	实参：方法调用时，实际传递给形参的数据 

 2.值传递机制：  如果参数是基本数据类型，此时实参赋值给形参的是实参真是存储的数据值。

```java
public class ValueTransferTest1 {

	public static void main(String[] args) {
		
		int m = 10;
		int n = 20;
		
		System.out.println("m = " + m + ", n = " + n);
		//交换两个变量的值的操作
//		int temp = m;
//		m = n;
//		n = temp;
		
		ValueTransferTest1 test = new ValueTransferTest1();
		test.swap(m, n);
		
		System.out.println("m = " + m + ", n = " + n);
		
	}
	
	public void swap(int m,int n){
		int temp = m;
		m = n;
		n = temp;
	}
}
```

##### 2.针对引用数据类型

**如果参数是引用数据类型，此时实参赋值给形参的是实参存储数据的地址值。**

```java
public class ValueTransferTest2 {

	public static void main(String[] args) {
		Data data = new Data();
		
		data.m = 10;
		data.n = 20;
		
		System.out.println("m = " + data.m + ", n = " + data.n);

		//交换m和n的值
//		int temp = data.m;
//		data.m = data.n;
//		data.n = temp;

		ValueTransferTest2 test = new ValueTransferTest2();
		test.swap(data);
		
		System.out.println("m = " + data.m + ", n = " + data.n);

	}
	
	public void swap(Data data){
		int temp = data.m;
		data.m = data.n;
		data.n = temp;
	}
}


class Data{
	
	int m;
	int n;
}
```

![img](https://img-blog.csdnimg.cn/img_convert/4e2fc6b32f4a88bd95ddc2691f84d3e0.png)

##### 3.练习1

```java
public class TransferTest3{
	public static void main(String args[]){
		TransferTest3 test=new TransferTest3();
		test.first();
	}
	
	public void first(){
		int i=5;
		Value v=new Value();
		v.i=25;
		second(v,i);
		System.out.println(v.i);
	}
	
	public void second(Value v,int i){
		i=0;
		v.i=20;
		Value val=new Value();
		v=val;
		System.out.println(v.i+" "+i);
		
	}
}
class Value {
	int i= 15;
} 
```

![img](https://img-blog.csdnimg.cn/img_convert/beae8aceffb02040a75f507e5f740b90.png)

##### 4.练习2

定义一个int型的数组：int[] arr = new int[]{12,3,3,34,56,77,432}; 让数组的每个位置上的值去除以首位置的元素，得到的结果，作为该位置上的新值。遍历新的数组。

```java
//错误写法
for(int i= 0;i < arr.length;i++){
	arr[i] = arr[i] / arr[0];
}

//正确写法1
for(int i = arr.length –1;i >= 0;i--){
	arr[i] = arr[i] / arr[0];
}

//正确写法2
int temp = arr[0];
for(int i= 0;i < arr.length;i++){
	arr[i] = arr[i] / temp;
}
```

##### 5.练习3


 * int[] arr = new int[10];

 * System.out.println(arr);//地址值?

    

 * char[] arr1 = new char[10];

 * System.out.println(arr1);//地址值?

**这个题比较特殊，System.out.println()传进去一个字符型数组会遍历这个字符型数组，记住这个知识点！**

```java
public class ArrayPrint {

	public static void main(String[] args) {
		int[] arr = new int[]{1,2,3};
        //传进去的是一个Object的对象
		System.out.println(arr);//地址值
		
		char[] arr1 = new char[]{'a','b','c'};
        //传进去的是一个数组，里面遍历数据了
		System.out.println(arr1);//abc
	}
}
```

##### 6.练习4

将对象作为参数传递给方法

 * (1)定义一个Circle类，包含一个double型的radius属性代表圆的半径，一个findArea()方法返回圆的面积。
 * 
 * (2)定义一个类PassObject，在类中定义一个方法printAreas()，该方法的定义如下：
 * public void printAreas(Circle c,int time)
 * 在printAreas方法中打印输出1到time之间的每个整数半径值，以及对应的面积。
 * 例如，times为5，则输出半径1，2，3，4，5，以及对应的圆面积。
 * 
 * (3)在main方法中调用printAreas()方法，调用完毕后输出当前半径值。

circle类：

```java
public class Circle {

	double radius;	//半径
	
	//返回圆的面积
	public double findArea(){
		return radius * radius * Math.PI;
	}
}
```

PassObject类：

```java
public class PassObject {
	
	public static void main(String[] args) {
		PassObject test = new PassObject();
		
		Circle c = new Circle();
		
		test.printAreas(c, 5);
		
		System.out.println("no radius is:" + c.radius);
	}
	
	public void printAreas(Circle c,int time){
		
		System.out.println("Radius\t\tAreas");
		
		//设置圆的半径
		for(int i = 1;i <= time ;i++){
			c.radius = i;
			System.out.println(c.radius + "\t\t" + c.findArea());
		}
		
		//重新赋值
		c.radius = time + 1;
	}
}
```

#### 9.递归

 递归方法的使用：

1.递归方法：一个方法体内调用它自身。

2.方法递归包含了一种隐式的循环，它会重复执行某段代码，但这种重复执行无须循环控制。

3.递归一定要向已知方向递归，否则这种递归就变成了无穷递归，类似于死循环。

```java
public class RecursionTest {

	public static void main(String[] args) {

		// 例1:计算1-100之间所有自然数的和
		// 方法1:
		int sum = 0;
		for (int i = 1; i <= 100; i++) {
			sum += i;
		}
		System.out.println("sum = " + sum);

		// 方法2:
		RecursionTest test = new RecursionTest();
		int sum1 = test.getSum(100);
		System.out.println("sum1 = " + sum1);
	}

	// 例1:计算1-n之间所有自然数的和
	public int getSum(int n) {

		if (n == 1) {
			return 1;
		} else {
			return n + getSum(n - 1);
		}
	}

	// 例2:计算1-n之间所有自然数的乘积
	//归求阶乘(n!)的算法
	public int getSum1(int n) {


		if (n == 1) {
			return 1;
		} else {
			return n * getSum1(n - 1);
		}
	}
}
```

练习1

```java
public class RecursionTest {

	public static void main(String[] args) {

		int value = test.f(10);
		System.out.println(value);
	}

	//例3:已知有一个数列：f(0) = 1,f(1) = 4,f(n+2)=2*f(n+1) + f(n),
	//其中n是大于0的整数，求f(10)的值。
	public int f(int n){
		if(n == 0){
			return 1;
		}else if(n == 1){
			return 4;
		}else{
			return 2*f(n-1) + f(n-2);
		}
	}
	
	//例4:已知一个数列：f(20) = 1,f(21) = 4,f(n+2) = 2*f(n+1)+f(n),
	//其中n是大于0的整数，求f(10)的值。
	public int f1(int n){
		if(n == 20){
			return 1;
		}else if(n == 21){
			return 4;
		}else{
			return 2*f1(n-1) + f1(n-2);
		}
	}
}
```

练习2

```java
/*
 * 输入一个数据n，计算斐波那契数列(Fibonacci)的第n个值
 * 1  1  2  3  5  8  13  21  34  55
 * 规律：一个数等于前两个数之和
 * 要求：计算斐波那契数列(Fibonacci)的第n个值，并将整个数列打印出来
 * 
 */
public class Recursion2 {

	public static void main(String[] args) {
		
		Recursion2 test = new Recursion2();
		int value = test.f(10);
		System.out.println(value);
	}
	
	public int f(int n) {

		if (n == 1 || n == 2) {
			return 1;
		} else {
			return f(n - 1) + f(n - 2);
		}
	}
}
```

### 5.面向对象特征之一：封装与隐藏

**高内聚，低耦合**

高内聚：类的内部数据操作自己完成，不允许外部干涉

低耦合：仅对外暴露少量方法用于使用

隐藏对象内部的复杂性，只对外公开简单的接口：

便于外界调用，从而提高系统的可扩展性、可维护性。通俗的说，**把该隐藏的隐藏起来，该暴露的暴露出来。这就是封装性的设计思想。**


 * **面向对象的特征一:封装与隐藏**
 * **一、问题的引入：**
 * **当我们创建一个类的对象以后，我们可以通过"对象.属性"的方式，对对象的属性进行赋值。这里，赋值操作要受到**
 * **属性的数据类型和存储范围的制约。但除此之外，没有其他制约条件。但是，实际问题中，我们往往需要给属性赋值**
 * **加入额外限制条件。这个条件就不能在属性声明时体现，我们只能通过方法进行条件的添加。比如说，setLegs**
 * **同时，我们需要避免用户再使用“对象.属性”的方式对属性进行赋值。则需要将属性声明为私有的(private)**
 * **--->此时，针对于属性就体现了封装性。**
 * **这只是封装性的一个体现，并不是完整的封装性，相当于充分必要条件**
 * 
 * **二、封装性的体现：**
 * **我们将类的属性私有化(private),同时,提供公共的(public)方法来获取(getXxx)和设置(setXxx)**
 * 
 * **拓展：封装性的体现：① 如上 ② 单例模式 （构造器私有化）③ 不对外暴露的的私有的方法从④如果不希望类在包外被调用，可以将类设置为缺省的。**

```java
public class AnimalTest {

	public static void main(String[] args) {
		Animal a = new Animal();
		a.name = "大黄";
//		a.age = 1;
//		a.legs = 4;//The field Animal.legs is not visible
		
		a.show();
		
//		a.legs = -4;
//		a.setLegs(6);
		a.setLegs(-6);
		
//		a.legs = -4;//The field Animal.legs is not visible
		a.show();
		
		System.out.println(a.name);
		System.out.println(a.getLegs());
	}
}
class Animal{
	
	String name;
	private int age;
	private int legs; //腿的个数
	
	//对于属性的设置
	public void setLegs(int l){
		if(l >= 0 && l % 2 == 0){
			legs = l;
		}else{
			legs = 0;
		}
	}
	
	//对于属性的获取
	public int getLegs(){
		return legs;
	}
	
	public void eat(){
		System.out.println("动物进食");
	}
	
	public void show(){
		System.out.println("name = " + name + ",age = " + age + ",legs = " + legs);
	}
	
	//提供关于属性 age 的 get 和 set 方法
	public int getAge(){
		return age;
	}
	
	public void setAge(int a){
		age = a;
	}
}
```

#### 1. 四种权限修饰符的理解和测试

**Java 权限修饰符`public、protected、default(缺省)、private` 置于类的成员定义前，用来限定对象对该类成员的访问权限。**

![图片: https://uploader.shimo.im/f/BnOxeu6anBqhLyCW.png](https://img-blog.csdnimg.cn/img_convert/ab992b12ef5b16774376e00dab0415e0.png)

**对于类（ class） 的权限修饰只可以用 public 和 default(缺省)。**

- **public 类可以在任意地方被访问。**
- **default 类只可以被同一个包内部的类访问**。



三、封装性的体现，需要权限修饰符来配合。

 *   1.Java 规定的 4 种权限：(从小到大排序)private、缺省、protected、public
 *   2.4 种权限用来修饰类及类的内部结构：**属性、方法、构造器、内部类**
 *   3.具体的，4 种权限都可以用来修饰类的内部结构：属性、方法、构造器、内部类
 *   **修饰类的话，只能使用：缺省、public**
 *   总结封装性：Java 提供了 4 中权限修饰符来修饰类积累的内部结构，体现类及类的内部结构的可见性的方法。

order类：

```java
public class Order {

	private int orderPrivate;
	int orderDefault;
	public int orderPublic;
	
	private void methodPrivate(){
		orderPrivate = 1;
		orderDefault = 2;
		orderPublic = 3;
	}
	
	void methodDefault(){
		orderPrivate = 1;
		orderDefault = 2;
		orderPublic = 3;
	}
	
	public void methodPublic(){
		orderPrivate = 1;
		orderDefault = 2;
		orderPublic = 3;
	}
}
```

ordertest类：

```java
public class OrderTest {

	public static void main(String[] args) {
		
		Order order = new Order();
		
		order.orderDefault = 1;
		order.orderPublic = 2;
		//出了 Order 类之后，私有的结构就不可调用了
//		order.orderPrivate = 3;//The field Order.orderPrivate is not visible
		
		order.methodDefault();
		order.methodPublic();
		//出了 Order 类之后，私有的结构就不可调用了
//		order.methodPrivate();//The method methodPrivate() from the type Order is not visible
	}
}
```

相同项目不同包的ordertest类：

```java
import github.Order;

public class OrderTest {

	public static void main(String[] args) {
		Order order = new Order();
		
		order.orderPublic = 2;
		//出了 Order 类之后，私有的结构、缺省的声明结构就不可调用了
//		order.orderDefault = 1;
//		order.orderPrivate = 3;//The field Order.orderPrivate is not visible
		
		order.methodPublic();
		//出了 Order 类之后，私有的结构、缺省的声明结构就不可调用了
//		order.methodDefault();
//		order.methodPrivate();//The method methodPrivate() from the type Order is not visible
	}
}
```

![img](https://gitee.com/lsqpic/BlogPicBed-1/raw/master/img/2021/01/28/20210131190033.png)

#### 2.封装性的练习

![img](https://img-blog.csdnimg.cn/img_convert/14df2c230ae124b47badd1df03f7f4ec.png)


 * 1.创建程序,在其中定义两个类：Person 和 PersonTest 类。
 * 定义如下：用 setAge()设置人的合法年龄(0~130)，用 getAge()返回人的年龄。


​    

```java
public class Person {

	private int age;
	
	public void setAge(int a){
		if(a < 0 || a > 130){
//			throw new RuntimeException("传入的数据据非法");
			System.out.println("传入的数据据非法");
			return;
		}
		
		age = a;
		
	}
	
	public int getAge(){
		return age;
	}
	
	//绝对不能这样写！！！
	public int doAge(int a){
		age = a;
		return age;
	}
}
```

测试类：

 *  在 PersonTest 类中实例化 Person 类的对象 b，
 *  调用 setAge()和 getAge()方法，体会 Java 的封装性。

```java
public class PersonTest {

	public static void main(String[] args) {
		Person p1 = new Person();
//		p1.age = 1;	//编译不通过
		
		p1.setAge(12);
		
		System.out.println("年龄为:" + p1.getAge());
	}
}
```

### 6.构造器（构造方法）

#### 1.构造器的理解

 * 类的结构之三:构造器(构造方法、constructor)的使用
 * constructor:
 * 
 * 一、构造器的作用:
 * 1.**创建对象**
 * 2.**初始化对象的结构**

 * 二、说明
 * 1.**如果没有显示的定义类的构造器的话，则系统默认提供一个空参的构造器（该默认空参构造器权限与类的权限相同，只有能用这个类的地方才能用这个构造器）。**
 * 2.定义构造器的格式:
 * 权限修饰符  类名(形参列表) { }
 * 3.一个类中定义的多个构造器，彼此构成重载。
 * 4**.一旦显示的定义了类的构造器之后，系统不再提供默认的空参构造器。**
 * 5.**一个类中，至少会有一个构造器**		

```java
public class PersonTest {

	public static void main(String[] args) {
		//创建类的对象:new + 构造器
		Person p = new Person();	//Person()这就是构造器
		
		p.eat();
		
		Person p1 = new Person("Tom");
		System.out.println(p1.name);
	}
}
class Person{
	//属性
	String name;
	int age;
	
	//构造器
	public Person(){
		System.out.println("Person()......");
	}
	
	public Person(String n){
		name = n;
	}
	
	public Person(String n,int a){
		name = n;
		age = a;
	}
	
	//方法
	public void eat(){
		System.out.println("人吃饭");
	}
	
	public void study(){
		System.out.println("人学习");
	}
}
```

练习1：

```java
/* 2.在前面定义的 Person 类中添加构造器，
 * 利用构造器设置所有人的 age 属性初始值都为 18。
 * 
 */
public class Person {

	private int age;
	
	public Person(){
		age = 18;
	}
}

public class PersonTest {

	public static void main(String[] args) {
		Person p1 = new Person();

		System.out.println("年龄为:" + p1.getAge());
	}
}
```

 练习2：

```java
/* 3.修改上题中类和构造器，增加 name 属性,
 *   使得每次创建 Person 对象的同时初始化对象的 age 属性值和 name 属性值。
 */
public class Person {

	private int age;
	private String name;
	
	public Person(){
		age = 18;
	}
	
	public Person(String n,int a){
		name = n;
		age = a;
	}
	
	public void setName(String n){
		name = n;
	}
	
	public String getName(){
		return name;
	}
	
	public void setAge(int a){
		if(a < 0 || a > 130){
//			throw new RuntimeException("传入的数据据非法");
			System.out.println("传入的数据据非法");
			return;
		}
		
		age = a;
		
	}
	
	public int getAge(){
		return age;
	}
}

public class PersonTest {

	public static void main(String[] args) {
		
		Person p2 = new Person("Tom",21);
		
		System.out.println("name = " + p2.getName() + ",age = " + p2.getAge());
	}
}
```

练习三：

```java
/*
 * 编写两个类，TriAngle 和 TriAngleTest，
 * 其中 TriAngle 类中声明私有的底边长 base 和高 height，同时声明公共方法访问私有变量。
 * 此外，提供类必要的构造器。另一个类中使用这些公共方法，计算三角形的面积。
 * 
 */
public class TriAngle {

	private double base;//底边长
	private double height;//高
	
	public TriAngle(){
		
	}
	
	public TriAngle(double b,double h){
		base = b;
		height = h;
	}
	
	public void setBase(double b){
		base = b;
	}
	
	public double getBase(){
		return base;
	}
	
	public void setHeight(double h){
		height = h;
	}
	
	public double getHeight(){
		return height;
	}
}

public class TriAngleTest {

	public static void main(String[] args) {
		
		TriAngle t1 = new TriAngle();
		t1.setBase(2.0);
		t1.setHeight(2.5);
//		t1.base = 2.5;//The field TriAngle.base is not visible
//		t1.height = 4.3;		
		System.out.println("base : " + t1.getBase() + ",height : " + t1.getHeight());
		
		TriAngle t2 = new TriAngle(5.1,5.6);
		System.out.println("面积 : " + t2.getBase() * t2.getHeight() / 2);

	}
}
```

#### 2.总结属性赋值的过程

**总结:属性赋值的先后顺序**



 * **① 默认初始化值**

 * **② 显式初始化**

 * **③ 构造器中赋值**

 * **④ 通过"对象.方法" 或 “对象.属性”的方式，赋值**

    

   **以上操作的先后顺序:① - ② - ③ - ④**

```java
public class UserTest {

	public static void main(String[] args) {
		User u = new User();
		
		System.out.println(u.age);
		
		User u1 = new User(2);
		
		u1.setAge(3);
		
		System.out.println(u1.age);
	}
}
class User{
	String name;
	int age = 1;
	
	public User(){
		
	}
	
	public User(int a){
		age = a;
	}
	
	public void setAge(int a){
		age = a;
	}
}
```

#### 3.javabean的使用


 * JavaBean 是一种 Java 语言写成的可重用组件。

 * 所谓 javaBean，是指符合如下标准的 Java 类：

      **类是公共的**

      **有一个无参的公共的构造器**

      **有属性，且有对应的 get、set 方法**

```java
public class Customer {
	
	private int id;
	private String name;

	public Customer(){
		
	}
	
	public void setId(int i){
		id = i;
	}
	
	public int getId(){
		return id;
	}
	
	public void setName(String n){
		name = n;
	}
	
	public String getName(){
		return name;
	}
}
```

#### 4.UML类图

![img](https://img-blog.csdnimg.cn/img_convert/4245a65d9610ec85f6b80c6f520d989e.png)

- **表示 public 类型，-表示 private 类型，#表示 protected 类型**
- **方法的写法: 方法的类型(+、-) ；方法名(参数名：参数类型)：返回值类型**

### 7.关键字：this的使用

#### 1.this调用属性、方法、构造器、

this 关键字的使用：

 * **1.this 用来修饰、调用：属性、方法、构造器**

 * **2.this 修饰属性和方法:**

   **this 理解为：当前对象,或当前正在创建的对象。**

   **2.1 在类的方法中，我们可以使用"this.属性"或"this.方法"的方式，调用当前对象属性和方法。**

   **通常情况下，我们都选择省略“this.”。特殊情况下，如果方法的形参和类的属性同名，我们必须显式的使用"this.变量"的方式，表明此变量是属性，而非形参。**

   **2.2 在类的构造器中，我们可以使用"this.属性"或"this.方法"的方式，调用正在创建的对象属性和方法。但是，通常情况下，我们都选择省略“this.”。特殊情况下，如果构造器的形参和类的属性同名，我们必须显式的使用"this.变量"的方式，表明此变量是属性，而非形参。**

 * 3.this 调用构造器

   ① 我们可以在类的构造器中，显式的使用"**this(形参列表)"**的方式，调用本类中重载的其他的构造器！

   ② **构造器中不能通过"this(形参列表)"的方式调用自己。**

   ③ **如果一个类中声明了n个构造器，则最多有n -1个构造器中使用了"this(形参列表)"。**

   ④ **"this(形参列表)"必须声明在类的构造器的首行！**

   ⑤ **在类的一个构造器中，最多只能声明一个"this(形参列表)"。**

```java
public class PersonTest {

	public static void main(String[] args) {
		Person p1 = new Person();
		
		p1.setAge(1);
		System.out.println(p1.getAge());
		
		p1.eat();
		System.out.println();
		
		Person p2 = new Person("jerry" ,20);
		System.out.println(p2.getAge());
	}
}
class Person{
	
	private String name;
	private int age;
	
	public Person(){
		this.eat();
		String info = "Person 初始化时，需要考虑如下的 1,2,3,4...(共 40 行代码)";
		System.out.println(info);
	}
	
	public Person(String name){
		this();
		this.name = name;
	}
	
	public Person(int age){
		this();
		this.age = age;
	}
	
	public Person(String name,int age){
		this(age);	//调用构造器的一种方式
		this.name = name;
//		this.age = age;
	}
	
	public void setNmea(String name){
		this.name = name;
	}
	
	public String getName(){
		return this.name;
	}
	
	public void setAge(int age){
		this.age = age;
	}
	
	public int getAge(){
		return this.age;
	}
	
	public void eat(){
		System.out.println("人吃饭");
		this.study();
	}
	
	public void study(){
		System.out.println("学习");
	}
}
```

#### 2.this的练习

##### **练习1！：**

![img](https://img-blog.csdnimg.cn/img_convert/d806071ae40c28f681eb09446130c886.png)

boy类：

```java
public class Boy {

	private String name;
	private int age;
	
	public void setName(String name){
		this.name = name;
	}
	
	public String getName(){
		return name;
	}
	
	public void setAge(int ahe){
		this.age = age;
	}
	
	public int getAge(){
		return age;
	}
	
	public Boy(String name, int age) {
		this.name = name;
		this.age = age;
	}


	public void marry(Girl girl){
		System.out.println("我想娶" + girl.getName());
	}
	
	public void shout(){
		if(this.age >= 22){
			System.out.println("可以考虑结婚");
		}else{
			System.out.println("好好学习");
		}
	}
}
```

Girl类：

```java
public class Girl {

	private String name;
	private int age;
	
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	
	public Girl(){
		
	}
	public Girl(String name, int age) {
		this.name = name;
		this.age = age;
	}
	
	public void marry(Boy boy){
		System.out.println("我想嫁给" + boy.getName());
	}
	/**
	  * 
	  * @Description 比较两个对象的大小
	  * @author subei
	  * @date 2020 年 4 月 21 日上午 9:17:35
	  * @param girl
	  * @return
	 */
	public int compare(Girl girl){
//		if(this.age >girl.age){
//			return 1;
//		}else if(this.age < girl.age){
//			return -1;
//		}else{
//			return 0;
//		}
		
		return this.age - girl.age;
	}
	
}
```

测试类：

```java
public class BoyGirlTest {

	public static void main(String[] args) {
		
		Boy boy = new Boy("罗密欧",21);
		boy.shout();
		
		Girl girl = new Girl("朱丽叶", 18);
		girl.marry(boy);
		
		Girl girl1 = new Girl("祝英台", 19);
		int compare = girl.compare(girl1);
		if(compare > 0){
			System.out.println(girl.getName() + "大");
		}else if(compare < 0){
			System.out.println(girl1.getName() + "大");
		}else{
			System.out.println("一样的");
		}
	}
}
```

##### **练习2！！：**

![image-20211206205543934](C:\Users\86156\AppData\Roaming\Typora\typora-user-images\image-20211206205543934.png)

Account类：

```java
public class Account {

	private int id; // 账号
	private double balance; // 余额
	private double annualInterestRate; // 年利率

	public void setId(int id) {

	}

	public double getBalance() {
		return balance;
	}

	public void setBalance(double balance) {
		this.balance = balance;
	}

	public double getAnnualInterestRate() {
		return annualInterestRate;
	}

	public void setAnnualInterestRate(double annualInterestRate) {
		this.annualInterestRate = annualInterestRate;
	}

	public int getId() {
		return id;
	}

	public void withdraw(double amount) { // 取钱
		if(balance < amount){
			System.out.println("余额不足，取款失败");
			return;
		}
		balance -= amount;
		System.out.println("成功取出" + amount);
	}

	public void deposit(double amount) { // 存钱
		if(amount > 0){
			balance += amount;
			System.out.println("成功存入" + amount);
		}
	}

	public Account(int id, double balance, double annualInterestRate) {
		this.id = id;
		this.balance = balance;
		this.annualInterestRate = annualInterestRate;
	}
	
	
}
```



![image-20211206211549558](C:\Users\86156\AppData\Roaming\Typora\typora-user-images\image-20211206211549558.png)

Customer类：

```java
public class Customer {

	private String firstName;
	private String lastName;
	private Account account;

	public Customer(String f, String l) {
		this.firstName = f;
		this.lastName = l;
	}

	public String getFirstName() {
		return firstName;
	}

	public String getLastName() {
		return lastName;
	}

	public Account getAccount() {
		return account;
	}

	public void setAccount(Account account) {
		this.account = account;
	}
	
}
```



![image-20211206212622758](C:\Users\86156\AppData\Roaming\Typora\typora-user-images\image-20211206212622758.png)

CustomerTest类：

```java
/*
 * 写一个测试程序。
 * （1）创建一个 Customer，名字叫 Jane Smith, 他有一个账号为 1000，
 * 余额为 2000 元，年利率为 1.23％的账户。
 * （2）对 Jane Smith 操作。存入 100 元，再取出 960 元。再取出 2000 元。
 * 打印出 Jane Smith 的基本信息
 * 
 * 成功存入：100.0
 * 成功取出：960.0
 * 余额不足，取款失败
 * Customer  [Smith,  Jane]  has  a  account:  id  is 1000, 
 *  annualInterestRate  is 1.23％,  balance  is 1140.0
 *  
 */
public class CustomerTest {

	public static void main(String[] args) {
		Customer cust = new Customer("Jane" , "Smith");
		
		Account acct = new Account(1000,2000,0.0123);
		
		cust.setAccount(acct);
		
		cust.getAccount().deposit(100); //存入 100
		cust.getAccount().withdraw(960); //取钱 960
		cust.getAccount().withdraw(2000); //取钱 2000
		
		System.out.println("Customer[" + cust.getLastName() + cust.getFirstName() + "]  has  a  account:  id  is "
				+ cust.getAccount().getId() + ",annualInterestRate  is " + cust.getAccount().getAnnualInterestRate() * 100 + "%,  balance  is "
				+ cust.getAccount().getBalance());
	}
}
```

##### **练习3！！！：**

![image-20211206224837756](C:\Users\86156\AppData\Roaming\Typora\typora-user-images\image-20211206224837756.png)

Account类：

```java
public class Account {

	private double balance;

	public double getBalance() {
		return balance;
	}

	public Account(double init_balance){
		this.balance = init_balance;
	}
	
	//存钱操作
	public void deposit(double amt){
		if(amt > 0){
			balance += amt;
			System.out.println("存钱成功");
		}
	}
	
	//取钱操作
	public void withdraw(double amt){
		if(balance >= amt){
			balance -= amt;
			System.out.println("取钱成功");
		}else{
			System.out.println("余额不足");
		}
	}
}
```

![image-20211206224952679](C:\Users\86156\AppData\Roaming\Typora\typora-user-images\image-20211206224952679.png)

Customer类：

```java
public class Customer {

	private String firstName;
	private String lastName;
	private Account account;
	
	public String getFirstName() {
		return firstName;
	}
	public String getLastName() {
		return lastName;
	}
	public Account getAccount() {
		return account;
	}
	public void setAccount(Account account) {
		this.account = account;
	}
	public Customer(String f, String l) {
		this.firstName = f;
		this.lastName = l;
	}	
}
```

![image-20211206225047265](C:\Users\86156\AppData\Roaming\Typora\typora-user-images\image-20211206225047265.png)

Bank类：

**注意对象数组的创建与初始化**！！！

要new两次！先new数组！再new单独的对象！！！

```java
public class Bank {

	private int numberOfCustomers;	//记录客户的个数
	private Customer[] customers;	//存放多个客户的数组
	
	public Bank(){
		customers = new Customer[10];
	}
	
	//添加客户
	public void addCustomer(String f,String l){
		Customer cust = new Customer(f,l);
//		customers[numberOfCustomers] = cust;
//		numberOfCustomers++;
		customers[numberOfCustomers++] = cust;
	}

	//获取客户的个数
	public int getNumberOfCustomers() {
		return numberOfCustomers;
	}

	//获取指定位置上的客户
	public Customer getCustomers(int index) {
//		return customers;	//可能报异常
		if(index >= 0 && index < numberOfCustomers){
			return customers[index];
		}
		
		return null;
	}	
	
}
```

Banktest类：

**注意匿名对象的使用，作为实参赋值，由于它创建后地址赋给了customer里的account属性，所以不会被回收！！！**

```java
public class BankTest {

	public static void main(String[] args) {
		
		Bank bank = new Bank();
		
		bank.addCustomer("Jane", "Smith");	
		
		bank.getCustomers(0).setAccount(new Account(2000));
		
		bank.getCustomers(0).getAccount().withdraw(500);
		
		double balance = bank.getCustomers(0).getAccount().getBalance();
		
		System.out.println("客户: " + bank.getCustomers(0).getFirstName() + "的账户余额为：" + balance);
		
		System.out.println("***************************");
		bank.addCustomer("万里", "杨");
		
		System.out.println("银行客户的个数为: " + bank.getNumberOfCustomers());
		
	}
}
```



### 8.关键字：package、import的应用

#### 1.关键字--package

一、package 关键字的使用

 * **1.为了更好的实现项目中类的管理，提供包的概念**

 * **2.使用 package 声明类或接口所属的包，声明在源文件的首行**

 * **3.包，属于标识符，遵循标识符的命名规则、规范"见名知意"**

 * **4.每“.”一次,就代表一层文件目录。**

   

 * **补充:同一个包下，不能命名同名接口或同名类**

 * **不同包下，可以命名同名的接口、类。**

JDK中主要包的介绍：

```java
1.java.lang----包含一些 Java 语言的核心类，如 String、Math、Integer、System 和 Thread，提供常用功能
2.java.net----包含执行与网络相关的操作的类和接口。
3.java.io----包含能提供多种输入/输出功能的类。
4.java.util----包含一些实用工具类，如定义系统特性、接口的集合框架类、使用与日期日历相关的函数。
5.java.text----包含了一些 java 格式化相关的类
6.java.sql----包含了 java 进行 JDBC 数据库编程的相关类/接口
7.java.awt----包含了构成抽象窗口工具集（abstractwindowtoolkits）的多个类，这些类被用来构建和管理应用程序的图形用户界面(GUI)。B/S  C/S
```

#### 2.MVC设计模式

MVC 是常用的设计模式之一，将整个程序分为三个层次：**视图模型层，控制器层，数据模型层**。这种将程序输入输出、数据处理，以及数据的展示分离开来的设计模式使程序结构变的灵活而且清晰，同时也描述了程序各个对象间的通信方式，降低了程序的耦合性。

![img](https://img-blog.csdnimg.cn/img_convert/9f9ff69148f88dede9093114379f7173.png)

![img](https://img-blog.csdnimg.cn/img_convert/4e1a5995c0b08f5fe36fb09d25e53b61.png)

#### 3.关键字--import



二、import关键字的使用

import:导入

 * 1.在源文件中显式的使用import结构导入指定包下的类、接口
 * 2.声明在包的声明和类的声明之间
 * 3.如果需要导入多个结构，则并列写出即可
 * 4.**可以使用"xxx.*"的方式,表示可以导入xxx包下的所有结构**。
 * 5.**如果导入的类或接口是java.lang包下的，或者是当前包下的，则可以省略此import语句。**
 * 6.**如果在代码中使用不同包下的同名的类。那么就需要使用类的全类名的方式指明调用的是哪个类。**
 * 7**.如果已经导入java.a包下的类。那么如果需要使用a包的*子包*下的类的话，仍然需要导入。（两个包之间已经没啥关系了）**
 * 8.**import static组合的使用：调用指定类或接口下的静态的属性或方法.**

```java
import java.util.*;
import account2.Bank;
import static java.lang.System.*;
public class PackageImportTest {

	public static void main(String[] args) {
		String info = Arrays.toString(new int[]{1,2,3});
		
		Bank bank = new Bank();
		
		ArrayList list = new ArrayList();
		HashMap map = new HashMap();
		
		Scanner s = null;	
		
		System.out.println("hello");
		
		UserTest us = new UserTest();
		out.println("hello");(静态类方法这样用)
	}
}
```

## 7.项目二（客户信息管理软件）

CMUtility工具类：

```java
package com.atguigu.p2;


import java.util.*;
/**
CMUtility工具类：
将不同的功能封装为方法，就是可以直接通过调用方法使用它的功能，而无需考虑具体的功能实现细节。
*/
public class CMUtility {
    private static Scanner scanner = new Scanner(System.in);
    /**
	用于界面菜单的选择。该方法读取键盘，如果用户键入’1’-’5’中的任意字符，则方法返回。返回值为用户键入字符。
	*/
	public static char readMenuSelection() {
        char c;
        for (; ; ) {
            String str = readKeyBoard(1, false);
            c = str.charAt(0);
            if (c != '1' && c != '2' && 
                c != '3' && c != '4' && c != '5') {
                System.out.print("选择错误，请重新输入：");
            } else break;
        }
        return c;
    }
	/**
	从键盘读取一个字符，并将其作为方法的返回值。
	*/
    public static char readChar() {
        String str = readKeyBoard(1, false);
        return str.charAt(0);
    }
	/**
	从键盘读取一个字符，并将其作为方法的返回值。
	如果用户不输入字符而直接回车，方法将以defaultValue 作为返回值。
	*/
    public static char readChar(char defaultValue) {
        String str = readKeyBoard(1, true);
        return (str.length() == 0) ? defaultValue : str.charAt(0);
    }
	/**
	从键盘读取一个长度不超过2位的整数，并将其作为方法的返回值。
	*/
    public static int readInt() {
        int n;
        for (; ; ) {
            String str = readKeyBoard(2, false);
            try {
                n = Integer.parseInt(str);
                break;
            } catch (NumberFormatException e) {
                System.out.print("数字输入错误，请重新输入：");
            }
        }
        return n;
    }
	/**
	从键盘读取一个长度不超过2位的整数，并将其作为方法的返回值。
	如果用户不输入字符而直接回车，方法将以defaultValue 作为返回值。
	*/
    public static int readInt(int defaultValue) {
        int n;
        for (; ; ) {
            String str = readKeyBoard(2, true);
            if (str.equals("")) {
                return defaultValue;
            }

            try {
                n = Integer.parseInt(str);
                break;
            } catch (NumberFormatException e) {
                System.out.print("数字输入错误，请重新输入：");
            }
        }
        return n;
    }
	/**
	从键盘读取一个长度不超过limit的字符串，并将其作为方法的返回值。
	*/
    public static String readString(int limit) {
        return readKeyBoard(limit, false);
    }
	/**
	从键盘读取一个长度不超过limit的字符串，并将其作为方法的返回值。
	如果用户不输入字符而直接回车，方法将以defaultValue 作为返回值。
	*/
    public static String readString(int limit, String defaultValue) {
        String str = readKeyBoard(limit, true);
        return str.equals("")? defaultValue : str;
    }
	/**
	用于确认选择的输入。该方法从键盘读取‘Y’或’N’，并将其作为方法的返回值。
	*/
    public static char readConfirmSelection() {
        char c;
        for (; ; ) {
            String str = readKeyBoard(1, false).toUpperCase();
            c = str.charAt(0);
            if (c == 'Y' || c == 'N') {
                break;
            } else {
                System.out.print("选择错误，请重新输入：");
            }
        }
        return c;
    }

    private static String readKeyBoard(int limit, boolean blankReturn) {
        String line = "";

        while (scanner.hasNextLine()) {
            line = scanner.nextLine();
            if (line.length() == 0) {
                if (blankReturn) return line;
                else continue;
            }

            if (line.length() < 1 || line.length() > limit) {
                System.out.print("输入长度（不大于" + limit + "）错误，请重新输入：");
                continue;
            }
            break;
        }

        return line;
    }
}
```

Customer类：


```java
package com.atguigu.p2;

public class Customer {
	private String name;
	private char gender;
	private int age;
	private String phone;
	private String email;

	public Customer(String name, char gender, int age) {
		this(name, gender, age, "", "");
	}

	public Customer(String name, char gender, int age, String phone,
			String email) {
		this.name = name;
		this.gender = gender;
		this.age = age;
		this.phone = phone;
		this.email = email;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public char getGender() {
		return gender;
	}

	public void setGender(char gender) {
		this.gender = gender;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public String getPhone() {
		return phone;
	}

	public void setPhone(String phone) {
		this.phone = phone;
	}

	public String getEmail() {
		return email;
	}

	public void setEmail(String email) {
		this.email = email;
	}

	public String getDetails() {
		return name + "\t" + gender + "\t" + age + "\t\t" + phone + "\t" + email;
	}
}
```

CustomerList类：

```java
package com.atguigu.p2;
public class CustomerList {
    private Customer[] customers;
    private int total = 0;

    public CustomerList(int totalCustomer) {
        customers = new Customer[totalCustomer];
    }

    public boolean addCustomer(Customer customer) {
        if (total >= customers.length) return false;
        
        customers[total++] = customer;
        return true;
    }
     
    public boolean replaceCustomer(int index, Customer cust) {
        if (index < 0 || index >= total) return false;
        
        customers[index] = cust;
        return true;
    }

    public boolean deleteCustomer(int index) {
        if (index < 0 || index >= total) return false;
        
        for (int i = index; i < total - 1; i++) {
            customers[i] = customers[i + 1];
        }
        
        customers[--total] = null;

        return true;
    }

    public Customer[] getAllCustomers() {
        Customer[] custs = new Customer[total];
        for (int i = 0; i < total; i++) {
            custs[i] = customers[i];
        }
        return custs;
    }

    public int getTotal() {
        return total;
    }

    public Customer getCustomer(int index) {
        if (index < 0 || index >= total) return null;
        
        return customers[index];
    }
}
```

CustomerView类：

```java
package com.atguigu.p2;

public class CustomerView {
	private CustomerList customers = new CustomerList(10);

	public CustomerView() {
		Customer cust = new Customer("张三", '男', 30, "010-56253825",
				"abc@email.com");
		customers.addCustomer(cust);
	}

	public void enterMainMenu() {
		boolean loopFlag = true;
		do {
			System.out
					.println("\n-----------------客户信息管理软件-----------------\n");
			System.out.println("                   1 添 加 客 户");
			System.out.println("                   2 修 改 客 户");
			System.out.println("                   3 删 除 客 户");
			System.out.println("                   4 客 户 列 表");
			System.out.println("                   5 退       出\n");
			System.out.print("                   请选择(1-5)：");

			char key = CMUtility.readMenuSelection();
			System.out.println();
			switch (key) {
			case '1':
				addNewCustomer();
				break;
			case '2':
				modifyCustomer();
				break;
			case '3':
				deleteCustomer();
				break;
			case '4':
				listAllCustomers();
				break;
			case '5':
				System.out.print("确认是否退出(Y/N)：");
				char yn = CMUtility.readConfirmSelection();
				if (yn == 'Y')
					loopFlag = false;
				break;
			}
		} while (loopFlag);
	}

	private void addNewCustomer() {
		System.out.println("---------------------添加客户---------------------");
		System.out.print("姓名：");
		String name = CMUtility.readString(4);
		System.out.print("性别：");
		char gender = CMUtility.readChar();
		System.out.print("年龄：");
		int age = CMUtility.readInt();
		System.out.print("电话：");
		String phone = CMUtility.readString(15);
		System.out.print("邮箱：");
		String email = CMUtility.readString(15);

		Customer cust = new Customer(name, gender, age, phone, email);
		boolean flag = customers.addCustomer(cust);
		if (flag) {
			System.out
					.println("---------------------添加完成---------------------");
		} else {
			System.out.println("----------------记录已满,无法添加-----------------");
		}
	}

	private void modifyCustomer() {
		System.out.println("---------------------修改客户---------------------");

		int index = 0;
		Customer cust = null;
		for (;;) {
			System.out.print("请选择待修改客户编号(-1退出)：");
			index = CMUtility.readInt();
			if (index == -1) {
				return;
			}

			cust = customers.getCustomer(index - 1);
			if (cust == null) {
				System.out.println("无法找到指定客户！");
			} else
				break;
		}

		System.out.print("姓名(" + cust.getName() + ")：");
		String name = CMUtility.readString(4, cust.getName());

		System.out.print("性别(" + cust.getGender() + ")：");
		char gender = CMUtility.readChar(cust.getGender());

		System.out.print("年龄(" + cust.getAge() + ")：");
		int age = CMUtility.readInt(cust.getAge());

		System.out.print("电话(" + cust.getPhone() + ")：");
		String phone = CMUtility.readString(15, cust.getPhone());

		System.out.print("邮箱(" + cust.getEmail() + ")：");
		String email = CMUtility.readString(15, cust.getEmail());

		cust = new Customer(name, gender, age, phone, email);

		boolean flag = customers.replaceCustomer(index - 1, cust);
		if (flag) {
			System.out
					.println("---------------------修改完成---------------------");
		} else {
			System.out.println("----------无法找到指定客户,修改失败--------------");
		}
	}

	private void deleteCustomer() {
		System.out.println("---------------------删除客户---------------------");

		int index = 0;
		Customer cust = null;
		for (;;) {
			System.out.print("请选择待删除客户编号(-1退出)：");
			index = CMUtility.readInt();
			if (index == -1) {
				return;
			}

			cust = customers.getCustomer(index - 1);
			if (cust == null) {
				System.out.println("无法找到指定客户！");
			} else
				break;
		}

		System.out.print("确认是否删除(Y/N)：");
		char yn = CMUtility.readConfirmSelection();
		if (yn == 'N')
			return;

		boolean flag = customers.deleteCustomer(index - 1);
		if (flag) {
			System.out
					.println("---------------------删除完成---------------------");
		} else {
			System.out.println("----------无法找到指定客户,删除失败--------------");
		}
	}

	private void listAllCustomers() {
        System.out.println("---------------------------客户列表---------------------------");
        Customer[] custs = customers.getAllCustomers();
        if (custs.length == 0) {
            System.out.println("没有客户记录！");
        } else {
            System.out.println("编号\t姓名\t性别\t年龄\t\t电话\t\t邮箱");
            for (int i = 0; i < custs.length; i++) {
//            System.out.println(i + 1 + "\t" + custs[i].getName() + "\t" + custs[i].getGender() + "\t" + custs[i].getAge() + "\t\t" + custs[i].getPhone() + "\t" + custs[i].getEmail());
            	System.out.println((i+1) + "\t" + custs[i].getDetails());
            }
        }

        System.out.println("-------------------------客户列表完成-------------------------");
    }

	public static void main(String[] args) {
		CustomerView cView = new CustomerView();
		cView.enterMainMenu();
	}
}
```

## 8.Eclipse快捷键

Eclipse中的快捷键：

 * **1.补全代码的声明：alt + /**
 * **2.快速修复: ctrl + 1**  
 * **3.批量导包：ctrl + shift + o**
 * **4.使用单行注释：ctrl + /**
 * **5.使用多行注释： ctrl + shift + /**   
 * **6.取消多行注释：ctrl + shift + \ **
 * **7.复制指定行的代码：ctrl + alt + down 或 ctrl + alt + up**
 * **8.删除指定行的代码：ctrl + d**
 * **9.上下移动代码：alt + up  或 alt + down**
 * **10.切换到下一行代码空位：shift + enter**
 * **11.切换到上一行代码空位：ctrl + shift + enter**
 * **12.如何查看源码：ctrl + 选中指定的结构   或  ctrl + shift + t**
 * **13.退回到前一个编辑的页面：alt + left** 
 * **14.进入到下一个编辑的页面(针对于上面那条来说的)：alt + right**
 * **15.光标选中指定的类，查看继承树结构：ctrl + t**
 * **16.复制代码： ctrl + c**
 * **17.撤销： ctrl + z**
 * **18.反撤销： ctrl + y**
 * **19.剪切：ctrl + x** 
 * **20.粘贴：ctrl + v**
 * **21.保存： ctrl + s**
 * **22.全选：ctrl + a**
 * **23.格式化代码： ctrl + shift + f**
 * **24.选中数行，整体往后移动：tab**
 * **25.选中数行，整体往前移动：shift + tab**
 * **26.在当前类中，显示类结构，并支持搜索指定的方法、属性等：ctrl + o**
 * **27.批量修改指定的变量名、方法名、类名等：alt + shift + r**
 * **28.选中的结构的大小写的切换：变成大写： ctrl + shift + x**
 * **29.选中的结构的大小写的切换：变成小写：ctrl + shift + y**
 * **30.调出生成getter/setter/构造器等结构： alt + shift + s**
 * **31.显示当前选择资源(工程 or 文件)的属性：alt + enter**
 * **32.快速查找：参照选中的Word快速定位到下一个 ：ctrl + k**
 * **33.关闭当前窗口：ctrl + w**
 * **34.关闭所有的窗口：ctrl + shift + w**
 * **35.查看指定的结构使用过的地方：ctrl + alt + g**
 * **36.查找与替换：ctrl + f**
 * **37.最大化当前的View：ctrl + m**
 * **38.直接定位到当前行的首位：home**
 * **39.直接定位到当前行的末位：end**

## 9.面向对象（中）

### 1.继承性的使用与理解

 * 面向对象的特征二:继承性

   为什么要有继承？

 * 多个类中存在相同属性和行为时，将这些内容抽取到单独一个类中，

 * 那么多个类无需再定义这些属性和行为，只要继承那个类即可。

 * * 一、继承性的好处

 * ① 减少了代码的冗余，提高了代码的复用性；

 * ② 便于功能的扩展；

 * ③ 为之后多态性的使用，提供了前提。

   二、继承性的格式

 * class A extends B{}

 * A:子类、派生类、subclass

 * B:父类、超类、基类、superclass

   2.1 体现：一旦子类 A 继承父类以后，子类 A 中就获取了父类 B 中声明的结构：属性、方法

 * 特别的，父类中声明为 private 的属性或方法，子类继承父类以后，仍然认为获取了父类中私有的结构。

 * 只有因为封装性的影响，使得子类不能直接调用父类的结构而已。

 * **可以用父类里面的方法或者是调用父类构造器来调用父类中私有的属性**

 * 2.2 子类继承父类以后，还可以声明自己特有的属性或方法，实现功能的拓展。

 * 子类和父类的关系：不同于子集与集合的关系。

 * extends:延展、扩展



Person类：

```java
/*
 * 为描述和处理个人信息，定义类 Person
 */
public class Person {
	
	String name;
	private int age;
	
	public Person(){
		
	}
	
	public Person(String name,int age){
		this.name = name;
		this.age = age;
	}
	
	public void eat(){
		System.out.println("吃饭");
		sleep();
	}
	
	private void sleep(){
		System.out.println("睡觉");
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}
	
}
```

student类：

```java
/*
 * 为描述和处理学生信息，定义类 Student
 */
public class Student extends Person {

//	String name;
//	int age;
	String major;
	
	public Student(){
		
	}
	
	public Student(String name,int age,String major){
		this.name = name;
//		this.age = age;
		setAge(age);
		this.major = major;
	}
	
//	public void eat(){
//		System.out.println("吃饭");
//	}
//	
//	public void sleep(){
//		System.out.println("睡觉");
//	}
	
	public void study(){
		System.out.println("学习");
	}
	
	public void show(){
		System.out.println("name:" + name + ",age = " + getAge());
	}

}
```

测试类：

```java
public class ExtendsTest {

	public static void main(String[] args) {
		Person p1 = new Person();
//		p1.age = 1;
		p1.eat();
		System.out.println("********************");
		
		Student s1 = new Student();
		s1.eat();
//		s1.sleep();
		s1.name = "Tom";
		
		s1.setAge(10);
		System.out.println(s1.getAge());
		
	}
}
```

![img](https://img-blog.csdnimg.cn/img_convert/cb041fed5ec912d35815aa8e72d8ecdf.png)

![img](https://img-blog.csdnimg.cn/img_convert/cc9569b92c2b8879b873cd05741fe753.png)

**Java中关于继承性的规定：**

**三、Java 中关于继承性的规定：**

1.一个类可以被多个类继承

 *  	2.Java 中类的单继承性：一个类只能有一个父类
 *  	3.子父类是相对的概念。
 *  	4.子类直接继承的父类，称为：直接父类。间接继承的父类，称为，间接父类。
 *  	5.子类继承父类后，就获取了直接父类以及所有间接父类中声明的**属性和方法。**
 *  	四、**1.如果我们没有显式的声明一个类的父类的话，则此类继承于 java.lang.Object 类**
 *  	2.所有的 java 类(除 java.long.Object 类之外)都直接或间接地继承于 java.lang.Object 类;
 *  	3.意味着，所有的 java 类具有 java.lang.Object 类声明的功能。

```java
public class ExtendsTest {

	public static void main(String[] args) {	
		s1.brease();
		
		Creature c = new Creature();
		System.out.println(c.toString());
		
	}
}
```

![img](https://img-blog.csdnimg.cn/img_convert/8db4be3118c475db5598c470284c8dd4.png)

#### 1.继承性的练习

练习一：

![img](https://img-blog.csdnimg.cn/img_convert/fddefc1254d3110ff26903251083c36b.png)

Mankind类：

```java
/*
 * 定义一个ManKind类，包括
 * 成员变量int sex和int salary；
 * 方法void manOrWoman()：根据sex的值显示“man”(sex==1)或者“woman”(sex==0)；
 * 方法void employeed()：根据salary的值显示“no job”(salary==0)或者“job”(salary!=0)。
 * 
 */
public class ManKind {

	private int sex;	//性别
	private int salary;	//薪资
	
	public ManKind() {
		
	}

	public ManKind(int sex, int salary) {
		this.sex = sex;
		this.salary = salary;
	}

	public void manOrWoman(){
		if(sex==1){
			System.out.println("man");
		}else if(sex==0){
			System.out.println("woman");
		}
	}
	
	public void employeed(){
		if(salary==0){
			System.out.println("no job");
		}else if(salary!=0){
			System.out.println("job");
		}
	}

	public int getSex() {
		return sex;
	}

	public void setSex(int sex) {
		this.sex = sex;
	}

	public int getSalary() {
		return salary;
	}

	public void setSalary(int salary) {
		this.salary = salary;
	}
	
}

```

kind类：

```java
/*
 * 定义类Kids继承ManKind，并包括
 * 成员变量int yearsOld；
 * 方法printAge()打印yearsOld的值
 * 
 */
public class Kids extends ManKind{

	private int yearsOld;	//年限
	
	public Kids() {


	}

	public Kids(int yearsOld) {
		this.yearsOld = yearsOld;
	}

	public int getYearsOld() {
		return yearsOld;
	}

	public void setYearsOld(int yearsOld) {
		this.yearsOld = yearsOld;
	}

	public void printAge(){
		System.out.println("I am " + yearsOld);
	}
}

```

kidstest类：

```java
/*
 * 定义类KidsTest，在类的main方法中实例化Kids的对象someKid，
 * 用该对象访问其父类的成员变量及方法。
 * 
 */
public class KidsTest {
	public static void main(String[] args) {
		
		Kids someKid = new Kids(12);
		
		someKid.printAge();
		
		someKid.setYearsOld(15);
		someKid.setSalary(0);
		someKid.setSex(1);
		
		someKid.employeed();
		someKid.manOrWoman();
	}
}

```

练习二：

![img](https://img-blog.csdnimg.cn/img_convert/c0be1eac6215b7a27e0b209d2fb4dd97.png)

circle类：

```java
public class Circle {

	public double radius;	//半径
	
	public Circle(){
		radius = 1.0;
	}

	public double getRadius() {
		return radius;
	}

	public void setRadius(double radius) {
		this.radius = radius;
	}
	
	public double findArea(){	//计算圆的面积
		return Math.PI * radius * radius;
	}
}
```

cylinder类：

```java
public class Cylinder extends Circle{

	private double length;
	
	public Cylinder(){
		length = 1.0;
	}

	public double getLength() {
		return length;
	}

	public void setLength(double length) {
		this.length = length;
	}
	
	public double findVolume(){	//计算圆柱体积
		return findArea() * length;
	}
}
```

test类：

```java
public class CylinderTest {
	public static void main(String[] args) {
		
		Cylinder cy = new Cylinder();
		
		cy.setRadius(2.1);
		cy.setLength(3.4);
		double volues = cy.findVolume();
		System.out.println("圆柱的体积:" + volues);
		
		double area = cy.findArea();
		System.out.println("圆的面积: " + area);
	}
}
```

### 2.方法的重写

person类：

```java
public class Person {

	String name;
	int age;
	
	public Person(){
		
	}
	
	public Person(String name,int age){
		this.name = name;
		this.age = age;
	}
	
	public void eat(){
		System.out.println("吃饭");
	}
	
	public void walk(int distance){
		System.out.println("走路，走的距离是：" + distance + "公里");
		show();
	}
	
	private void show(){
		System.out.println("我是一个人。");
	}
	
	public Object info(){
		return null;
	}
	
	public double info1(){
		return 1.0;
	}
}
```

student类：

```java
public class Student extends Person{

	String major;
	
	public Student(){
		
	}
	
	public Student(String major){
		this.major = major;
	}
	
	public void study(){
		System.out.println("学习，专业是:" + major);
	}
	
	//对父类中的eat()进行了重写
	public void eat(){
		System.out.println("学生应该多吃有营养的。");
	}
	
	public void show(){
		System.out.println("我是一个学生。");
	}
	
	public String info(){
		return null;
	}
	
	//不是一个类型，所以报错。
//	public int info1(){
//		return 1;
//	}
	
	//可以直接将父类的方法的第一行粘过来，直接写方法体
//	public void walk(int distance){
//		System.out.println("重写的方法");
//	}
	
	//直接输入父类的方法名，Alt + /，选择即可生成
	@Override
	public void walk(int distance) {
		System.out.println("自动生成");
	}
}
```

test类；

```java
public class PersonTest {


	public static void main(String[] args) {
		Student s = new Student("计算机科学与技术");
		s.eat();
		s.walk(10);
		
		s.study();
	}
}
```

**方法的重写(override/overwrite)：**



1.重写：子类继承父类以后，可以对父类中的方法进行覆盖操作。

2.应用：重写以后，当创建子类对象以后，通过子类对象去调用子父类中同名同参数方法时，执行的是子类重写父类的方法。

 * 即在程序执行时，子类的方法将覆盖父类的方法。

   面试题：区分方法的重载与重写(有的书也叫做“覆盖”)

 * 答：方法的重写Overriding和重载Overloading是Java多态性的不同表现。

 * 重写Overriding是父类与子类之间多态性的一种表现，重载Overloading是一个类中多态性的一种表现。

 * 如果在子类中定义某方法与其父类有相同的名称和参数，我们说该方法被重写 (Overriding)。

 * 子类的对象使用这个方法时，将调用子类中的定义，对它而言，父类中的定义如同被"屏蔽"了。

 * 如果在一个类中定义了多个同名的方法，它们或有不同的参数个数或有不同的参数类型，则称为方法的重载(Overloading)。

#### 1.方法重写的细节

**重写的规定：**

 * **方法的声明：权限修饰符 返回值类型 方法名(形参列表){**

   **//方法体}**

   

 * **约定俗称:子类中的叫重写的方法，父类中的叫被重写的方法。**

 * **① 子类重写的方法的方法名和形参列表必须和父类被重写的方法的方法名、形参列表相同;** 

 * **② 子类重写的方法使用的访问权限不能小于父类被重写的方法的访问权限,**

   **特殊情况: 子类不能重写父类中声明为private权限的方法;！！！**

   **③ 返回值类型:**

   **父类被重写的方法的返回值类型是void,则子类重写的方法的返回值类型只能是void;**

   **父类被重写的方法的返回值类型是A类型，则子类重写的方法的返回值类型可以是A类或A类的子类;**

   **父类被重写的方法的返回值类型如果是基本数据类型(比如:double)，则子类重写的方法的返回值类型必须是相同的基本数据类型(必须是:double)。**

   

 * **④ 子类方法抛出的异常不能大于父类被重写的方法抛出的异常**

   

 * **注意：子类与父类中同名同参数的方法必须同时声明为非static的(即为重写)，或者同时声明为static的（不是重写）。**

 * **因为static方法是属于类的，子类无法覆盖父类的方法。**

### 3.四种权限修饰符

![img](https://img-blog.csdnimg.cn/img_convert/c10d9f7a2cfc118c122baa567ba968ca.png)

order类：

```java
package githubb;
/*
 * 体会四种不同的权限修饰符
 */
public class Order {

	private int orderPrivate;
	int orderDefault;
	protected int orderProtected;
	public int orderPublic;
	
	private void methodPrivate(){
		orderPrivate = 1;
		orderDefault = 2;
		orderProtected = 3;
		orderPublic = 4;
	}
	
	void methodDefault(){
		orderPrivate = 1;
		orderDefault = 2;
		orderProtected = 3;
		orderPublic = 4;
	}
	
	protected void methodProtected(){
		orderPrivate = 1;
		orderDefault = 2;
		orderProtected = 3;
		orderPublic = 4;
	}
	
	public void methodPublic(){
		orderPrivate = 1;
		orderDefault = 2;
		orderProtected = 3;
		orderPublic = 4;
	}
}
```

ordertest类：

```java
package githubb;

public class OrderTest {
	public static void main(String[] args) {
		
		Order order = new Order();
		
		order.orderDefault = 1;
		order.orderProtected = 2;
		order.orderPublic = 3;
		
		order.methodDefault();
		order.methodProtected();
		order.methodPublic();
		
		//同一个包中的其它类，不可以调用Order类中私有的属性
//		order.orderPrivate = 4;	//The field Order.orderPrivate is not visible
//		order.methoPrivate();
	}
}
```

suborder类：

```java
package githubc;

import githubb.Order;

public class SubOrder extends Order{

	public void method(){
		orderProtected = 1;
		orderPublic = 2;
		
		methodProtected();
		methodPublic();
		
		//在不同包的子类中，不能调用Order类中声明为private和缺省的权限的属性、方法
//		orderDefault = 3;
//		orderPrivate = 4;
//		
//		methodDefault();
//		methodPrivate();
	}
}
```

ordertest类：

```java
package githubc;

import githubb.Order;

public class OrderTest {
	public static void main(String[] args) {
		
		Order order = new Order();
		order.orderPublic = 1;
		order.methodPublic();
		
		//不同包下的普通类(非子类)要使用Order类，不可以调用声明为private、缺省、protected权限的属性、方法。
//		order.orderPrivate = 2;
//		order.orderProtected = 3;
//		order.orderProtected = 4;
//		
//		order.methodPrivate();
//		order.methodDefault();
//		order.methodProtected();
		
	}
	
	public void show(Order order){
		order.orderPublic = 1;
		order.methodPublic();
		
		//不同包下的普通类(非子类)要使用Order类，不可以调用声明为private、缺省、protected权限的属性、方法。
//		order.orderPrivate = 2;
//		order.orderProtected = 3;
//		order.orderProtected = 4;
//		
//		order.methodPrivate();
//		order.methodDefault();
//		order.methodProtected();
	}
}
```

### 4.super关键字



super关键字的使用

 * 1.super理解为:父类的

 * 2.super可以用来调用:属性、方法、构造器 

 * 

 * 3.super的使用

 * 3.1 我们可以在子类的方法或构造器中，通过"super.属性"或"super.方法"的方式，显式的调用父类中声明的属性或方法。但是，通常情况下，我们习惯去省略这个"super."

 * 3.2 **特殊情况:当子类和父类中定义了同名的属性时，我们要想在子类中调用父类中声明的属性，则必须显式的 使用"super.属性"的方式，表明调用的是父类中声明的属性。**

 * 3.3 **特殊情况:当子类重写了父类中的方法后，我们想在子类的方法中调用父类中被重写的方法时，必须显式的使用"super.方法"的方式，表明调用的是父类中被重写的方法。**

     

   4.super调用构造器

 * 4.1  我们可以在子类的构造器中显式的使用"super(形参列表)"的方式,调用父类中声明的指定的构造器

 * 4.2 **"super(形参列表)"的使用，必须声明在子类构造器的首行！**

 * 4.3 **我们在类的构造器中，针对于"this(形参列表)"或"super(形参列表)"只能二选一，不能同时出现**。

 * 4.4 **在构造器的首行，既没有显式的声明"this(形参列表)"或"super(形参列表)",则默认的调用的是父类中的空参构造器。super()**

 * 4.5 **在类的多个构造器中，至少有一个类的构造器使用了"super(形参列表)",调用父类中的构造器。**

     





person类：

```java
public class Person {

	String name;
	int age;
	int id = 1003;	//身份证号
	
	public Person(){
		System.out.println("我无处不在");
	}
	
	public Person(String name){
		this.name = name;
	}
	
	public Person(String name,int age){
		this(name);
		this.age = age;
	}
	
	public void eat(){
		System.out.println("人，吃饭");
	}
	
	public void walk(){
		System.out.println("人，走路");
	}
}
```

student类：

```java
public class Student extends Person{
	
	String major;
	int id = 1002;	//学号
	
	public Student(){

	}
	
	public Student(String name,int age,String major){
//		this.age = age;
//		this.name = name;
		super(name,age);
		this.major = major;
	}
	
	public Student(String major){
		this.major = major;
	}
	
	public void eat(){
		System.out.println("学生多吃有营养的食物");
	}
	
	public void Study(){
		System.out.println("学生，学习知识。");
		this.eat();
		//如果，想调用父类中被重写的，不想调用子类中的方法，可以：
		super.eat();
		super.walk();//子父类中未重写的方法，用"this."或"super."调用都可以
	}
	public void show(){
		System.out.println("name = " + this.name + ",age = " + super.age);
		System.out.println("id = " + this.id);	
		System.out.println("id = " + super.id);
	}
}
```

测试类：

```java
public class SuperTest {
	public static void main(String[] args) {
		
		Student s = new Student();
		s.show();
		
		s.Study();
		
		Student s1 = new Student("Ton",21,"IT" );
		s1.show();
		
		System.out.println("***********************");
		Student s2 = new Student();
		
	}
}
```

### 5.子类对象实例化的过程

![img](https://img-blog.csdnimg.cn/img_convert/2add7cbc6ccf4e7b02966a050c178675.png)

![img](https://img-blog.csdnimg.cn/img_convert/408eeec5cf31085be7d7e0321aa39b3d.png)

子类对象实例化的全过程



1.从结果上看:

 * 		子类继承父类以后，就获取了父类中声明的属性或方法。
 * 		创建子类的对象中，在堆空间中，就会加载所有父类中声明的属性。

 * 		2.从过程上看:
 * 		**当我们通过子类的构造器创建子类对象时,我们一定会直接或间接的调用其父类构造器，** **直到调用了java.lang.Object类中空参的构造器为止。正因为加载过所有的父类结构，所以才可以看到内存中有父类中的结构，子类对象可以考虑进行调用。**

 * 		明确:**虽然创建子类对象时，调用了父类的构造器，但自始至终就创建过一个对象，即为new的子类对象。**


### 6.面向对象特征之三：多态性

面向对象之三:多态性



 * 1.理解多态性:可以理解为一个事物的多种态性。
 * 2.何为多态性:
 * **对象的多态性:父类的引用指向子类的对象(或子类的对象赋值给父类的引用)**
 * 
 * 3.多态的使用：**虚拟方法调用**
 * 有了对象多态性以后，我们在编译期，只能调用父类声明的方法，但在执行期实际执行的是子类重写父类的方法
 * 简称：**编译时，看左边；运行时，看右边。**

 * 若编译时类型和运行时类型不一致，就出现了对象的多态性(Polymorphism)
 * 多态情况下，
 * **“看左边”：看的是父类的引用（父类中不具备子类特有的方法）**
 * **“看右边”：看的是子类的对象（实际运行的是子类重写父类的方法）**
 * 
 * 4.**多态性的使用前提：**
 * **① 类的继承关系**
 * **② 方法的重写**
 * **5.对象的多态性:只适用于方法，不适用于属性(编译和运行都看左边)**





person类：

```java
public class Person {
	String name;
	int age;
	
	public void eat(){
		System.out.println("人，吃饭");
	}
	
	public void walk(){
		System.out.println("人，走路");
	}
	
}
```

woman类：

```java
public class Woman extends Person{

	boolean isBeauty;
	
	public void goShopping(){
		System.out.println("女人喜欢购物");
	}
	
	public void eat(){
		System.out.println("女人少吃，为了减肥。");
	}
	
	public void walk(){
		System.out.println("女人，窈窕的走路。");
	}
}
```

man类：

```java
public class Man extends Person{
	
	boolean isSmoking;
	
	public void earnMoney(){
		System.out.println("男人负责工作养家");
	}
	
	public void eat() {
		System.out.println("男人多吃肉，长肌肉");
	}
	
	public void walk() {
		System.out.println("男人霸气的走路");
	}
}
```

测试类：

```java
public class PersonTest {
	public static void main(String[] args) {
		
	Person p1 = new Person();
	p1.eat();
	
	Man man = new Man();
	man.eat();
	man.age = 25;
	man.earnMoney();
	
	//************************************
	//对象的多态性，父类的引用指向子类的对象
	Person p2 = new Man();
//	Person p3 = new Woman();
	
	//多态的使用:当调用子父类同名同参数方法时，实际调用的是子类重写父类的方法---虚拟方法调用
	p2.eat();
	p2.walk();
	
//	p2.earnMoney();
	
	}
}
```

#### 1.虚拟方法的补充

从编译和运行的角度看：

 * 重载，是指允许存在多个同名方法，而这些方法的参数不同。

 * 编译器根据方法不同的参数表，对同名方法的名称做修饰。

 * 对于编译器而言，这些同名方法就成了不同的方法。

 * **它们的调用地址在编译期就绑定了。Java的重载是可以包括父类和子类的，**

 * **即子类可以重载父类的同名不同参数的方法。所以：对于重载而言，在方法调用之前，编译器就已经确定了所要调用的方法，这称为“早绑定”或“静态绑定”；**

 * **而对于多态，只有等到方法调用的那一刻，解释运行器才会确定所要调用的具体方法，**

   **这称为“晚绑定”或“动态绑定”。**

 * 引用一句Bruce Eckel的话：“不要犯傻，如果它不是晚绑定，它就不是多态。”






```java
import java.util.Random;
//面试题：多态是编译时行为还是运行时行为？
//证明如下：
class Animal  {
 
	protected void eat() {
		System.out.println("animal eat food");
	}
}

class Cat  extends Animal  {
 
	protected void eat() {
		System.out.println("cat eat fish");
	}
}

class Dog  extends Animal  {
 
	public void eat() {
		System.out.println("Dog eat bone");

	}

}

class Sheep  extends Animal  {
 
	public void eat() {
		System.out.println("Sheep eat grass");

	}
 
}

public class InterviewTest {

	public static Animal  getInstance(int key) {
		switch (key) {
		case 0:
			return new Cat ();
		case 1:
			return new Dog ();
		default:
			return new Sheep ();
		}

	}

	public static void main(String[] args) {
		int key = new Random().nextInt(3);

		System.out.println(key);

		Animal  animal = getInstance(key);
		
		animal.eat();
		 
	}

}
```

#### 2.向下转型的使用

  instanceof关键字的使用：

​     **a instanceof A:判断对象a是否是类A的实例。**如果，返回true，如果不是，返回false;

  使用情境:为了避免在向下转型时出现ClassCastException异常，我们在进行向下转型之前，先进行
 instanceof的判断,一旦返回true,就进行向下转型。如果返回false，不进行向下转型。

  **如果a instanceof A返回true,则a instanceof B也返回true。 其中类B是类A的父类。**

```java
public class PersonTest {
	public static void main(String[] args) {

		Person p1 = new Person();
		p1.eat();

		Man man = new Man();
		man.eat();
		man.age = 25;
		man.earnMoney();

		// ************************************
		System.out.println("************************");
		// 对象的多态性，父类的引用指向子类的对象
		Person p2 = new Man();
		// Person p3 = new Woman();

		// 多态的使用:当调用子父类同名同参数方法时，实际调用的是子类重写父类的方法---虚拟方法调用
		p2.eat();
		p2.walk();

		// p2.earnMoney();

		System.out.println("**************************");
		// 不能调用子类所特有的方法、属性，编译时，p2是Person类型，

		// p2.earnMoney();

		p2.name = "Tom";
		// p2.isSmoking = true;
		// 有了对象的多态性以后，内存中实际上是加载了子类特有的属性和方法，但是由于变量声明为父类类型，导致
		// 编译时，只能调用父类中声明的属性和方法。子类的属性和方法不能调用。

		// 如何才能调用子类所特有的属性和方法？
		// 使用强制类型转换符，也可称为:向下转型
		Man m1 = (Man) p2;
		m1.earnMoney();
		m1.isSmoking = true;

		// 使用强转时，可能出现ClassCastException异常
		// Woman w1 = (Woman)p2;
		// w1.goShopping();

		/*
		 * instanceof关键字的使用
		 * 
		 * a instanceof A:判断对象a是否是类A的实例。如果，返回true，如果不是，返回false;
		 * 
		 * 使用情境:为了避免在向下转型时出现ClassCastException异常，我们在进行向下转型之前，先进行
		 * instanceof的判断,一旦返回true,就进行向下转型。如果返回false，不进行向下转型。
		 * 
		 * 如果a instanceof A返回true,则a instanceof B也返回true。 其中类B是类A的父类。
		 * 
		 */

		if (p2 instanceof Woman) {
			Woman w1 = (Woman) p2;
			w1.goShopping();
			System.out.println("**********Woman*********");
		}

		if (p2 instanceof Man) {
			Man m2 = (Man) p2;
			m2.earnMoney();
			System.out.println("*********Man************");
		}

		if (p2 instanceof Person) {
			System.out.println("***********Person************");
		}

		if (p2 instanceof Object) {
			System.out.println("***********object************");
		}
		
		//向下转型的常见问题
		//练习
		//问题1:编译时通过，运行时不通过
		//举例一
//		Person p3 = new Woman();
//		Man m3 = (Man)p3;
		
		//举例二
		Person p4 = new Person();
		Man m4 = (Man)p4;
		
		//问题二:编译通过，运行时也通过
		Object obj = new Woman();
		Person p = (Person)obj;
		
		//问题三:编译不通过
//		Man m5 = new woman();
		
//		String str = new Date();
		
//		Object o = new Date();
//		String str1 = (String)o;
	}
}
```

![img](https://img-blog.csdnimg.cn/img_convert/c6dcce377d1fae98ba497cc11d3b4163.png)

#### 3.多态性的练习

练习1：

```java
/*
 * 练习:子类继承父类
 * 
 * 1.若子类重写了父类方法，就意味着子类里定义的方法彻底覆盖了父类里的同名方法，
 * 系统将不可能把父类里的方法转移到子类中。
 * 
 * 2.对于实例变量则不存在这样的现象，即使子类里定义了与父类完全相同的实例变量，
 * 这个实例变量依然不可能覆盖父类中定义的实例变量
 * 
 */
public class FieldMethodTest {
	public static void main(String[] args){
		Sub s= new Sub();
		System.out.println(s.count);	//20
		s.display();//20
		
		Base b = s;
		//==:对于引用数据类型来讲，比较的是两个引用数据类型变量的地址值是否一样。
		System.out.println(b == s);	//true
		System.out.println(b.count);	//10
		b.display();
	}
}

class Base {
	int count= 10;
	public void display() {
		System.out.println(this.count);
	}
}

class Sub extends Base {
	int count= 20;
	public void display() {
		System.out.println(this.count);
	}
}
```

练习2：

```java
/*
 * 建立InstanceTest 类，在类中定义方法method(Person e);
 * 
 * 在method中:
 * (1)根据e的类型调用相应类的getInfo()方法。
 * (2)根据e的类型执行：
 * 		如果e为Person类的对象，输出：“a person”;
 * 		如果e为Student类的对象，输出：“a student”“a person ”
 * 		如果e为Graduate类的对象，输出：“a graduated student”
 * 		“a student” “a person”
 * 
 */
class Person {
	protected String name = "person";
	protected int age = 50;


	public String getInfo() {
		return "Name: " + name + "\n" + "age: " + age;
	}
}

class Student extends Person {
	protected String school = "pku";

	public String getInfo() {
		return "Name: " + name + "\nage: " + age + "\nschool: " + school;
	}
}

class Graduate extends Student {
	public String major = "IT";

	public String getInfo() {
		return "Name: " + name + "\nage: " + age + "\nschool: " + school + "\nmajor:" + major;
	}
}


public class InstanceTest{
	
	public static void main(String[] args) {
		//虚拟方法调用
		InstanceTest test = new InstanceTest();
		test.method(new Student());
		
	}
	
	public void method(Person e){
		String info = e.getInfo();
		System.out.println(info);
		
		//方法一
		if(e instanceof Graduate){
			System.out.println("a graduated student");
			System.out.println("a student");
			System.out.println("a person");
		}else if(e instanceof Student){
			System.out.println("a student");
			System.out.println("a person");
		}else{
			System.out.println("a person");
		}
		
		//方法二
		if(e instanceof Graduate){
			System.out.println("a graduated student");
		}
		if(e instanceof Student){
			System.out.println("a student");
		}
		if(e instanceof Person){
			System.out.println("a person");
		}
	}
}
```

练习3：

```java
/*
 * 定义三个类，父类GeometricObject代表几何形状，子类Circle代表圆形，MyRectangle代表矩形。
 */
public class GeometricObject {
	protected String color;
	protected double weight;
	public String getColor() {
		return color;
	}
	public void setColor(String color) {
		this.color = color;
	}
	public double getWeight() {
		return weight;
	}
	public void setWeight(double weight) {
		this.weight = weight;
	}
	public GeometricObject(String color, double weight) {
		super();
		this.color = color;
		this.weight = weight;
	}
	
	public double findArea(){
		return 0.0;
	}
}

public class Circle extends GeometricObject {

	private double radius;
	
	public Circle(double weight,String color, double radius) {
		super(color,weight);
		this.radius = radius;
	}

	public double getRadius() {
		return radius;
	}

	public void setRadius(double radius) {
		this.radius = radius;
	}
	
	@Override
	public double findArea() {
		return 3.14 * radius * radius;
	}
}

public class MyRectangle extends GeometricObject {

	private double width;
	private double height;
	
	public MyRectangle(double width, double height,String color,double weight) {
		super(color, weight);
		this.height = height;
		this.width = width;
	}

	public double getWidth() {
		return width;
	}

	public void setWidth(double width) {
		this.width = width;
	}

	public double getHeight() {
		return height;
	}

	public void setHeight(double height) {
		this.height = height;
	}

	@Override
	public double findArea() {
		return width * height;
	}
}

/*
 * 定义一个测试类GeometricTest，编写equalsArea方法测试两个对象的面积是否相等（注意方法的参数类型，利用动态绑定技术），
 * 编写displayGeometricObject方法显示对象的面积（注意方法的参数类型，利用动态绑定技术）。
 * 
 */
public class GeometricTest {
	
	public static void main(String[] args) {
		GeometricTest test = new GeometricTest();
		
		Circle c1 = new Circle(2.3,"white",1.0);
		test.displayGeometricObject(c1);
		
		Circle c2 = new Circle(3.3,"white",1.0);
		test.displayGeometricObject(c2);
		
		boolean isEqual = test.equalsArea(c1, c2);
		System.out.println("面积是否相等: " + isEqual);
		
		MyRectangle rect = new MyRectangle(2.1, 3.4,"red",1.0);
		test.displayGeometricObject(rect);
	}
	
	public void displayGeometricObject(GeometricObject o){
		System.out.println("面积为: " + o.findArea());
	}
	
	//测试两个对象的面积是否相等
	public boolean equalsArea(GeometricObject o1,GeometricObject o2){
		return o1.findArea() == o2.findArea();
	}
}

```

#### 4.面试题拓展

```java
/* 考查多态的笔试题目：
 * 面试题：多态是编译时行为还是运行时行为？如何证明？
 * 
 * 拓展问题
 */
public class InterviewTest1 {

	public static void main(String[] args) {
		Base base = new Sub();
		base.add(1, 2, 3);

//		Sub s = (Sub)base;
//		s.add(1,2,3);
	}
}

class Base {
	public void add(int a, int... arr) {
		System.out.println("base");
	}
}

class Sub extends Base {

	public void add(int a, int[] arr) {
		System.out.println("sub_1");
	}

//	public void add(int a, int b, int c) {
//		System.out.println("sub_2");
//	}这样不是重写，不可以调用，附：如果可以调用两个重载的方法，其中一个是可变个数形参，另一个是确定个数形参，则优先调用确定个数形参的方法！

}

```

### 7.Object类的使用

java.lang.Object类

 	1.**Object类是所有Java类的根父类**;
 	
 	2**.如果在类的声明中未使用extends关键字指明其父类，默认父类为java.lang.Object类**

​	  3.Object类中的功能(属性、方法)就具有通用性。

属性:无

方法:equals() / toString() / getClass() / hashCode() / clone() /finalize()

wait() 、notify()、notifyAll()

​	4.**Object类只声明了一个空参的构造器**。

#### 1.Object类中的主要结构

![img](https://img-blog.csdnimg.cn/img_convert/d9de1281feb25f434a69f809adeb4a24.png)

#### 2.==操作符和equals方法

面试题: ==和equals的区别

一、回顾==的使用

 * == : 运算符

 * 1.可以使用在基本数据类型变量和引用数据类型变量中

 * 2.如果比较的是基本数据类型变量：比较两个变量保存的数据是否相等。(不一定类型要相同)

 * 如果比较的是引用数据类型变量：比较两个对象的地址值是否相同,即两个引用是否指向同一个对象实体

 * 补充: == 符号使用时，必须保证符号左右两边的变量类型一致。
   *

 * 二、equals()方法的使用

 * 1.是一个方法，而非运算符

 * 2.只能适用于引用数据类型。

 * 3.Object类中equals()的定义：

 * public boolean equals(Object obj){

 * return (this == obj);

   }

 * 说明：**Object类中定义的equals()和==的作用是相同的，比较两个对象的地址值是否相同，即两个引用是否指向同一个对象实体。**

 * 4.像String、Date、File、包装类等都重写了Object类中的equals()方法.

 * 两个引用的地址是否相同，而是比较两个对象的“实体内容”是否相同。

 * 5.通常情况下，我们自定义的类如果使用equals()的话，也通常是比较两个对象的"实体内容"是否相同。那么，我们

 * 就需要对Object类中的equals()进行重写。

 * 重写的原则:**比较两个对象的实体内容是否相同。**


    	
    		

```java
public class EqualsTest {
public static void main(String[] args) {
//基本数据类型
int i = 10;
int j = 10;
double d = 10.0;
System.out.println(i == j);	//true
System.out.println(i == d); //true
//		boolean b =true;
//		System.out.println(i == b);
char c = 10;
	System.out.println(i == c); //true
	
	char c1 = 'A';
	char c2 = 65;
	System.out.println(c1 == c2); //true
	
	//引用数据类型
	Customer cust1 = new Customer("Tom" ,21);
	Customer cust2 = new Customer("Tom" ,21);
	System.out.println(cust1 == cust2); //false
	
	String str1 = new String("BAT");
	String str2 = new String("BAT");
	System.out.println(str1 == str2); //false
	System.out.println("*************************");
	System.out.println(cust1.equals(cust2));	//false
	System.out.println(str1.equals(str2));	//true
	
	Date date1 = new Date(23432525324L);
	Date date2 = new Date(23432525324L);
	System.out.println(date1.equals(date2));	//true
}
}
	
```

```java
public class Customer {
	
	private String name;
	private int age;
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		this.age = age;
	}
	public Customer() {
		super();
	}
	public Customer(String name, int age) {
		super();
		this.name = name;
		this.age = age;
	}


	//自动生成的equals()
	@Override
	public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		Customer other = (Customer) obj;
		if (age != other.age)
			return false;
		if (name == null) {
			if (other.name != null)
				return false;
		} else if (!name.equals(other.name))
			return false;
		return true;
	}
	
	//重写原则，比较两个对象的实体内容(即name和age)是否相同
	//手动实现equals()的重写
//	@Override
//	public boolean equals(Object obj) {
//		
		System.out.println("Customer equals()....");
//		if(this == obj){
//			return true;
//		}
//		
//		if(obj instanceof Customer){
//			Customer cust = (Customer)obj;
//			//比较两个对象的属性是否都相同
			if(this.age == cust.age && this.name.equals(cust.name)){
				return true;
			}else{
				return false;
			}
//			
//			//或
//			return this.age == cust.age && this.name.equals(cust.name);
//		}
//		
//		return false;
//	}
		
}

```

##### 1.重写equals()方法的原则

对称性：如果x.equals(y)返回是“true”，那么y.equals(x)也应该返回是“true”。
自反性：x.equals(x)必须返回是“true”。
传递性：如果x.equals(y)返回是“true”，而且y.equals(z)返回是“true”，那么z.equals(x)也应该返回是“true”。
一致性：如果x.equals(y)返回是“true”，只要x和y内容一直不变，不管你重复x.equals(y)多少次，返回都是“true”。
任何情况下，x.equals(null)，永远返回是“false”；x.equals(和x不同类型的对象)永远返回是“false”。



练习1

```java
/*
 * .编写Order类，有int型的orderId，String型的orderName，
 * 相应的getter()和setter()方法，两个参数的构造器，重写父类的equals()方法：public booleanequals(Object obj)，
 * 并判断测试类中创建的两个对象是否相等。
 * 
 * 
 */
public class OrderTest {
	public static void main(String[] args) {
		Order order1 = new Order(1001,"AA");
		Order order2 = new Order(1001,"BB");
		
		System.out.println(order1.equals(order2));	//false
		
		Order order3 = new Order(1001,"BB");
		System.out.println(order2.equals(order3)); //true
	}
}

class Order{
	private int orderId;
	private String orderName;
	public int getOrderId() {
		return orderId;
	}
	public void setOrderId(int orderId) {
		this.orderId = orderId;
	}
	public String getOrderName() {
		return orderName;
	}
	public void setOrderName(String orderName) {
		this.orderName = orderName;
	}
	public Order(int orderId, String orderName) {
		super();
		this.orderId = orderId;
		this.orderName = orderName;
	}
	public boolean equals(Object obj){
		if(this == obj){			
			return true;
		}
		if(obj instanceof Order){
			Order order = (Order)obj;
			//正确的
			return this.orderId == order.orderId && this.orderName.equals(order.orderName);
			//错误的
//			return this.orderId == order.orderId && this.orderName == order.orderName;
		}
		return false;
	}
}

```

练习2：

```java
/*
 * 请根据以下代码自行定义能满足需要的MyDate类,在MyDate类中覆盖equals方法，
 * 使其判断当两个MyDate类型对象的年月日都相同时，结果为true，否则为false。
 * public boolean equals(Object o)
 */
public class MyDateTest {
	public static void main(String[] args) {
		MyDate m1= new MyDate(14, 3, 1976);
		MyDate m2= new MyDate(14, 3, 1976);
		if(m1== m2) {
			System.out.println("m1==m2");
		} else{
			System.out.println("m1!=m2"); // m1 != m2
		}
		
		if(m1.equals(m2)) {
			System.out.println("m1 is equal to m2");// m1 is equal to m2
		} else{
			System.out.println("m1 is not equal to m2");
		}
	}
}

class MyDate{
	private int day;
	private int month;
	private int year;
	
	public MyDate(int day, int month, int year) {
		super();
		this.day = day;
		this.month = month;
		this.year = year;
	}

	public int getDay() {
		return day;
	}

	public void setDay(int day) {
		this.day = day;
	}

	public int getMonth() {
		return month;
	}


	public void setMonth(int month) {
		this.month = month;
	}

	public int getYear() {
		return year;
	}

	public void setYear(int year) {
		this.year = year;
	}
	
	@Override
	public boolean equals(Object obj) {
		if(this == obj){
			return true;
		}
		if(obj instanceof MyDate){
			MyDate myDate = (MyDate)obj;
			return this.day == myDate.day && this.month == myDate.month &&
					this.year == myDate.year;
		}
		return false;
	}

//	@Override
//	public boolean equals(Object obj) {
//		if (this == obj)
//			return true;
//		if (obj == null)
//			return false;
//		if (getClass() != obj.getClass())
//			return false;
//		MyDate other = (MyDate) obj;
//		if (day != other.day)
//			return false;
//		if (month != other.month)
//			return false;
//		if (year != other.year)
//			return false;
//		return true;
//	}
		
}
```

#### 		3.toString()的应用

 * Object类中toString()的使用

   

 * 1.当我们输出一个引用对象时，实际上就是调用当前对象的toString()

 * 2.Object类中toString的定义方法

 * public String toString() {

 * return getClass().getName() + "@"+Integer.toHexString(hashCode());

 * }

   

 * 3.**像String、Date、File、包装类等都重写了Object类中的toString()方法**。

 * 使得在调用toString()时，返回"实体内容"信息.

 * 4.**自定义类如果重写toString()方法，当调用此方法时，返回对象的"实体内容"**.

  

  练习

  GeometricObject类

  ```java
public class GeometricObject {
	protected  String  color;
	protected  double  weight;
	
	public GeometricObject() {
		super();
		this.color = "white";
		this.weight = 1.0;
	}
	
	public GeometricObject(String color, double weight) {
		super();
		this.color = color;
		this.weight = weight;
	}

	public String getColor() {
		return color;
	}

	public void setColor(String color) {
		this.color = color;
	}

	public double getWeight() {
		return weight;
	}

	public void setWeight(double weight) {
		this.weight = weight;
	}
}
  ```

  circle类

  ```java
public class Circle extends GeometricObject{
	private double radius;

	public Circle() {	//初始化对象的color属性为“white”，weight属性为1.0，radius属性为1.0。
		super();	//super自带，不需再写
//		this.color = "white";
//		this.weight = 1.0;
		this.radius = 1.0;
	}

	//初始化对象的color属性为“white”，weight属性为1.0，radius根据参数构造器确定。
	public Circle(double radius) {	
		super();	//super自带，不需再写
//		this.color = "white";
//		this.weight = 1.0;
		this.radius = radius;
	}

	public Circle(double radius,String color,double weight) {
		super(color,weight);
		this.radius = radius;
	}
	
	public double getRadius() {
		return radius;
	}

	public void setRadius(double radius) {
		this.radius = radius;
	}

	//计算圆的面积
	public double findArea(){
		return Math.PI * radius * radius;
	}
	
	@Override	//重写equals方法,比较两个圆的半径是否相等，如相等，返回true。
	public boolean equals(Object obj) {
		if(this == obj){
			return true;
		}
		
		if(obj instanceof Circle){
			Circle c = (Circle)obj;
			return this.radius == c.radius;
		}
		
		return false;
	}

	@Override
	public String toString() {	//重写toString方法,输出圆的半径。
		return "Circle [radius=" + radius + "]";
	}
	
}
  ```

  测试类

  ```java
/*
 * 写一个测试类，创建两个Circle对象，判断其颜色是否相等；
 * 利用equals方法判断其半径是否相等；利用toString()方法输出其半径。
 * 
 */
public class CircleTest {
	public static void main(String[] args) {
		
		Circle circle1 = new Circle(2.3);
		Circle circle2 = new Circle(3.3,"white",2.0);
		
		System.out.println("颜色是否相等: " + circle1.getColor().equals(circle2.color));
		
		System.out.println("半径是否相等: " + circle1.equals(circle2));
		
		System.out.println(circle1);
		System.out.println(circle2.toString());
	}
}
  ```

  ### 8.包装类的使用

####   1.单元测试方法的使用

java中的JUnit单元测试

步骤:

 * 1.选中当前项目工程 --》 右键:build path --》 add libraries --》 JUnit 5--》 下一步
 * 2.创建一个Java类进行单元测试。
 * **此时的Java类要求:①此类是公共的 ②此类提供一个公共的无参构造器** 
 * 3.此类中声明单元测试方法。
 * 此时的单元测试方法:方法的权限是public,没有返回值，没有形参。
 * 
 * 4.**此单元测试方法上需要声明注解:@Test并在单元测试类中调用import org.junit.jupiter.api.Test**;
 * 5.声明好单元测试方法以后，就可以在方法体内测试代码。
 * 6.**写好代码后，左键双击单元测试方法名：右键 --》 run as --》 JUnit Test**

 * 说明:如果执行结果无错误，则显示是一个绿色进度条，反之，错误即为红色进度条。

```java
import java.util.Date;
import org.junit.Test;
public class JUnit {
	
	int num = 10;
	
	//第一个单元测试方法
	@Test
	public void testEquals(){
		String s1 = "MM";
		String s2 = "MM";
		System.out.println(s1.equals(s2));
		
		//ClassCastException的异常
//		Object obj = new String("GG");
//		Date date = (Date)obj;
		
		System.out.println(num);
		show();
	}
	
	public void show(){
		num = 20;
		System.out.println("show()...");
	}
	
	//第二个单元测试方法
	@Test
	public void testToString(){
		String s2 = "MM";
		System.out.println(s2.toString());
	}
}
```

#### 2.包装类的使用

包装类的使用

 * 1.java提供了8种基本数据类型对应的包装类，使得基本数据类型的变量具有类的特征

 * 基本数据类型		包装类

 * byte			Byte

 * short			Short

 * int 			Integer

 * long			Long

 * float			Float

 * double			Double

 * boolean			Boolean

 * char			Character

 * 注意:**其中Byte、Short、Integer、Long、Float、Double的父类是:Number**

   

#### 3.包装类与基本数据类型的互换

![img](https://img-blog.csdnimg.cn/img_convert/fa0116bbaf03d264cc9650a3319da2a8.png)

```java
import org.junit.Test;
/*
 * 2.基本数据类型、包装类、String三者之间的相互转换。
 * 
 */
public class WrapperTest {
	
	//String类型---> 基本数据类型、包装类,调用包装类的parseXxx()
	@Test
	public void test5(){
		String str1 = "123";
//		String str1 = "123a";
		
		//错误的情况，可能会报错
//		int num1 = (int)str1;
//		Integer in1 = (Integer)str1;
		
		int num2 = Integer.parseInt(str1); 
		System.out.println(num2 + 1);	//124
		
		String str2 = "true";
		Boolean b1 = Boolean.parseBoolean(str2);
		System.out.println(b1);	//true
        //注意：只要是非true的内容均会识别为false！
		
	}
	
	//基本数据类型、包装类---》String类型，调用String重载的valueOf(Xxx xxx)
	@Test
	public void test4(){
		int num1 = 10;
		//方式1:连接运算
		String str1 = num1 + "";
		//方式2:调用String的valueOf(Xxx xxx)
		float f1 = 12.3f;
		String str2 = String.valueOf(f1); //"12.3"
		
		Double d1 = new Double(12.4);
		String str3 = String.valueOf(d1);
		System.out.println(str2);
		System.out.println(str3);	//"12.4"
		
	}
	
	/*
	 * JDK 5.0 新特性:自动装箱与自动拆箱
	 */
	@Test
	public void test3(){
//		int num1 = 10;
//		//基本数据类型 --》 包装类的对象
//		method(num1);	//Object obj = num1
		
		//自动装箱:基本数据类型 --》 包装类
		int num2 = 10;
		Integer in1 = num2;//自动装箱
		
		boolean b1 = true;
		Boolean b2 = b1;//自动装箱
		
		//自动拆箱：包装类 --》 基本数据类型
		System.out.println(in1.toString());
		
		int num3 = in1;
		
	}
	
	public void method(Object obj){
		System.out.println(obj);
	}
	
	//包装类 --》 基本数据类型:调用包装类的xxxValue()
	@Test
	public void test2() {
		Integer in1 = new Integer(12);
		int i1 = in1.intValue();
		System.out.println(i1 + 1); 
		
		Float f1 = new Float(12.3f);
		float f2 = f1.floatValue();
		System.out.println(f2 + 1); 
	}
	
	//基本数据类型--》包装类,调用包装类的构造器
	@Test
	public void test1() {
		int num1 = 10;
//		System.out.println(num1.toString());
		
		Integer in1 = new Integer(num1);
		System.out.println(in1.toString());
		
		Integer in2 = new Integer("123");
		System.out.println(in2.toString());
		
		//报异常
//		Integer in3 = new Integer("123abc");
//		System.out.println(in3.toString());
		
		Float f1 = new Float(12.3f);
		Float f2 = new Float("12.3");
		System.out.println(f1);
		System.out.println(f2);
		
		Boolean b1 = new Boolean(true);
		Boolean b2 = new Boolean("true");
		
		Boolean b3 = new Boolean("true123");
		System.out.println(b3); //false
		
		Order order = new Order();
		System.out.println(order.isMale); //false
		System.out.println(order.isFemale); //null
		
	}
}

class Order{
	
	boolean isMale;
	Boolean isFemale;
}
```

#### 4.练习

1.面试题

```java
import org.junit.Test;
/*
 * 如下两个题目输出结果相同吗？各是什么：
 * 		Object o1= true? new Integer(1) : new Double(2.0);
 * 		System.out.println(o1);//
 * 
 * 		Object o2;
 * 		if(true)
 * 			o2 = new Integer(1);
 *		else 
 *			o2 = new Double(2.0);
 *		System.out.println(o2);//
 *
 */
public class InterViewTest {

	@Test
	public void test(){
		Object o1= true? new Integer(1) : new Double(2.0);
		System.out.println(o1);// 1.0（三元运算符自动类型提升！）
	}
	
	@Test
	public void test2(){
		Object o2;
		if(true)
			o2 = new Integer(1);
		else 
			o2 = new Double(2.0);
		System.out.println(o2);// 1
	}
	
	@Test
	public void method1() {
		Integer i = new Integer(1);
		Integer j = new Integer(1);
		System.out.println(i == j); //false
		
	    //Integer内部定义了一个IntegerCache结构，IntegerCache中定义Integer[]
		//保存了从-128-127范围的整数。如果我们使用自动装箱的方式，给Integer赋值的范围在其中时，
		//可以直接使用数组中的元素，不用再去new了。目的，提高效率。
		
		Integer m = 1;
		Integer n = 1;
		System.out.println(m == n);//true
		
		Integer x = 128;//相当于new了一个Integer对象
		Integer y = 128;//相当于new了一个Integer对象
		System.out.println(x == y);//false

	}
}

```

2.编程题

![img](https://img-blog.csdnimg.cn/img_convert/c80ea8669572b20379dbbd018fadb155.png)

```java
import java.util.Scanner;
import java.util.Vector;

/*
 * 利用Vector代替数组处理：从键盘读入学生成绩（以负数代表输入结束），
 * 找出最高分，并输出学生成绩等级。
 * 
 * 提示：数组一旦创建，长度就固定不变，所以在创建数组前就需要知道它的长度。
 * 而向量类java.util.Vector可以根据需要动态伸缩。
 * 
 * 创建Vector对象：Vector v=new Vector();
 * 给向量添加元素：v.addElement(Object obj);   //obj必须是对象
 * 取出向量中的元素：Object  obj=v.elementAt(0);
 * 注意第一个元素的下标是0，返回值是Object类型的。
 * 计算向量的长度：v.size();
 * 若与最高分相差
 * 		10分内：A等；
 * 		20分内：B等；
 * 		30分内：C等；
 * 		其它：D等
 * 
 */
public class VectorTest {
	public static void main(String[] args) {
		// 1.实例化Scanner，用于从键盘获取学生成绩
		Scanner scan = new Scanner(System.in);

		// 2.创建Vector对象：Vector v=new Vector();相当于原来的数组
		Vector v = new Vector();

		// 3.通过for(;;)或while(true)方式，给Vector中添加数组
		int maxScore = 0;
		for (;;) {
			System.out.println("请输入学生成绩（以负数代表输入结束）");
			int score = scan.nextInt();
			// 3.2 当输入是负数时，跳出循环
			if (score < 0) {
				break;
			}
			if (score > 100) {
				System.out.println("输入的数据非法，请重新输入");
				continue;
			}
			// 3.1 添加操作：：v.addElement(Object obj)
			// jdk5.0之前：
			// Integer inScore = new Integer(score);
			// v.addElement(inScore);//多态
			// jdk5.0之后：
			v.addElement(score);// 自动装箱
			// 4.获取学生成绩的最大值
			if (maxScore < score) {
				maxScore = score;
			}
		}

		// 5.遍历Vector，得到每个学生的成绩，并与最大成绩比较，得到每个学生的等级。
		char level;
		for (int i = 0; i < v.size(); i++) {
			Object obj = v.elementAt(i);
			// jdk 5.0之前：
			// Integer inScore = (Integer)obj;
			// int score = inScore.intValue();
			// jdk 5.0之后：
			int score = (int) obj;

			if (maxScore - score <= 10) {
				level = 'A';
			} else if (maxScore - score <= 20) {
				level = 'B';
			} else if (maxScore - score <= 30) {
				level = 'C';
			} else {
				level = 'D';
			}

			System.out.println("student-" + i + " score is " + score + ",level is " + level);

		}
	}
}
```

## 10.面向对象(下)

### 1.关键字：static

#### 1-1. static的使用

当我们编写一个类时，其实就是在描述其对象的属性和行为，而并没有产生实质上的对象，只有通过 new 关键字才会产生出对象，这时系统才会分配内存空间给对象，其方法才可以供外部调用。

我们有时候希望无论是否产生了对象或无论产生了多少对象的情况下，某些特定的数据在内存空间里只有一份。

例如所有的中国人都有个国家名称，每一个中国人都共享这个国家名称，不必在每一个中国人的实例对象中都单独分配一个用于代表国家名称的变量。
![img](https://img-blog.csdnimg.cn/img_convert/2057c0097587294fd28906287961f445.png)

static 关键字的使用



1. static:静态的。

2. static 可以用来修饰:**属性、方法、代码块、内部类**。

3. 使用 static 修饰属性:静态变量(或类变量)。

3.1  属性:是否使用 static 修饰，又分为:静态属性 VS 非静态属性(实例变量)

实例变量:**我们创建了类的多个对象，每个对象都独立的拥有了一套类中的非静态属性。当修改其中一个非静态属性时，不会导致其他对象中同样的属性值的修饰**。

静态变量:**我们创建了类的多个对象，多个对象共享同一个静态变量。当通过静态变量去修改某一个变量时，会导致其他对象调用此静态变量时，是修改过的**。

3.2 static 修饰属性的其他说明:

① 静态变量随着类的加载而加载。可以通过"**类.静态变量**"的方式进行调用。

② 静态变量的加载要早于对象的创建。

③ 由于类只会加载一次，则静态变量在内存中也只会存在一次。存在方法区的**静态域**中。

④ 		类变量		实例变量

类		yes			no

对象		yes			yes

3.3 静态属性举例:System.out.Math.PI;

```java
public class StaticTest {
	public static void main(String[] args) {
		
		Chinese.nation = "中国";
		
		Chinese c1 = new Chinese();
		c1.name = "姚明";
		c1.age = 40;
		c1.nation = "CHN";
		
		Chinese c2 = new Chinese();
		c2.name = "马龙";
		c2.age = 30;
		c2.nation = "CHINA";
		
		System.out.println(c1.nation); 
		
		//编译不通过
//		Chinese.name = "张继科";
		
	}
}
//中国人
class Chinese{
	
	String name;
	int age;
	static String nation;
}
```

#### 1-2类变量vs实例变量内存解析

![img](https://img-blog.csdnimg.cn/img_convert/97cc52e6668ddb59b0a2fc1d63b99607.png)

#### 1-3 static修饰方法

4.使用 static 修饰方法:静态方法

​    ① 随着类的加载而加载，可以通过"类.静态方法"的方式调用

​    ②  			静态方法		非静态方法

​               类		yes			no

​            对象		yes			yes

③ 静态方法中，只能调用静态的方法或属性

非静态的方法中，可以调用所有的方法或属性

5. static 注意点:

5.1  在静态的方法内，不能使用 this 关键字、super 关键字

5.2 关于静态属性和静态方法的使用，大家从**生命周期**的角度去理解。

6.开发中，如何确定一个属性是否需要声明 static 的？

》 属性是可以被多个对象所共享的，不会随着对象的不同而不同的。

》 **类中的常量也常常声明为 static**

开发中，如何确定一个方法是否要声明为 static 的？

》 **操作静态属性的方法，通常设置为 static 的**

》 **工具类中的方法，习惯上声明为 static 的**。比如：Math、Arrays、Collections

```java
public class StaticTest {
	public static void main(String[] args) {
		
		Chinese.nation = "中国";
		
		Chinese c1 = new Chinese();
		
		//编译不通过
//		Chinese.name = "张继科";
		
		c1.eat();
		
		Chinese.show();
		//编译不通过
//		chinese.eat();
//		Chinese.info();
	}
}
//中国人
class Chinese{
	
	String name;
	int age;
	static String nation;
	
	public void eat(){
		System.out.println("中国人吃中餐");
		//调用非静态结构
		this.info();
		System.out.println("name : " + name);
		//调用静态结构
		walk();
		System.out.println("nation : " + Chinese.nation);
	}
	
	public static void show(){
		System.out.println("我是一个中国人！");
//		eat();
//		name = "Tom";
		//可以调用静态的结构
		System.out.println(Chinese.nation);
		walk();
	}
	
	public void info(){
		System.out.println("name : " + name + ",age : " + age);
	}
	
	public static void walk(){
		
	}
}
```

#### 1-4自定义ArrayUtil的优化

```java
/*
 * 自定义数组工具类
 */
public class ArrayUtil {

	// 求数组的最大值
	public static int getMax(int[] arr) {
		int maxValue = arr[0];
		for (int i = 1; i < arr.length; i++) {
			if (maxValue < arr[i]) {
				maxValue = arr[i];
			}
		}
		return maxValue;
	}

	// 求数组的最小值
	public static int getMin(int[] arr) {
		int minValue = arr[0];
		for (int i = 1; i < arr.length; i++) {
			if (minValue > arr[i]) {
				minValue = arr[i];
			}
		}
		return minValue;
	}

	// 求数组总和
	public static int getSum(int[] arr) {
		int sum = 0;
		for (int i = 0; i < arr.length; i++) {
			sum += arr[i];
		}
		return sum;
	}

	// 求数组平均值
	public static int getAvg(int[] arr) {
		int avgValue = getSum(arr) / arr.length;
		return avgValue;
	}

	//如下两个同名方法构成重载
	// 反转数组
	public static void reverse(int[] arr) {
		for (int i = 0; i < arr.length / 2; i++) {
			int temp = arr[i];
			arr[i] = arr[arr.length - i - 1];
			arr[arr.length - i - 1] = temp;
		}
	}
	
	public void reverse(String[] arr){
		
	}

	// 复制数组
	public static int[] copy(int[] arr) {
		int[] arr1 = new int[arr.length];
		for (int i = 0; i < arr1.length; i++) {
			arr1[i] = arr[i];
		}
		return null;
	}

	// 数组排序
	public static void sort(int[] arr) {
		for (int i = 0; i < arr.length - 1; i++) {
			for (int j = 0; j < arr.length - 1 - i; j++) {
				if (arr[j] > arr[j + 1]) {
//					int temp = arr[j];
//					arr[j] = arr[j + 1];
//					arr[j + 1] = temp;
					//错误的：
//					swap(arr[j],arr[j+1]);
					
					swap(arr,j ,j+1);
				}
			}
		}
	}
	
	//错误的:交换数组中两个指定位置元素的值
//	public void swap(int i,int j){
//		int temp = i;
//		i = j;
//		j = temp;
//	}
	
	//正确的：
	private static void swap(int[] arr,int i,int j){
		int temp = arr[i];
		arr[i] = arr[j];
		arr[j] = temp;
	}

	// 遍历数组
	public static void print(int[] arr) {
		System.out.print("[");
		for (int i = 0; i < arr.length; i++) {
			System.out.print(arr[i] + ",");
		}
		System.out.println("]");
	}

	// 查找指定元素
	public static int getIndex(int[] arr, int dest) {
		//线性查找
		for (int i = 0; i < arr.length; i++) {

			if (dest==arr[i]) {
				return i;
			}

		}
		return -1;
	}

}
```

测试类：

```java
public class ArrayUtilTest {

	public static void main(String[] args) {
//		ArrayUtil util = new ArrayUtil();
		int[] arr = new int[]{32,5,26,74,0,96,14,-98,25};
		int max = ArrayUtil.getMax(arr);
		System.out.println("最大值为:" + max);
		
		System.out.print("排序前:");
		ArrayUtil.print(arr);
		
		ArrayUtil.sort(arr);
		System.out.print("排序后:");
		ArrayUtil.print(arr);
		
//		System.out.println("查找:");
//		int index = util.getIndex(arr, 5);
//		if(index > 0){
//			System.out.println("找到了，索引地址:" + index);
//		}else{
//			System.out.println("没找到");
//		}
	}
}
```

#### 1-5 static的应用举例

```java
//static 关键字的应用
public class CircleTest {
	public static void main(String[] args) {
		
		Circle c1 = new Circle();
		
		Circle c2 = new Circle();
		
		Circle c3 = new Circle();
		
		System.out.println("c1 的 ID:" + c1.getId());
		System.out.println("c2 的 ID:" + c2.getId());
		System.out.println("c3 的 ID:" + c3.getId());
		
		System.out.println("创建圆的个数: " + Circle.getTotal());
		
	}
	
}

class Circle{
	
	private double radius;
	private int id;	//需要自动赋值
	
	public Circle(){
		id = init++;
		total++;
	}
	
	public Circle(double radius){
		this();
		//或
//		id = init++;
//		total++;
		this.radius = radius;
	}
	
	private static int total;//记录创建圆的个数
	private static int init = 1001;//static 声明的属性被所有对象所共享
	
	public double findArea(){
		return 3.14 * radius * radius;
	}

	public double getRadius() {
		return radius;
	}

	public void setRadius(double radius) {
		this.radius = radius;
	}

	public int getId() {
		return id;
	}

	public static int getTotal() {
		return total;
	}
	
}
```

#### 1-6  static的练习



```java
/*
 * 编写一个类实现银行账户的概念，包含的属性有“帐号”、“密码”、“存款余额”、
 * “利率”、“最小余额”，定义封装这些属性的方法。
 * 账号要自动生成。编写主类，使用银行账户类，输入、输出 3 个储户的上述信息。
 * 考虑：哪些属性可以设计成 static 属性。
 * 
 */
public class Account {
	
	private int id;	//账号
	private String pwd = "000000";	//密码
	private double balance; //存款余额
	
	private static double interestRate; //利率
	private static double minMoney = 1.0;  //最小余额
	private static int init = 1001;	//用于自动生成 id
	
	public Account(){	//账号自动生成
		id = init++;
	}
	
	public Account(String pwd,double balance){
		id = init++;
		this.pwd = pwd;
		this.balance = balance;
	}
	
	public String getPwd() {
		return pwd;
	}
	
	public void setPwd(String pwd) {
		this.pwd = pwd;
	}
	
	public static double getInterestRate() {
		return interestRate;
	}
	
	public static void setInterestRate(double interestRate) {
		Account.interestRate = interestRate;
	}
	
	public static double getMinMoney() {
		return minMoney;
	}
	
	public static void setMinMoney(double minMoney) {
		Account.minMoney = minMoney;
	}
	
	public int getId() {
		return id;
	}
	
	public double getBalance() {
		return balance;
	}

	@Override
	public String toString() {
		return "Account [id=" + id + ", pwd=" + pwd + ", balance=" + balance + "]";
	}
	
}
```

测试类：

```java
public class AccountTest {
	public static void main(String[] args) {
		
		Account acct1 = new Account();
		Account acct2 = new Account("qwerty",2000);
		
		Account.setInterestRate(0.012); 
		Account.setMinMoney(100);
		
		System.out.println(acct1);
		System.out.println(acct2);
		
		System.out.println(acct1.getInterestRate()); 
		System.out.println(acct1.getMinMoney());
	}
}
```

#### 1-7 单例（Singleton）设计模式

设计模式是**在大量的实践中总结和理论化之后优选的代码结构、编程风格、以及解决问题的思考方式。**设计模免去我们自己再思考和摸索。就像是经典的棋谱，不同的棋局，我们用不同的棋谱。”套路”

所谓类的单例设计模式，就是采取一定的方法保证在整个的软件系统中，对**某个类只能存在一个对象实例**。并且该类**只提供一个取得其对象实例的方法**。如果我们要让类在一个虚拟机中只能产生一个对象，我们首先必须将**类的构造器的访问权限设置为 private**，这样，就不能用 new 操作符在类的外部产生类的对象了，但在类内部仍可以产生该类的对象。因为在类的外部开始还无法得到类的对象，**只能调用该类的某个静态方法以返回类内部创建的对象，静态方法只能访问类中的静态成员变量，所以，指向类内部产生的该类对象的变量也必须定义成静态的。**



单例设计模式:

​	1.所谓类的单例设计模式，就是采取一定的方法保证在整个的软件系统中，对**某个类只能存在一个对象实例**

​	2.如何实现？

​           饿汉式	VS	懒汉式

​	3.区分饿汉式和懒汉式。

饿汉式：  坏处:**对象加载时间过长**。

​				好处:饿汉式是**线程安全**的。

懒汉式：   好处:**延迟对象的创建**。

​                 坏处:目前的写法，会**线程不安全**。---》到多线程内容时，再修改

##### 7-1 单例模式的饿汉式

```java
public class SingletonTest {
	public static void main(String[] args) {
//		Bank bank1 = new Bank(); 
//		Bank bank2 = new Bank(); 
		
		Bank bank1 = Bank.getInstance();
		Bank bank2 = Bank.getInstance();
		
		System.out.println(bank1 == bank2);
		
	}
}

//单例的饿汉式
class Bank{
	
	//1.私有化类的构造器
	private Bank(){
		
	}
	
	//2.内部创见类的对象
	//4.要求此对象也必须声明为静态的
	private static Bank instance = new Bank();
	
	//3.提供公共的静态的方法，返回类的对象。
	public static Bank getInstance(){
		return instance;
	}
}
```

##### 7-2单例模式的懒汉式

```java
/*
 * 单例的懒汉式实现
 * 
 */
public class SingletonTest2 {
	public static void main(String[] args) {
		
		Order order1 = Order.getInstance();
		Order order2 = Order.getInstance();
		
		System.out.println(order1 == order2);
	}
}
class Order{
	//1.私有化类的构造器
	private Order(){
		
	}
	
	//2.声明当前类对象，没有初始化。
	//此对象也必须声明为 static 的
	private static Order instance = null;
	
	//3.声明 public、static 的返回当前类对象的方法
	public static Order getInstance(){
		if(instance == null){
			instance = new Order();			
		}
		return instance;
	}
}
```

##### 7-3单例模式的优点

由于单例模式只生成一个实例，**减少了系统性能开销**，当一个对象的产生需要比较多的资源时，如读取配置、产生其他依赖对象时，则可以通过在应用启动时直接产生一个单例对象，然后永久驻留内存的方式来解决。

![img](https://img-blog.csdnimg.cn/img_convert/5b12c0fa376f3b691fe7b660b1d73baf.png)

##### 7-4单例设计模式的应用场景

 **网站的计数器**，一般也是单例模式实现，否则难以同步。
**应用程序的日志应用**，一般都使用单例模式实现，这一般是由于共享的日志文件一直处于打开状态，因为只能有一个实例去操作，否则内容不好追加。
**数据库连接池**的设计一般也是采用单例模式，因为数据库连接是一种数据库资源。
项目中，**读取配置文件的类**，一般也只有一个对象。没有必要每次使用配置文件数据，都生成一个对象去读取。
Application也是单例的典型应用
Windows 的 **Task Manager (任务管理器)**就是很典型的单例模式
Windows 的 **Recycle Bin(回收站)**也是典型的单例应用。在整个系统运行过程中，回收站一直维护着仅有的一个实例。

### 2.理解main方法的语法

由于 Java 虚拟机需要调用类的 main()方法，所以该方法的访问权限必须是 public，又因为 Java 虚拟机在执行 main()方法时不必创建对象，所以该方法必须是 static 的，该方法接收一个 String 类型的数组参数，该数组中保存执行 Java 命令时传递给所运行的类的参数。

又因为 main() 方法是静态的，我们不能直接访问该类中的非静态成员，必须创建该类的一个实例对象后，才能通过这个对象去访问类中的非静态成员，这种情况，我们在之前的例子中多次碰到。

```java
/*
 * main()方法的使用说明
 * 1.main()方法作为程序的入口;
 * 2.main()方法也是一个普通的静态方法
 * 3.main()方法也可以作为我们与控制台交互的方式。(之前，使用 Scanner)
 * 
 * 
 */
public class MainTest {
	public static void main(String[] args) {	//入口
		
		Main.main(new String[100]);
		
		MainTest test = new MainTest();
		test.show();
	}
	
	public void show(){
		
	}
}

class Main{
	public static void main(String[] args) {
		args = new String[100];
		for(int i = 0;i < args.length;i++){
			args[i] = "args_" + i;
			System.out.println(args[i]);
		}
	}
}
```

命令行参数用法举例

```java
public class MainDemo {
	public static void main(String[] args) {
		
		for(int i = 0;i < args.length;i++){
			System.out.println("/*/*/*/"+ args[i]);
		}	
	}
}

```

运行过程

```java
javac MainDemo.java
java MainDemo “Tom” “Jerry” “Shkstart”
```

![img](https://img-blog.csdnimg.cn/img_convert/433e2dc60420147446a1954fc80dff97.png)

### 3.类的成员之四：代码块

 * 类的成员之四:代码块（或初始化块）

 * 1.代码块的作用：**用来初始化类、对象的**

 * 2.代码块如果有修饰的话，**只能使用 static**

 * 3.分类:静态代码块 vs 非静态代码块

 * 4.静态代码块

 * 》内部可以有输出语句

 * 》随着类的加载而执行,而且**只执行一次**

 * 》作用:初始化类的信息

 * 》如果一个类中，定义了多个静态代码块，则**按照声明的先后顺序执行**

 * 》静态代码块的执行，优先于非静态代码块的执行

 * 》**静态代码块内只能调用静态的属性、静态的方法，不能调用非静态的结构**

 * 5.非静态代码块

 * >内部可以有输出语句

 * >随着对象的创建而执行

 * >**每创建一个对象，就执行一次非静态代码块**。

 * >作用:**可以在创建对象时，对对象的属性等进行初始化**。

 * >如果一个类中，定义了多个非静态代码块，则**按照声明的先后顺序执行**

 * >**非静态代码块内可以调用静态的属性、静态的方法，或非静态的属性、非静态的方法。**

 * 对属性可以赋值的位置:

 * ①默认初始化

 * ②显式初始化

 * ③构造器中初始化

 * ④有了对象以后，可以通过"对象.属性"或"对象.方法"的方式，进行赋值。

 * ⑤在代码块中赋值


```java
public class BlockTest {
	public static void main(String[] args) {
		
		String desc = Person.desc;
		System.out.println(desc);
		
		Person p1 = new Person();
		Person p2 = new Person();
		System.out.println(p1.age);
		
		Person.info();
	}
}

class Person{
	//属性
	String name;
	int age;
	static String desc = "我是一个青年";
	
	//构造器
	public Person(){
		
	}
	
	//static 的代码块
	static{
		System.out.println("hello,static block-1");
		//调用静态结构
		desc = "我是一个爱小说的人";
		info();
		//不能调用非静态结构
//		eat();
//		name = "Tom";
	}
	
	static{
		System.out.println("hello,static block-2");
	}
	
	//非 static 的代码块
	{
		System.out.println("hello,block-2");
	}
	{
		System.out.println("hello,block-1");
		//调用非静态结构
		age = 1;
		eat();
		//调用静态结构
		desc = "我是一个爱小说的人 1";
		info();
	}	
	
	//方法
	public Person(String name,int age){
		this.name = name;
		this.age = age;
	}
	
	public void eat(){
		System.out.println("吃饭");
	}

	@Override
	public String toString() {
		return "Person [name=" + name + ", age=" + age + "]";
	}
	public static void info(){
		System.out.println("我是一个快乐的人。");
	}
	
}
```

举例1：

```java
//总结:由父类到子类，静态先行
class Root{
	static{
		System.out.println("Root 的静态初始化块");
	}
	{
		System.out.println("Root 的普通初始化块");
	}
	public Root(){
		System.out.println("Root 的无参数的构造器");
	}
}
class Mid extends Root{
	static{
		System.out.println("Mid 的静态初始化块");
	}
	{
		System.out.println("Mid 的普通初始化块");
	}
	public Mid(){
		System.out.println("Mid 的无参数的构造器");
	}
	public Mid(String msg){
		//通过 this 调用同一类中重载的构造器
		this();
		System.out.println("Mid 的带参数构造器，其参数值："
			+ msg);
	}
}
class Leaf extends Mid{
	static{
		System.out.println("Leaf 的静态初始化块");
	}
	{
		System.out.println("Leaf 的普通初始化块");
	}	
	public Leaf(){
		//通过 super 调用父类中有一个字符串参数的构造器
		super("尚硅谷");
		System.out.println("Leaf 的构造器");
	}
}
public class LeafTest{
	public static void main(String[] args){
		new Leaf(); 
		//new Leaf();
	}
}
```

举例2：

```java
class Father {
	static {
		System.out.println("11111111111");
	}
	{
		System.out.println("22222222222");
	}

	public Father() {
		System.out.println("33333333333");

	}

}

public class Son extends Father {
	static {
		System.out.println("44444444444");
	}
	{
		System.out.println("55555555555");
	}
	public Son() {
		System.out.println("66666666666");
	}

	public static void main(String[] args) { // 由父及子 静态先行
		System.out.println("77777777777");
		System.out.println("************************");
		new Son();
		System.out.println("************************");

		new Son();
		System.out.println("************************");
		new Father();
	}

}
```

属性赋值的执行顺序

![img](https://img-blog.csdnimg.cn/img_convert/35c39171e6d8d7a2a25bd0c9edd48ee9.png)



```java
/*
 * 对属性可以赋值的位置:
 *  ①默认初始化
 *  ②显式初始化 / ⑤在代码块中赋值
 *  ③构造器中初始化
 *  ④有了对象以后，可以通过"对象.属性"或"对象.方法"的方式，进行赋值。
 *  
 *  执行的先后顺序:① - ② / ⑤ - ③ - ④
 */
public class OrderTest {
	public static void main(String[] args) {
		Order order = new Order();
		System.out.println(order.orderId);
	}
}
class Order{
	
	int orderId = 3;
	{
		orderId = 4;
	}
	
}
```

### 4.关键字：final


 * final:最终的

 * 1. final可以用来修饰的结构:**类、方法、变量**

 * 2. final用来修饰一个**类:此类不能被其他类所继承**。**
 * 比如:String类、System类、StringBuffer类
 * 3. final修饰一个**方法:final标记的方法不能被子类重写**。
 * 比如：Object类中的getClass()。 
 * 4. final用来修饰变量:**此时的"变量"(成员变量或局部变量)就是一个常量。名称大写，且只能被赋值一次**。
 * 4.1 final修饰属性，可以考虑赋值的位置有**:显式初始化、代码块中初始化、构造器中初始化**
 * 4.2 final修饰局部变量:
 * 尤其是使用final修饰形参时，**表明此形参是一个常量。当我们调用此方法时，给常量形参赋一个实参一旦赋值以后，就只能在方法体内使用此形参，但不能进行重新赋值。**

 * static final 用来修饰:**全局常量**


```java
public class FinalTest {
	
	final int WIDTH = 0;
	final int LEFT;
	final int RIGHT;
//	final int DOWN;
	
	{
		LEFT = 1;
	}
	
	public FinalTest(){
		RIGHT = 2;
	}
	
	public FinalTest(int n){
		RIGHT = n;
	}
	
//	public void setDown(int down){
//		this.DOWN = down;
//	}
	
	public void dowidth(){
//		width = 20;	//width cannot be resolved to a variable
	}
	
	public void show(){
		final int NUM = 10;	//常量
//		num += 20;
	}
	
	public void show(final int num){
		System.out.println(num);
	}
	
	public static void main(String[] args) {
		
		int num = 10;
		
		num = num + 5;
		
		FinalTest test = new FinalTest();
//		test.setDown(5);
		
		test.show(10);
	}
}

final class FianlA{
	
}

//class B extends FinalA{     //错误，不能被继承。
//	
//}

//class C extends String{
//	
//}

class AA{
	public final void show(){
		
	}
}

//class BB extends AA{	// 错误，不能被重写。
//	public void show(){
//		
//	}
//}
```

面试题1：

```java
public class Something {
	public int addOne(final int x) {
		return ++x; // return x + 1;
	}
}
```

面试题2：

```java
public class Something {

	public static void main(String[] args) {
		Other o = new Other();
		new Something().addOne(o);
	}

	public void addOne(final Other o) {
		// o = new Other();
		o.i++;
	}
}

class Other {
	public int i;
}
```

### 5.抽象类与抽象方法

​        随着继承层次中一个个新子类的定义，类变得越来越具体，而父类则更一般，更通用。类的设计应该保证父类和子类能够共享特征。有时将一个父类设计得非常抽象，以至于它没有具体的实例，这样的类叫做**抽象类**。

![img](https://img-blog.csdnimg.cn/img_convert/367a5bc4e1045fec15a665827ad1a665.png)

/*

 * abstract 关键字的使用

 * 

 * 1.abstract:抽象的

 * 2.abstract 可以用来修饰的结构:类、方法

 * 3.abstract 修饰类:抽象类

 * 》 **此类不能实例化**

 * 》 **抽象类中一定有构造器，便于子类实例化时调用**(涉及:子类对象实例化全过程)

 * 》 **开发中，都会提供抽象类的子类，让子类对象实例化，实现相关的操作**

 * 

 * 4. abstract 修饰方法:**抽象方法**

    ​      抽象方法，**只有方法的声明，没有方法体。**

     ​    **包含抽象方法的类，一定是一个抽象类。反之，抽象类中可以没有抽象方法**

     若子类重写了父类中所有的抽象方法，此子类可实例化，

     若子类没有重写父类中所有的抽象方法，则此子类也是一个抽象类，需要使用abstract修饰 

 * abstract 使用上的注意点:

 * 1. abstract 不能用来修饰变量、代码块、构造器；

    

 * 2. abstract 不能用来修饰**私有方法、静态方法（静态方法不可被重写，静态方法随着类的加载而加载，一直在内存里存在）、final 的方法、final 的类。**



```java
public class AbstractTest {
	public static void main(String[] args) {
		//一旦 Person 类抽象了，就不可实例化
//		Person p1 = new Person();
//		p1.eat();
		
	}
}

abstract class Creature{
	public abstract void breath();
}

abstract class Person extends Creature{
	String name;
	int age;
	
	public Person(){
		
	}
	
	public Person(String name,int age){
		this.name = name;
		this.age = age;
	}
	
	//不是抽象方法
//	public void eat(){
//		System.out.println("人吃饭");
//	}
	
	//抽象方法
	public abstract void eat();
	
	public void walk(){
		System.out.println("人走路");
	}
}

class Student extends Person{
	public Student(String name,int age){
		super(name,age);
	}
	public void eat(){
		System.out.println("学生应该多吃有营养的。");
	}
	@Override
	public void breath() {
		System.out.println("学生应该呼吸新鲜的无雾霾空气");
	}
}
```

#### 5-1抽象类应用

抽象类是用来模型化那些父类无法确定全部实现，而是由其子类提供具体实现的对象的类。

![img](https://img-blog.csdnimg.cn/img_convert/fae4ad700aef40c0402a7e092da91106.png)

问题：卡车(Truck)和驳船(RiverBarge)的燃料效率和行驶距离的计算方法完全不同。Vehicle 类不能提供计算方法，但子类可以。

```java
/* Java 允许类设计者指定：超类声明一个方法但不提供实现，该方法的实现由子类提  供。这样的方法称为抽象方法。有一个或更多抽象方法的类称为抽象类。
 * Vehicle 是一个抽象类，有两个抽象方法。
 * 注意：抽象类不能实例化 new Vihicle()是非法的
 */
public abstract class Vehicle{
	public abstract double calcFuelEfficiency();//计算燃料效率的抽象方法
	public abstract double calcTripDistance();//计算行驶距离的抽象方法
}
public class Truck extends Vehicle{
	public double calcFuelEfficiency(){ 
		//写出计算卡车的燃料效率的具体方法
	}
	public double calcTripDistance(){ 
		//写出计算卡车行驶距离的具体方法
	}
}
public class RiverBarge extends Vehicle{
	public double calcFuelEfficiency() { 
		//写出计算驳船的燃料效率的具体方法
	}
	public double calcTripDistance( )  {  
		//写出计算驳船行驶距离的具体方法
	}
}
```

#### 5-2练习

```java
/*
 * 编写一个 Employee 类，声明为抽象类，
 * 包含如下三个属性：name，id，salary。
 * 提供必要的构造器和抽象方法：work()。
 * 对于 Manager 类来说，他既是员工，还具有奖金(bonus)的属性。
 * 请使用继承的思想，设计 CommonEmployee 类和 Manager 类，
 * 要求类中提供必要的方法进行属性访问。
 * 
 */
public abstract class Employee {
	
	private String name;
	private int id;
	private double salary;
	
	public Employee(){
		super();
	}

	public Employee(String name, int id, double salary) {
		super();
		this.name = name;
		this.id = id;
		this.salary = salary;
	}
	
	public abstract void work();	
}
```

Manager类：

```java
/*
 * 对于 Manager 类来说，他既是员工，还具有奖金(bonus)的属性。
 * 
 */
public class Manager extends Employee{

	private double bonus;	//奖金
	
	public Manager(double bonus) {
		super();
		this.bonus = bonus;
	}
	
	public Manager(String name, int id, double salary, double bonus) {
		super(name, id, salary);
		this.bonus = bonus;
	}


	@Override
	public void work() {
		System.out.println("管理员工，提高公司运行效率。");		
	}
}
```

CommonEmployee类：

```java
public class CommonEmployee extends Employee {

	@Override
	public void work() {
		System.out.println("员工在一线车间生产产品。");
	}

}
```

测试类：

```java
/*
 * 请使用继承的思想，设计 CommonEmployee 类和 Manager 类，
 */
public class EmployeeTest {
	public static void main(String[] args) {
		
		Employee manager = new Manager("库克",1001,5000,50000);
		
		manager.work();
		
		CommonEmployee commonEmployee = new CommonEmployee();
		commonEmployee.work();
	}
}
```

#### 5-3创建抽象类的匿名子类对象

```java
public class Num {

}

abstract class Creature{
	public abstract void breath();
}

abstract class Person extends Creature{
	String name;
	int age;
	
	public Person(){
		
	}
	
	public Person(String name,int age){
		this.name = name;
		this.age = age;
	}
	
	//不是抽象方法
//	public void eat(){
//		System.out.println("人吃饭");
//	}
	
	//抽象方法
	public abstract void eat();
	
	public void walk(){
		System.out.println("人走路");
	}
}

class Student extends Person{
	public Student(String name,int age){
		super(name,age);
	}
	public Student(){

	}
	public void eat(){
		System.out.println("学生应该多吃有营养的。");
	}
	@Override
	public void breath() {
		System.out.println("学生应该呼吸新鲜的无雾霾空气");
	}
}
```

PersonTest类：

```java
/*
 * 抽象类的匿名子类
 * 
 */
public class PersonTest {
	public static void main(String[] args) {
		
		method(new Student());	//匿名对象
		
		Worker worker = new Worker(); 
		method1(worker);	//非匿名的类非匿名的对象
		
		method1(new Worker());	//非匿名的类匿名的对象
		
		System.out.println("*********************");
		
		//创建了一个匿名子类的对象:p
		Person p = new Person(){

			@Override
			public void eat() {
				System.out.println("吃东西");
			}

			@Override
			public void breath() {
				System.out.println("呼吸空气");
			}
			
		};
		method1(p);
		System.out.println("**********************"); 
		//创建匿名子类的匿名对象
		method1(new Person(){

			@Override
			public void eat() {
				System.out.println("吃零食");
			}

			@Override
			public void breath() {
				System.out.println("云南的空气");
			}
			
		});
	}
	
	public static void method1(Person p){
		p.eat();
		p.walk();
	}
	
	public static void method(Student s){
		
	}
}
class Worker extends Person{
	
	@Override
	public void eat() {
	}

	@Override
	public void breath() {
	}
}
```

#### 5-4多态的应用：模板方法设计模式

​      抽象类体现的就是一种模板模式的设计，抽象类作为多个子类的通用模板，子类在抽象类的基础上进行扩展、改造，但子类总体上会保留抽象类的行为方式。

解决的问题：

​         当功能内部一部分实现是确定的，一部分实现是不确定的。这时可以把不确定的部分暴露出去，让子类去实现。
​         换句话说，**在软件开发中实现一个算法时，整体步骤很固定、通用，这些步骤已经在父类中写好了。但是某些部分易变，易变部分可以抽象出来，供不同子类实现。这就是一种模板模式**

例1：

```java
/*
 * 抽象类的应用:模板方法的设计模式
 */
public class TemplateTest {
	public static void main(String[] args) {
		
		SubTemlate t = new SubTemlate();
		
		t.sendTime();
	}
}
abstract class Template{
	
	//计算某段代码执行所需花费的时间
	public void sendTime(){
		
		long start = System.currentTimeMillis();
		
		code();	//不确定部分，易变的部分
		
		long end = System.currentTimeMillis();
		
		System.out.println("花费的时间为:" + (end - start));
	}
	
	public abstract void code();
}

class SubTemlate extends Template{
	
	@Override
	public void code() {
		
		for(int i = 2;i <= 1000;i++){
			boolean isFlag = true;
			for(int j = 2;j <= Math.sqrt(i);j++){
				if(i % j == 0){
					isFlag = false;
					break;
				}
			}
			if(isFlag){
				System.out.println(i);
			}
		}
	}
}
```

例2：

```java
//抽象类的应用：模板方法的设计模式
public class TemplateMethodTest {

	public static void main(String[] args) {
		BankTemplateMethod btm = new DrawMoney();
		btm.process();

		BankTemplateMethod btm2 = new ManageMoney();
		btm2.process();
	}
}
abstract class BankTemplateMethod {
	// 具体方法
	public void takeNumber() {
		System.out.println("取号排队");
	}

	public abstract void transact(); // 办理具体的业务 //钩子方法

	public void evaluate() {
		System.out.println("反馈评分");
	}

	// 模板方法，把基本操作组合到一起，子类一般不能重写
	public final void process() {
		this.takeNumber();

		this.transact();// 像个钩子，具体执行时，挂哪个子类，就执行哪个子类的实现代码

		this.evaluate();
	}
}

class DrawMoney extends BankTemplateMethod {
	public void transact() {
		System.out.println("我要取款！！！");
	}
}

class ManageMoney extends BankTemplateMethod {
	public void transact() {
		System.out.println("我要理财！我这里有 2000 万美元!!");
	}
}
```

模板方法设计模式是编程中经常用得到的模式。各个框架、类库中都有他的影子，比如常见的有：

数据库访问的封装
Junit 单元测试
JavaWeb 的 Servlet 中关于 doGet/doPost 方法调用
Hibernate 中模板程序
Spring 中 JDBCTemlate、HibernateTemplate 等

#### 5-5抽象类的练习

![img](https://img-blog.csdnimg.cn/img_convert/a36e51e665b20673f270cb9b2b921e20.png)

![img](https://img-blog.csdnimg.cn/img_convert/56ace48e046b22da15db7100a2edfccb.png)

Employee类：

```java
/*
 * 定义一个 Employee 类，
 * 该类包含：private 成员变量 name,number,birthday，
 * 其中 birthday 为 MyDate 类的对象；
 * abstract 方法 earnings()；
 * toString()方法输出对象的 name,number 和 birthday。
 * 
 */
public abstract class Employee {
	private String name;
	private int number;
	private MyDate birthday;
	
	public Employee(String name, int number, MyDate birthday) {
		super();
		this.name = name;
		this.number = number;
		this.birthday = birthday;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getNumber() {
		return number;
	}

	public void setNumber(int number) {
		this.number = number;
	}

	public MyDate getBirthday() {
		return birthday;
	}

	public void setBirthday(MyDate birthday) {
		this.birthday = birthday;
	}

	public abstract double earnings();

	@Override
	public String toString() {
		return "name=" + name + ", number=" + number + ", birthday=" + birthday.toDateString() + "]";
	}
	
}
```

MyDate类

```java
/*
 * MyDate 类包含:private 成员变量 year,month,day；
 * toDateString()方法返回日期对应的字符串：xxxx 年 xx 月 xx 日
 */
public class MyDate {
	private int year;
	private int month;
	private int day;
	
	public MyDate(int year, int month, int day) {
		super();
		this.year = year;
		this.month = month;
		this.day = day;
	}

	public int getYear() {
		return year;
	}

	public void setYear(int year) {
		this.year = year;
	}

	public int getMonth() {
		return month;
	}

	public void setMonth(int month) {
		this.month = month;
	}

	public int getDay() {
		return day;
	}

	public void setDay(int day) {
		this.day = day;
	}

	public String toDateString(){
		return year + "年" + month + "月" + day + "日";
	}
}
```

SalariedEmployee类：

```java
/*
 * 定义 SalariedEmployee 类继承 Employee 类，实现按月计算工资的员工处理。
 * 该类包括：private 成员变量 monthlySalary；实现父类的抽象方法 earnings(),
 * 该方法返回 monthlySalary 值；
 * toString()方法输出员工类型信息及员工的 name，number,birthday。
 * 
 */
public class SalariedEmployee extends Employee{
	private double monthlySalary;	//月工资

	public SalariedEmployee(String name,int number,MyDate birthday) {
		super(name,number,birthday);
	}
	
	public SalariedEmployee(String name, int number, MyDate birthday, double monthlySalary) {
		super(name, number, birthday);
		this.monthlySalary = monthlySalary;
	}

	@Override
	public double earnings() {
		return monthlySalary;		
	}

	@Override
	public String toString() {
		return "SalariedEmployee [" + super.toString() + "]";
	}	
}
```

HourlyEmployee 类：

```java
/*
 * 参照 SalariedEmployee 类定义 HourlyEmployee 类，
 * 实现按小时计算工资的员工处理。该类包括：private 成员变量 wage 和 hour；
 * 实现父类的抽象方法 earnings(),该方法返回 wage*hour 值；
 * toString()方法输出员工类型信息及员工的 name，number,birthday。
 * 
 */
public class HourlyEmployee extends Employee{
	private int wage;	//每小时的工资
	private int hour;	//月工作的小时数
	
	public HourlyEmployee(String name, int number, MyDate birthday) {
		super(name, number, birthday);
	}

	public HourlyEmployee(String name, int number, MyDate birthday, int wage, int hour) {
		super(name, number, birthday);
		this.wage = wage;
		this.hour = hour;
	}

	@Override
	public double earnings() {
		return wage*hour;
	}

	public int getWage() {
		return wage;
	}

	public void setWage(int wage) {
		this.wage = wage;
	}

	public int getHour() {
		return hour;
	}

	public void setHour(int hour) {
		this.hour = hour;
	}
	
	public String toString(){
		return "HourlyEmployee[" + super.toString() + "]"; 
	}
}
```

PayrollSystem 类：

```java
import java.util.Calendar;
import java.util.Scanner;
/*
 * 定义 PayrollSystem 类，创建 Employee 变量数组并初始化，
 * 该数组存放各类雇员对象的引用。利用循环结构遍历数组元素，
 * 输出各个对象的类型,name,number,birthday,以及该对象生日。
 * 当键盘输入本月月份值时，
 * 如果本月是某个 Employee 对象的生日，还要输出增加工资信息。
 * 
 */
public class PayrollSystem {
	public static void main(String[] args) {
		//方式一：
//		Scanner scanner = new Scanner(System.in);
//		System.out.println("请输入当月的月份：");
//		int month = scanner.nextInt();
		
		//方式二：
		Calendar calendar = Calendar.getInstance();
		int month = calendar.get(Calendar.MONTH);//获取当前的月份
//		System.out.println(month);//一月份：0
		
		Employee[] emps = new Employee[2];
		
		emps[0] = new SalariedEmployee("马良", 1002,new MyDate(1992, 2, 28),10000);
		emps[1] = new HourlyEmployee("博西", 2001, new MyDate(1991, 1, 6),60,240);
		
		for(int i = 0;i < emps.length;i++){
			System.out.println(emps[i]);
			double salary = emps[i].earnings();
			System.out.println("月工资为：" + salary);
			
			if((month+1) == emps[i].getBirthday().getMonth()){
				System.out.println("生日快乐！奖励 100 元");
			}
			
		}
	}
}
```

### 6.接口(interface)

#### 6-1概述

​       一方面，有时必须从几个类中派生出一个子类，继承它们所有的属性和方法。但是，Java 不支持多重继承。有了接口，就可以得到多重继承的效果。

​       另一方面，有时必须从几个类中抽取出一些共同的行为特征，而它们之间又没有 is-a 的关系，仅仅是具有相同的行为特征而已。例如：鼠标、键盘、打印机、扫描仪、摄像头、充电器、MP3 机、手机、数码相机、移动硬盘等都支持 USB 连接。

​       接口就是规范，定义的是一组规则，体现了现实世界中“如果你是/要…则必须能…”的思想。继承是一个"是不是"的关系，而接口实现则是"能不能"的关系。

​       接口的本质是契约，标准，规范，就像我们的法律一样。制定好后大家都要遵守。


![img](https://img-blog.csdnimg.cn/img_convert/aec8823d72652f568ac820b927069e4e.png)

接口(interface)是抽象方法和常量值定义的集合。

接口的特点：

 * 用 interface 来定义。
 * 接口中的所有成员变量都默认是由 public static final 修饰的。
 * 接口中的所有抽象方法都默认是由 public abstract 修饰的。
 * 接口中没有构造器。
 * 接口采用多继承机制。

![img](https://img-blog.csdnimg.cn/img_convert/729b5a0b77e2881568a2c029920e0f2e.png)

```java
/*
 * 接口的使用
 * 1.接口使用 interface 来定义。
 * 2.在 Java 中:接口和类是并列的两个结构
 * 3.如何去定义两个接口:定义接口中的成员
 * 	》3.1 JDK7 及以前:只能定义全局常量和抽象方法
 * 		》全局常量:public static final 的,但是书写中，可以省略不写。
 * 		》抽象方法:public abstract 的
 * 
 *  》3.2 JDK8:除了全局常量和抽象方法之外，还可以定义静态方法、默认方法(略)。
 * 
 * 4.接口中不能定义构造器！意味着接口不可以实例化。
 * 
 * 5.Java 开发中，接口通过让类去实现(implements)的方式来使用。
 *   如果实现类覆盖了接口中的所有方法，则此实现类就可以实例化
 *   如果实现类没有覆盖接口中所有的抽象方法，则此实现类仍为一个抽象类
 * 
 * 6.Java 类可以实现多个接口 ---》弥补了 Java 单继承性的局限性
 *  格式:class AA extends BB implementd CC,DD,EE
 *  
 *  7.接口与接口之间是继承,而且可以多继承
 *  
 **********************************
 * 8.接口的具体使用，体现多态性
 * 	   接口的主要用途就是被实现类实现。（面向接口编程）
 * 9.接口，实际可以看作是一种规范
 * 
 * 面试题:抽象类与接口有哪些异同？
 *  
 */
public class InterfaceTest {
	public static void main(String[] args) {
		System.out.println(Flayable.MAX_SPEED);
		System.out.println(Flayable.MIN_SPEED);
	}
}
interface Flayable{
	
	//全局变量
	public static final int MAX_SPEED = 7900;	
	int MIN_SPEED = 1;//省略了 public static final 
	
	//抽象方法
	public abstract void fly();
	
	void stop();//省略了 public abstract 
	//Interfaces cannot have constructors
//	public Flayable(){
//		
//	}	
}
interface Attackable{
	void attack();
}

class Plane implements Flayable{

	@Override
	public void fly() {
		System.out.println("飞机通过引擎起飞");
		
	}

	@Override
	public void stop() {
		System.out.println("驾驶员减速停止");
	}
	
}
abstract class Kite implements Flayable{

	@Override
	public void fly() {
		
	}
}

class Bullet extends Object implements Flayable,Attackable,CC{

	@Override
	public void attack() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void fly() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void stop() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void method1() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void method2() {
		// TODO Auto-generated method stub
		
	}
}

//*********************************
interface AA{
	void method1();
}
interface BB{
	void method2();
}
interface CC extends AA,BB{
	
}
```

![img](https://img-blog.csdnimg.cn/img_convert/1c9cab10d5aac0ca205e787df6f7bed2.png)

#### 6-2举例

```java
/*
 * 接口的使用
 * 1.接口使用上也满足多态性
 * 2.接口，实际上就是定义了一种规范
 * 3.开发中，体会面向接口编程！
 * 
 */
public class USBTest {
	public static void main(String[] args) {
		
		Computer com = new Computer();
		//1.创建了接口的非匿名实现类的非匿名对象
		Flash flash = new Flash();
		com.transferData(flash); 
		//2. 创建了接口的非匿名实现类的匿名对象
		com.transferData(new Printer());
		//3. 创建了接口的匿名实现类的非匿名对象
		USB phone = new USB(){

			@Override
			public void start() {
				System.out.println("手机开始工作");
			}

			@Override
			public void stop() {
				System.out.println("手机结束工作");
			}
			
		};
		com.transferData(phone);
		//4. 创建了接口的匿名实现类的匿名对象
		com.transferData(new USB(){
			@Override
			public void start() {
				System.out.println("mp3 开始工作");
			}

			@Override
			public void stop() {
				System.out.println("mp3 结束工作");
			}
		});
	}
}

class Computer{
	
	public void transferData(USB usb){//USB usb = new Flash();
		usb.start();
		
		System.out.println("具体传输数据的细节");
		
		usb.stop();
	}
	
}

interface USB{
	//常量:定义了长、宽
	void start();
	
	void stop();
}
class Flash implements USB{

	@Override
	public void start() {
		System.out.println("U 盘开始工作");
	}

	@Override
	public void stop() {
		System.out.println("U 盘结束工作");
	}
}
class Printer implements USB{
	@Override
	public void start() {
		System.out.println("打印机开启工作");
	}

	@Override
	public void stop() {
		System.out.println("打印机结束工作");
	}
	
}
```

#### 6-3接口的应用：代理模式(proxy)

​      代理模式是 Java 开发中使用较多的一种设计模式。代理设计就是为其他对象提供一种代理以控制对这个对象的访问。

![img](https://img-blog.csdnimg.cn/img_convert/6be3acfe541841343c9338f669a58d0c.png)

```java
/*
 * 接口的应用:代理模式
 * 
 * 
 */
public class NetWorkTest {
	public static void main(String[] args) {
		
		Server server = new Server();
//		server.browse();
		ProxyServer proxyServer = new ProxyServer(server);
		
		proxyServer.browse();
	}
}
interface NetWork{
	public void browse();
	
}
//被代理类
class Server implements NetWork{


	@Override
	public void browse() {
		System.out.println("真实的服务器来访问网络");
	}
}
//代理类
class ProxyServer implements NetWork{
	
	private NetWork work;
	
	public ProxyServer(NetWork work){
		this.work = work;
	}
	
	public void check(){
		System.out.println("联网前的检查工作");
	}

	@Override
	public void browse() {
		check();
		
		work.browse();
	}
	
}
```

应用场景：

* 安全代理：屏蔽对真实角色的直接访问。

* 远程代理：通过代理类处理远程方法调用（RMI）

* 延迟加载：先加载轻量级的代理对象，真正需要再加载真实对象

  ​	比如你要开发一个大文档查看软件，大文档中有大的图片，有可能一个图片有 100MB，在打开文件时，不可能将所有的图片都显示出来，这样就可以使用代理模式，当需要查看图片时，用 proxy 来进行大图片的打开。

分类：

- 静态代理（静态定义代理类）
- 动态代理（动态生成代理类）
  - JDK 自带的动态代理，需要反射等知识

```java
public class StaticProxyTest {

	public static void main(String[] args) {
		Proxy s = new Proxy(new RealStar());
		s.confer();
		s.signContract();
		s.bookTicket();
		s.sing();
		s.collectMoney();
	}
}

interface Star {
	void confer();// 面谈

	void signContract();// 签合同

	void bookTicket();// 订票

	void sing();// 唱歌

	void collectMoney();// 收钱
}
//被代理类
class RealStar implements Star {

	public void confer() {
	}

	public void signContract() {
	}

	public void bookTicket() {
	}

	public void sing() {
		System.out.println("明星：歌唱~~~");
	}

	public void collectMoney() {
	}
}

//代理类
class Proxy implements Star {
	private Star real;

	public Proxy(Star real) {
		this.real = real;
	}

	public void confer() {
		System.out.println("经纪人面谈");
	}

	public void signContract() {
		System.out.println("经纪人签合同");
	}

	public void bookTicket() {
		System.out.println("经纪人订票");
	}

	public void sing() {
		real.sing();
	}

	public void collectMoney() {
		System.out.println("经纪人收钱");
	}
}
```

#### 6-4接口的应用：工厂模式

拓展：[工厂设计模式](C:/Users/86156/Desktop/笔记/拓展：工厂设计模式.pdf)

接口与抽象类之间的对比

No.	区别点	抽象类	接口
1	定义	包含抽象方法的类	主要是抽象方法和全局常量的集合
2	组成	构造方法、抽象方法、普通方法、常量、变量	常量、抽象方法、(jdk8.0:默认方法、静态方法)
3	使用	子类继承抽象类(extends)	子类实现接口(implements)
4	关系	抽象类可以实现多个接口	接口不能继承抽象类，但允许继承多个接口
5	常见设计模式	模板方法	简单工厂、工厂方法、代理模式
6	对象	都通过对象的多态性产生实例化对象	
7	局限	抽象类有单继承的局限	接口没有此局限
8	实际	作为一个模板	是作为一个标准或是表示一种能力
9	选择	如果抽象类和接口都可以使用的话，优先使用接口，因为避免单继承的局限	

在开发中，常看到一个类不是去继承一个已经实现好的类，而是要么继承抽象类，要么实现接口。
-【面试题】排错：

```java
interface A {
	int x = 0;
}
class B {
	int x = 1;
}
class C extends B implements A {
	public void pX() {
//		编译不通过，x 不明确
		System.out.println(x);
//		System.out.println(super.x); //1
//		System.out.println(A.x);//0
	}
	public static void main(String[] args) {
		new C().pX();
	}
}
```

```java
interface Playable {
	void play();
}
interface Bounceable {
	void play();
}
interface Rollable extends Playable, Bounceable {
	Ball ball= new Ball("PingPang"); //省略了 public static final
}
public class Ball implements Rollable {
	private String name;
	public String getName() {
		return name;
	}
	public Ball(String name) {
		this.name= name;
	}
	public void play() {
		ball = new Ball("Football"); //The final field Rollable.ball cannot be assigned	
		System.out.println(ball.getName());
	}
}
```

练习：

![img](https://img-blog.csdnimg.cn/img_convert/6593e549625053470aca56f338387d98.png)

CompareObject 类：

```java
/*
 * 定义一个接口用来实现两个对象的比较。
 * 
 */
public interface CompareObject {
	public int compareTo(Object o);
	//若返回值是 0,代表相等;若为正数，代表当前对象大；负数代表当前对象小
	
}
```

Circle 类：

```java
/*
 * 定义一个 Circle 类，声明 redius 属性，提供 getter 和 setter 方法
 */
public class Circle {
	
	private Double radius;

	public Double getRadius() {
		return radius;
	}

	public void setRadius(Double radius) {
		this.radius = radius;
	}

	public Circle() {
		super();
	}

	public Circle(Double radius) {
		super();
		this.radius = radius;
	}
		
}
```

ComparableCircle 类：

```java
/*
 * 定义一个 ComparableCircle 类，继承 Circle 类并且实现 CompareObject 接口。在 ComparableCircle 类中给出接口中方法 compareTo 的实现体，
 * 用来比较两个圆的半径大小。
 */
public class ComparableCircle extends Circle implements CompareObject{

	public ComparableCircle(double radius) {
		super(radius);
	}
	@Override
	public int compareTo(Object o) {
		if(this == o){
			return 0;
		}
		if(o instanceof ComparableCircle){
			ComparableCircle c = (ComparableCircle)o;
			//错误的写法
//			return (int)(this.getRedius() - c.getRedius());
			//正确的方式一：
//			if(this.getRadius() > c.getRadius()){
//				return 1;
//			}else if(this.getRadius() < c.getRadius()){
//				return -1;
//			}else{
//				return 0;
//			}
			//当属性 radius 声明为 Double 类型时，可以调用包装类的方法
			//正确的方式二：
			return this.getRadius().compareTo(c.getRadius());
		}else{
			return 0;
//			throw new RuntimeException("传入数据类型不匹配");
		}
	}
}
```

InterfaceTest 类：

```java
/*
 * 定义一个测试类 InterfaceTest，创建两个 ComparableCircle 对象，
 * 调用 compareTo 方法比较两个类的半径大小。
 * 
 */
public class InterfaceTest {
	public static void main(String[] args) {
		
		ComparableCircle c1 = new ComparableCircle(3.4);
		ComparableCircle c2 = new ComparableCircle(3.6);
		
		int compareValue = c1.compareTo(c2);
		if(compareValue > 0){
			System.out.println("c1 对象大");
		}else if(compareValue < 0){
			System.out.println("c2 对象大");
		}else{
			System.out.println("两个一样的");
		}
		
		int compareValue1 = c1.compareTo(new String("AA"));
		System.out.println(compareValue1);
	}
}
```

### 7.Java8中关于接口的改进

Java 8 中，你可以为接口添加静态方法和默认方法。从技术角度来说，这是完全合法的，只是它看起来违反了接口作为一个抽象定义的理念。

静态方法：

​	使用 static 关键字修饰。可以通过接口直接调用静态方法，并执行其方法体。我们经常在相互一起使用的类中使用静态方法。你可以在标准库中找到像 Collection/Collections 或者 Path/Paths 这样成对的接口和类。

默认方法：

​	默认方法使用 default 关键字修饰。可以通过实现类对象来调用。我们在已有的接口中提供新方法的同时，还保持了与旧版本代码的兼容性。比如：java 8 API 中对 Collection、List、Comparator 等接口提供了丰富的默认方法。

例1：

interface 类；

```java
/*
 * JDK8:除了全局常量和抽象方法之外，还可以定义静态方法、默认方法(略)。
 * 
 * 
 */
public interface CompareA {

	//静态方法
	public static void method1() {
		System.out.println("CompareA:西安");
	}
	
	//默认方法
	public default void method2(){
		System.out.println("CompareA:深圳");
	}
	
	default void method3(){
		System.out.println("CompareA:杭州");
	}
}
```

SubClassTest 类：

```java
public class SubClassTest {

	public static void main(String[] args) {
		SubClass s = new SubClass();
//		s.method1();
//		SubClass.method1();
//		知识点 1：接口中定义的静态方法，只能通过接口来调用。
		CompareA.method1();
//		知识点 2：通过实现类的对象，可以调用接口中的默认方法。
//		如果实现类重写了接口中的默认方法，调用时，仍然调用的是重写以后的方法
		s.method2();
//		知识点 3：如果子类(或实现类)继承的父类和实现的接口中声明了同名同参数的默认方法，
//		那么子类在没有重写此方法的情况下，默认调用的是父类中的同名同参数的方法。-->类优先原则
//		知识点 4：如果实现类实现了多个接口，而这多个接口中定义了同名同参数的默认方法，
//		那么在实现类没有重写此方法的情况下，报错。-->接口冲突。
//		这就需要我们必须在实现类中重写此方法
		s.method3();
		
	}
}
class SubClass extends SuperClass implements CompareA,CompareB{
	
	public void method2(){
		System.out.println("SubClass：上海");
	}
	
	public void method3(){
		System.out.println("SubClass：深圳");
	}
	
//	知识点 5：如何在子类(或实现类)的方法中调用父类、接口中被重写的方法
	public void myMethod(){
		method3(); //调用自己定义的重写的方法
		super.method3(); //调用的是父类中声明的
//		调用接口中的默认方法
		CompareA.super.method3();
		CompareB.super.method3();
	}
}
```

SuperClass 类：

```java
public class SuperClass {
	public void method3(){
		System.out.println("SuperClass:北京");
	}
}
```

CompareB 类：

```java
public interface CompareB {
	default void method3(){
		System.out.println("CompareB：上海");
	}
}
```

例2：

```java
/*
 * 练习：接口冲突的解决方式
 */
interface Filial {// 孝顺的
	default void help() {
		System.out.println("老妈，我来救你了");
	}
}

interface Spoony {// 痴情的
	default void help() {
		System.out.println("媳妇，别怕，我来了");
	}
}

class Father{
	public void help(){
		System.out.println("儿子，救我媳妇！");
	}
}

class Man extends Father implements Filial, Spoony {

	@Override
	public void help() {
		System.out.println("我该就谁呢？");
		Filial.super.help();
		Spoony.super.help();
	}
	
}
```

### 8.类的内部成员之五：内部类

​	当一个事物的内部，还有一个部分需要一个完整的结构进行描述，而这个内部的完整的结构又只为外部事物提供服务，那么整个内部的完整结构最好使用内部类。

```java
/*
 * 类的内部成员之五:内部类
 * 
 * 1.Java中允许将一个类A声明在另一个类B中,则类A就是内部类,类B就是外部类.
 * 
 * 2.内部类的分类:成员内部类	VS	局部内部类(方法内、代码块内、构造器内)
 * 		
 * 3.成员内部类
 * 	》作为外部类的成员,
 * 		- 调用外部类的结构
 * 		- 可以被static修饰
 * 		- 可以被4种不同的权限修饰
 * 
 *  》作为一个类，
 *  	- 类内可以定义属性、方法、构造器等
 *  	- 可以被final修饰，表示此类不能被继承。言外之意，不使用final，就可以被继承
 *  	- 可以abstract修饰
 * 
 * 4.关注如下的3个问题
 *   》 如何实例化成员内部类的对象
 *   》 如何在成员内部类中区分调用外部类的结构
 *   》 开发中局部内部类的使用  见《InnerClassTest1.java》
 */
public class InnerClassTest {
	public static void main(String[] args) {
		
		//创建Dog实例(静态的成员内部类)
		Person.Dog dog = new Person.Dog();
		dog.show();
		
		//创建Bird实例(非静态的成员内部类)
//		Person.Bird bird = new Person.Bird();
		Person p = new Person();
		Person.Bird bird = p.new Bird();
		bird.sing();
		
		System.out.println();
		
		bird.display("喜鹊");
	}
}
class Person{
	String name = "李雷";
	int age;
	
	public void eat(){
		System.out.println("人，吃饭");
	}
	
	//静态成员内部类
	static class Dog{
		String name;
		int age;
		
		public void show(){
			System.out.println("卡拉是条狗");
//			eat();
		}
	}
	
	//非静态成员内部类
	class Bird{
		String name = "杜鹃";
		public Bird(){
			
		}
		
		public void sing(){
			System.out.println("我是一只猫头鹰");
			Person.this.eat();//调用外部类的非静态属性
			eat();
			System.out.println(age);
		}
		
		public void display(String name){
			System.out.println(name);	//方法的形参
			System.out.println(this.name);	//内部类的属性
			System.out.println(Person.this.name);	//外部类的属性
		}
	}
	public void method(){
		//局部内部类
		class AA{
			
		}
	}
	
	{
		//局部内部类
		class BB{
			
		}
	}
	
	public Person(){
		//局部内部类
		class CC{
			
		}
	}
}
```

InnerClassTest1类：

```java
public class InnerClassTest1 {
	
//	开发中很少见
	public void method(){
//		局部内部类
		class AA{
			
		}
	}
	
//	返回一个实现了Comparable接口的类的对象
	public Comparable getComparable(){
		
//		创建一个实现了Comparable接口的类:局部内部类
		//方式一：
//		class MyComparable implements Comparable{
//
//			@Override
//			public int compareTo(Object o) {
//				return 0;
//			}
//			
//		}
//		
//		return new MyComparable();
		
		//方式二：
		return new Comparable(){


			@Override
			public int compareTo(Object o) {
				return 0;
			}
			
		};
		
	}
}
```

#### 8-1匿名内部类

```java
/*
 * 1.匿名内部类不能定义任何静态成员、方法和类，只能创建匿名内部类的一个实例。
 * 一个匿名内部类一定是在new的后面，用其隐含实现一个接口或实现一个类。
 * 
 * 2.格式：
 * 		new 父类构造器（实参列表）|实现接口(){
 * 				//匿名内部类的类体部分
 * 		}
 * 
 * 3.匿名内部类的特点
 * 		> 匿名内部类必须继承父类或实现接口
 * 		> 匿名内部类只能有一个对象
 * 		> 匿名内部类对象只能使用多态形式引用
 */
interface Product{
	public double getPrice();
	public String getName();
}
public class AnonymousTest{
	public void test(Product p){
		System.out.println("购买了一个" + p.getName() + "，花掉了" + p.getPrice());
	}
	public static void main(String[] args) {
		AnonymousTest ta = new AnonymousTest();
		//调用test方法时，需要传入一个Product参数，
		//此处传入其匿名实现类的实例
		ta.test(new Product(){
			public double getPrice(){
				return 567.8;
			}
			public String getName(){
				return "AGP显卡";
			}
		});
	}
}
```

#### 8-2局部内部类的使用注意

```java
public class InnerClassTest {
	
//	public void onCreate(){
//	
//	int number = 10;
//	
//	View.OnClickListern listener = new View.OnClickListener(){
//		
//		public void onClick(){
//			System.out.println("hello!");
//			System.out.println(number);
//		}
//		
//	}
//	
//	button.setOnClickListener(listener);
//	
//}

	/*
	 * 在局部内部类的方法中(比如:show)如果调用局部内部类所声明的方法(比如：method)中的局部变量(比如：num)的话,
	 * 要求此局部变量声明为final的。
	 * 
	 * jdk 7及之前版本：要求此局部变量显式的声明为final的
	 * jdk 8及之后的版本：可以省略final的声明
	 * 
	 */
	public void method(){
		//局部变量
		int num = 10;
		
		class AA{
			
			public void show(){
//				num = 20;	//Local variable num defined in an enclosing scope must be final or effectively final
				System.out.println(num);
			}
		}
	}
}
```

总结：

成员内部类和局部内部类，在编译后都会生成字节码文件

格式：

成员内部类：外部类$内部类名.class

局部内部类：外部类$数字 内部类名.class

### 9.异常

#### 9-1异常概述与异常体系结构

​	在使用计算机语言进行项目开发的过程中，即使程序员把代码写得尽善尽美，在系统的运行过程中仍然会遇到一些问题，因为很多问题不是靠代码能够避免的，比如：客户输入数据的格式，读取文件是否存在，网络是否始终保持通畅等等。

异常：

​	在Java语言中，将程序执行中发生的不正常情况称为“异常”。(**开发过程中的语法错误和逻辑错误不是异常**)

Java程序在执行过程中所发生的异常事件可分为两类：

**Error**：Java虚拟机无法解决的严重问题。如：JVM系统内部错误、资源耗尽等严重情况。比如：StackOverflowError和OOM。一般不编写针对性的代码进行处理。

```java
/*
 * Java虚拟机无法解决的严重问题。如：JVM系统内部错误、资源耗尽等严重情况。
 * 比如：StackOverflowError和OOM。
 * 一般不编写针对性的代码进行处理。
 * 
 */
public class ErrorTest {
	public static void main(String[] args) {
		//1.栈溢出:java.lang.StackOverflowError
//		main(args);
		//2.堆溢出:java.lang.OutOfMemoryError
//		Integer[] arr = new Integer[1024*1024*1024];
		
	}
}
```

- **Exception**:其它因编程错误或偶然的外在因素导致的一般性问题，可以使用针对性的代码进行处理。例如：
  - 空指针访问
  - 试图读取不存在的文件
  - 网络连接中断
  - 数组角标越界

对于这些错误，一般有两种解决方法：

- 一是遇到错误就终止程序的运行。
- 另一种方法是由程序员在编写程序时，就考虑到错误的检测、错误消息的提示，以及错误的处理。

捕获错误最理想的是在编译期间，但有的错误只有在运行时才会发生。比如：除数为0，数组下标越界等

异常分类：**编译时异常**和**运行时异常**

运行时异常：
	是指编译器不要求强制处置的异常。一般是指编程时的逻辑错误，是程序员应该积极避免其出现的异常。java.lang.RuntimeException类及它的子类都是运行时异常。
	对于这类异常，可以不作处理，因为这类异常很普遍，若全处理可能会对程序的可读性和运行效率产生影响。
编译时异常：
	是指编译器要求必须处置的异常。即程序在运行时由于外界因素造成的一般性异常。编译器要求Java程序必须捕获或声明所有编译时异常。
	对于这类异常，如果程序不处理，可能会带来意想不到的结果。

#### 9-2常见异常

```java
import java.io.File;
import java.io.FileInputStream;
import java.util.Date;
import java.util.Scanner;
import org.junit.Test;

/*
 * 一、java异常体系结构
 * 
 * java.lang.Throwable
 * 		|----java.lang.Error:一般不编写针对性的代码进行处理
 * 		|----java.lang.Exception:可以进行异常处理
 * 			|----编译时异常(checked)
 * 				|----IOEXception
 * 					|----FileNotFoundException
 * 				|----ClassNotFoundException
 * 			|----运行时异常(unchecked)
 * 				|----NullPointerException
 * 				|----ArrayIndexOutOfBoundsException
 * 				|----ClassCaseException
 * 				|----NumberFormatException
 * 				|----InputMismatchException
 * 				|----ArithmaticException
 * 
 * 面试题:常见的异常有哪些？举例说明
 * 
 */
public class ExceptionTest {

	// ******************以下是编译时异常***************************
	@Test
	public void test7() {
//		File file = new File("hello.txt");
//		FileInputStream fis = new FileInputStream(file);
//		
//		int data = fis.read();
//		while(data != -1){
//			System.out.print((char)data);
//			data = fis.read();
//		}
//		
//		fis.close();
	}

	// ******************以下是运行时异常***************************
	// ArithmeticException
	@Test
	public void test6() {
		int a = 10;
		int b = 0;
		System.out.println(a / b);
	}

	// InputMismatchException
	@Test
	public void test5() {
		Scanner scanner = new Scanner(System.in);
		int score = scanner.nextInt();
		System.out.println(score);

		scanner.close();
	}

	// NumberFormatException
	@Test
	public void test4() {
		String str = "123";
		str = "abc";
		int num = Integer.parseInt(str);
	}

	// ClassCaseException
	@Test
	public void test3() {
		 Object obj = new Date();
		 String str = (String)obj;
	}

	// ArrayIndexOutOfBoundsException
	@Test
	public void test2() {
		// int[] arr = new int[10];
		// System.out.println(arr[10]);

		// String str = "abc";
		// System.out.println(str.charAt(3));
	}

	// NullPointerException
	@Test
	public void test1() {
		// int[] arr = null;
		// System.out.println(arr[3]);

		// String str = "abc";
		// str = null;
		// System.out.println(str.charAt(0));
	}
}
```

#### 9-3异常处理机制一：try-catch-finally

​	在编写程序时，经常要在可能出现错误的地方加上检测的代码，如进行x/y运算时，要检测分母为0，数据为空，输入的不是数据而是字符等。过多的if-else分支会导致程序的代码加长、臃肿，可读性差。因此采用异常处理机制。

Java异常处理:

Java采用的异常处理机制，是将异常处理的程序代码集中在一起，与正常的程序代码分开，使得程序简洁、优雅，并易于维护。

方式一：try-catch-finally

方式二：[throws](https://so.csdn.net/so/search?q=throws&spm=1001.2101.3001.7020) + 异常类型

Java异常处理的方式: try-catch-finally：

try：
	捕获异常的第一步是用try{…}语句块选定捕获异常的范围，将可能出现异常的代码放在try语句块中。
catch(Exceptiontypee)：
	在catch语句块中是对异常对象进行处理的代码。每个try语句块可以伴随一个或多个catch语句，用于处理可能产生的不同类型的异常对象。
	捕获异常的有关信息：与其它对象一样，可以访问一个异常对象的成员变量或调用它的方法。
	getMessage() 获取异常信息，返回字符串
	printStackTrace() 获取异常类名和异常信息，以及异常出现在程序中的位置。返回值void。
![img](https://img-blog.csdnimg.cn/img_convert/1856fe718d55f0f2180950b88deb622d.png)

finally：
	捕获异常的最后一步是通过finally语句为异常处理提供一个统一的出口，使得在控制流转到程序的其它部分以前，能够对程序的状态作统一的管理。
	不论在try代码块中是否发生了异常事件，catch语句是否执行，catch语句是否有异常，catch语句中是否有return，finally块中的语句都会被执行。
	finally语句和catch语句是任选的

![img](https://img-blog.csdnimg.cn/img_convert/8f4596135485e78881d6ee1cba3026b9.png)

```java
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

import org.junit.Test;

/*
 * 异常的处理:抓抛模型
 * 
 * 过程一:“抛”：程序在征程执行过程中，一旦出现异常，就会在异常代码处生成一个对应异常类的对象
 * 			 并将此对象抛出。
 * 			一旦抛出对象以后，其后的代码就不再执行。
 * 
 * 过程二:“抓”:可以理解为异常的处理方式：① try-catch-finally  ② throws
 * 
 * 二、try-catch-finally的使用
 * 
 * try{
 * 		//可能出现异常的代码
 * }catch(异常类型1 变量名1){
 * 		//处理异常的方式1
 * }catch(异常类型2 变量名2){
 * 		//处理异常的方式2
 * }catch(异常类型3 变量名3){
 * 		//处理异常的方式3
 * }
 * ...
 * finally{
 * 		//一定会执行的代码
 * }
 * 
 * 说明:
 * 1.finally是可选的。
 * 2.使用try将可能出现异常代码包装起来，在执行过程中，一旦出现异常，就会生成一个对应异常类的对象，根据此对象
 *   的类型，去catch中进行匹配。
 * 3.一旦try中的异常对象匹配到某一个catch时，就进入catch中进行异常的处理。一旦处理完成，就跳出当前的
 *   try-catch结构（在没有写finally的情况）。继续执行其后的代码。
 * 4.catch中的异常类型如果没有子父类关系，则谁声明在上，谁声明在下无所谓。
 *   catch中的异常类型如果满足子父类关系，则要求子类一定声明在父类的上面。否则，报错
 * 5.常用的异常对象处理的方式： ① String  getMessage()    ② printStackTrace()
 * 6.在try结构中声明的变量，再出了try结构以后，就不能再被调用,例65行:System.out.println(num);
 * 7.try-catch-finally结构可以嵌套  
 * 
 * 体会1：使用try-catch-finally处理编译时异常，是得程序在编译时就不再报错，但是运行时仍可能报错。
 *     相当于我们使用try-catch-finally将一个编译时可能出现的异常，延迟到运行时出现。
 *     
 * 体会2：开发中，由于运行时异常比较常见，所以我们通常就不针对运行时异常编写try-catch-finally了。
 *      针对于编译时异常，我们说一定要考虑异常的处理。
 */
public class ExceptionTest1 {
	
	@Test
	public void test2(){
		try{
			File file = new File("hello.txt");
			FileInputStream fis = new FileInputStream(file);
			
			int data = fis.read();
			while(data != -1){
				System.out.print((char)data);
				data = fis.read();
			}
			
			fis.close();
		}catch(FileNotFoundException e){
			e.printStackTrace();
		}catch(IOException e){
			e.printStackTrace();
		}
	}

	@Test
	public void test1(){
		
		String str = "123";
		str = "abc";
		try{
			int num = Integer.parseInt(str);	
			
			System.out.println("hello-----1");
		}catch(NumberFormatException e){
//			System.out.println("出现数值转换异常了，不要着急....");
			//String getMessage():
//			System.out.println(e.getMessage());
			//printStackTrace():
			e.printStackTrace();
		}catch(NullPointerException e){
			System.out.println("出现空指针异常了，不要着急....");
		}catch(Exception e){
			System.out.println("出现异常了，不要着急....");
		}
//		System.out.println(num);
		
		System.out.println("hello----2");
	}
}
```

##### 1. finally的使用

```java
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

import org.junit.Test;

/*
 * try-catch-finally中finally的使用：
 * 
 * 1.finally是可选的。
 * 2.finally中声明的是一定会被执行的代码。即使catch中又出现异常了，try中有return语句，catch中有
 *   return语句等情况。
 * 3.像数据库连接、输入输出流、网络编程Socket等资源，JVM是不能自动的回收的，我们需要自己手动的进行资源的
 *   释放。此时的资源释放，就需要声明在finally中。
 * 
 */
public class FinallyTest {

	@Test
	public void test2() {
		FileInputStream fis = null;
		try {
			File file = new File("hello1.txt");//文件可能不存在，而出现异常
			fis = new FileInputStream(file);

			int data = fis.read();
			while (data != -1) {
				System.out.print((char) data);
				data = fis.read();
			}

		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if (fis != null)
					fis.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
	}

	@Test
	public void testMethod() {
		int num = method();
		System.out.println(num);
	}

	public int method() {

		try {
			int[] arr = new int[10];
			System.out.println(arr[10]);
			return 1;
		} catch (ArrayIndexOutOfBoundsException e) {
			e.printStackTrace();
			return 2;
		} finally {
			System.out.println("我一定会被执行");
			return 3;
		}
	}

	@Test
	public void test1() {
		try {
			int a = 10;
			int b = 0;
			System.out.println(a / b);
		} catch (ArithmeticException e) {
			// e.printStackTrace();

			int[] arr = new int[10];
			System.out.println(arr[10]);

		} catch (Exception e) {
			e.printStackTrace();
		}
		// System.out.println("我好慢呀~~~");
		finally {
			System.out.println("我好慢呀~~~");
		}
	}
}
```

#### 9-4异常处理机制二：throws

​	声明抛出异常是Java中处理异常的第二种方式
​	如果一个方法(中的语句执行时)可能生成某种异常，但是并不能确定如何处理这种异常，**则此方法应显示地声明抛出异常**，表明该方法将不对这些异常进行处理，而由该方法的调用者负责处理。
​	**在方法声明中用throws语句可以声明抛出异常的列表，throws后面的异常类型可以是方法中产生的异常类型，也可以是它的父类**。

```java
/*
 * 异常处理的方式二：throws + 异常类型
 * 
 * 1. "throws + 异常类型"写在方法的声明处。指明此方法执行时，可能会抛出的异常类型。
 *     一旦当方法体执行时，出现异常，仍会在异常代码处生成一个异常类的对象，此对象满足throws后异常
 *     类型时，就会被抛出。异常代码后续的代码，就不再执行！
 *
 *     关于异常对象的产生:① 系统自动生成的异常对象
 * 					② 手动生成一个异常对象，并抛出(throw)
 *     
 * 2. 体会：try-catch-finally:真正的将异常给处理掉了。
 *        throws的方式只是将异常抛给了方法的调用者。  并没有真正将异常处理掉。  
 * 
 */
public class ExceptionTest2 {
	
	public static void main(String[] args){
		try {
			method2();
		} catch (IOException e) {
			e.printStackTrace();
		}
		
		method3();
	}
	
	public static void method3(){
		try {
			method2();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
	
	public static void method2() throws IOException{
		method1();
	}

	
	public static void method1() throws FileNotFoundException,IOException{
		File file = new File("hello1.txt");
		FileInputStream fis = new FileInputStream(file);
		
		int data = fis.read();
		while(data != -1){
			System.out.print((char)data);
			data = fis.read();
		}
		
		fis.close();
		
		System.out.println("hahaha!");
	}
}
```

![img](https://img-blog.csdnimg.cn/img_convert/a349a3eb15bb86490d6c86c2b2a667ac.png)

##### 1.重写方法声明抛出异常的原则

```java
import java.io.FileNotFoundException;
import java.io.IOException;

/*
 * 方法重写的规则之一：
 * 子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常类型
 * 
 */
public class OverrideTest {
	
	public static void main(String[] args) {
		OverrideTest test = new OverrideTest();
		test.display(new SubClass());
	}
	
	public void display(SuperClass s){
		try {
			s.method();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
	
}
class SuperClass{
	
	public void method() throws IOException{
		
	}
}
class SubClass extends SuperClass{
	public void method()throws FileNotFoundException{
		
	}
}
```

3. 开发中如何选择使用try-catch-finally 还是使用throws？

 *   3.1 如果父类中被重写的方法没有throws方式处理异常，则子类重写的方法也不能使用throws，意味着如果子类重写的方法中有异常，必须使用try-catch-finally方式处理。
 *   3.2 执行的方法a中，先后又调用了另外的几个方法，这几个方法是递进关系执行的。我们建议这几个方法使用throws的方式进行处理。而执行的方法a可以考虑使用try-catch-finally方式进行处理。

#### 9-5手动抛出异常

Java异常类对象除在程序执行过程中出现异常时由系统自动生成并抛出，也可根据需要使用人工创建并抛出。

- 首先要生成异常类对象，然后通过throw语句实现抛出操作(提交给Java运行环境)
- 可以抛出的异常必须是Throwable或其子类的实例。下面的语句在编译时将会产生语法错误：

```java
public class StudentTest {
	public static void main(String[] args) {
		try {
			Student s = new Student();
//		s.regist(1001);
			s.regist(-1001);
			System.out.println(s);
		} catch (Exception e) {
//			e.printStackTrace();
			System.out.println(e.getMessage());
		}
	}
}
class Student{
	private int id;
	
	public void regist(int id) throws Exception{
		if(id > 0){
			this.id = id;
		}else{
//			System.out.println("您输入的数据非法！");
			//手动抛出异常
//			throw new RuntimeException("您输入的数据非法！");
			throw new Exception("您输入的数据非法！");
			
		}
	}

	@Override
	public String toString() {
		return "Student [id=" + id + "]";
	}
	
}
```

#### 9-6用户自定义异常类

- 一般地，用户自定义异常类都是RuntimeException的子类。
- 自定义异常类通常需要编写几个重载的构造器。
- 自定义异常需要提供serialVersionUID
- 自定义的异常通过throw抛出。
- 自定义异常最重要的是异常类的名字，当异常出现时，可以根据名字判断异常类型。

```java
/*
 * 如何自定义异常类？
 * 1.继承于现有的异常结构：RuntimeException 、Exception
 * 2.提供全局常量：serialVersionUID
 * 3.提供重载的构造器
 * 
 */
public class MyException extends RuntimeException{
	static final long serialVersionUID = -7034897193246939L;
	
	public MyException(){
		
	}
	
	public MyException(String msg){
		super(msg);
	}
}
```

![img](https://img-blog.csdnimg.cn/img_convert/388532badc2034628c974ab4503db151.png)

##### 1.练习

练习1——ReturnExceptionDemo类

```java
public class ReturnExceptionDemo {
	static void methodA() {
		try {
			System.out.println("进入方法A");
			throw new RuntimeException("制造异常");
		} finally {
			System.out.println("用A方法的finally");
		}
	}

	static void methodB() {
		try {
			System.out.println("进入方法B");
			return;
		} finally {
			System.out.println("调用B方法的finally");
		}
	}

	public static void main(String[] args) {
		try {
			methodA();
		} catch (Exception e) {
			System.out.println(e.getMessage());
		}
			
		methodB();
	}
}
```

练习二：

```java
/*
 * 编写应用程序EcmDef.java，接收命令行的两个参数，
 * 		要求不能输入负数，计算两数相除。
 * 		对 数 据 类 型 不 一 致(NumberFormatException)、
 * 		缺 少 命 令 行 参 数(ArrayIndexOutOfBoundsException、
 * 		除0(ArithmeticException)及输入负数(EcDef自定义的异常)进行异常处理。
 *
 * 提示：
 * 		(1)在主类(EcmDef)中定义异常方法(ecm)完成两数相除功能。
 * 		(2)在main()方法中使用异常处理语句进行异常处理。
 * 		(3)在程序中，自定义对应输入负数的异常类(EcDef)。
 * 		(4)运行时接受参数java EcmDef2010//args[0]=“20”args[1]=“10”
 * 		(5)Interger类的static方法parseInt(Strings)将s转换成对应的int值。
 * 		如：int a=Interger.parseInt(“314”);//a=314;
 */
public class EcmDef {
	public static void main(String[] args) {
		try {
			int i = Integer.parseInt(args[0]);
			int j = Integer.parseInt(args[0]);
			
			int result = ecm(i,j);
			
			System.out.println(result);
		} catch (NumberFormatException e) {
			System.out.println("数据类型不一致");
		}catch (ArrayIndexOutOfBoundsException e){
			System.out.println("缺少命令行参数");
		}catch (ArithmeticException e){
			System.out.println("除0");
		}catch (EcDef e) {
			System.out.println(e.getMessage());
		}
	}
	
	public static int ecm(int i, int j) throws EcDef{
		if(i < 0 || j < 0){
			throw new EcDef("分子或分母为负数了！");
		}
		return i / j;
	}
}
```

练习2的自定义异常类——EcDef

```java
//自定义异常类
public class EcDef extends Exception {

	static final long serialVersionUID = -33875164229948L;

	public EcDef() {
		
	}

	public EcDef(String msg) {
		super(msg);
	}
}
```

#### 9-7异常总结

总结：异常处理5个关键字

![img](https://img-blog.csdnimg.cn/img_convert/4614aa28f89b84571c65636790a8f087.png)

## 11.多线程

### 1.基本概念：程序、进程、线程

* 程序(program)：为完成特定任务、用某种语言编写的一组指令的集合。即指一段静态的代码，静态对象。

* 进程(process)：程序的一次执行过程，或是正在运行的一个程序。是一个动态的过程：有它自身的产生、存在和消亡的过程。——生命周期。

​		如：运行中的QQ，运行中的MP3播放器程序是静态的，进程是动态的
​		进程作为资源分配的单位，系统在运行时会为每个进程分配不同的内存区域

* 线程(thread)，进程可进一步细化为线程，是一个程序内部的一条执行路径。
  	若一个进程同一时间并行执行多个线程，就是支持多线程的
  	线程是调度和执行的单位，每个线程拥有独立的运行栈和程序计数器(pc)，线程切换的开销小
  	一个进程中的多个线程共享相同的内存单元/内存地址空间—》它们从同一堆中分配对象，可以访问相同的变量和对象。这就使得线程间通信更简便、高效。但多个线程操作共享的系统资源可能就会带来安全的隐患。

![img](https://gitee.com/lsqpic/BlogPicBed-1/raw/master/img/2021/01/16/20210123234440.jpg)

#### 1-1进程与线程

![img](https://gitee.com/lsqpic/BlogPicBed-1/raw/master/img/2021/01/16/20210123234436.jpg)

单核CPU与多核CPU的理解

* 单核CPU，其实是一种假的多线程，因为在一个时间单元内，也只能执行一个线程的任务。例如：虽然有多车道，但是收费站只有一个工作人员在收费，只有收了费才能通过，那么CPU就好比收费人员。如果有某个人不想交钱，那么收费人员可以把他“挂起”（晾着他，等他想通了，准备好了钱，再去收费）。但是因为CPU时间单元特别短，因此感觉不出来。
* 如果是多核的话，才能更好的发挥多线程的效率。（现在的服务器都是多核的）
* 一个Java应用程序java.exe，其实至少有三个线程：main()主线程，gc()垃圾回收线程，异常处理线程。当然如果发生异常，会影响主线程。

并行与并发

- 并行：多个CPU同时执行多个任务。比如：多个人同时做不同的事。
- 并发：一个CPU(采用时间片)同时执行多个任务。比如：秒杀、多个人做同一件事。

#### 1-2使用多线程的优点

背景：

​		以单核CPU为例，只使用单个线程先后完成多个任务（调用多个方法），肯定比用多个线程来完成用的时间更短，为何仍需多线程呢？

多线程程序的优点：

1. 提高应用程序的响应。对图形化界面更有意义，可增强用户体验。
2. 提高计算机系统CPU的利用率
3. 改善程序结构。将既长又复杂的进程分为多个线程，独立运行，利于理解和修改

#### 1-3何时需要多线程

- 程序需要同时执行两个或多个任务。
- 程序需要实现一些需要等待的任务时，如用户输入、文件读写操作、网络操作、搜索等。
- 需要一些后台运行的程序时。

### 2.线程的创建与使用

#### 2.1线程的创建与启动

* Java语言的JVM允许程序运行多个线程，它通过java.lang.Thread类来体现。
* Thread类的特性：
  	每个线程都是通过某个特定Thread对象的run()方法来完成操作的，经常把run()方法的主体称为线程体
  	通过该Thread对象的start()方法来启动这个线程，而非直接调用run()

#### 2-2Thread类

* Thread()：创建新的Thread对象
* Thread(String threadname)：创建线程并指定线程实例名
* Thread(Runnabletarget)：指定创建线程的目标对象，它实现了Runnable接口中的run方法
* Thread(Runnable target, String name)：创建新的Thread对象

#### 2-3 API中创建线程的两种方式

- JDK1.5之前创建新执行线程有两种方法：
  - 继承`Thread`类的方式
  - 实现`Runnable`接口的方式

##### 2-3-1创建多线程的方式一：继承Thread类

```java
/**
 * 多线程的创建，方式一：继承于Thread类
 * 1.创建一个继承于Thread类的子类
 * 2.重写Thread的run()方法 ---> 将此线程的方法声明在run()中
 * 3.创建Thread类的子对象
 * 4.通过此对象调用start()
 *
 * 例子:遍历100以内的所有的偶数
 */

//1.创建一个继承于Thread类的子类
class MyThread extends Thread{
    //重写Thread类的run()
    @Override
    public void run() {
        for(int i = 1;i < 100;i++){
            if(i % 2 == 0){
                System.out.println(i);
            }
        }
    }
}

public class ThreadTest {
    public static void main(String[] args) {
        //3.创建Thread类的子对象
        MyThread t1 = new MyThread();

        //4.通过此对象调用start():①启动当前线程 ②调用当前线程的run()
        t1.start();

        //如下操作仍在main线程中执行的
        for(int i = 1;i < 100;i++){
            if(i % 2 == 0){
                System.out.println(i + "***main()***");
            }
        }
    }
}
```

子线程的创建与启动过程：

![img](https://img-blog.csdnimg.cn/img_convert/4e851e2caa89df9b9838a273ad69249d.png)

![img](https://img-blog.csdnimg.cn/img_convert/04e20e90637405c92469045cac1fbb54.png)

##### 2-3-2创建过程中的两个问题说明

```java
//1.创建一个继承于Thread类的子类
class MyThread extends Thread{
    //重写Thread类的run()
    @Override
    public void run() {
        for(int i = 1;i < 100;i++){
            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}

public class ThreadTest {
    public static void main(String[] args) {
        //3.创建Thread类的子对象
        MyThread t1 = new MyThread();

        //4.通过此对象调用start():①启动当前线程 ②调用当前线程的run()
        t1.start();
        //问题1:我们不能通过直接调用run()的方式启动线程。
//        t1.run();

        //问题二:再启动一个线程，遍历100以内的偶数。不可以还让已经start()的线程去执行。会报IllegalThreadStateException
//        t1.start();
        //我们需要重现创建一个线程的对象，去start().
        MyThread t2 = new MyThread();
        t2.start();

        //如下操作仍在main线程中执行的
        for(int i = 1;i < 100;i++){
            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ":" + i + "***main()***");
            }
        }
    }
}
```

##### 2-3-3练习1

写法一：

```java
/**
 * 练习:创建两个分线程，其中一个遍历100以内的偶数，另一个遍历100以内的奇数
 */
public class ThreadDemo {
    public static void main(String[] args) {
        MyThread m1 = new MyThread();
        m1.start();

        MyThread2 m2 = new MyThread2();
        m2.start();
    }
}
class MyThread extends Thread{
    @Override
    public void run() {
        for(int i = 0;i < 100;i++){
            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}
class MyThread2 extends Thread{
    @Override
    public void run() {
        for(int i = 0;i < 100;i++){
            if(i % 2 != 0){
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}
```

写法二：

```java
/**
 * 练习:创建两个分线程，其中一个遍历100以内的偶数，另一个遍历100以内的奇数
 */
public class ThreadDemo {
    public static void main(String[] args) {

        //创建Thread类的匿名子类的方式
        new Thread(){
            @Override
            public void run() {
                for(int i = 0;i < 100;i++){
                    if(i % 2 == 0){
                        System.out.println(Thread.currentThread().getName() + ":" + i);
                    }
                }
            }
        }.start();

        new Thread(){
            @Override
            public void run() {
                for(int i = 0;i < 100;i++){
                    if(i % 2 != 0){
                        System.out.println(Thread.currentThread().getName() + ":" + i);
                    }
                }
            }
        }.start();
    }
}
```

##### 2-3-4 Thread类的有关方法

```java
/**
 * 测试Thread类的常用方法
 * 1.start():启动当前线程，执行当前线程的run()
 * 2.run():通常需要重写Thread类中的此方法，将创建的线程要执行的操作声明在此方法中
 * 3.currentThread(): 静态方法，返回当前代码执行的线程
 * 4.getName():获取当前线程的名字
 * 5.setName():设置当前线程的名字
 * 6.yield():释放当前CPU的执行权
 * 7.join():在线程a中调用线程b的join(),此时线程a就进入阻塞状态，直到线程b完全执行完以后，线程a才
 *          结束阻塞状态。
 * 8.stop():已过时。当执行此方法时，强制结束当前线程。
 * 9.sleep(long millitime)：让当前线程“睡眠”指定时间的millitime毫秒)。在指定的millitime毫秒时间内，
 *                          当前线程是阻塞状态的。
 * 10.isAlive()：返回boolean，判断线程是否还活着
 */

class HelloThread extends Thread{
    @Override
    public void run() {
        for(int i = 0;i < 100; i++){

            try {
                sleep(10);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
//            if(i % 20 == 0){
//                yield();
//            }
        }
    }

    public HelloThread(String name){
        super(name);
    }
}

public class ThreadModeTest {
    public static void main(String[] args) {
        HelloThread h1 = new HelloThread("Thread : 1");

//        h1.setName("线程一");

        h1.start();

        //给主线程命名
        Thread.currentThread().setName("主线程");

        for(int i = 0;i < 100; i++){
            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }

            if(i == 20){
                try {
                    h1.join();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }

        System.out.println(h1.isAlive());
    }
}
```

##### 2-3-5线程的调度

调度策略

- 时间片

![img](https://img-blog.csdnimg.cn/img_convert/df274b909314af5c7603df80e60c64f9.png)

- **抢占式：高优先级的线程抢占CPU**

- Java的调度方法
  - 同优先级线程组成先进先出队列（先到先服务），使用时间片策略
  - 对高优先级，使用优先调度的抢占式策略

##### 2-3-6线程的优先级

```java
/**
 * - 线程的优先级等级
 *   - MAX_PRIORITY：10
 *   - MIN _PRIORITY：1
 *   - NORM_PRIORITY：5 --->默认优先级
 * - 涉及的方法
 *   - getPriority() ：返回线程优先值
 *   - setPriority(intnewPriority) ：改变线程的优先级
 *
 *   说明:高优先级的线程要抢占低优先级线程cpu的执行权。
 *       但是只是从概率上讲，高优先级的线程高概率的情况下被执行。
 *       并不意味着只有当高优先级的线程执行完以后，低优先级的线程才会被执行。
 */

class HelloThread extends Thread {
    @Override
    public void run() {
        for (int j = 0; j < 100; j++) {

//            try {
//                sleep(10);
//            } catch (InterruptedException e) {
//                e.printStackTrace();
//            }

            if (j % 2 == 0) {
                System.out.println(getName() + ":" + getPriority() + ":" + j);
            }
        }
    }
    public HelloThread(String name){
        super(name);
    }
}

public class ThreadModeTest {
    public static void main(String[] args) {
        HelloThread h2 = new HelloThread("Thread : 1");
        h2.start();

        //设置分线程的优先级
        h2.setPriority(Thread.MAX_PRIORITY);

        //给主线程命名
        Thread.currentThread().setName("主线程");
        Thread.currentThread().setPriority((Thread.MIN_PRIORITY));

        for(int j = 0;j < 100; j++){
            if(j % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ":" + Thread.currentThread().getPriority() + ":" + j);
            }

//            if(j == 20){
//                try {
//                    h2.join();
//                } catch (InterruptedException e) {
//                    e.printStackTrace();
//                }
//            }
        }

        System.out.println(h2.isAlive());
    }
}
```

##### 2-3-7练习二

1.多窗口卖票

```java
/**
 * 例子：创建三个c窗口卖票，总票数为100张
 *
 * 存在线程的安全问题，待解决。
 */
class Windows extends Thread{

    private static int ticket = 100;

    @Override
    public void run() {
        while(true){
            if(ticket > 0){
                System.out.println(getName() + ":卖票，票号为: " + ticket);
                ticket--;
            }else{
                break;
            }
        }
    }
}

public class WindowsTest {
    public static void main(String[] args) {
        Windows t1 = new Windows();
        Windows t2 = new Windows();
        Windows t3 = new Windows();

        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();
    }
}
```

##### 2-3-8创建多线程的方式二：实现Runnable接口

```java
/**
 * 创建多线程的方式二：实现Runnable接口
 * 1.创建一个实现了Runnable接口得类
 * 2.实现类去实现Runnable中的抽象方法:run()
 * 3.创建实现类的对象
 * 4.将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象
 * 5.通过Thread类的对象调用start()
 */
//1.创建一个实现了Runnable接口得类
class MThread implements Runnable{

    //2.实现类去实现Runnable中的抽象方法:run()
    @Override
    public void run() {
        for(int i = 0;i < 100;i++){
            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}

public class ThreadTest1 {
    public static void main(String[] args) {
        //3.创建实现类的对象
        MThread m1 = new MThread();
        //4.将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象
        Thread t1 = new Thread(m1);
        //5.通过Thread类的对象调用start():①启动线程 ②调用当前线程的run() --> 调用了Runnable类型的target的run()
        t1.start();

        //再启动一个线程，遍历100以内的偶数
        Thread t2 = new Thread(m1);
        t2.setName("线程2");
        t2.start();
    }
}
```

##### 2-3-9继承方式与实现方式的联系与区别

 *  比较创建线程的两种方式。
 *  开发中：优先选择：实现Runnable接口的方式
 *  原因：
 *  1. 实现的方式没有类的单继承性的局限性
 *  2. 实现的方式更适合来处理多个线程有共享数据的情况。
 *  联系：public class Thread implements Runnable
 *  相同点：两种方式都需要重写run(),将线程要执行的逻辑声明在run()中。

##### 2-3-10补充：线程的分类

Java中的线程分为两类：一种是守护线程，一种是用户线程。

* 它们在几乎每个方面都是相同的，唯一的区别是判断JVM何时离开。
* 守护线程是用来服务用户线程的，通过在start()方法前调用**thread.setDaemon(true)**可以把一个用户线程变成一个守护线程。
* Java垃圾回收就是一个典型的守护线程。
* 若JVM中都是守护线程，当前JVM将退出。
* 形象理解：兔死狗烹，鸟尽弓藏

### 3、线程的生命周期

JDK中用Thread.State类定义了线程的几种状态

* 新建：当一个Thread类或其子类的对象被声明并创建时，新生的线程对象处于新建状态
* 就绪：处于新建状态的线程被start()后，将进入线程队列等待CPU时间片，此时它已具备了运行的条件，只是没分配到CPU资源
* 运行：当就绪的线程被调度并获得CPU资源时,便进入运行状态，run()方法定义了线程的操作和功能
* 阻塞：在某种特殊情况下，被人为挂起或执行输入输出操作时，让出CPU并临时中止自己的执行，进入阻塞状态
* 死亡：线程完成了它的全部工作或线程被提前强制性地中止或出现异常导致结束

线程的生命周期

![img](https://img-blog.csdnimg.cn/img_convert/b29133ad93d3839d259de57bbfa1397a.png)

### 4、线程的同步

1、提出问题：

 多个线程执行的不确定性引起执行结果的不稳定,多个线程对账本的共享，会造成操作的不完整性，会破坏数据。

![img](https://img-blog.csdnimg.cn/img_convert/b10da50b242810bf311c0f7f8062e729.png)

2、例题：模拟火车站售票程序，开启三个窗口售票。

```java
class Windows1 implements Runnable{

    private int ticket = 100;

    @Override
    public void run() {
        while(true){
            if(ticket > 0){
                System.out.println(Thread.currentThread().getName() + ":卖票，票号为: " + ticket);
                ticket--;
            }else{
                break;
            }
        }
    }
}

public class WindowsTest1 {
    public static void main(String[] args) {
        Windows1 w = new Windows1();

        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);

        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();
    }
}
```

3、理想状态

![img](https://img-blog.csdnimg.cn/img_convert/7a640e36cea308b9eeaabe6e715eb4bd.png)

4、极端状态

![img](https://img-blog.csdnimg.cn/img_convert/3b3d209bdf2c3351f5f525a73eacea0a.png)

#### 4-1同步代码块处理实现Runnable的线程安全问题

```java
/**
 *  例子：创建三个窗口卖票，总票数为100张.使用实现Runnable接口的方式
 *  1.卖票过程中出现重票、错票 ---》出现了线程的安全问题
 *  2.问题出现的原因:当某个线程操作车票的过程中，尚未操作完成时，其他线程参与进来，也操作车票
 *  3.如何解决：当一个线程在操作ticket的时候，其他线程不能参与进来。直到线程a操作完ticket时，其他
 *            线程才可以操作ticket。这种情况即使线程a出现了阻塞，也不能被改变。
 *  4.在java中，我们通过同步机制，来解决线程的安全问题。
 *
 *  方式一：同步代码块
 *  synchronized(同步监视器){
 *      //需要被同步的代码
 * 
 *  }
 *  说明：1.操作共享数据的代码，即为需要被同步的代码 --->不能包含代码多了，也不能包含代码少了。
 *       2.共享数据：多个线程共同操作的变量。比如：ticket就是共享数据
 *       3.同步监视器，俗称：锁。任何一个类的对象，都可以来充当锁。
 *          要求：多个线程必须要共用同一把锁。
 *
 *       补充：在实现Runnable接口创建多线程的方式中，我们可以考虑使用this充当同步监视器。
 *
 *  方式二：同步方法
 *      如果操作共享数据的代码完整的声明在一个方法中，我们不妨将此方法声明同步的
 *
 *  5.同步的方式，解决了线程的安全问题。---好处
 *    操作同步代码时，只能有一个线程参与，其他线程等待。相当于是一个单线程的过程，效率低。---局限性
 */

class Windows1 implements Runnable{

    private int ticket = 100;
//    Object obj = new Object();
//    Dog dog = new Dog();

    @Override
    public void run() {
        while(true){
            synchronized (this) {//此时的this:唯一的windows1的对象 //方式二:synchronized (dog) {
                if (ticket > 0) {

                    try{
                        Thread.sleep(100);
                    }catch (InterruptedException e){
                        e.printStackTrace();
                    }

                    System.out.println(Thread.currentThread().getName() + ":卖票，票号为: " + ticket);
                    ticket--;
                } else {
                    break;
                }
            }
        }
    }
}

public class WindowsTest1 {
    public static void main(String[] args) {
        Windows1 w = new Windows1();

        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);

        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();
    }
}
class Dog{

}
```

分析同步原理：

![img](https://img-blog.csdnimg.cn/img_convert/3d05078b85d041ca81c335b48afa8607.png)

#### 4-2同步代码块处理继承Thread类的线程安全问题

```java
/**
 * 使用同步代码块解决继承Thread类的方式的线程安全问题
 *
 * 例子：创建三个c窗口卖票，总票数为100张
 */
class Windows extends Thread{

    private static int ticket = 100;
    private static Object obj = new Object();

    @Override
    public void run() {
        while(true){
            //正确的
//            synchronized (obj) {
            synchronized (Windows.class){   //Class clazz = Windows.class
            //错误的，因为此时this表示的是t1,t2,t3三个对象
//            synchronized (this) {
                if (ticket > 0) {

                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    System.out.println(getName() + ":卖票，票号为: " + ticket);
                    ticket--;
                } else {
                    break;
                }
            }
        }
    }
}

public class WindowsTest2 {
    public static void main(String[] args) {
        Windows t1 = new Windows();
        Windows t2 = new Windows();
        Windows t3 = new Windows();

        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();
    }
}
```

#### 4-3同步方法处理实现Runnable的线程安全问题

```java
/**
 * 使用同步方法解决实现Runnable接口的线程安全问题
 *
 * 关于同步方法的总结:
 *  1. 同步方法仍然涉及到同步监视器，只是不需要我们显式的声明。
 *  2. 非静态的同步方法，同步监视器是：this
 *     静态的同步方法，同步监视器是：当前类本身
 */

class Windows3 implements Runnable {

    private int ticket = 100;

    @Override
    public void run() {
        while (true) {
            show();
        }
    }

    public synchronized void show() { //同步监视器:this
//        synchronized (this){
            if (ticket > 0) {
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println(Thread.currentThread().getName() + ":卖票，票号为: " + ticket);
                ticket--;
            }
//        }
    }
}

public class WindowsTest3 {
    public static void main(String[] args) {
        Windows3 w3 = new Windows3();

        Thread t1 = new Thread(w3);
        Thread t2 = new Thread(w3);
        Thread t3 = new Thread(w3);

        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();
    }
}

```

#### 4-4同步方法处理继承Thread类的线程安全问题

```java
/**
 * 使用同步方法处理继承Thread类的方式中的线程安全问题
 */
class Windows4 extends Thread {

    private static int ticket = 100;

    @Override
    public void run() {

        while (true) {

            show();
        }

    }
    private static synchronized void show(){//同步监视器：Window4.class
        //private synchronized void show(){ //同步监视器：t1,t2,t3。此种解决方式是错误的
        if (ticket > 0) {

            try {
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

            System.out.println(Thread.currentThread().getName() + "：卖票，票号为：" + ticket);
            ticket--;
        }
    }
}


public class WindowsTest4 {
    public static void main(String[] args) {
        Windows4 t1 = new Windows4();
        Windows4 t2 = new Windows4();
        Windows4 t3 = new Windows4();


        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();

    }
}
```

#### 4-5线程安全的单例模式之懒汉式

```java
/**
 * 使用同步机制将单例模式中的懒汉式改写为线程安全的
 */
public class BankTest {
}
class Bank{

    private Bank(){}

    private static Bank instance = null;

    public static Bank getInstance(){
        //方式一：效率稍差
        //快捷键:Alt+Shift+Z
//        synchronized (Bank.class) {
//            if(instance == null){
//                instance = new Bank();
//            }
//            return instance;
//        }

        //方式二：效率较高
        if(instance == null) {
            synchronized (Bank.class) {
                if (instance == null) {
                    instance = new Bank();
                }
            }
        }
        return instance;
    }
}
```

#### 4-6死锁的问题

例一：

```java
/**
 * 演示线程的死锁
 *
 * 1.死锁的理解：不同的线程分别占用对方需要的同步资源不放弃，
 *       都在等待对方放弃自己需要的同步资源，就形成了线程的死锁
 * 2.说明:
 *      》出现死锁后，不会出现异常，不会出现提示，只是所有的线程都处于阻塞状态，无法继续
 *      》我们使用同步时，要避免出现死锁。
 */
public class ThreadTest {
    public static void main(String[] args) {

        StringBuffer s1 = new StringBuffer();
        StringBuffer s2 = new StringBuffer();

        new Thread(){
            @Override
            public void run() {

                synchronized (s1){
                    s1.append("a");
                    s2.append("1");

                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    synchronized (s2){
                        s1.append("b");
                        s2.append("2");

                        System.out.println(s1);
                        System.out.println(s2);
                    }
                }
            }
        }.start();

        new Thread(new Runnable() {
            @Override
            public void run() {
                synchronized (s2){
                    s1.append("c");
                    s2.append("3");

                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    synchronized (s1){
                        s1.append("d");
                        s2.append("4");

                        System.out.println(s1);
                        System.out.println(s2);
                    }
                }
            }
        }).start();
    }
}
```

例二：

```java
class A {
	public synchronized void foo(B b) {
		System.out.println("当前线程名: " + Thread.currentThread().getName()
				+ " 进入了A实例的foo方法"); // ①
		try {
			Thread.sleep(200);
		} catch (InterruptedException ex) {
			ex.printStackTrace();
		}
		System.out.println("当前线程名: " + Thread.currentThread().getName()
				+ " 企图调用B实例的last方法"); // ③
		b.last();
	}

	public synchronized void last() {
		System.out.println("进入了A类的last方法内部");
	}
}

class B {
	public synchronized void bar(A a) {
		System.out.println("当前线程名: " + Thread.currentThread().getName()
				+ " 进入了B实例的bar方法"); // ②
		try {
			Thread.sleep(200);
		} catch (InterruptedException ex) {
			ex.printStackTrace();
		}
		System.out.println("当前线程名: " + Thread.currentThread().getName()
				+ " 企图调用A实例的last方法"); // ④
		a.last();
	}

	public synchronized void last() {
		System.out.println("进入了B类的last方法内部");
	}
}

public class DeadLock implements Runnable {
	A a = new A();
	B b = new B();

	public void init() {
		Thread.currentThread().setName("主线程");
		// 调用a对象的foo方法
		a.foo(b);
		System.out.println("进入了主线程之后");
	}

	public void run() {
		Thread.currentThread().setName("副线程");
		// 调用b对象的bar方法
		b.bar(a);
		System.out.println("进入了副线程之后");
	}

	public static void main(String[] args) {
		DeadLock dl = new DeadLock();
		new Thread(dl).start();
		dl.init();
	}
}
```

#### 4-7 Lock锁方式解决线程安全问题

* java.util.concurrent.locks.Lock接口是控制多个线程对共享资源进行访问的工具。锁提供了对共享资源的独占访问，每次只能有一个线程对Lock对象加锁，线程开始访问共享资源之前应先获得Lock对象。

* ReentrantLock类实现了Lock ，它拥有与synchronized相同的并发性和内存语义，在实现线程安全的控制中，比较常用的是ReentrantLock，可以显式加锁、释放锁。

* 从JDK 5.0开始，Java提供了更强大的线程同步机制——通过显式定义同步锁对象来实现同步。同步锁使用Lock对象充当。

  ```java
  import java.util.concurrent.locks.ReentrantLock;
  
  /**
   * 解决线程安全问题的方式三：lock锁---》JDK5.0新增
   *
   * 注意：如果同步代码有异常，要将unlock()写入finally语句块
   *
   * 1. 面试题：synchronized 与 Lock的异同？
   *    相同：二者都可以解决线程安全问题
   *    不同：synchronized机制在执行完相应的同步代码以后，自动的释放同步监视器
   *         Lock需要手动的启动同步（lock()），同时结束同步也需要手动的实现（unlock()）
   *
   * 2.优先使用顺序：
   *      Lock 同步代码块（已经进入了方法体，分配了相应资源）同步方法（在方法体之外）
   *
   * 面试题：如何解决线程安全问题？有几种方式
   */
  
  class Windows implements Runnable{
  
      private int ticket = 100;
      //1.实例化ReentrantLock
      private ReentrantLock lock = new ReentrantLock();
  
  
      @Override
      public void run() {
          while(true){
              try{
  
                  //调用锁定方法：lock()
                  lock.lock();
  
                  if(ticket > 0){
  
                      try {
                          Thread.sleep(100);
                      } catch (InterruptedException e) {
                          e.printStackTrace();
                      }
  
                      System.out.println(Thread.currentThread().getName() + ":售票，票号为: " + ticket);
                      ticket --;
                  }else{
                      break;
                  }
              }finally {
                  //3.调用解锁方法：unlock()
                  lock.unlock();
              }
          }
      }
  }
  
  public class LockTest {
      public static void main(String[] args) {
          Windows w = new Windows();
  
          Thread t1 = new Thread(w);
          Thread t2 = new Thread(w);
          Thread t3 = new Thread(w);
  
          t1.setName("窗口1");
          t2.setName("窗口2");
          t3.setName("窗口3");
  
          t1.start();
          t2.start();
          t3.start();
      }
  }
  ```

  练习：

  ```java
  /**
   * 银行有一个账户。
   * 有两个储户分别向同一个账户存3000元，每次存1000，存3次。
   * 每次存完打印账户余额。
   *
   * 分析：
   *      1.是否是多线程问题？是，两个储户线程
   *      2.是否有共享数据？有，账户（或账户余额）
   *      3.是否有线程安全问题？有
   *      4.需要考虑如何解决线程安全问题？同步机制：有三种方式。
   */
  class Account{
      private double balance;
  
      public Account(double balance){
          this.balance = balance;
      }
  
      //存钱
      public synchronized void deposit(double amt){
          if(amt > 0){
  
              try {
                  Thread.sleep(1000);
              } catch (InterruptedException e) {
                  e.printStackTrace();
              }
  
              balance += amt;
              System.out.println(Thread.currentThread().getName() + ":" + "存钱成功，当前余额:" + balance);
          }
      }
  }
  
  class Customer extends Thread{
  
      private Account acct;
      public Customer(Account acct){
          this.acct = acct;
      }
  
      @Override
      public void run() {
  
          for(int i = 0;i < 3;i++){
              acct.deposit(1000);
          }
      }
  }
  
  public class AccountTest {
      public static void main(String[] args) {
          Account acct = new Account(0);
          Customer c1 = new Customer(acct);
          Customer c2 = new Customer(acct);
  
          c1.setName("甲");
          c2.setName("乙");
  
          c1.start();
          c2.start();
      }
  }
  ```

### 5 线程的通信

  ```java
/**
 * 线程通信的例子：使用两个线程打印1-100。线程1, 线程2 交替打印
 *
 * 涉及到的三个方法：
 * wait():一旦执行此方法，当前线程就进入阻塞状态，并释放同步监视器。
 * notify():一旦执行此方法，就会唤醒被wait的一个线程。如果有多个线程被wait，就唤醒优先级高的那个。
 * notifyAll():一旦执行此方法，就会唤醒所有被wait的线程。
 *
 * 说明：
 *      1.wait()，notify()，notifyAll()三个方法必须使用在同步代码块或同步方法中。
 *      2.wait()，notify()，notifyAll()三个方法的调用者必须是同步代码块或同步方法中的同步监视器。
 *         否则，会出现IllegalMonitorStateException异常
 *      3.wait()，notify()，notifyAll()三个方法是定义在java.lang.Object类中。
 */

class Number implements Runnable{

    private int number = 1;
    public Object obj = new Object();

    @Override
    public void run() {

        while (true){
            synchronized (obj) {

                obj.notify();

                if(number <= 100){

                    try {
                        Thread.sleep(10);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    System.out.println(Thread.currentThread().getName() + ":" + number);
                    number++;

                    try {
                        //使得调用如下wait()方法的线程进入阻塞状态
                        obj.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                }else{
                    break;
                }
            }
        }
    }
}

public class CommunicationTest {
    public static void main(String[] args) {
        Number number = new Number();
        Thread t1 = new Thread(number);
        Thread t2 = new Thread(number);

        t1.setName("线程1");
        t2.setName("线程2");

        t1.start();
        t2.start();
    }
}

  ```

#### 5-1 sleep() 和wait()的异同

  面试题：sleep() 和 wait()的异同？

   * 1.相同点：一旦执行方法，都可以使得当前的线程进入阻塞状态。
   * 2.不同点：1）两个方法声明的位置不同：Thread类中声明sleep() , Object类中声明wait()
   * 2）调用的要求不同：sleep()可以在任何需要的场景下调用。 wait()必须使用在同步代码块或同步方法中
   * 3）关于是否释放同步监视器：如果两个方法都使用在同步代码块或同步方法中，sleep()不会释放锁，wait()会释放锁。

#### 5-2、经典例题：生产者/消费者问题

![img](https://img-blog.csdnimg.cn/img_convert/ac291433d4e2f43d4517b1b92043e95a.png)

```java
/**
 * 线程通信的应用：经典例题：生产者/消费者问题
 *
 * 生产者(Productor)将产品交给店员(Clerk)，而消费者(Customer)从店员处取走产品，
 * 店员一次只能持有固定数量的产品(比如:20），如果生产者试图生产更多的产品，
 * 店员会叫生产者停一下，如果店中有空位放产品了再通知生产者继续生产；
 * 如果店中没有产品了，店员会告诉消费者等一下，
 * 如果店中有产品了再通知消费者来取走产品。
 *
 * 分析：
 *      1.是否是多线程的问题？是，生产者的线程，消费者的线程
 *      2.是否有共享数据的问题？是，店员、产品、产品数
 *      3.如何解决线程的安全问题？同步机制，有三种方法
 *      4.是否涉及线程的通信？是
 */

class Clerk{

    private int productCount = 0;

    //生产产品
    public synchronized void produceProduct() {

        if(productCount < 20){
            productCount++;
            System.out.println(Thread.currentThread().getName() + ": 开始生产第" + productCount + "个产品");

            notify();
        }else{
            //等待
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }

    }

    //消费产品
    public synchronized void consumeProduct() {

        if(productCount > 0){
            System.out.println(Thread.currentThread().getName() + ":开始消费第" + productCount + "个产品");
            productCount--;

            notify();
        }else{
            //等待
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }

}

class Producer extends Thread{//生产者
    private Clerk clerk;

    public Producer(Clerk clerk){
        this.clerk = clerk;
    }

    @Override
    public void run() {
        System.out.println(getName() + ": 开始生产产品......");

        while(true){

            try {
                Thread.sleep(10);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

            clerk.produceProduct();
        }
    }
}

class Consumer extends Thread{  //消费者
    private Clerk clerk;

    public Consumer(Clerk clerk){
        this.clerk = clerk;
    }

    @Override
    public void run() {
        System.out.println(getName() + ": 开始消费产品......");

        while(true){

            try {
                Thread.sleep(20);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

            clerk.consumeProduct();
        }

    }
}

public class ProductTest {
    public static void main(String[] args) {
        Clerk clerk = new Clerk();

        Producer p1 = new Producer(clerk);
        p1.setName("生产者1");

        Consumer c1 = new Consumer(clerk);
        c1.setName("消费者1");
        Consumer c2 = new Consumer(clerk);
        c2.setName("消费者2");

        p1.start();
        c1.start();
        c2.start();
    }
}				
```

### 6、JDK5.0新增线程创建方式

#### 6-1、创建多线程的方式三：实现Callable接口

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

/**
 * 创建多线程的方式三：实现Callable接口 ---> JDK 5.0新增
 *
 * 如何理解实现Callable接口的方式创建多线程比实现Runnable接口创建多线程方式强大？
 *      1.call()可以有返回值的。
 *      2.call()可以抛出异常，被外面的操作捕获，获取异常的信息
 *      3.Callable是支持泛型的
 *      4.需要借助FutureTask类，比如获取返回结果
 */
//1.创建一个实现Callable的实现类
class NumThread implements Callable{

    //2.实现call方法，将此线程需要执行的操作声明在call()中
    @Override
    public Object call() throws Exception {
        int sum = 0;
        for(int i = 1;i <= 100;i++){
            if(i % 2 == 0){
                System.out.println(i);
                sum += i;
            }
        }
        return sum;
    }
}

public class ThreadNew {
    public static void main(String[] args) {
        //3.创建Callable接口实现类的对象
        NumThread numThread = new NumThread();

        //4.将此Callable接口实现类的对象作为传递到FutureTask构造器中，创建FutureTask的对象
        FutureTask futureTask = new FutureTask(numThread);

        //5.将FutureTask的对象作为参数传递到Thread类的构造器中，创建Thread对象，并调用start()
        new Thread(futureTask).start();

        try {
            //6.获取Callable中call方法的返回值
            //get()返回值即为FutureTask构造器参数Callable实现类重写的call()的返回值。
            Object sum = futureTask.get();
            System.out.println("总和为:" + sum);
        } catch (InterruptedException e) {
            e.printStackTrace();
        } catch (ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

Future接口

* 可以对具体Runnable、Callable任务的执行结果进行取消、查询是否完成、获取结果等。
* FutrueTask是Futrue接口的唯一的实现类
* FutureTask同时实现了Runnable, Future接口。它既可以作为Runnable被线程执行，又可以作为Future得到Callable的返回值

#### 6-2使用线程池的好处

1、背景：

经常创建和销毁、使用量特别大的资源，比如并发情况下的线程，对性能影响很大。

2、思路：

提前创建好多个线程，放入线程池中，使用时直接获取，使用完放回池中。可以避免频繁创建销毁、实现重复利用。类似生活中的公共交通工具。

3、好处：

* 提高响应速度（减少了创建新线程的时间）
* 降低资源消耗（重复利用线程池中线程，不需要每次都创建）
* 便于线程管理
  	corePoolSize：核心池的大小
  	maximumPoolSize：最大线程数
  	keepAliveTime：线程没有任务时最多保持多长时	间后会终止
  	…

#### 6-3创建多线程的方式四：使用线程池

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.ThreadPoolExecutor;

/**
 * 创建多线程的方式四：使用线程池
 *
 * 好处：
 *      1.提高响应速度（减少了创建新线程的时间）
 *      2.降低资源消耗（重复利用线程池中线程，不需要每次都创建）
 *      3.便于线程管理
 *          corePoolSize：核心池的大小
 *          maximumPoolSize：最大线程数
 *          keepAliveTime：线程没有任务时最多保持多长时间后会终止
 *
 * 面试题：创建多线程有几种方式？四种！
 */

class NumberThread implements Runnable{
    @Override
    public void run() {
        for(int i = 0;i <= 100;i++){
            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}

class NumberThread1 implements Runnable{
    @Override
    public void run() {
        for(int i = 0;i <= 100;i++){
            if(i % 2 != 0){
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}

public class ThreadPool {
    public static void main(String[] args) {

        //1. 提供指定线程数量的线程池
        ExecutorService service = Executors.newFixedThreadPool(10);
        ThreadPoolExecutor service1 = (ThreadPoolExecutor) service;
        //设置线程池的属性
//        System.out.println(service.getClass());
//        service1.setCorePoolSize(15);
//        service1.setKeepAliveTime();

        //2.执行指定的线程的操作。需要提供实现Runnable接口或Callable接口实现类的对象
        service.execute(new NumberThread());  //适合适用于Runable
        service.execute(new NumberThread1());  //适合适用于Runable

//        service.submit(Callable callable);   //适合适用于Callable

        //3.关闭连接池
        service.shutdown();
    }
}
```

线程池相关API

​		JDK 5.0起提供了线程池相关API：ExecutorService和Executors

* ExecutorService：真正的线程池接口。常见子类ThreadPoolExecutor
  * void execute(Runnable command) ：执行任务/命令，没有返回值，一般用来执行Runnable
  * Future submit(Callable task)：执行任务，有返回值，一般又来执行Callable
    void shutdown()：关闭连接池
* Executors：工具类、线程池的工厂类，用于创建并返回不同类型的线程池
  * Executors.newCachedThreadPool()：创建一个可根据需要创建新线程的线程池
  * Executors.newFixedThreadPool(n); 创建一个可重用固定线程数的线程池
  * Executors.newSingleThreadExecutor()：创建一个只有一个线程的线程池
  * Executors.newScheduledThreadPool(n)：创建一个线程池，它可安排在给定延迟后运行命令或者定期地执行。

## 12、常用类

### 1.字符串相关类

#### 1-1、String类的概述

####  

```java
import org.junit.Test;

/**
 * String的使用
 */
public class StringTest {

    /**
     * String:字符串，使用一对“”引起来表示。
     * 1.String声明为final的，不可被继承
     * 2.String实现了Serializable接口：表示字符串是支持序列化的。
     *         实现了Comparable接口：表示String可以比较大小
     * 3.String内部定义了final char[] value用于存储字符串数据
     * 4.String:代表不可变的字符序列。简称：不可变性。
     *      体现：
     *
     */
    @Test
    public void Test1(){

    }
}

```

#### 1-2理解String 的不可变性

```java
import org.junit.Test;

/**
 * String的使用
 */
public class StringTest {

    /**
     * String:字符串，使用一对“”引起来表示。
     * 1.String声明为final的，不可被继承
     * 2.String实现了Serializable接口：表示字符串是支持序列化的。
     *         实现了Comparable接口：表示String可以比较大小
     * 3.String内部定义了final char[] value用于存储字符串数据
     * 4.String:代表不可变的字符序列。简称：不可变性。
     *      体现：1.当对字符串重新赋值时，需要重写指定内存区域赋值，不能使用原有的value进行赋值。
     *           2.当对现有的字符串进行连接操作时，也需要重新指定内存区域赋值，不能使用原有的value进行赋值。
     *           3.当调用String的replace()方法修改指定字符或字符串时，也需要重新指定内存区域赋值，不能使用原有的value进行赋值。
     * 5.通过字面量的方式（区别于new）给一个字符串赋值，此时的字符串值声明在字符串常量池中。
     * 6.字符串常量池中是不会存储相同内容的字符串的。
     *
     */
    @Test
    public void Test1(){
        String s1 = "abc";  //字面量的定义方式
        String s2 = "abc";
        s1 = "hello";

        System.out.println(s1 == s2);//比较s1和s2的地址值

        System.out.println(s1);//hello
        System.out.println(s2);//abc

        System.out.println("*********************");

        String s3 = "abc";
        s3 += "def";
        System.out.println(s3);//abcdef

        System.out.println("**********************");

        String s4 = "abc";
        String s5 = s4.replace('a', 'm');
        System.out.println(s4);//abc
        System.out.println(s5);//mbc
    }
}

```

![img](https://img-blog.csdnimg.cn/20200509201648472.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTUzOTQ5,size_16,color_FFFFFF,t_70#pic_center)

#### 1-3、String不同实例化方式的对比

1、String对象的创建

```java
String str = "hello";

//本质上this.value = new char[0];
String  s1 = new String(); 

//this.value = original.value;
String  s2 = new String(String original); 

//this.value = Arrays.copyOf(value, value.length);
String  s3 = new String(char[] a);

String  s4 = new String(char[] a,int startIndex,int count);

```

![img](https://img-blog.csdnimg.cn/20200509201719650.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTUzOTQ5,size_16,color_FFFFFF,t_70#pic_center)

![img](https://img-blog.csdnimg.cn/20200509201719569.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTUzOTQ5,size_16,color_FFFFFF,t_70#pic_center)

**2、String str1 = “abc”;与String str2 = new String(“abc”);的区别？**

- 字符串常量存储在字符串常量池，目的是共享
- 字符串非常量对象存储在堆中。

![img](https://img-blog.csdnimg.cn/20200509201753900.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTUzOTQ5,size_16,color_FFFFFF,t_70#pic_center)

3、**练习**

![img](https://img-blog.csdnimg.cn/20200509201810827.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTUzOTQ5,size_16,color_FFFFFF,t_70#pic_center)

```java
import org.junit.Test;

/**
 * String的使用
 */
public class StringTest {

    /**
     * String的实例化方式
     * 方式一：通过字面量定义的方式
     * 方式二：通过new + 构造器的方式
     *
     * 面试题：String s = new String("abc");方式创建对象，在内存中创建了几个对象？
     *      两个:一个是堆空间中new结构，另一个是char[]对应的常量池中的数据："abc"
     *
     */
    @Test
    public void test2(){
        //通过字面量定义的方式：此时的s1和s2的数据javaEE声明在方法区中的字符串常量池中。
        String s1 = "javaEE";
        String s2 = "javaEE";

        //通过new + 构造器的方式:此时的s3和s4保存的地址值，是数据在堆空间中开辟空间以后对应的地址值。
        String s3 = new String("javaEE");
        String s4 = new String("javaEE");

        System.out.println(s1 == s2);//true
        System.out.println(s1 == s3);//false
        System.out.println(s1 == s4);//false
        System.out.println(s3 == s4);//false

        System.out.println("***********************");
        Person p1 = new Person("Tom",12);
        Person p2 = new Person("Tom",12);

        System.out.println(p1.name.equals(p2.name));//true
        System.out.println(p1.name == p2.name);//true

        p1.name = "Jerry";
        System.out.println(p2.name);//Tom
    }
}

```

```java
/**
 * @author subei
 * @create 2020-05-09 11:20
 */
public class Person {

    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public Person() {

    }
}
```

![img](https://img-blog.csdnimg.cn/20200509201833464.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTUzOTQ5,size_16,color_FFFFFF,t_70#pic_center)

#### 1-4、String 不同拼接操作的对比

```java
import org.junit.Test;

/**
 * String的使用
 */
public class StringTest {

    /**
     * 结论
     *     1.常量与常量的拼接结果在常量池。且常量池中不会存在相同内容的常量。
     *     2.只要其中有一个是变量，结果就在堆中
     *     3.如果拼接的结果调用intern()方法，返回值就在常量池中
     *
     */
    @Test
    public void test4(){
        String s1 = "javaEEhadoop";
        String s2 = "javaEE";
        String s3 = s2 + "hadoop";
        System.out.println(s1 == s3);//false

        final String s4 = "javaEE";//s4:常量
        String s5 = s4 + "hadoop";
        System.out.println(s1 == s5);//true

    }

    @Test
    public void test3(){
        String s1 = "javaEE";
        String s2 = "hadoop";

        String s3 = "javaEEhadoop";
        String s4 = "javaEE" + "hadoop";
        String s5 = s1 + "hadoop";
        String s6 = "javaEE" + s2;
        String s7 = s1 + s2;

        System.out.println(s3 == s4);//true
        System.out.println(s3 == s5);//false
        System.out.println(s3 == s6);//false
        System.out.println(s5 == s6);//false
        System.out.println(s3 == s7);//false
        System.out.println(s5 == s6);//false
        System.out.println(s5 == s7);//false
        System.out.println(s6 == s7);//false

        String s8 = s5.intern();//返回值得到的s8使用的常量值中已经存在的“javaEEhadoop”
        System.out.println(s3 == s8);//true
    }
}
```

##### 1-4-1、String使用陷阱

1、String s1 = “a”;

说明：在字符串常量池中创建了一个字面量为"a"的字符串。

2、s1 = s1 + “b”;

说明：实际上原来的“a”字符串对象已经丢弃了，现在在堆空间中产生了一个字符串s1+“b”（也就是"ab")。如果多次执行这些改变串内容的操作，会导致大量副本字符串对象存留在内存中，降低效率。如果这样的操作放到循环中，会极大影响程序的性能。

3、String s2 = “ab”;

说明：直接在字符串常量池中创建一个字面量为"ab"的字符串。

4、String s3 = “a” + “b”;

说明：s3指向字符串常量池中已经创建的"ab"的字符串。

5、String s4 = s1.intern();

说明：堆空间的s1对象在调用intern()之后，会将常量池中已经存在的"ab"字符串赋值给s4。
6、练习

![img](https://img-blog.csdnimg.cn/20200509201854255.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTUzOTQ5,size_16,color_FFFFFF,t_70#pic_center)

#### 1-5、String的一道面试题

```java
/**
 * 一道面试题
 */
public class StringTest {
    String str = new String("good");
    char[] ch = { 't', 'e', 's', 't' };

    public void change(String str, char ch[]) {
        str = "test ok";
        ch[0] = 'b';
    }
    public static void main(String[] args) {
        StringTest ex = new StringTest();
        ex.change(ex.str, ex.ch);
        System.out.println(ex.str);//good
        System.out.println(ex.ch);//best
    }
}

```

#### 1-6、JVM中涉及字符串的内存结构

![img](https://img-blog.csdnimg.cn/img_convert/4bf4b2285af70e363da6445fe73896c7.png)

![img](https://img-blog.csdnimg.cn/img_convert/5a2f00eaeeb8d0ec04465632e551dca8.png)

![img](https://img-blog.csdnimg.cn/img_convert/94b148a54b3c86ec101b9b88fc885067.png)

![img](https://img-blog.csdnimg.cn/img_convert/aa3755823eee56483b00f06c1e905ec6.png)

![img](https://img-blog.csdnimg.cn/img_convert/d48e2620b1e1997102c86dfc932977ff.png)

![img](https://img-blog.csdnimg.cn/img_convert/c5c4dd11e2610077965445af6e822767.png)

![img](https://img-blog.csdnimg.cn/img_convert/83d0b732dff16d3852b75b44231f56b1.png)

![img](https://img-blog.csdnimg.cn/img_convert/e71ddbdda5c97fd91a19e3538987a7a2.png)

![img](https://img-blog.csdnimg.cn/img_convert/705c8dc581ebcd5279ac303302c88247.png)

![img](https://img-blog.csdnimg.cn/img_convert/4a022a19ef84a70eb734285dd81340bd.png)

![img](https://img-blog.csdnimg.cn/img_convert/a1d069bfdf3b25e95a2b5e793a8cfab7.png)

#### 1-7、String的常用方法

```java
import org.junit.Test;

public class StringMethodTest {

    /**
     * int length()：返回字符串的长度：return value.length
     * char charAt(int index)：返回某索引处的字符return value[index]
     * boolean isEmpty()：判断是否是空字符串：return value.length==0
     * String toLowerCase()：使用默认语言环境，将String中的所有字符转换为小写
     * String toUpperCase()：使用默认语言环境，将String中的所有字符转换为大写
     * String trim()：返回字符串的副本，忽略前导空白和尾部空白
     * boolean equals(Object obj)：比较字符串的内容是否相同
     * boolean equals IgnoreCase(String anotherString)：与equals方法类似，忽略大小写
     * String concat(String str)：将指定字符串连接到此字符串的结尾。等价于用“+”
     * int compareTo(String anotherString)：比较两个字符串的大小
     * String substring(int beginIndex)：返回一个新的字符串，它是此字符串的从beginIndex开始截取到最后的一个子字符串。
     * String substring(int beginIndex,int endIndex)：返回一个新字符串，它是此字符串从beginIndex开始截取到endIndex(不包含)的一个子字符串。
     */
    @Test
    public void test2(){
        String s1 = "HelloWorld";
        String s2 = "helloworld";
        System.out.println(s1.equals(s2));//false
        System.out.println(s1.equalsIgnoreCase(s2));//true
        
        String s3 = "abc";
        String s4 = s3.concat("def");
        System.out.println(s4);//abcdef

        String s5 = "abc";
        String s6 = new String("abe");
        System.out.println(s5.compareTo(s6));//-2   //涉及到字符串的排序

        String s7 = "周围好吵啊";
        String s8 = s7.substring(2);
        System.out.println(s7);
        System.out.println(s8);

        String s9 = s7.substring(0, 2);
        System.out.println(s9);
    }

    @Test
    public void Test1(){
        String s1 = "helloworld";
        System.out.println(s1.length());
        System.out.println(s1.length());
        System.out.println(s1.charAt(0));
        System.out.println(s1.charAt(9));
//        System.out.println(s1.charAt(10));
//        s1 = "";
        System.out.println(s1.isEmpty());

        String s2 = s1.toLowerCase();
        System.out.println(s1);//s1不可变的，仍然为原来的字符串
        System.out.println(s2);//改成小写以后的字符串

        String s3 = "   he  llo   world   ";
        String s4 = s3.trim();
        System.out.println("-----" + s3 + "-----");
        System.out.println("-----" + s4 + "-----");
    }

}
```

#### 1-8、String的常用方法2

```java
import org.junit.Test;

public class StringMethodTest {

    /**
     * boolean endsWith(String suffix)：测试此字符串是否以指定的后缀结束
     * boolean startsWith(String prefix)：测试此字符串是否以指定的前缀开始
     * boolean startsWith(String prefix, int toffset)：测试此字符串从指定索引开始的子字符串是否以指定前缀开始
     *
     * boolean contains(CharSequence s)：当且仅当此字符串包含指定的 char 值序列时，返回 true
     * int indexOf(String str)：返回指定子字符串在此字符串中第一次出现处的索引
     * int indexOf(String str, int fromIndex)：返回指定子字符串在此字符串中第一次出现处的索引，从指定的索引开始
     * int lastIndexOf(String str)：返回指定子字符串在此字符串中最右边出现处的索引
     * int lastIndexOf(String str, int fromIndex)：返回指定子字符串在此字符串中最后一次出现处的索引，从指定的索引开始反向搜索
     *
     * 注：indexOf和lastIndexOf方法如果未找到都是返回-1
     */
    @Test
    public void test3(){
        String str1 = "helloworld";
        boolean b1 = str1.endsWith("rld");
        System.out.println(b1);

        boolean b2 = str1.startsWith("He");
        System.out.println(b2);

        boolean b3 = str1.startsWith("ll",2);
        System.out.println(b3);

        String str2 = "wor";
        System.out.println(str1.contains(str2));

        System.out.println(str1.indexOf("lo"));

        System.out.println(str1.indexOf("lo",5));

        String str3 = "hellorworld";

        System.out.println(str3.lastIndexOf("or"));
        System.out.println(str3.lastIndexOf("or",6));

        //什么情况下，indexOf(str)和lastIndexOf(str)返回值相同？
        //情况一：存在唯一的一个str。情况二：不存在str
    }
}

```

#### 1-9、String的常用方法3

```java
import org.junit.Test;

public class StringMethodTest {

    /**
     * 替换：
     * String replace(char oldChar, char newChar)：返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的所有 oldChar 得到的。
     * String replace(CharSequence target, CharSequence replacement)：使用指定的字面值替换序列替换此字符串所有匹配字面值目标序列的子字符串。
     * String replaceAll(String regex, String replacement)：使用给定的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串。
     * String replaceFirst(String regex, String replacement)：使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。
     *
     * 匹配:
     * boolean matches(String regex)：告知此字符串是否匹配给定的正则表达式。
     *
     * 切片：
     * String[] split(String regex)：根据给定正则表达式的匹配拆分此字符串。
     * String[] split(String regex, int limit)：根据匹配给定的正则表达式来拆分此字符串，最多不超过limit个，如果超过了，剩下的全部都放到最后一个元素中。
     *
     */
    @Test
    public void test4(){
        String str1 = "西藏布达拉宫欢迎您";
        String str2 = str1.replace('西','东');

        System.out.println(str1);
        System.out.println(str2);

        String str3 = str1.replace("北京", "南京");
        System.out.println(str3);

        System.out.println("*************************");
        String str = "12hello34world5java7891mysql456";
        //把字符串中的数字替换成,，如果结果中开头和结尾有，的话去掉
        String string = str.replaceAll("\\d+", ",").replaceAll("^,|,$", "");
        System.out.println(string);

        System.out.println("*************************");
        str = "12345";
        //判断str字符串中是否全部有数字组成，即有1-n个数字组成
        boolean matches = str.matches("\\d+");
        System.out.println(matches);
        String tel = "0571-4534289";
        //判断这是否是一个杭州的固定电话
        boolean result = tel.matches("0571-\\d{7,8}");
        System.out.println(result);

        System.out.println("*************************");
        str = "hello|world|java";
        String[] strs = str.split("\\|");
        for (int i = 0; i < strs.length; i++) {
            System.out.println(strs[i]);
        }
        System.out.println();
        str2 = "hello.world.java";
        String[] strs2 = str2.split("\\.");
        for (int i = 0; i < strs2.length; i++) {
            System.out.println(strs2[i]);
        }
    }
}
```

#### 1-10、String与基本数据类型包装类的转换

```java
import org.junit.Test;

/**
 * 涉及到String类与其他结构之间的转换
 */
public class StringTest1 {

    /**
     * 复习
     *    String与基本数据类型、包装类之间的转换
     *
     *    String --> 基本数据类型、包装类：调用包装类的静态方法：parseXxx(str)
     *    基本数据类型、包装类 --> String:调用String重载的valueOf(xxx)
     */
    @Test
    public void test1(){
        String str1 = "123";
//        int num = (int)str1;//错误的
        int num = Integer.parseInt(str1);

        String str2 = String.valueOf(num);   //"123
        String str3 = num + "";

        System.out.println(str1 == str3);   //false
    }

}
```

#### 1-11、String与char[]之间的转换

```java
import org.junit.Test;

/**
 * 涉及到String类与其他结构之间的转换
 */
public class StringTest1 {

    /**
     * String 与 char[]之间的转换
     *
     * String --> char[]:调用String的toCharArray()
     * char[] --> String:调用String的构造器
     */
    @Test
    public void test2(){
        String str1 = "abc123"; //题目： a21cb3

        char[] charArray = str1.toCharArray();
        for (int i = 0; i < charArray.length; i++) {
            System.out.println(charArray[i]);
        }

        char[] arr = new char[]{'h','e','l','l','o'};
        String str2 = new String(arr);
        System.out.println(str2);
    }
}
```

#### 1-12、String与byte[]之间的转换

```java
import org.junit.Test;

import java.io.UnsupportedEncodingException;
import java.util.Arrays;

/**
 * 涉及到String类与其他结构之间的转换
 */
public class StringTest1 {

    /**
     * String 与 byte[]之间的转换
     *
     * 编码：String --> byte[]:调用String的getBytes()
     * 解码：byte[] --> String:调用String的构造器
     *
     * 编码：字符串 -->字节  (看得懂 --->看不懂的二进制数据)
     * 解码：编码的逆过程，字节 --> 字符串 （看不懂的二进制数据 ---> 看得懂）
     *
     * 说明：解码时，要求解码使用的字符集必须与编码时使用的字符集一致，否则会出现乱码。
     *
     */
    @Test
    public void test3() throws UnsupportedEncodingException {
        String str1 = "abc123重工";
        byte[] bytes = str1.getBytes();//使用默认的字符编码集,进行转换
        System.out.println(Arrays.toString(bytes));

        byte[] gbks = str1.getBytes("gbk");//使用gbk字符集进行编码。
        System.out.println(Arrays.toString(gbks));

        System.out.println("*****************************");

        String str2 = new String(bytes);//使用默认的字符集，进行解码。
        System.out.println(str2);

        String str3 = new String(gbks);
        System.out.println(str3);//出现乱码。原因：编码集和解码集不一致！

        String str4 = new String(gbks,"gbk");
        System.out.println(str4);//没有出现乱码。原因：编码集和解码集一致！
    }
}
```

#### 1-13、面试中String算法考查的说明

1、模拟一个trim方法，去除字符串两端的空格。

```java
import org.junit.Test;

/*
 * 1.模拟一个trim方法，去除字符串两端的空格。
 * 
 */
public class StringExer {

	// 第1题
	public String myTrim(String str) {
		if (str != null) {
			int start = 0;// 用于记录从前往后首次索引位置不是空格的位置的索引
			int end = str.length() - 1;// 用于记录从后往前首次索引位置不是空格的位置的索引

			while (start < end && str.charAt(start) == ' ') {
				start++;
			}

			while (start < end && str.charAt(end) == ' ') {
				end--;
			}
			if (str.charAt(start) == ' ') {
				return "";
			}

			return str.substring(start, end + 1);
		}
		return null;
	}
	
	@Test
	public void testMyTrim() {
		String str = "   a   ";
		// str = " ";
		String newStr = myTrim(str);
		System.out.println("---" + newStr + "---");
	}
}
```

2、将一个字符串进行反转。将字符串中指定部分进行反转。比如“abcdefg”反转为”abfedcg”

```java
import org.junit.Test;

public class StringDemo {

    /**
     * 将一个字符串进行反转。将字符串中指定部分进行反转。比如“abcdefg”反转为”abfedcg”
     *
     * 方式一：转换为char[]
     */
    public String reverse(String str,int startIndex,int endIndex){

        if(str != null && str.length() != 0) {
            char[] arr = str.toCharArray();
            for (int x = startIndex, y = endIndex; x < y; x++, y--) {
                char temp = arr[x];
                arr[x] = arr[y];
                arr[y] = temp;
            }
            return new String(arr);
        }
        return null;
    }

    /**
     * 方式二：使用String的拼接
     */
    public String reverse2(String str, int startIndex, int endIndex) {
        if(str != null) {
            // 第一部分
            String reverStr = str.substring(0,startIndex);// ab
            // 第二部分
            for (int i = endIndex; i >= startIndex; i--) {
                reverStr += str.charAt(i);
            } // abfedc
            // 第三部分
            reverStr += str.substring(endIndex + 1);

            return reverStr;
        }
        return null;
    }

    //方式三：使用StringBuffer/StringBuilder替换String
    public String reverse3(String str, int startIndex, int endIndex) {
        StringBuilder builder = new StringBuilder(str.length());

        if(str != null) {
            //第一部分
            builder.append(str.substring(0, startIndex));

            //第二部分
            for (int i = endIndex; i >= startIndex; i--) {

                builder.append(str.charAt(i));
            }
            //第三部分
            builder.append(str.substring(endIndex + 1));

            return builder.toString();
        }
        return null;
    }

    @Test
    public void testReverse() {
        String str = "abcdefg";
        String str1 = reverse3(str, 2, 5);
        System.out.println(str1);// abfedcg

    }
}
```

3、获取一个字符串在另一个字符串中出现的次数。比如：获取“ ab”在“abkkcadkabkebfkabkskab” 中出现的次数

```java
import org.junit.Test;

public class StringDemo2 {
    /**
     * 获取一个字符串在另一个字符串中出现的次数。
     * 比如：获取“ ab”在“abkkcadkabkebfkabkskab” 中出现的次数
     *
     */

    /**
     * 获取subStr在mainStr中出现的次数
     * @param mainStr
     * @param subStr
     */
    public int getCount(String mainStr,String subStr){
        int mainLength = mainStr.length();
        int subLength = subStr.length();
        int count = 0;
        int index = 0;

        if(mainLength >= subLength){

            //方式一：
//            while((index = mainStr.indexOf(subStr)) != -1){
//                count++;
//                mainStr = mainStr.substring(index + subStr.length());
//            }
            //方式二：对方式一的改进
            while((index = mainStr.indexOf(subStr,index)) != -1){
                count++;
                index += subLength;
            }

            return count;
        }else{
            return 0;
        }
    }

    @Test
    public void testGetCount(){
        String mainStr = "abkkcadkabkebfkabkskab";
        String subStr = "ab";
        int count = getCount(mainStr,subStr);
        System.out.println(count);
    }

}
```

4、获取两个字符串中最大相同子串。比如：

```
str1 = "abcwerthelloyuiodef“;str2 = “cvhellobnm”
```

提示：将短的那个串进行长度依次递减的子串与较长的串比较。

```java
import org.junit.Test;

import java.util.Arrays;

public class StringDemo3 {
    /**
     * 获取两个字符串中最大相同子串。比如：
     * str1 = "abcwerthelloyuiodef“;str2 = "cvhellobnm"
     * 提示：将短的那个串进行长度依次递减的子串与较长的串比较。
     */
    //前提：两个字符串中只有一个最大相同子串
    public String getMaxSameString(String str1,String str2){
        if(str1 != null && str2 != null){
            String maxStr = (str1.length() >= str2.length())? str1 : str2;
            String minStr = (str1.length() < str2.length())? str1 : str2;
            int length = minStr.length();

            for(int i = 0;i < length;i++){
                for(int x = 0,y = length - i;y <= length;x++,y++){
                    String subStr = minStr.substring(x,y);
                    if(maxStr.contains(subStr)){
                        return subStr;
                    }

                }
            }

        }
        return null;
    }

    // 如果存在多个长度相同的最大相同子串
    // 此时先返回String[]，后面可以用集合中的ArrayList替换，较方便
    public String[] getMaxSameString1(String str1, String str2) {
        if (str1 != null && str2 != null) {
            StringBuffer sBuffer = new StringBuffer();
            String maxString = (str1.length() > str2.length()) ? str1 : str2;
            String minString = (str1.length() > str2.length()) ? str2 : str1;

            int len = minString.length();
            for (int i = 0; i < len; i++) {
                for (int x = 0, y = len - i; y <= len; x++, y++) {
                    String subString = minString.substring(x, y);
                    if (maxString.contains(subString)) {
                        sBuffer.append(subString + ",");
                    }
                }
//                System.out.println(sBuffer);
                if (sBuffer.length() != 0) {
                    break;
                }
            }
            String[] split = sBuffer.toString().replaceAll(",$", "").split("\\,");
            return split;
        }

        return null;
    }

    @Test
    public void testGetMaxSameString(){
        String str1 = "abcwerthello1yuiodefabcdef";
        String str2 = "cvhello1bnmabcdef";
        String[] maxSameStrings = getMaxSameString1(str1, str2);
        System.out.println(Arrays.toString(maxSameStrings));

    }

}
```

5、对字符串中字符进行自然顺序排序。

提示：

1）字符串变成字符数组。

2）对数组排序，选择，冒泡，Arrays.sort();

3）将排序后的数组变成字符串。

```java
import org.junit.Test;
import java.util.Arrays;

/**
 *
 * 5.对字符串中字符进行自然顺序排序。"abcwerthelloyuiodef"
 * 提示：
 * 		1）字符串变成字符数组。
 * 		2）对数组排序，选择，冒泡，Arrays.sort(str.toCharArray());
 * 		3）将排序后的数组变成字符串。
 *
 */

public class StringDemo4 {

	// 第5题
	@Test
	public void testSort() {
		String str = "abcwerthelloyuiodef";
		char[] arr = str.toCharArray();
		Arrays.sort(arr);

		String newStr = new String(arr);
		System.out.println(newStr);
	}
}
```

#### 1-14、StringBuffer和StringBuilder的介绍

```java
/**
 * String、StringBuffer、StringBuilder三者的异同？
 *
 * String:不可变的字符序列；底层使用char[]存储
 * StringBuffer:可变的字符序列；线程安全的，效率低；底层使用char[]存储
 * StringBuilder:可变的字符序列；jdk5.0新增的，线程不安全的，效率高；底层使用char[]存储
 *
 */

```

#### 1-15、StringBuffer的源码分析

```java
import org.junit.Test;

/**
 * 关于StringBuffer和StringBuilder的使用
 */
public class StringBufferBuilderTest {
    /**
     *
     * 源码分析：
     * String str = new String();//char[] value = new char[0];
     * String str1 = new String("abc");//char[] value = new char[]{'a','b','c'};
     *
     * StringBuffer sb1 = new StringBuffer();//char[] value = new char[16];底层创建了一个长度是16的数组。
     * System.out.println(sb1.length());//
     * sb1.append('a');//value[0] = 'a';
     * sb1.append('b');//value[1] = 'b';
     *
     * StringBuffer sb2 = new StringBuffer("abc");//char[] value = new char["abc".length() + 16];
     *
     * //问题1.System.out.println(sb2.length());//3
     * //问题2.扩容问题:如果要添加的数据底层数组盛不下了，那就需要扩容底层的数组。
     *        默认情况下，扩容为原来容量的2倍 + 2，同时将原有数组中的元素复制到新的数组中。
     *
     * 意义：开发中建议大家使用：StringBuffer(int capacity) 或 StringBuilder(int capacity)
     *
     */
    @Test
    public void test1(){
        StringBuffer sb1 = new StringBuffer("abc");
        sb1.setCharAt(0,'m');
        System.out.println(sb1);

        StringBuffer sb2 = new StringBuffer();
        System.out.println(sb2.length());   //0
    }
}
```

#### 1-16、StringBuffer中的常用方法

```java
import org.junit.Test;

/**
 * 关于StringBuffer和StringBuilder的使用
 */
public class StringBufferBuilderTest {

    /**
     * StringBuffer的常用方法：
     *
     * StringBuffer append(xxx)：提供了很多的append()方法，用于进行字符串拼接
     * StringBuffer delete(int start,int end)：删除指定位置的内容
     * StringBuffer replace(int start, int end, String str)：把[start,end)位置替换为str
     * StringBuffer insert(int offset, xxx)：在指定位置插入xxx
     * StringBuffer reverse() ：把当前字符序列逆转
     * public int indexOf(String str)
     * public String substring(int start,int end):返回一个从start开始到end索引结束的左闭右开区间的子字符串
     * public int length()
     * public char charAt(int n )
     * public void setCharAt(int n ,char ch)
     *
     * 总结：
     *     增：append(xxx)
     *     删：delete(int start,int end)
     *     改：setCharAt(int n ,char ch) / replace(int start, int end, String str)
     *     查：charAt(int n )
     *     插：insert(int offset, xxx)
     *     长度：length();
     *     遍历：for() + charAt() / toString()
     *
     */
    @Test
    public void test2(){
        StringBuffer s1 = new StringBuffer("abc");
        s1.append(1);
        s1.append('1');
        System.out.println(s1);
//        s1.delete(2,4);
//        s1.replace(2,4,"hello");
//        s1.insert(2,false);
//        s1.reverse();
        String s2 = s1.substring(1,3);
        System.out.println(s1);
        System.out.println(s1.length());
        System.out.println(s2);
    }
}
```

#### 1-17、String、StringBuffer、StringBuilder效率对比

```java
import org.junit.Test;

/**
 * 关于StringBuffer和StringBuilder的使用
 */
public class StringBufferBuilderTest {

    /**
     * 对比String、StringBuffer、StringBuilder三者的效率：
     * 从高到低排列：StringBuilder > StringBuffer > String
     *
     */
    @Test
    public void test3(){
        //初始设置
        long startTime = 0L;
        long endTime = 0L;
        String text = "";
        StringBuffer buffer = new StringBuffer("");
        StringBuilder builder = new StringBuilder("");
        //开始对比
        startTime = System.currentTimeMillis();
        for (int i = 0; i < 20000; i++) {
            buffer.append(String.valueOf(i));
        }
        endTime = System.currentTimeMillis();
        System.out.println("StringBuffer的执行时间：" + (endTime - startTime));

        startTime = System.currentTimeMillis();
        for (int i = 0; i < 20000; i++) {
            builder.append(String.valueOf(i));
        }
        endTime = System.currentTimeMillis();
        System.out.println("StringBuilder的执行时间：" + (endTime - startTime));

        startTime = System.currentTimeMillis();
        for (int i = 0; i < 20000; i++) {
            text = text + i;
        }
        endTime = System.currentTimeMillis();
        System.out.println("String的执行时间：" + (endTime - startTime));

    }
}
```

### 2、JDK8之前的日期时间API

![img](https://img-blog.csdnimg.cn/img_convert/01409d8ae2e27491b95fb69d861520ee.png)

#### 2-1、System类中获取时间戳的方法

System类提供的public static long currentTimeMillis()用来返回当前时间与1970年1月1日0时0分0秒之间以毫秒为单位的时间差。

此方法适于计算时间差。
计算世界时间的主要标准有：
UTC(Coordinated Universal Time)
GMT(Greenwich Mean Time)
CST(Central Standard Time)

```java
import org.junit.Test;

/**
 * JDK 8之前日期和时间的API测试
 */
public class DateTimeTest {

    //1.System类中的currentTimeMillis()
    @Test
    public void test1(){
        long time = System.currentTimeMillis();
        //返回当前时间与1970年1月1日0时0分0秒之间以毫秒为单位的时间差。
        //称为时间戳
        System.out.println(time);
    }
}
```

#### 2-2、Java中两个Date类的使用

```java
import org.junit.Test;

import java.util.Date;

/**
 * JDK 8之前日期和时间的API测试
 */
public class DateTimeTest {

    /**
     * java.util.Date类 ---> 表示特定的瞬间，精确到毫秒
     *            |---java.sql.Date类
     *
     * 1.两个构造器的使用
     *     >构造器一：Date()：创建一个对应当前时间的Date对象
     *     >构造器二：创建指定毫秒数的Date对象
     * 2.两个方法的使用
     *     >toString():显示当前的年、月、日、时、分、秒
     *     >getTime():获取当前Date对象对应的毫秒数。（时间戳）
     *
     * 3. java.sql.Date对应着数据库中的日期类型的变量
     *     >如何实例化
     *     >如何将java.util.Date对象转换为java.sql.Date对象
     *
     */
    @Test
    public void test2(){
        //构造器一：Date()：创建一个对应当前时间的Date对象
        Date date1 = new Date();
        System.out.println(date1.toString());   //Sat May 09 20:09:11 CST 2020

        System.out.println(date1.getTime());    //1589026216998

        //构造器二：创建指定毫秒数的Date对象
        Date date2 = new Date(1589026216998L);
        System.out.println(date2.toString());

        //创建java.sql.Date对象
        java.sql.Date date3 = new java.sql.Date(35235325345L);
        System.out.println(date3);  //1971-02-13

        //如何将java.util.Date对象转换为java.sql.Date对象
        //情况一：
//        Date date4 = new java.sql.Date(2343243242323L);
//        java.sql.Date date5 = (java.sql.Date) date4;
        //情况二：
        Date date6 = new Date();
        java.sql.Date date7 = new java.sql.Date(date6.getTime());
    }
}
```

### 3、JDK8之前的日期时间API

#### 3-1、SimpleDateFormat的使用

- `Date`类的API不易于国际化，大部分被废弃了，`java.text.SimpleDateFormat`类是一个不与语言环境有关的方式来格式化和解析日期的具体类。
- 它允许进行
  - 格式化：日期—>文本
  - 解析：文本—>日期

```java
import org.junit.Test;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

/**
 * jdk 8 之前的日期时间的API测试
 * 1.System类中currentTimeMillis();
 * 2.java.util.Date和字类java.sql.Date
 * 3.SimpleDateFormat
 * 4.Calendar
 */
public class DateTime {
    /**
     * SimpleDateFormat的使用：SimpleDateFormat对日期Date类的格式化和解析
     * 1.两个操作
     * 1.1格式化：日期---》字符串
     * 1.2解析：格式化的逆过程，字符串---》日期
     *
     * 2.SimpleDateFormat的实例化
     */
    @Test
    public void testSimpleDateFormat() throws ParseException {
        //实例化SimpleDateFormat
        SimpleDateFormat sdf = new SimpleDateFormat();

        //格式化：日期---》字符串
        Date date = new Date();
        System.out.println(date);   //Sun May 10 16:34:30 CST 2020

        String format = sdf.format(date);
        System.out.println(format); //20-5-10 下午4:34

        //解析：格式化的逆过程，字符串---》日期
        String str = "19-12-18 上午11:43";
        Date date1 = sdf.parse(str);
        System.out.println(date1);  //Wed Dec 18 11:43:00 CST 2019

        //*************按照指定的方式格式化和解析：调用带参的构造器*****************
//        SimpleDateFormat sdf1 = new SimpleDateFormat("yyyyy.MMMMM.dd GGG hh:mm aaa");
        SimpleDateFormat sdf1 = new SimpleDateFormat("yyyyy.MMMMM.dd GGG hh:mm aaa");
        //格式化
        String format1 = sdf1.format(date);
        System.out.println(format1);    //02020.五月.10 公元 04:32 下午
        //解析:要求字符串必须是符合SimpleDateFormat识别的格式(通过构造器参数体现),
        //否则，抛异常
        Date date2 = sdf1.parse("02020.五月.10 公元 04:32 下午");
        System.out.println(date2);  //Sun May 10 16:32:00 CST 2020
    }
}

```

#### 3-2、SimpleDateFormat的练习

练习一：

```java
import org.junit.Test;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

/**
 * jdk 8 之前的日期时间的API测试
 * 1.System类中currentTimeMillis();
 * 2.java.util.Date和字类java.sql.Date
 * 3.SimpleDateFormat
 * 4.Calendar
 */
public class DateTime {

    /**
     * 练习1：字符串"2020-09-08"转换为java.sql.Date
     *
     */
    @Test
    public void testExer() throws ParseException {
        String birth = "2020-09-08";

        SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd");
        Date date = sdf1.parse(birth);
//        System.out.println(date);

        java.sql.Date birthDate = new java.sql.Date(date.getTime());
        System.out.println(birthDate);
    }
}

```

练习2

```java
    /**
     * 练习二："三天打渔两天晒网"   1990-01-01  xxxx-xx-xx 打渔？晒网？
     *
     *     举例：2020-09-08 ？ 总天数
     *
     *     总天数 % 5 == 1,2,3 : 打渔
     *     总天数 % 5 == 4,0 : 晒网
     *
     *     总天数的计算？
     *     方式一：( date2.getTime() - date1.getTime()) / (1000 * 60 * 60 * 24) + 1
     *     方式二：1990-01-01  --> 2019-12-31  +  2020-01-01 -->2020-09-08
     *
     */
```

#### 3-3、Calender日历类的使用

Calendar是一个抽象基类，主用用于完成日期字段之间相互操作的功能。
获取Calendar实例的方法
使用Calendar.getInstance()方法
调用它的子类GregorianCalendar的构造器。
一个Calendar的实例是系统时间的抽象表示，通过get(intfield)方法来取得想要的时间信息。比如YEAR、MONTH、DAY_OF_WEEK、HOUR_OF_DAY 、MINUTE、SECOND
public void set(intfield,intvalue)
public void add(intfield,intamount)
public final Date getTime()
public final void setTime(Date date)
注意:
获取月份时：一月是0，二月是1，以此类推，12月是11
获取星期时：周日是1，周二是2，。。。。周六是7

```java
import java.util.Calendar;
import java.util.Date;

import org.junit.Test;

/**
 * jdk 8 之前的日期时间的API测试
 * 1.System类中currentTimeMillis();
 * 2.java.util.Date和字类java.sql.Date
 * 3.SimpleDateFormat
 * 4.Calendar
 */
public class DateTime {

    /**
     * Calendar日历类的使用
     */
    @Test
    public void testCalendar(){
        //1.实例化
        //方式一：创建其子类（GregorianCalendar）的对象
        //方式二：调用其静态方法getInstance()
        Calendar calendar = Calendar.getInstance();

//        System.out.println(calendar.getClass());    //class java.util.GregorianCalendar

        //2.常用方法
        //get()
        int days = calendar.get(Calendar.DAY_OF_MONTH);
        System.out.println(days);   //10
        System.out.println(calendar.get(Calendar.DAY_OF_YEAR)); //131,今天是这一年的131天

        //set()
        //calendar可变性
        calendar.set(Calendar.DAY_OF_MONTH,22);
        days = calendar.get(Calendar.DAY_OF_MONTH);
        System.out.println(days);   //22

        //add()
        calendar.add(Calendar.DAY_OF_MONTH,-3);
        days = calendar.get(Calendar.DAY_OF_MONTH);
        System.out.println(days);   //22-3 --》19

        //getTime():日历类---> Date
        Date date = calendar.getTime();
        System.out.println(date);   //Tue May 19 17:12:06 CST 2020

        //setTime():Date ---> 日历类
        Date date1 = new Date();
        calendar.setTime(date1);
        days = calendar.get(Calendar.DAY_OF_MONTH);
        System.out.println(days);   //10
    }
}
```

### 4、JDK8中的日期时间API的介绍

1、新日期时间API出现的背景

如果我们可以跟别人说：“我们在1502643933071见面，别晚了！”那么就再简单不过了。但是我们希望时间与昼夜和四季有关，于是事情就变复杂了。JDK 1.0中包含了一个java.util.Date类，但是它的大多数方法已经在JDK 1.1引入Calendar类之后被弃用了。而Calendar并不比Date好多少。它们面临的问题是：

可变性：像日期和时间这样的类应该是不可变的。
偏移性：Date中的年份是从1900开始的，而月份都从0开始。
格式化：格式化只对Date有用，Calendar则不行。
此外，它们也不是线程安全的；不能处理闰秒等。

```java
import org.junit.Test;
import java.util.Date;

/**
 * jdk 8中日期时间API的测试
 *
 */
public class JDK8DateTimeTest {

    @Test
    public void testDate(){
        //偏移量
        Date date1 = new Date(2020,9,8);
        System.out.println(date1);  //Fri Oct 08 00:00:00 CST 3920

        Date date2 = new Date(2020 - 1900,9 - 1,8);
        System.out.println(date2); //Tue Sep 08 00:00:00 CST 2020
    }
}
```

第三次引入的API是成功的，并且Java 8中引入的java.time API 已经纠正了过去的缺陷，将来很长一段时间内它都会为我们服务。

Java 8 吸收了Joda-Time 的精华，以一个新的开始为Java 创建优秀的API。新的java.time 中包含了所有关于本地日期（LocalDate）、本地时间（LocalTime）、本地日期时间（LocalDateTime）、时区（ZonedDateTime）和持续时间（Duration）的类。历史悠久的Date 类新增了toInstant()方法，用于把Date 转换成新的表示形式。这些新增的本地化时间日期API 大大简化了日期时间和本地化的管理。

```java
java.time–包含值对象的基础包
java.time.chrono–提供对不同的日历系统的访问java.time.format–格式化和解析时间和日期java.time.temporal–包括底层框架和扩展特性java.time.zone–包含时区支持的类

说明：大多数开发者只会用到基础包和format包，也可能会用到temporal包。因此，尽管有68个新的公开类型，大多数开发者，大概将只会用到其中的三分之一。

```

#### 4-1、LocalDate、LocalTime、LocalDateTime的使用

LocalDate、LocalTime、LocalDateTime类是其中较重要的几个类，它们的实例是不可变的对象，分别表示使用ISO-8601日历系统的日期、时间、日期和时间。它们提供了简单的本地日期或时间，并不包含当前的时间信息，也不包含与时区相关的信息。
LocalDate代表IOS格式（yyyy-MM-dd）的日期,可以存储生日、纪念日等日期。
LocalTime表示一个时间，而不是日期。
LocalDateTime是用来表示日期和时间的，这是一个最常用的类之一。
注：ISO-8601日历系统是国际标准化组织制定的现代公民的日期和时间的表示法，也就是公历

```java
import org.junit.Test;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;

/**
 * jdk 8中日期时间API的测试
 */
public class JDK8DateTimeTest {

    /**
     * LocalDate、LocalTime、LocalDateTime的使用
     *
     */
    @Test
    public void test1(){
        //now():获取当前的日期、时间、日期+时间
        LocalDate localDate = LocalDate.now();
        LocalTime localTime = LocalTime.now();
        LocalDateTime localDateTime = LocalDateTime.now();

        System.out.println(localDate);
        System.out.println(localTime);
        System.out.println(localDateTime);

        //of():设置指定的年、月、日、时、分、秒。没有偏移量
        LocalDateTime localDateTime1 = LocalDateTime.of(2020, 10, 6, 13, 23, 43);
        System.out.println(localDateTime1);

        //getXxx()：获取相关的属性
        System.out.println(localDateTime.getDayOfMonth());
        System.out.println(localDateTime.getDayOfWeek());
        System.out.println(localDateTime.getMonth());
        System.out.println(localDateTime.getMonthValue());
        System.out.println(localDateTime.getMinute());

        //体现不可变性
        //withXxx():设置相关的属性
        LocalDate localDate1 = localDate.withDayOfMonth(22);
        System.out.println(localDate);
        System.out.println(localDate1);

        LocalDateTime localDateTime2 = localDateTime.withHour(4);
        System.out.println(localDateTime);
        System.out.println(localDateTime2);

        //不可变性
        LocalDateTime localDateTime3 = localDateTime.plusMonths(3);
        System.out.println(localDateTime);
        System.out.println(localDateTime3);

        LocalDateTime localDateTime4 = localDateTime.minusDays(6);
        System.out.println(localDateTime);
        System.out.println(localDateTime4);
    }
}
```

![img](https://img-blog.csdnimg.cn/img_convert/914ba4708727b970905de339e5817e25.png)

#### 4-2、Intsant类的使用

Instant：时间线上的一个瞬时点。这可能被用来记录应用程序中的事件时间戳。
在处理时间和日期的时候，我们通常会想到年,月,日,时,分,秒。然而，这只是时间的一个模型，是面向人类的。第二种通用模型是面向机器的，或者说是连续的。在此模型中，时间线中的一个点表示为一个很大的数，这有利于计算机处理。在UNIX中，这个数从1970年开始，以秒为的单位；同样的，在Java中，也是从1970年开始，但以毫秒为单位。
java.time包通过值类型Instant提供机器视图，不提供处理人类意义上的时间单位。Instant表示时间线上的一点，而不需要任何上下文信息，例如，时区。概念上讲，它只是简单的表示自1970年1月1日0时0分0秒（UTC）开始的秒数。因为java.time包是基于纳秒计算的，所以Instant的精度可以达到纳秒级。
(1 ns = 10-9s) 1秒= 1000毫秒=106微秒=109纳秒

![img](https://img-blog.csdnimg.cn/img_convert/ec6afaca3ba677f17ecb872ea9ce28f3.png)

时间戳是指格林威治时间1970年01月01日00时00分00秒(北京时间1970年01月01日08时00分00秒)起至现在的总秒数。
![img](https://img-blog.csdnimg.cn/img_convert/64f3a70472a5112da67f2ab693576115.png)

```java
import org.junit.Test;

import java.time.*;

/**
 * jdk 8中日期时间API的测试
 */
public class JDK8DateTimeTest {

    /**
     * Instant的使用
     */
    @Test
    public void test2(){
        //now():获取本初子午线对应的标准时间
        Instant instant = Instant.now();
        System.out.println(instant);    //2020-05-10T09:55:55.561Z

        //添加时间的偏移量
        OffsetDateTime offsetDateTime = instant.atOffset(ZoneOffset.ofHours(8));//东八区
        System.out.println(offsetDateTime); //2020-05-10T18:00:00.641+08:00

        //toEpochMilli():获取自1970年1月1日0时0分0秒（UTC）开始的毫秒数  ---> Date类的getTime()
        long milli = instant.toEpochMilli();
        System.out.println(milli);  //1589104867591

        //ofEpochMilli():通过给定的毫秒数，获取Instant实例  -->Date(long millis)
        Instant instant1 = Instant.ofEpochMilli(1550475314878L);
        System.out.println(instant1);   //2019-02-18T07:35:14.878Z
    }
}
```

#### 4-3、DateTimeFormatter的使用

java.time.format.DateTimeFormatter 类：该类提供了三种格式化方法：

预定义的标准格式。如：ISO_LOCAL_DATE_TIME;ISO_LOCAL_DATE;ISO_LOCAL_TIME
本地化相关的格式。如：ofLocalizedDateTime(FormatStyle.LONG)
自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)

![img](https://img-blog.csdnimg.cn/img_convert/da69c33ec0d15ba85fcb6768d62d2686.png)

```java
import org.junit.Test;

import java.time.*;
import java.time.format.DateTimeFormatter;
import java.time.format.FormatStyle;
import java.time.temporal.TemporalAccessor;

/**
 * jdk 8中日期时间API的测试
 */
public class JDK8DateTimeTest {

    /**
     * DateTimeFormatter:格式化或解析日期、时间
     *     类似于SimpleDateFormat
     */
    @Test
    public void test3(){
        //方式一：预定义的标准格式。如：ISO_LOCAL_DATE_TIME;ISO_LOCAL_DATE;ISO_LOCAL_TIME
        DateTimeFormatter formatter = DateTimeFormatter.ISO_LOCAL_DATE_TIME;
        //格式化:日期-->字符串
        LocalDateTime localDateTime = LocalDateTime.now();
        String str1 = formatter.format(localDateTime);
        System.out.println(localDateTime);
        System.out.println(str1);//2020-05-10T18:26:40.234

        //解析：字符串 -->日期
        TemporalAccessor parse = formatter.parse("2020-05-10T18:26:40.234");
        System.out.println(parse);

        //方式二：
        //本地化相关的格式。如：ofLocalizedDateTime()
        //FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT :适用于LocalDateTime
        DateTimeFormatter formatter1 = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.LONG);
        //格式化
        String str2 = formatter1.format(localDateTime);
        System.out.println(str2);//2020年5月10日 下午06时26分40秒

        //本地化相关的格式。如：ofLocalizedDate()
        //FormatStyle.FULL / FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT : 适用于LocalDate
        DateTimeFormatter formatter2 = DateTimeFormatter.ofLocalizedDate(FormatStyle.MEDIUM);
        //格式化
        String str3 = formatter2.format(LocalDate.now());
        System.out.println(str3);//2020-5-10


       //重点： 方式三：自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)
        DateTimeFormatter formatter3 = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm:ss");
        //格式化
        String str4 = formatter3.format(LocalDateTime.now());
        System.out.println(str4);//2020-05-10 06:26:40

        //解析
        TemporalAccessor accessor = formatter3.parse("2020-05-10 06:26:40");
        System.out.println(accessor);

    }
}
```

#### 4-4、其它日期时间相关API的使用、

ZoneId：该类中包含了所有的时区信息，一个时区的ID，如Europe/Paris
ZonedDateTime：一个在ISO-8601日历系统时区的日期时间，如2007-12-03T10:15:30+01:00Europe/Paris。
其中每个时区都对应着ID，地区ID都为“{区域}/{城市}”的格式，例如：Asia/Shanghai等

```java
import org.junit.Test;

import java.time.*;
import java.util.Set;

/**
 * jdk 8中日期时间API的测试
 */
public class JDK8DateTimeTest {
	
	@Test
	public void test1(){
		//ZoneId:类中包含了所有的时区信息
		// ZoneId的getAvailableZoneIds():获取所有的ZoneId
		Set<String> zoneIds= ZoneId.getAvailableZoneIds();
		for(String s: zoneIds) {
			System.out.println(s);
		}
		// ZoneId的of():获取指定时区的时间
		LocalDateTime localDateTime= LocalDateTime.now(ZoneId.of("Asia/Tokyo"));
		System.out.println(localDateTime);
		
		//ZonedDateTime:带时区的日期时间
		// ZonedDateTime的now():获取本时区的ZonedDateTime对象
		ZonedDateTime zonedDateTime= ZonedDateTime.now();
		System.out.println(zonedDateTime);
		// ZonedDateTime的now(ZoneId id):获取指定时区的ZonedDateTime对象
		ZonedDateTime zonedDateTime1= ZonedDateTime.now(ZoneId.of("Asia/Tokyo"));
		System.out.println(zonedDateTime1);
	}
}
```

Clock：使用时区提供对当前即时、日期和时间的访问的时钟。
持续时间：Duration，用于计算两个“时间”间隔
日期间隔：Period，用于计算两个“日期”间隔
TemporalAdjuster : 时间校正器。有时我们可能需要获取例如：将日期调整到“下一个工作日”等操作。
TemporalAdjusters : 该类通过静态方法(firstDayOfXxx()/lastDayOfXxx()/nextXxx())提供了大量的常用TemporalAdjuster 的实现

```java
import java.time.Duration;
import java.time.LocalDateTime;
import java.time.LocalTime;

import org.junit.Test;

public class JDK8APITest {
	
	@Test
	public void test2(){
		//Duration:用于计算两个“时间”间隔，以秒和纳秒为基准
		LocalTime localTime= LocalTime.now();
		LocalTime localTime1= LocalTime.of(15, 23, 32);
		//between():静态方法，返回Duration对象，表示两个时间的间隔
		Duration duration= Duration.between(localTime1, localTime);
		System.out.println(duration);
		
		System.out.println(duration.getSeconds());
		System.out.println(duration.getNano());
		
		LocalDateTime localDateTime= LocalDateTime.of(2016, 6, 12, 15, 23, 32);
		LocalDateTime localDateTime1= LocalDateTime.of(2017, 6, 12, 15, 23, 32);
		
		Duration duration1= Duration.between(localDateTime1, localDateTime);
		System.out.println(duration1.toDays());
	}
}

```

```java
import java.time.Period;
import org.junit.Test;

public class JDK8APITest {
	
	@Test
	public void test3(){
		//Period:用于计算两个“日期”间隔，以年、月、日衡量
		LocalDate localDate= LocalDate.now();
		LocalDate localDate1= LocalDate.of(2028, 3, 18);
		
		Period period= Period.between(localDate, localDate1);
		System.out.println(period);
        System.out.println(period.getYears());
		
		System.out.println(period.getMonths());
		System.out.println(period.getDays());
		
		Period period1= period.withYears(2);
		System.out.println(period1);
	}
}
```

#### 4-4-1、参考：与传统日期处理的转换

![img](https://img-blog.csdnimg.cn/img_convert/316c319a548bac159483c82432690094.png)

### 5、java比较器

#### 5-1、概述

Java中的对象，正常情况下，只能进行比较：==或 != 。不能使用 >或<的，但是在开发场景中，我们需要对多个对象进行排序，言外之意，就需要比较对象的大小。 如何实现？使用两个接口中的任何一个：Comparable或 Comparator

Java实现对象排序的方式有两种：
自然排序：java.lang.Comparable
定制排序：java.util.Comparator

#### 5-2、Comparable自然排序举例

```java
import org.junit.Test;
import java.util.Arrays;

public class CompareTest {

    /**
     * Comparable接口的使用举例：  自然排序
     * 1.像String、包装类等实现了Comparable接口，重写了compareTo(obj)方法，给出了比较两个对象大小的方式。
     * 2.像String、包装类重写compareTo()方法以后，进行了从小到大的排列
     * 3. 重写compareTo(obj)的规则：
     *    如果当前对象this大于形参对象obj，则返回正整数，
     *    如果当前对象this小于形参对象obj，则返回负整数，
     *    如果当前对象this等于形参对象obj，则返回零。
     *
     */
    @Test
    public void test1(){
        String[] arr = new String[]{"AA","CC","KK","MM","GG","JJ","DD"};

        Arrays.sort(arr);

        System.out.println(Arrays.toString(arr));
    }

}
```

#### 5-3、自定义实现Comparable自然排序

测试类：

```java
import org.junit.Test;
import java.util.Arrays;

public class CompareTest {

    /**
     * 4.对于自定义类来说，如果需要排序，我们可以让自定义类实现Comparable接口，重写compareTo(obj)方法。
     *   在compareTo(obj)方法中指明如何排序
     */
    @Test
    public void test2(){
        Goods[] arr = new Goods[5];
        arr[0] = new Goods("lenovoMouse",34);
        arr[1] = new Goods("dellMouse",43);
        arr[2] = new Goods("xiaomiMouse",12);
        arr[3] = new Goods("huaweiMouse",65);
        arr[4] = new Goods("microsoftMouse",43);

        Arrays.sort(arr);

        System.out.println(Arrays.toString(arr));
    }

}
```

goods类：

```java
/**
 * 商品类
 */
public class Goods implements Comparable{

    private String name;
    private double price;

    public Goods() {
    }

    public Goods(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    @Override
    public String toString() {
        return "Goods{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }

    //指明商品比较大小的方式:按照价格从低到高排序,再按照产品名称从高到低排序
    @Override
    public int compareTo(Object o) {
//        System.out.println("**************");
        if(o instanceof Goods){
            Goods goods = (Goods)o;
            //方式一：
            if(this.price > goods.price){
                return 1;
            }else if(this.price < goods.price){
                return -1;
            }else{
//                return 0;
                return -this.name.compareTo(goods.name);
            }
            //方式二：
//           return Double.compare(this.price,goods.price);
        }
//        return 0;
        throw new RuntimeException("传入的数据类型不一致！");
    }
}
```

#### 5-4、使用Comparator实现定制排序

```java
import org.junit.Test;
import java.util.Arrays;
import java.util.Comparator;

/**
 * 一、说明：Java中的对象，正常情况下，只能进行比较：==  或  != 。不能使用 > 或 < 的
 *          但是在开发场景中，我们需要对多个对象进行排序，言外之意，就需要比较对象的大小。
 *          如何实现？使用两个接口中的任何一个：Comparable 或 Comparator
 *
 * 二、Comparable接口与Comparator的使用的对比：
 *    Comparable接口的方式一旦一定，保证Comparable接口实现类的对象在任何位置都可以比较大小。
 *    Comparator接口属于临时性的比较。
 */
public class CompareTest {

    /**
     * Comparator接口的使用：定制排序
     *     1.背景：
     *     当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，
     *     或者实现了java.lang.Comparable接口的排序规则不适合当前的操作，
     *     那么可以考虑使用 Comparator 的对象来排序
     *     2.重写compare(Object o1,Object o2)方法，比较o1和o2的大小：
     *     如果方法返回正整数，则表示o1大于o2；
     *     如果返回0，表示相等；
     *     返回负整数，表示o1小于o2。
     */
    @Test
    public void test3(){
        String[] arr = new String[]{"AA","CC","KK","MM","GG","JJ","DD"};
        Arrays.sort(arr,new Comparator(){

            //按照字符串从大到小的顺序排列
            @Override
            public int compare(Object o1, Object o2) {
                if(o1 instanceof String && o2 instanceof  String){
                    String s1 = (String) o1;
                    String s2 = (String) o2;
                    return -s1.compareTo(s2);
                }
//                return 0;
                throw new RuntimeException("输入的数据类型不一致");
            }
        });
        System.out.println(Arrays.toString(arr));
    }

    @Test
    public void test4(){
        Goods[] arr = new Goods[6];
        arr[0] = new Goods("lenovoMouse",34);
        arr[1] = new Goods("dellMouse",43);
        arr[2] = new Goods("xiaomiMouse",12);
        arr[3] = new Goods("huaweiMouse",65);
        arr[4] = new Goods("huaweiMouse",224);
        arr[5] = new Goods("microsoftMouse",43);

        Arrays.sort(arr, new Comparator() {
            //指明商品比较大小的方式:按照产品名称从低到高排序,再按照价格从高到低排序
            @Override
            public int compare(Object o1, Object o2) {
                if(o1 instanceof Goods && o2 instanceof Goods){
                    Goods g1 = (Goods)o1;
                    Goods g2 = (Goods)o2;
                    if(g1.getName().equals(g2.getName())){
                        return -Double.compare(g1.getPrice(),g2.getPrice());
                    }else{
                        return g1.getName().compareTo(g2.getName());
                    }
                }
                throw new RuntimeException("输入的数据类型不一致");
            }
        });

        System.out.println(Arrays.toString(arr));
    }
```

**Comparable接口与Comparator的使用的对比**：

- Comparable接口的方式一旦一定，保证Comparable接口实现类的对象在任何位置都可以比较大小。
- Comparator接口属于临时性的比较。

### 6、System类、Math类、BigInteger与BigDecimal

#### 6-1、System类

System类代表系统，系统级的很多属性和控制方法都放置在该类的内部。该类位于java.lang包。

由于该类的构造器是private的，所以无法创建该类的对象，也就是无法实例化该类。其内部的成员变量和成员方法都是static的，所以也可以很方便的进行调用。

成员变量

System类内部包含in、out和err三个成员变量，分别代表标准输入流(键盘输入)，标准输出流(显示器)和标准错误输出流(显示器)。
成员方法

* native long currentTimeMillis()：

该方法的作用是返回当前的计算机时间，时间的表达格式为当前计算机时间和GMT时间(格林威治时间)1970年1月1号0时0分0秒所差的毫秒数。

* void exit(int status)：

该方法的作用是退出程序。其中status的值为0代表正常退出，非零代表异常退出。使用该方法可以在图形界面编程中实现程序的退出功能等。

* void gc()：

该方法的作用是请求系统进行垃圾回收。至于系统是否立刻回收，则取决于系统中垃圾回收算法的实现以及系统执行时的情况。String

* getProperty(String key)：

该方法的作用是获得系统中属性名为key的属性对应的值。系统中常见的属性名以及属性的作用如下表所示：
![img](https://img-blog.csdnimg.cn/img_convert/a487be6770c3eacff3bc0bb872ab1d27.png)

```java
import org.junit.Test;

/**
 * 其他常用类的使用
 * 1.System
 * 2.Math
 * 3.BigInteger 和 BigDecimal
 */
public class OtherClassTest {

    @Test
    public void test1() {
        String javaVersion = System.getProperty("java.version");
        System.out.println("java的version:" + javaVersion);

        String javaHome = System.getProperty("java.home");
        System.out.println("java的home:" + javaHome);

        String osName = System.getProperty("os.name");
        System.out.println("os的name:" + osName);

        String osVersion = System.getProperty("os.version");
        System.out.println("os的version:" + osVersion);

        String userName = System.getProperty("user.name");
        System.out.println("user的name:" + userName);

        String userHome = System.getProperty("user.home");
        System.out.println("user的home:" + userHome);

        String userDir = System.getProperty("user.dir");
        System.out.println("user的dir:" + userDir);

    }
}
```

#### 6-2、Math类

java.lang.Math提供了一系列静态方法用于科学计算。其方法的参数和返回值类型一般为double型。

abs 绝对值
acos,asin,atan,cos,sin,tan 三角函数
sqrt 平方根
pow(double a,doble b) a的b次幂
log 自然对数
exp e为底指数
max(double a,double b)
min(double a,double b)
random() 返回0.0到1.0的随机数
long round(double a) double型数据a转换为long型（四舍五入）
toDegrees(double angrad) 弧度—>角度
toRadians(double angdeg) 角度—>弧度

#### 6-3、BigInteger与BigDecimal

​	Integer类作为int的包装类，能存储的最大整型值为2^31 -1，Long类也是有限的，最大为2^63 -1。如果要表示再大的整数，不管是基本数据类型还是他们的包装类都无能为力，更不用说进行运算了。
​	java.math包的BigInteger可以表示不可变的任意精度的整数。BigInteger提供所有Java 的基本整数操作符的对应物，并提供java.lang.Math 的所有相关方法。另外，BigInteger还提供以下运算：模算术、GCD 计算、质数测试、素数生成、位操作以及一些其他操作。
​	构造器
​	BigInteger(String val)：根据字符串构建BigInteger对象
常用方法
![img](https://img-blog.csdnimg.cn/img_convert/a1b9e65f934b5efe345447284641b6b5.png)

一般的Float类和Double类可以用来做科学计算或工程计算，但在商业计算中，要求数字精度比较高，故用到java.math.BigDecimal类。
BigDecimal类支持不可变的、任意精度的有符号十进制定点数。
构造器
public BigDecimal(double val)
public BigDecimal(String val)
常用方法
public BigDecimal add(BigDecimal augend)
public BigDecimal subtract(BigDecimal subtrahend)
public BigDecimal multiply(BigDecimal multiplicand)
public BigDecimal divide(BigDecimal divisor, int scale, int roundingMode)

```java
import org.junit.Test;

import java.math.BigDecimal;
import java.math.BigInteger;

/**
 * 其他常用类的使用
 * 1.System
 * 2.Math
 * 3.BigInteger 和 BigDecimal
 */
public class OtherClassTest {

    @Test
    public void test2() {
        BigInteger bi = new BigInteger("1243324112234324324325235245346567657653");
        BigDecimal bd = new BigDecimal("12435.351");
        BigDecimal bd2 = new BigDecimal("11");
        System.out.println(bi);
//         System.out.println(bd.divide(bd2));
        System.out.println(bd.divide(bd2, BigDecimal.ROUND_HALF_UP));
        System.out.println(bd.divide(bd2, 25, BigDecimal.ROUND_HALF_UP));

    }
}
```

## 13、枚举类与注解

### 1、枚举类的使用

#### 1-1、枚举类的理解

类的对象只有有限个，确定的。举例如下：
星期：Monday(星期一)、…、Sunday(星期天)
性别：Man(男)、Woman(女)
季节：Spring(春节)…Winter(冬天)
支付方式：Cash（现金）、WeChatPay（微信）、Alipay(支付宝)、BankCard(银行卡)、CreditCard(信用卡)
就职状态：Busy、Free、Vocation、Dimission
订单状态：Nonpayment（未付款）、Paid（已付款）、Delivered（已发货）、Return（退货）、Checked（已确认）Fulfilled（已配货）、
线程状态：创建、就绪、运行、阻塞、死亡
当需要定义一组常量时，强烈建议使用枚举类
枚举类的实现
JDK1.5之前需要自定义枚举类
JDK 1.5 新增的enum 关键字用于定义枚举类、

若枚举只有一个对象, 则可以作为一种单例模式的实现方式。

#### 1-2、自定义枚举类

> 枚举类的属性

- 枚举类对象的属性不应允许被改动, 所以应该使用`private final`修饰
- 枚举类的使用`private final` 修饰的属性应该在构造器中为其赋值
- 若枚举类显式的定义了带参数的构造器, 则在列出枚举值时也必须对应的传入参数

```java
/**
 * 一、枚举类的使用
 * 1.枚举类的理解：类的对象只有有限个，确定的。我们称此类为枚举类。
 * 2.当需要定义一组常量时，强烈建议使用枚举类
 * 3.若枚举只有一个对象, 则可以作为一种单例模式的实现方式。
 *
 * 二、如何定义枚举类
 *     方式一：JDK1.5之前需要自定义枚举类
 *     方式二：JDK 1.5 新增的enum 关键字用于定义枚举类
 *
 */
public class SeasonTest {
    public static void main(String[] args) {
        Season spring = Season.SPRING;
        System.out.println(spring);
    }
}
//自定义枚举类
class Season{
    //1.声明Season对象的属性:private final修饰
    private final String seasonName;
    private final String seasonDesc;

    //2.私有化类的构造器,并给对象属性赋值
    private Season(String seasonName,String seasonDesc){
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    //3.提供当前枚举类的多个对象
    public static final Season SPRING = new Season("春天","万物复苏");
    public static final Season SUMMER = new Season("夏天","烈日炎炎");
    public static final Season AUTUMN = new Season("秋天","金秋送爽");
    public static final Season WINTER = new Season("冬天","白雪皑皑");

    //4.其他诉求：获取枚举类对象的属性
    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }

    //4.其他诉求1：提供toString()
    @Override
    public String toString() {
        return "Season{" +
                "seasonName='" + seasonName + '\'' +
                ", seasonDesc='" + seasonDesc + '\'' +
                '}';
    }
}
```

#### 1-3、使用enum关键字定义枚举类

使用说明

使用enum定义的枚举类默认继承了java.lang.Enum类，因此不能再继承其他类
枚举类的构造器只能使用private 权限修饰符
枚举类的所有实例必须在枚举类中显式列出(, 分隔; 结尾)。列出的实例系统会自动添加public static final 修饰
必须在枚举类的第一行声明枚举类对象
JDK 1.5 中可以在switch 表达式中使用Enum定义的枚举类的对象作为表达式, case 子句可以直接使用枚举值的名字, 无需添加枚举类作为限定。

```java
/**
 * 使用enum关键字定义枚举类
 * 说明：定义的枚举类默认继承于java.lang.Enum类
 */
public class SeasonTest1 {
    public static void main(String[] args) {
        Season1 summer = Season1.SUMMER;
        //toString():
        System.out.println(summer.toString());
        
        System.out.println(Season1.class.getSuperclass());
    }
}

//使用enum关键字枚举类
enum Season1{
    //1.提供当前枚举类的对象，多个对象之间用","隔开，末尾对象";"结束
    SPRING("春天","万物复苏"),
    SUMMER("夏天","烈日炎炎"),
    AUTUMN("秋天","金秋送爽"),
    WINTER("冬天","白雪皑皑");

    //2.声明Season对象的属性:private final修饰
    private final String seasonName;
    private final String seasonDesc;

    //3.私有化类的构造器,并给对象属性赋值
    private Season1(String seasonName,String seasonDesc){
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    //4.其他诉求：获取枚举类对象的属性
    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }

    //4.其他诉求1：提供toString()
//    @Override
//    public String toString() {
//        return "Season{" +
//                "seasonName='" + seasonName + '\'' +
//                ", seasonDesc='" + seasonDesc + '\'' +
//                '}';
//    }
}
```

#### 1-4、enum类中的常用方法

![img](https://img-blog.csdnimg.cn/img_convert/c8159e5419e4c0375de1312dc227d2c0.png)

Enum类的主要方法：

values()方法：返回枚举类型的对象数组。该方法可以很方便地遍历所有的枚举值。
valueOf(String str)：可以把一个字符串转为对应的枚举类对象。要求字符串必须是枚举类对象的“名字”。如不是，会有运行时异常：IllegalArgumentException。
toString()：返回当前枚举类对象常量的名称

```java
/**
 * 使用enum关键字定义枚举类
 * 说明：定义的枚举类默认继承于java.lang.Enum类
 *
 * 三、Enum类的常用方法
 *      values()方法：返回枚举类型的对象数组。该方法可以很方便地遍历所有的枚举值。
 *      valueOf(String str)：可以把一个字符串转为对应的枚举类对象。要求字符串必须是枚举类对象的“名字”。如不是，会有运行时异常：IllegalArgumentException。
 *      toString()：返回当前枚举类对象常量的名称
 */
public class SeasonTest1 {
    public static void main(String[] args) {
        Season1 summer = Season1.SUMMER;
        //toString():
        System.out.println(summer.toString());

//        System.out.println(Season1.class.getSuperclass());
        System.out.println("**************************");
        //values():返回所有的枚举类对象构成的数组
        Season1[] values = Season1.values();
        for(int i = 0;i < values.length;i++){
            System.out.println(values[i]);
        }
        System.out.println("****************************");
        Thread.State[] values1 = Thread.State.values();
        for(int i = 0;i < values1.length;i++){
            System.out.println(values1[i]);
        }

        //valueOf(String objName):返回枚举类中对象名是objName的对象。
        Season1 winter = Season1.valueOf("WINTER");
        //如果没有objName的枚举类对象，则抛异常：IllegalArgumentException
//        Season1 winter = Season1.valueOf("WINTER1");
        System.out.println(winter);

    }
}

//使用enum关键字枚举类
enum Season1{
    //1.提供当前枚举类的对象，多个对象之间用","隔开，末尾对象";"结束
    SPRING("春天","万物复苏"),
    SUMMER("夏天","烈日炎炎"),
    AUTUMN("秋天","金秋送爽"),
    WINTER("冬天","白雪皑皑");

    //2.声明Season对象的属性:private final修饰
    private final String seasonName;
    private final String seasonDesc;

    //3.私有化类的构造器,并给对象属性赋值
    private Season1(String seasonName,String seasonDesc){
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    //4.其他诉求：获取枚举类对象的属性
    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }

    //4.其他诉求1：提供toString()
//    @Override
//    public String toString() {
//        return "Season{" +
//                "seasonName='" + seasonName + '\'' +
//                ", seasonDesc='" + seasonDesc + '\'' +
//                '}';
//    }
}
```

#### 1-5、使用enum关键字定义的枚举类实现接口

```java
/**
 * 使用enum关键字定义枚举类
 * 说明：定义的枚举类默认继承于java.lang.Enum类
 *
 * 四、使用enum关键字定义的枚举类实现接口的情况
 *   情况一：实现接口，在enum类中实现抽象方法
 *   情况二：让枚举类的对象分别实现接口中的抽象方法
 */
public class SeasonTest1 {
    public static void main(String[] args) {
        //values():返回所有的枚举类对象构成的数组
        Season1[] values = Season1.values();
        for(int i = 0;i < values.length;i++){
            System.out.println(values[i]);
            values[i].show();
        }

        //valueOf(String objName):返回枚举类中对象名是objName的对象。
        Season1 winter = Season1.valueOf("WINTER");
        winter.show();
    }
}

interface Info{
    void show();
}

//使用enum关键字枚举类
enum Season1 implements Info{
    //1.提供当前枚举类的对象，多个对象之间用","隔开，末尾对象";"结束
    SPRING("春天","春暖花开"){
        @Override
        public void show() {
            System.out.println("一元复始、万物复苏");
        }
    },
    SUMMER("夏天","夏日炎炎"){
        @Override
        public void show() {
            System.out.println("蝉声阵阵、烈日当空");
        }
    },
    AUTUMN("秋天","秋高气爽"){
        @Override
        public void show() {
            System.out.println("天高气清、金桂飘香");
        }
    },
    WINTER("冬天","冰天雪地"){
        @Override
        public void show() {
            System.out.println("寒冬腊月、滴水成冰");
        }
    };

    //2.声明Season对象的属性:private final修饰
    private final String seasonName;
    private final String seasonDesc;

    //3.私有化类的构造器,并给对象属性赋值
    private Season1(String seasonName,String seasonDesc){
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    //4.其他诉求：获取枚举类对象的属性
    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }

    //4.其他诉求1：提供toString()
//    @Override
//    public String toString() {
//        return "Season{" +
//                "seasonName='" + seasonName + '\'' +
//                ", seasonDesc='" + seasonDesc + '\'' +
//                '}';
//    }

//    @Override
//    public void show() {
//        System.out.println("这是一个季节。");
//    }
}
```

### 2、注解的使用

#### 2-1、注解的理解

从JDK 5.0 开始, Java 增加了对元数据(MetaData) 的支持, 也就是Annotation(注解)
Annotation 其实就是代码里的特殊标记, 这些标记可以在编译, 类加载, 运行时被读取, 并执行相应的处理。通过使用Annotation, 程序员可以在不改变原有逻辑的情况下, 在源文件中嵌入一些补充信息。代码分析工具、开发工具和部署工具可以通过这些补充信息进行验证或者进行部署。
Annotation 可以像修饰符一样被使用, 可用于修饰包,类, 构造器, 方法, 成员变量, 参数, 局部变量的声明, 这些信息被保存在Annotation 的“name=value” 对中。
在JavaSE中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在JavaEE/Android中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替JavaEE旧版中所遗留的繁冗代码和XML配置等。
未来的开发模式都是基于注解的，JPA是基于注解的，Spring2.5以上都是基于注解的，Hibernate3.x以后也是基于注解的，现在的Struts2有一部分也是基于注解的了，注解是一种趋势，一定程度上可以说：**框架= 注解+ 反射+ 设计模式。**

#### 2-2、Annotation的使用示例

使用Annotation 时要在其前面增加@ 符号, 并把该Annotation 当成一个修饰符使用。用于修饰它支持的程序元素
示例一：生成文档相关的注解
@author标明开发该类模块的作者，多个作者之间使用,分割
@version标明该类模块的版本
@see参考转向，也就是相关主题
@since从哪个版本开始增加的
@param对方法中某参数的说明，如果没有参数就不能写
@return对方法返回值的说明，如果方法的返回值类型是void就不能写
@exception对方法可能抛出的异常进行说明，如果方法没有用throws显式抛出的异常就不能写其中
@param@return和@exception这三个标记都是只用于方法的。
@param的格式要求：@param形参名形参类型形参说明
@return的格式要求：@return返回值类型返回值说明
@exception的格式要求：@exception异常类型异常说明
@param和@exception可以并列多个
示例二：在编译时进行格式检查(JDK内置的三个基本注解)
@Override: 限定重写父类方法, 该注解只能用于方法
@Deprecated: 用于表示所修饰的元素(类, 方法等)已过时。通常是因为所修饰的结构危险或存在更好的选择
@SuppressWarnings: 抑制编译器警告
示例三：跟踪代码依赖性，实现替代配置文件功能
Servlet3.0提供了注解(annotation),使得不再需要在web.xml文件中进行Servlet的部署。
spring框架中关于“事务”的管理

```java
import java.util.ArrayList;
import java.util.Date;

/**
 * 注解的使用
 *
 * 1. 理解Annotation:
 * ① jdk 5.0 新增的功能
 *
 * ② Annotation 其实就是代码里的特殊标记, 这些标记可以在编译, 类加载, 运行时被读取, 并执行相应的处理。通过使用 Annotation,
 *    程序员可以在不改变原有逻辑的情况下, 在源文件中嵌入一些补充信息。
 *
 * ③在JavaSE中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在JavaEE/Android
 *  中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替JavaEE旧版中所遗留的繁冗
 *  代码和XML配置等。
 *
 * 2. Annocation的使用示例
 *  示例一：生成文档相关的注解
 *  示例二：在编译时进行格式检查(JDK内置的三个基本注解)
 *      @Override: 限定重写父类方法, 该注解只能用于方法
 *      @Deprecated: 用于表示所修饰的元素(类, 方法等)已过时。通常是因为所修饰的结构危险或存在更好的选择
 *      @SuppressWarnings: 抑制编译器警告
 *
 *  示例三：跟踪代码依赖性，实现替代配置文件功能
 */
public class AnnotationTest {
    public static void main(String[] args) {
        Person p = new Student();
        p.walk();

        Date date = new Date(2020, 10, 11);
        System.out.println(date);

        @SuppressWarnings("unused")
        int num = 10;

//        System.out.println(num);

        @SuppressWarnings({ "unused", "rawtypes" })
        ArrayList list = new ArrayList();
    }
}

class Person{
    private String name;
    private int age;

    public Person() {
        super();
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    public void walk(){
        System.out.println("学习中……");
    }
    public void eat(){
        System.out.println("摸鱼中……");
    }
}

interface Info{
    void show();
}

class Student extends Person implements Info{

    @Override
    public void walk() {
        System.out.println("喷子走开");
    }

    @Override
    public void show() {

    }
}
```

#### 2-3、如何自定义注解

定义新的Annotation类型使用**@interface**关键字
自定义注解自动继承了**java.lang.annotation.Annotation**接口
Annotation的成员变量在Annotation定义中以无参数方法的形式来声明。其方法名和返回值定义了该成员的名字和类型。我们称为配置参数。类型只能是八种基本数据类型、String类型、Class类型、enum类型、Annotation类型、以上所有类型的数组。
可以在定义Annotation的成员变量时为其指定初始值,指定成员变量的初始值可使用**default**关键字
如果只有一个参数成员，建议使用参数名为value
如果定义的注解含有配置参数，那么使用时必须指定参数值，除非它有默认值。格式是“参数名=参数值”，如果只有一个参数成员，且名称为value，可以省略“value=”
没有成员定义的Annotation称为标记;包含成员变量的Annotation称为元数据Annotation
注意：自定义注解必须配上注解的信息处理流程才有意义。

```java
public @interface MyAnnotation {

    String value();
}
/**
 * 注解的使用
 *
 *  3.如何自定义注解：参照@SuppressWarnings定义
 *      ① 注解声明为：@interface
 *      ② 内部定义成员，通常使用value表示
 *      ③ 可以指定成员的默认值，使用default定义
 *      ④ 如果自定义注解没有成员，表明是一个标识作用。
 *
 *      如果注解有成员，在使用注解时，需要指明成员的值。
 *      自定义注解必须配上注解的信息处理流程(使用反射)才有意义。
 *      自定义注解通过都会指明两个元注解：Retention、Target
 *
 */

@MyAnnotation(value = "hello")
```

#### 2-4、jdk中4个基本的元注解的使用1

JDK 的元Annotation 用于修饰其他Annotation 定义

JDK5.0提供了4个标准的meta-annotation类型，分别是：

Retention
Target
Documented
Inherited
元数据的理解：String name = “MyBlog”;

@Retention: 只能用于修饰一个Annotation定义, 用于指定该Annotation 的生命周期, @Rentention包含一个RetentionPolicy类型的成员变量, 使用@Rentention时必须为该value 成员变量指定值:

RetentionPolicy.SOURCE:在源文件中有效（即源文件保留），编译器直接丢弃这种策略的注释
RetentionPolicy.CLASS:在class文件中有效（即class保留），当运行Java 程序时, JVM 不会保留注解。这是默认值
RetentionPolicy.RUNTIME:在运行时有效（即运行时保留），当运行Java 程序时, JVM 会保留注释。程序可以通过反射获取该注释。

![img](https://img-blog.csdnimg.cn/img_convert/655f60ccb2126424b1b8f7f2cf4c4cde.png)

```java
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;

@Retention(RetentionPolicy.SOURCE)
public @interface MyAnnotation {

    String value();

}
/**
 * 注解的使用
 *
 *   4.jdk 提供的4种元注解
 *     元注解：对现有的注解进行解释说明的注解
 *     Retention:指定所修饰的 Annotation 的生命周期：SOURCE\CLASS（默认行为）\RUNTIME
 *               只有声明为RUNTIME生命周期的注解，才能通过反射获取。
 *     Target:
 *     Documented:
 *     Inherited:
 *
 */
public class AnnotationTest {
    public static void main(String[] args) {

    }
}

@MyAnnotation(value = "hello")
class Person{
    private String name;
    private int age;

    public Person() {
        super();
    }

    @MyAnnotation(value = "jack")
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public void walk(){
        System.out.println("学习中……");
    }
    public void eat(){
        System.out.println("摸鱼中……");
    }
}
```

#### 2-5、jdk中4个基本的元注解的使用2

- `@Target`: 用于修饰Annotation 定义, 用于指定被修饰的Annotation 能用于修饰哪些程序元素。@Target 也包含一个名为value 的成员变量。

![img](https://img-blog.csdnimg.cn/img_convert/55f870273e1957635488dbcab66a299d.png)

@Documented: 用于指定被该元Annotation 修饰的Annotation 类将被javadoc工具提取成文档。默认情况下，javadoc是不包括注解的。
定义为Documented的注解必须设置Retention值为RUNTIME。
@Inherited: 被它修饰的Annotation 将具有继承性。如果某个类使用了被@Inherited 修饰的Annotation, 则其子类将自动具有该注解。
比如：如果把标有@Inherited注解的自定义的注解标注在类级别上，子类则可以继承父类类级别的注解
实际应用中，使用较少

```java
import org.junit.Test;

import java.lang.annotation.Annotation;
import java.util.ArrayList;
import java.util.Date;

/**
 * 注解的使用
 *
 *   4.jdk 提供的4种元注解
 *     元注解：对现有的注解进行解释说明的注解
 *     Retention:指定所修饰的 Annotation 的生命周期：SOURCE\CLASS（默认行为）\RUNTIME
 *               只有声明为RUNTIME生命周期的注解，才能通过反射获取。
 *     Target:用于指定被修饰的 Annotation 能用于修饰哪些程序元素
 *     *******出现的频率较低*******
 *     Documented:表示所修饰的注解在被javadoc解析时，保留下来。
 *     Inherited:被它修饰的 Annotation 将具有继承性。
 *     
 * 5.通过反射获取注解信息 ---到反射内容时系统讲解
 */
public class AnnotationTest {
    public static void main(String[] args) {

    }

    @Test
    public void testGetAnnotation(){
        Class clazz = Student.class;
        Annotation[] annotations = clazz.getAnnotations();
        for(int i = 0;i < annotations.length;i++){
            System.out.println(annotations[i]);
        }
    }
}

@MyAnnotation(value = "hello")
class Person{
    private String name;
    private int age;

    public Person() {
        super();
    }

    @MyAnnotation
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @MyAnnotation
    public void walk(){
        System.out.println("学习中……");
    }
    public void eat(){
        System.out.println("摸鱼中……");
    }
}



@Inherited
@Retention(RetentionPolicy.RUNTIME)
@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE,TYPE_PARAMETER,TYPE_USE})
public @interface MyAnnotation {
    String value() default "book";
}
```

#### 2-6、利用反射获取注解信息

JDK 5.0 在java.lang.reflect包下新增了AnnotatedElement接口, 该接口代表程序中可以接受注解的程序元素
当一个Annotation 类型被定义为运行时Annotation 后, 该注解才是运行时可见, 当class文件被载入时保存在class 文件中的Annotation 才会被虚拟机读取
程序可以调用AnnotatedElement对象的如下方法来访问Annotation 信息
![img](https://img-blog.csdnimg.cn/img_convert/bb4244ff4c021141be68e5435779912d.png)

#### 2-7、jdk8新特性：可重复注解

Java 8对注解处理提供了两点改进：可重复的注解及可用于类型的注解。此外，反射也得到了加强，在Java8中能够得到方法参数的名称。这会简化标注在方法参数上的注解。

> 可重复注解示例：

```java
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

import static java.lang.annotation.ElementType.*;

@Retention(RetentionPolicy.RUNTIME)
@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})
public @interface MyAnnotations {

    MyAnnotation[] value();
}
```

```java
import java.lang.annotation.*;
import static java.lang.annotation.ElementType.*;

@Repeatable(MyAnnotations.class)
@Retention(RetentionPolicy.RUNTIME)
@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE,TYPE_PARAMETER,TYPE_USE})
public @interface MyAnnotation {

    String value() default "hello";

}
```

```java
import java.lang.annotation.Annotation;

/**
 * 注解的使用
 *
 * 6.jdk 8 中注解的新特性：可重复注解、类型注解
 *
 *   6.1可重复注解：① 在MyAnnotation上声明@Repeatable，成员值为MyAnnotations.class
 *                ② MyAnnotation的Target和Retention等元注解与MyAnnotations相同。
 *
 *
 * @author subei
 * @create 2020-05-11 11:19
 */
public class AnnotationTest {
    public static void main(String[] args) {
    }
}

@MyAnnotation(value = "hi")
@MyAnnotation(value = "abc")
//jdk 8之前的写法：
//@MyAnnotations({@MyAnnotation(value="hi"),@MyAnnotation(value="hi")})

```

#### 2-8、jdk8新特性：类型注解

JDK1.8之后，关于元注解@Target的参数类型ElementType枚举值多了两个：TYPE_PARAMETER,TYPE_USE。
在Java8之前，注解只能是在声明的地方所使用，Java8开始，注解可以应用在任何地方。
ElementType.TYPE_PARAMETER表示该注解能写在类型变量的声明语句中（如：泛型声明）。
ElementType.TYPE_USE表示该注解能写在使用类型的任何语句中。

```java
import java.util.ArrayList;

/**
 * 注解的使用
 *
 * 6.jdk 8 中注解的新特性：可重复注解、类型注解
 *
 *   6.1可重复注解：① 在MyAnnotation上声明@Repeatable，成员值为MyAnnotations.class
 *                ② MyAnnotation的Target和Retention等元注解与MyAnnotations相同。
 *
 *   6.2类型注解：
 *      ElementType.TYPE_PARAMETER 表示该注解能写在类型变量的声明语句中（如：泛型声明）。
 *      ElementType.TYPE_USE 表示该注解能写在使用类型的任何语句中。
 *
 */
public class AnnotationTest {
 
}


class Generic<@MyAnnotation T>{

    public void show() throws @MyAnnotation RuntimeException{

        ArrayList<@MyAnnotation String> list = new ArrayList<>();

        int num = (@MyAnnotation int) 10L;
    }

}
```

MyAnnotation：

```java
import java.lang.annotation.*;

import static java.lang.annotation.ElementType.*;

@Retention(RetentionPolicy.RUNTIME)
@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE,TYPE_PARAMETER,TYPE_USE})
public @interface MyAnnotation {

    String value() default "hello";

}
```

## 14、集合

### 1、java集合框架概述

#### 1-1、集合框架与数组的对比及概述

 * 1.集合、数组都是对多个数据进行存储操作的结构，简称Java容器。
 * 说明；此时的存储，主要是指能存层面的存储，不涉及到持久化的存储（.txt,.jpg,.avi,数据库中）
    *
 * 2.1数组在存储多个数据封面的特点：
 * 》一旦初始化以后，它的长度就确定了。
 * 》数组一旦定义好，它的数据类型也就确定了。我们就只能操作指定类型的数据了。
 * 比如：String[] arr;int[] str;
 * 2.2数组在存储多个数据方面的特点：
 * 》一旦初始化以后，其长度就不可修改。
 * 》数组中提供的方法非常有限，对于添加、删除、插入数据等操作，非常不便，同时效率不高。
 * 》获取数组中实际元素的个数的需求，数组没有现成的属性或方法可用
 * 》数组存储数据的特点：有序、可重复。对于无序、不可重复的需求，不能满足。


1、集合的使用场景

![img](https://img-blog.csdnimg.cn/img_convert/47d7501e379e9554f1c0e32f16d4aa19.png)

![img](https://img-blog.csdnimg.cn/img_convert/7dd14b25935d46725bf3e42f9c47a47a.png)

#### 1-2、集合框架涉及到的API

Java 集合可分为Collection和Map两种体系

Collection接口：单列数据，定义了存取一组对象的方法的集合
List：元素有序、可重复的集合
Set：元素无序、不可重复的集合
Map接口：双列数据，保存具有映射关系“key-value对”的集合

1、Collection接口继承树
![img](https://img-blog.csdnimg.cn/img_convert/4a9d3171541866ba77e2291ce41e9962.png)

2、**Map接口继承树**

![img](https://img-blog.csdnimg.cn/img_convert/a1fdb6d75598e87a224697d12c2c2bcf.png)

 * 二、集合框架
 * &---Collection接口：单列集合，用来存储一个一个的对象
 * &---List接口：存储有序的、可重复的数据。  -->“动态”数组
 * &---ArrayList、LinkedList、Vector
    *
 * &---Set接口：存储无序的、不可重复的数据   -->高中讲的“集合”
 * &---HashSet、LinkedHashSet、TreeSet
    *
 * &---Map接口：双列集合，用来存储一对(key - value)一对的数据   -->高中函数：y = f(x)
 * &---HashMap、LinkedHashMap、TreeMap、Hashtable、Properties

### 2、Collection接口方法

Collection 接口是List、Set 和Queue 接口的父接口，该接口里定义的方法既可用于操作Set 集合，也可用于操作List 和Queue 集合。
JDK不提供此接口的任何直接实现，而是提供更具体的子接口(如：Set和List)实现。
在Java5 之前，Java 集合会丢失容器中所有对象的数据类型，把所有对象都当成Object 类型处理；从JDK 5.0 增加了泛型以后，Java 集合可以记住容器中对象的数据类型。

#### 2-1、Collection接口中的常用方法1

添加
	add(Objec tobj)
	addAll(Collection coll)
获取有效元素的个数
	int size()
清空集合
	void clear()
是否是空集合
	boolean isEmpty()
是否包含某个元素
	boolean contains(Object obj)：是通过元素的equals方法来判断是否是同一个对象
	boolean containsAll(Collection c)：也是调用元素的equals方法来比较的。拿两个集合的元素挨个比较。
删除
	boolean remove(Object obj) ：通过元素的equals方法判断是否是要删除的那个元素。只会删除找到的第一个元素
	boolean removeAll(Collection coll)：取当前集合的差集
取两个集合的交集
	boolean retainAll(Collection c)：把交集的结果存在当前集合中，不影响c
集合是否相等
	boolean equals(Object obj)
转成对象数组
	Object[] toArray()
获取集合对象的哈希值
	hashCode()
遍历
	iterator()：返回迭代器对象，用于集合遍历

```java
import org.junit.Test;
import java.util.ArrayList;
import java.util.Collection;
import java.util.Date;

/**
 *
 * 三、Collection接口中的方法的使用
 *
 */
public class CollectionTest {

    @Test
    public void test1(){
        Collection coll = new ArrayList();

        //add(Object e):将元素e添加到集合coll中
        coll.add("AA");
        coll.add("BB");
        coll.add(123);  //自动装箱
        coll.add(new Date());

        //size():获取添加的元素的个数
        System.out.println(coll.size());    //4

        //addAll(Collection coll1):将coll1集合中的元素添加到当前的集合中
        Collection coll1 = new ArrayList();
        coll1.add(456);
        coll1.add("CC");
        coll.addAll(coll1);

        System.out.println(coll.size());    //6
        System.out.println(coll);

        //clear():清空集合元素
        coll.clear();

        //isEmpty():判断当前集合是否为空
        System.out.println(coll.isEmpty());
    }
}
```

#### 2-2、Collection接口中的常用方法2

1、Person类

```java
import java.util.Objects;

public class Person {

    private String name;
    private int age;

    public Person() {
        super();
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        System.out.println("Person equals()....");
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person person = (Person) o;
        return age == person.age &&
                Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {

        return Objects.hash(name, age);
    }
}
```

2、测试类

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collection;

/**
 * Collection接口中声明的方法的测试
 *
 * 结论：
 * 向Collection接口的实现类的对象中添加数据obj时，要求obj所在类要重写equals().
 */
public class CollectinoTest {

    @Test
    public void test(){
        Collection coll = new ArrayList();
        coll.add(123);
        coll.add(456);

//        Person p = new Person("Jerry",20);
//        coll.add(p);
        coll.add(new Person("Jerry",20));

        coll.add(new String("Tom"));
        coll.add(false);
//			用形参的equals方法来比！
        //1.contains(Object obj):判断当前集合中是否包含obj
        //我们在判断时会调用obj对象所在类的equals()。
        boolean contains = coll.contains(123);
        System.out.println(contains);
        System.out.println(coll.contains(new String("Tam")));
//        System.out.println(coll.contains(p));//true
        System.out.println(coll.contains(new Person("Jerry",20)));//false -->true
//			用形参的equals方法来比！
        //2.containsAll(Collection coll1):判断形参coll1中的所有元素是否都存在于当前集合中。
        Collection coll1 = Arrays.asList(123,4567);
        System.out.println(coll.containsAll(coll1));
    }

}
```

#### 2-3、Collection接口中的常用方法3

1、Person类

```java
import java.util.Objects;

public class Person {

    private String name;
    private int age;

    public Person() {
        super();
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        System.out.println("Person equals()....");
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person person = (Person) o;
        return age == person.age &&
                Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {

        return Objects.hash(name, age);
    }
}
```

2、测试类

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collection;

/**
 * Collection接口中声明的方法的测试
 *
 * 结论：
 * 向Collection接口的实现类的对象中添加数据obj时，要求obj所在类要重写equals().
 *
 */
public class CollectinoTest {

    @Test
    public void test2(){
        //3.remove(Object obj):从当前集合中移除obj元素。
        Collection coll = new ArrayList();
        coll.add(123);
        coll.add(456);
        coll.add(new Person("Jerry",20));
        coll.add(new String("Tom"));
        coll.add(false);

        coll.remove(1234);
        System.out.println(coll);

        coll.remove(new Person("Jerry",20));
        System.out.println(coll);

        //4. removeAll(Collection coll1):差集：从当前集合中移除coll1中所有的元素。删除所有相同项
        Collection coll1 = Arrays.asList(123,456);//每个coll1中元素把coll中所有元素都比较一遍！
        coll.removeAll(coll1);
        System.out.println(coll);
    }

    @Test
    public void test3(){
        Collection coll = new ArrayList();
        coll.add(123);
        coll.add(456);
        coll.add(new Person("Jerry",20));
        coll.add(new String("Tom"));
        coll.add(false);

        //5.retainAll(Collection coll1):交集：获取当前集合和coll1集合的交集，并返回给当前集合
//        Collection coll1 = Arrays.asList(123,456,789);
//        coll.retainAll(coll1);
//        System.out.println(coll);
//aslist()方法:将需要转化的对象数组作为参数，或者直接把数组元素作为参数!(如果是一个对象数组加上一些元素，则把对象数组整体当作一个对象，输出时只会输出地址，如果是int数组，则不会当作对象数组，当成单独元素，同样输出地址值，除非将int数组改为inteager数组)
        //6.equals(Object obj):要想返回true，需要当前集合和形参集合的元素都相同。
        Collection coll1 = new ArrayList();
        coll1.add(456);
        coll1.add(123);
        coll1.add(new Person("Jerry",20));
        coll1.add(new String("Tom"));
        coll1.add(false);

        System.out.println(coll.equals(coll1));
    }

}
```

#### 2-4、Collection接口中的常用方法4

1、Person类

```java
import java.util.Objects;

public class Person {

    private String name;
    private int age;

    public Person() {
        super();
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        System.out.println("Person equals()....");
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person person = (Person) o;
        return age == person.age &&
                Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {

        return Objects.hash(name, age);
    }
}
```

2、测试类

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collection;
import java.util.List;

/**
 * Collection接口中声明的方法的测试
 *
 * 结论：
 * 向Collection接口的实现类的对象中添加数据obj时，要求obj所在类要重写equals().
 *
 */
public class CollectinoTest {

    @Test
    public void test4(){
        Collection coll = new ArrayList();
        coll.add(123);
        coll.add(456);
        coll.add(new Person("Jerry",20));
        coll.add(new String("Tom"));
        coll.add(false);

        //7.hashCode():返回当前对象的哈希值
        System.out.println(coll.hashCode());

        //8.集合 --->数组：toArray()
        Object[] arr = coll.toArray();
        for(int i = 0;i < arr.length;i++){
            System.out.println(arr[i]);
        }

        //拓展：数组 --->集合:调用Arrays类的静态方法asList()
        List<String> list = Arrays.asList(new String[]{"AA", "BB", "CC"});
        System.out.println(list);

        List arr1 = Arrays.asList(123, 456);
        System.out.println(arr1);//[123, 456]

        List arr2 = Arrays.asList(new int[]{123, 456});
        System.out.println(arr2.size());//1

        List arr3 = Arrays.asList(new Integer[]{123, 456});
        System.out.println(arr3.size());//2

        //9.iterator():返回Iterator接口的实例，用于遍历集合元素。放在IteratorTest.java中测试
    }
}
```

### 3、iterator迭代器接口

Iterator对象称为迭代器(设计模式的一种)，主要用于遍历Collection 集合中的元素。
GOF给迭代器模式的定义为：提供一种方法访问一个容器(container)对象中各个元素，而又不需暴露该对象的内部细节。迭代器模式，就是为容器而生。类似于“公交车上的售票员”、“火车上的乘务员”、“空姐”。
Collection接口继承了java.lang.Iterable接口，该接口有一个iterator()方法，那么所有实现了Collection接口的集合类都有一个iterator()方法，用以返回一个实现了Iterator接口的对象。
Iterator 仅用于遍历集合，Iterator本身并不提供承装对象的能力。如果需要创建Iterator 对象，则必须有一个被迭代的集合。
集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标都在集合的第一个元素之前。

![img](https://img-blog.csdnimg.cn/img_convert/92824284e855a3c578bcd9a977bc528c.png)

#### 3-1、使用Iterator[遍历](https://so.csdn.net/so/search?q=遍历&spm=1001.2101.3001.7020)Collection

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

/**
 * 集合元素的遍历操作，使用迭代器Iterator接口
 * 内部的方法：hasNext()和 next()
 *
 */
public class IteratorTest {

    @Test
    public void test(){
        Collection coll = new ArrayList();
        coll.add(123);
        coll.add(456);
        coll.add(new Person("Jerry",20));
        coll.add(new String("Tom"));
        coll.add(false);

        Iterator iterator = coll.iterator();

        //方式一：
//        System.out.println(iterator.next());
//        System.out.println(iterator.next());
//        System.out.println(iterator.next());
//        System.out.println(iterator.next());
//        System.out.println(iterator.next());
//        //报异常：NoSuchElementException
//        //因为：在调用it.next()方法之前必须要调用it.hasNext()进行检测。若不调用，且下一条记录无效，直接调用it.next()会抛出NoSuchElementException异常。
//        System.out.println(iterator.next());

        //方式二：不推荐
//        for(int i = 0;i < coll.size();i++){
//            System.out.println(iterator.next());
//        }

        //方式三：推荐
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }
    }
}
```

#### 3-2、迭代器Iterator的执行原理

![img](https://img-blog.csdnimg.cn/img_convert/e22bd60a120c0355cbb2ae3601442cb7.png)

#### 3-3、Iterator遍历集合的两种错误写法

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

/**
 * 集合元素的遍历操作，使用迭代器Iterator接口
 * 1.内部的方法：hasNext()和 next()
 * 2.集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标都在集合的第一个元素之前。
 */
public class IteratorTest {

    @Test
    public void test2(){
        Collection coll = new ArrayList();
        coll.add(123);
        coll.add(456);
        coll.add(new Person("Jerry",20));
        coll.add(new String("Tom"));
        coll.add(false);

        //错误方式一：
//        Iterator iterator = coll.iterator();
//        while(iterator.next() != null){
//            System.out.println(iterator.next());
//        }

        //错误方式二：
        //集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标都在集合的第一个元素之前。
        while(coll.iterator().hasNext()){
            System.out.println(coll.iterator().next());
        }
    }
}
```

#### 3-4、Iterator迭代器remove()的使用

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

/**
 * 集合元素的遍历操作，使用迭代器Iterator接口
 * 1.内部的方法：hasNext()和 next()
 * 2.集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标都在集合的第一个元素之前。
 * 3.内部定义了remove(),可以在遍历的时候，删除集合中的元素。此方法不同于集合直接调用remove()
 */
public class IteratorTest {

    //测试Iterator中的remove()方法
    @Test
    public void test3(){
        Collection coll = new ArrayList();
        coll.add(123);
        coll.add(456);
        coll.add(new Person("Jerry",20));
        coll.add(new String("Tom"));
        coll.add(false);

        //删除集合中”Tom”
        //如果还未调用next()或在上一次调用 next 方法之后已经调用了 remove 方法，
        // 再调用remove都会报IllegalStateException。
        Iterator iterator = coll.iterator();
        while(iterator.hasNext()){
//            iterator.remove();
            Object obj = iterator.next();
            if("Tom".equals(obj)){
                iterator.remove();
//                iterator.remove();                
            }
        }

        //遍历集合
        iterator = coll.iterator();
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }

    }
}

```

注意：

Iterator可以删除集合的元素，但是是遍历过程中通过迭代器对象的remove方法，不是集合对象的remove方法。
如果还未调用next()或在上一次调用next方法之后已经调用了remove方法，再调用remove都会报IllegalStateException。

#### 3-5、新特性foreach循环遍历集合或数组

- Java 5.0 提供了foreach循环迭代访问Collection和数组。
- 遍历操作不需获取Collection或数组的长度，无需使用索引访问元素。
- 遍历集合的底层调用Iterator完成操作。
- foreach还可以用来遍历数组。

![img](https://img-blog.csdnimg.cn/img_convert/7f424cc6c34bd887f20adac6cd9afa0f.png)

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Collection;

/**
 * jdk 5.0 新增了foreach循环，用于遍历集合、数组
 *
 */
public class ForTest {

    @Test
    public void test(){
        Collection coll = new ArrayList();
        coll.add(123);
        coll.add(456);
        coll.add(new Person("Jerry",20));
        coll.add(new String("Tom"));
        coll.add(false);

        //for(集合元素的类型 局部变量 : 集合对象),内部仍然调用了迭代器。
        for(Object obj : coll){
            System.out.println(obj);
        }
    }

    @Test
    public void test2(){
        int[] arr = new int[]{1,2,3,4,5,6};
        //for(数组元素的类型 局部变量 : 数组对象)
        for(int i : arr){
            System.out.println(i);
        }
    }

    //练习题
    @Test
    public void test3(){
        String[] arr = new String[]{"SS","KK","RR"};

//        //方式一：普通for赋值
//        for(int i = 0;i < arr.length;i++){
//            arr[i] = "HH";
//        }

        //方式二：增强for循环
        for(String s : arr){
            s = "HH";
        }

        for(int i = 0;i < arr.length;i++){
            System.out.println(arr[i]);
        }
    }
}
```

### 4、Collection子接口之一：List接口

鉴于Java中数组用来存储数据的局限性，我们通常使用List替代数组
List集合类中元素有序、且可重复，集合中的每个元素都有其对应的顺序索引。
List容器中的元素都对应一个整数型的序号记载其在容器中的位置，可以根据序号存取容器中的元素。
JDK API中List接口的实现类常用的有：ArrayList、LinkedList和Vector。

#### 4-1、List接口常用实现类的对比

```java
/**
 * 1. List接口框架
 *
 *    |----Collection接口：单列集合，用来存储一个一个的对象
 *          |----List接口：存储有序的、可重复的数据。  -->“动态”数组,替换原有的数组
 *              |----ArrayList：作为List接口的主要实现类；线程不安全的，效率高；底层使用Object[] elementData存储
 *              |----LinkedList：对于频繁的插入、删除操作，使用此类效率比ArrayList高；底层使用双向链表存储
 *              |----Vector：作为List接口的古老实现类；线程安全的，效率低；底层使用Object[] elementData存储
 *
 *
 * 面试题：比较ArrayList、LinkedList、Vector三者的异同？
 *        同：三个类都是实现了List接口，存储数据的特点相同：存储有序的、可重复的数据
 *        不同：见上
 *
 */

```

#### 4-2、ArrayList的源码分析

- ArrayList是List 接口的典型实现类、主要实现类
- 本质上，ArrayList是对象引用的一个”变长”数组

```java
/** 
 * 2.ArrayList的源码分析：
 *   2.1 jdk 7情况下
 *      ArrayList list = new ArrayList();//底层创建了长度是10的Object[]数组elementData
 *      list.add(123);//elementData[0] = new Integer(123);
 *      ...
 *      list.add(11);//如果此次的添加导致底层elementData数组容量不够，则扩容。
 *      默认情况下，扩容为原来的容量的1.5倍，同时需要将原有数组中的数据复制到新的数组中。
 *
 *      结论：建议开发中使用带参的构造器：ArrayList list = new ArrayList(int capacity)
 *
 *   2.2 jdk 8中ArrayList的变化：
 *      ArrayList list = new ArrayList();//底层Object[] elementData初始化为{}.并没有创建长度为10的数组
 *
 *      list.add(123);//第一次调用add()时，底层才创建了长度10的数组，并将数据123添加到elementData[0]
 *      ...
 *      后续的添加和扩容操作与jdk 7 无异。
 *   2.3 小结：jdk7中的ArrayList的对象的创建类似于单例的饿汉式，而jdk8中的ArrayList的对象
 *            的创建类似于单例的懒汉式，延迟了数组的创建，节省内存。
 * 
 */

```

#### 4-3、LinkedList的源码分析

- 对于频繁的插入或删除元素的操作，建议使用LinkedList类，效率较高
- LinkedList：双向链表，内部没有声明数组，而是定义了Node类型的first和last，用于记录首末元素。同时，定义内部类Node，作为LinkedList中保存数据的基本结构。

![img](https://img-blog.csdnimg.cn/img_convert/1694eedac8f9664aa96cf0a673679e94.png)

```java
/**
  * 3.LinkedList的源码分析：
  *       LinkedList list = new LinkedList(); 内部声明了Node类型的first和last属性，默认值为null
  *       list.add(123);//将123封装到Node中，创建了Node对象。
  *
  *       其中，Node定义为：体现了LinkedList的双向链表的说法
  *       private static class Node<E> {
  *            E item;
  *            Node<E> next;
  *            Node<E> prev;
  *
  *            Node(Node<E> prev, E element, Node<E> next) {
  *            this.item = element;
  *            this.next = next;     //next变量记录下一个元素的位置
  *            this.prev = prev;     //prev变量记录前一个元素的位置
  *            }
  *        }
  */

```

#### 4-4、Vector的源码分析

Vector 是一个古老的集合，JDK1.0就有了。大多数操作与ArrayList相同，区别之处在于Vector是线程安全的。
在各种list中，最好把ArrayList作为缺省选择。当插入、删除频繁时，使用LinkedList；Vector总是比ArrayList慢，所以尽量避免使用。

```java
/** 
  * 4.Vector的源码分析：jdk7和jdk8中通过Vector()构造器创建对象时，底层都创建了长度为10的数组。
  *      在扩容方面，默认扩容为原来的数组长度的2倍。
  */ 

```

#### 4-5、List接口中的常用方法测试

List除了从Collection集合继承的方法外，List 集合里添加了一些根据索引来操作集合元素的方法。

void add(intindex, Object ele):在index位置插入ele元素
boolean addAll(int index, Collection eles):从index位置开始将eles中的所有元素添加进来
Object get(int index):获取指定index位置的元素
int indexOf(Object obj):返回obj在集合中首次出现的位置
int lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置
Object remove(int index):移除指定index位置的元素，并返回此元素
Object set(int index, Object ele):设置指定index位置的元素为ele
List subList(int fromIndex, int toIndex):返回从fromIndex到toIndex位置的子集合

```java
import org.junit.Test;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Iterator;
import java.util.List;

/**
 *
 * 5.List接口的常用方法
 */
public class ListTest {
    /**
     *
     * void add(int index, Object ele):在index位置插入ele元素
     * boolean addAll(int index, Collection eles):从index位置开始将eles中的所有元素添加进来
     * Object get(int index):获取指定index位置的元素
     * int indexOf(Object obj):返回obj在集合中首次出现的位置
     * int lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置
     * Object remove(int index):移除指定index位置的元素，并返回此元素
     * Object set(int index, Object ele):设置指定index位置的元素为ele
     * List subList(int fromIndex, int toIndex):返回从fromIndex到toIndex位置的子集合
     *
     * 总结：常用方法
     * 增：add(Object obj)
     * 删：remove(int index) / remove(Object obj)
     * 改：set(int index, Object ele)
     * 查：get(int index)
     * 插：add(int index, Object ele)
     * 长度：size()
     * 遍历：① Iterator迭代器方式
     *      ② 增强for循环
     *      ③ 普通的循环
     *
     */

    @Test
    public void test3(){
        ArrayList list = new ArrayList();
        list.add(123);
        list.add(456);
        list.add("AA");

        //方式一：Iterator迭代器方式
        Iterator iterator = list.iterator();
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }

        System.out.println("***************");

        //方式二：增强for循环
        for(Object obj : list){
            System.out.println(obj);
        }

        System.out.println("***************");

        //方式三：普通for循环
        for(int i = 0;i < list.size();i++){
            System.out.println(list.get(i));
        }
    }

    @Test
    public void tets2(){
        ArrayList list = new ArrayList();
        list.add(123);
        list.add(456);
        list.add("AA");
        list.add(new Person("Tom",12));
        list.add(456);
        //int indexOf(Object obj):返回obj在集合中首次出现的位置。如果不存在，返回-1.
        int index = list.indexOf(4567);
        System.out.println(index);

        //int lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置。如果不存在，返回-1.
        System.out.println(list.lastIndexOf(456));

        //Object remove(int index):移除指定index位置的元素，并返回此元素
        Object obj = list.remove(0);
        System.out.println(obj);
        System.out.println(list);

        //Object set(int index, Object ele):设置指定index位置的元素为ele
        list.set(1,"CC");
        System.out.println(list);

        //List subList(int fromIndex, int toIndex):返回从fromIndex到toIndex位置的左闭右开区间的子集合
        List subList = list.subList(2, 4);
        System.out.println(subList);
        System.out.println(list);
    }

    @Test
    public void test(){
        ArrayList list = new ArrayList();
        list.add(123);
        list.add(456);
        list.add("AA");
        list.add(new Person("Tom",12));
        list.add(456);

        System.out.println(list);

        //void add(int index, Object ele):在index位置插入ele元素
        list.add(1,"BB");
        System.out.println(list);

        //boolean addAll(int index, Collection eles):从index位置开始将eles中的所有元素添加进来
        List list1 = Arrays.asList(1, 2, 3);
        list.addAll(list1);
//        list.add(list1);
        System.out.println(list.size());//9

        //Object get(int index):获取指定index位置的元素
        System.out.println(list.get(2));

    }
}
```

#### 4-6、List的一个面试小题

> 1、面试题1

请问ArrayList/LinkedList/Vector的异同？谈谈你的理解？ArrayList底层是什么？扩容机制？Vector和ArrayList的最大区别?

```java
   /**
     * 请问ArrayList/LinkedList/Vector的异同？谈谈你的理解？
     * ArrayList底层是什么？扩容机制？Vector和ArrayList的最大区别?
     * 
     * ArrayList和LinkedList的异同二者都线程不安全，相对线程安全的Vector，执行效率高。
     * 此外，ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。
     * 对于随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针。
     * 对于新增和删除操作add(特指插入)和remove，LinkedList比较占优势，因为ArrayList要移动数据。
     * 
     * ArrayList和Vector的区别Vector和ArrayList几乎是完全相同的,
     * 唯一的区别在于Vector是同步类(synchronized)，属于强同步类。
     * 因此开销就比ArrayList要大，访问要慢。正常情况下,
     * 大多数的Java程序员使用ArrayList而不是Vector,
     * 因为同步完全可以由程序员自己来控制。Vector每次扩容请求其大小的2倍空间，
     * 而ArrayList是1.5倍。Vector还有一个子类Stack。
     */

```

2、面试题2

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.List;

public class ListEver {
    /**
     * 区分List中remove(int index)和remove(Object obj)
     */

    @Test
    public void testListRemove() {
        List list = new ArrayList();
        list.add(1);
        list.add(2);
        list.add(3);
        updateList(list);
        System.out.println(list);//
    }

    private void updateList(List list) {
//        list.remove(2);
        list.remove(new Integer(2));
    }
}
```

### 5、Collection子接口之二：Set接口

- Set接口是Collection的子接口，set接口没有提供额外的方法
- Set 集合不允许包含相同的元素，如果试把两个相同的元素加入同一个Set 集合中，则添加操作失败。
- **Set 判断两个对象是否相同不是使用`==`运算符，而是根据`equals()`方法**

#### 5-1、Set接口实现类的对比

```java
/**
 * 1.Set接口的框架：
 * |----Collection接口：单列集合，用来存储一个一个的对象
 *          |----Set接口：存储无序的、不可重复的数据   -->高中讲的“集合”
 *             |----HashSet：作为Set接口的主要实现类；线程不安全的；可以存储null值
 *                 |----LinkedHashSet：作为HashSet的子类；遍历其内部数据时，可以按照添加的顺序遍历
 *                                    对于频繁的遍历操作，LinkedHashSet效率高于HashSet.
 *             |----TreeSet：可以按照添加对象的指定属性，进行排序。
 */

```

#### 5-2、Set的无序性与不可重复性的理解

1、测试类

```java
import org.junit.Test;

import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

/**
 *
 * 1.Set接口中没有定义额外的方法，使用的都是Collection中声明过的方法。
 *
 */
public class SetTest {

    /**
     * 一、Set:存储无序的、不可重复的数据
     *      1.无序性：不等于随机性。存储的数据在底层数组中并非按照数组索引的顺序添加，而是根据数据的哈希值决定的。
     *
     *      2.不可重复性：保证添加的元素按照equals()判断时，不能返回true.即：相同的元素只能添加一个。
     *
     * 二、添加元素的过程：以HashSet为例：
     *
     *
     */
    @Test
    public void test(){
        Set set = new HashSet();
        set.add(123);
        set.add(456);
        set.add("fgd");
        set.add("book");
        set.add(new User("Tom",12));
        set.add(new User("Tom",12));
        set.add(129);

        Iterator iterator = set.iterator();
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }
    }
}
```

2、User类

```java
public class User{
    private String name;
    private int age;

    public User() {
    }

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        System.out.println("User equals()....");
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        User user = (User) o;

        if (age != user.age) return false;
        return name != null ? name.equals(user.name) : user.name == null;
    }

    @Override
    public int hashCode() { 
        int result = name != null ? name.hashCode() : 0;
        result = 31 * result + age;
        return result;
    }
}

```

#### 5-3、HashSet中元素的添加过程

HashSet是Set 接口的典型实现，大多数时候使用Set 集合时都使用这个实现类。
HashSet按Hash 算法来存储集合中的元素，因此具有很好的存取、查找、删除性能。
HashSet具有以下特点：不能保证元素的排列顺序
HashSet不是线程安全的
集合元素可以是null
底层也是数组，初始容量为16，当如果使用率超过0.75，（16*0.75=12）就会扩大容量为原来的2倍。（16扩容为32，依次为64,128…等）
HashSet 集合判断两个元素相等的标准：两个对象通过hashCode() 方法比较相等，并且两个对象的equals()方法返回值也相等。
对于存放在Set容器中的对象，对应的类一定要重写equals()和hashCode(Object obj)方法，以实现对象相等规则。即：“相等的对象必须具有相等的散列码”。

```java
/**
     * 一、Set:存储无序的、不可重复的数据
     *      1.无序性：不等于随机性。存储的数据在底层数组中并非按照数组索引的顺序添加，而是根据数据的哈希值决定的。
     *
     *      2.不可重复性：保证添加的元素按照equals()判断时，不能返回true.即：相同的元素只能添加一个。
     *
     * 二、添加元素的过程：以HashSet为例：
     *      我们向HashSet中添加元素a,首先调用元素a所在类的hashCode()方法，计算元素a的哈希值，
     *      此哈希值接着通过某种算法计算出在HashSet底层数组中的存放位置（即为：索引位置），判断
     *      数组此位置上是否已经有元素：
     *          如果此位置上没有其他元素，则元素a添加成功。 --->情况1
     *          如果此位置上有其他元素b(或以链表形式存在的多个元素），则比较元素a与元素b的hash值：
     *              如果hash值不相同，则元素a添加成功。--->情况2
     *              如果hash值相同，进而需要调用元素a所在类的equals()方法：
     *                    equals()返回true,元素a添加失败
     *                    equals()返回false,则元素a添加成功。--->情况2
     *
     *      对于添加成功的情况2和情况3而言：元素a 与已经存在指定索引位置上数据以链表的方式存储。
     *      jdk 7 :元素a放到数组中，指向原来的元素。
     *      jdk 8 :原来的元素在数组中，指向元素a
     *      总结：七上八下
     *
     * HashSet底层：数组+链表的结构。
     *
     */

```

![img](https://img-blog.csdnimg.cn/img_convert/9cadfe3cd3721e9c7ba5f414f57434ec.png)

#### 5-4、关于hashCode()和equals()的重写

##### 5-4-1、重写hashCode() 方法的基本原则

- 在程序运行时，同一个对象多次调用`hashCode()`方法应该返回相同的值。
- 当两个对象的`equals()`方法比较返回`true`时，这两个对象的`hashCode()`方法的返回值也应相等。
- 对象中用作`equals()` 方法比较的`Field`，都应该用来计算`hashCode`值。

##### 5-4-2、重写equals() 方法的基本原则

以自定义的Customer类为例，何时需要重写equals()？

当一个类有自己特有的“逻辑相等”概念,当改写equals()的时候，总是要改写hashCode()，根据一个类的equals方法（改写后），两个截然不同的实例有可能在逻辑上是相等的，但是，根据Object.hashCode()方法，它们仅仅是两个对象。
因此，违反了“相等的对象必须具有相等的散列码”。
结论：复写equals方法的时候一般都需要同时复写hashCode方法。通常参与计算hashCode的对象的属性也应该参与到equals()中进行计算。

##### 5-4-3、Eclipse/IDEA工具里hashCode()的重写

以Eclipse/IDEA为例，在自定义类中可以调用工具自动重写equals和hashCode。问题：为什么用Eclipse/IDEA复写hashCode方法，有31这个数字？

选择系数的时候要选择尽量大的系数。因为如果计算出来的hash地址越大，所谓的“冲突”就越少，查找起来效率也会提高。（减少冲突）
并且31只占用5bits,相乘造成数据溢出的概率较小。
31可以由i*31== (i<<5)-1来表示,现在很多虚拟机里面都有做相关优化。（提高算法效率）
31是一个素数，素数作用就是如果我用一个数字来乘以这个素数，那么最终出来的结果只能被素数本身和被乘数还有1来整除！(减少冲突)

```java
/**
  * 2.要求：向Set(主要指：HashSet、LinkedHashSet)中添加的数据，其所在的类一定要重写hashCode()和equals()
  *   要求：重写的hashCode()和equals()尽可能保持一致性：相等的对象必须具有相等的散列码
  *        重写两个方法的小技巧：对象中用作 equals() 方法比较的 Field，都应该用来计算 hashCode 值。
 */

```

#### 5-5、LinkedHashSet的使用

LinkedHashSet是HashSet的子类
LinkedHashSet根据元素的hashCode值来决定元素的存储位置，但它同时使用双向链表维护元素的次序，这使得元素看起来是以插入顺序保存的。
LinkedHashSet插入性能略低于HashSet，但在迭代访问Set 里的全部元素时有很好的性能。
LinkedHashSet不允许集合元素重复。
![img](https://img-blog.csdnimg.cn/img_convert/142499a55331e1ce03aa23593f2f66a7.png)

1.测试类

```java
import org.junit.Test;

import java.util.Iterator;
import java.util.LinkedHashSet;
import java.util.Set;

public class SetTest {

    /**
     * LinkedHashSet的使用
     * LinkedHashSet作为HashSet的子类，在添加数据的同时，每个数据还维护了两个引用，记录此数据前一个
     * 数据和后一个数据。
     * 优点：对于频繁的遍历操作，LinkedHashSet效率高于HashSet
     */
    @Test
    public void test2(){
        Set set = new LinkedHashSet();
        set.add(456);
        set.add(123);
        set.add(123);
        set.add("AA");
        set.add("CC");
        set.add(new User("Tom",12));
        set.add(new User("Tom",12));
        set.add(129);

        Iterator iterator = set.iterator();
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }
    }
}

```

2.User类

```java
public class User{
    private String name;
    private int age;

    public User() {
    }

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        System.out.println("User equals()....");
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        User user = (User) o;

        if (age != user.age) return false;
        return name != null ? name.equals(user.name) : user.name == null;
    }

    @Override
    public int hashCode() { //return name.hashCode() + age;
        int result = name != null ? name.hashCode() : 0;
        result = 31 * result + age;
        return result;
    }
}
```

#### 5.6、TreeSet的自然排序

TreeSet是SortedSet接口的实现类，TreeSet可以确保集合元素处于排序状态。
TreeSet底层使用红黑树结构存储数据
新增的方法如下：(了解)
Comparator comparator()
Object first()
Object last()
Object lower(Object e)
Object higher(Object e)
SortedSet subSet(fromElement, toElement)
SortedSet headSet(toElement)
SortedSet tailSet(fromElement)
TreeSet两种排序方法：自然排序和定制排序。默认情况下，TreeSet采用自然排序。
TreeSet和后面要讲的TreeMap采用红黑树的存储结构
特点：有序，查询速度比List快
自然排序：TreeSet会调用集合元素的compareTo(Object obj)方法来比较元素之间的大小关系，然后将集合元素按升序(默认情况)排列。
如果试图把一个对象添加到TreeSet时，则该对象的类必须实现Comparable 接口。
实现Comparable 的类必须实现compareTo(Object obj)方法，两个对象即通过compareTo(Object obj)方法的返回值来比较大小。
Comparable 的典型实现：
BigDecimal、BigInteger以及所有的数值型对应的包装类：按它们对应的数值大小进行比较
Character：按字符的unicode值来进行比较
Boolean：true 对应的包装类实例大于false 对应的包装类实例
String：按字符串中字符的unicode 值进行比较
Date、Time：后边的时间、日期比前面的时间、日期大
向TreeSet中添加元素时，只有第一个元素无须比较compareTo()方法，后面添加的所有元素都会调用compareTo()方法进行比较。
因为只有相同类的两个实例才会比较大小，所以向TreeSet中添加的应该是同一个类的对象。
对于TreeSet集合而言，它判断两个对象是否相等的唯一标准是：两个对象通过compareTo(Object obj)方法比较返回值。
当需要把一个对象放入TreeSet中，重写该对象对应的equals()方法时，应保证该方法与compareTo(Object obj) 方法有一致的结果：如果两个对象通过equals()方法比较返回true，则通过compareTo(Object obj)方法比较应返回0。否则，让人难以理解。
![img](https://img-blog.csdnimg.cn/img_convert/dceafcf11f36434b2fba8584a0202e3a.png)

1.测试类

```java
import org.junit.Test;

import java.util.Iterator;
import java.util.TreeSet;

/**
 * 1.向TreeSet中添加的数据，要求是相同类的对象。
 * 2.两种排序方式：自然排序（实现Comparable接口） 和 定制排序（Comparator）
 * 3.自然排序中，比较两个对象是否相同的标准为：compareTo()返回0.不再是equals().
 * 4.定制排序中，比较两个对象是否相同的标准为：compare()返回0.不再是equals().
 */
public class TreeSetTest {

    @Test
    public void test() {
        TreeSet set = new TreeSet();

        //失败：不能添加不同类的对象
//        set.add(123);
//        set.add(456);
//        set.add("AA");
//        set.add(new User("Tom",12));

        //举例一：
//        set.add(34);
//        set.add(-34);
//        set.add(43);
//        set.add(11);
//        set.add(8);

        //举例二：
        set.add(new User("Tom",12));
        set.add(new User("Jerry",32));
        set.add(new User("Jim",2));
        set.add(new User("Mike",65));
        set.add(new User("Jack",33));
        set.add(new User("Jack",56));

        Iterator iterator = set.iterator();
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }
    }
}
```

2.User类

```java
public class User implements Comparable{
    private String name;
    private int age;

    public User() {
    }

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        System.out.println("User equals()....");
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        User user = (User) o;

        if (age != user.age) return false;
        return name != null ? name.equals(user.name) : user.name == null;
    }

    @Override
    public int hashCode() { //return name.hashCode() + age;
        int result = name != null ? name.hashCode() : 0;
        result = 31 * result + age;
        return result;
    }

    //按照姓名从大到小排列,年龄从小到大排列
    @Override
    public int compareTo(Object o) {
        if (o instanceof User) {
            User user = (User) o;
//            return this.name.compareTo(user.name);  //按照姓名从小到大排列
//            return -this.name.compareTo(user.name);  //按照姓名从大到小排列
            int compare = -this.name.compareTo(user.name);  //按照姓名从大到小排列
            if(compare != 0){   //年龄从小到大排列
                return compare;
            }else{
                return Integer.compare(this.age,user.age);
            }
        } else {
            throw new RuntimeException("输入的类型不匹配");
        }
    }
}
```

#### 5-7、TreeSet的定制排序

TreeSet的自然排序要求元素所属的类实现Comparable接口，如果元素所属的类没有实现Comparable接口，或不希望按照升序(默认情况)的方式排列元素或希望按照其它属性大小进行排序，则考虑使用定制排序。定制排序，通过Comparator接口来实现。需要重写compare(T o1,T o2)方法。
利用int compare(T o1,T o2)方法，比较o1和o2的大小：如果方法返回正整数，则表示o1大于o2；如果返回0，表示相等；返回负整数，表示o1小于o2。
要实现定制排序，需要将实现Comparator接口的实例作为形参传递给TreeSet的构造器。
此时，仍然只能向TreeSet中添加类型相同的对象。否则发生ClassCastException异常。
使用定制排序判断两个元素相等的标准是：通过Comparator比较两个元素返回了0。
1、测试类

```java
import org.junit.Test;

import java.util.Comparator;
import java.util.Iterator;
import java.util.TreeSet;

/**
 * 1.向TreeSet中添加的数据，要求是相同类的对象。
 * 2.两种排序方式：自然排序（实现Comparable接口） 和 定制排序（Comparator）
 * 3.自然排序中，比较两个对象是否相同的标准为：compareTo()返回0.不再是equals().
 * 4.定制排序中，比较两个对象是否相同的标准为：compare()返回0.不再是equals().
 */
public class TreeSetTest {

    @Test
    public void tets2(){
        Comparator com = new Comparator() {
            //按照年龄从小到大排列
            @Override
            public int compare(Object o1, Object o2) {
                if(o1 instanceof User && o2 instanceof User){
                    User u1 = (User)o1;
                    User u2 = (User)o2;
                    return Integer.compare(u1.getAge(),u2.getAge());
                }else{
                    throw new RuntimeException("输入的数据类型不匹配");
                }
            }
        };

        TreeSet set = new TreeSet(com);
        set.add(new User("Tom",12));
        set.add(new User("Jerry",32));
        set.add(new User("Jim",2));
        set.add(new User("Mike",65));
        set.add(new User("Mary",33));
        set.add(new User("Jack",33));
        set.add(new User("Jack",56));


        Iterator iterator = set.iterator();
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }
    }
}
```

2.User类

```java
public class User implements Comparable{
    private String name;
    private int age;

    public User() {
    }

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        System.out.println("User equals()....");
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        User user = (User) o;

        if (age != user.age) return false;
        return name != null ? name.equals(user.name) : user.name == null;
    }

    @Override
    public int hashCode() { //return name.hashCode() + age;
        int result = name != null ? name.hashCode() : 0;
        result = 31 * result + age;
        return result;
    }

    //按照姓名从大到小排列,年龄从小到大排列
    @Override
    public int compareTo(Object o) {
        if (o instanceof User) {
            User user = (User) o;
//            return this.name.compareTo(user.name);  //按照姓名从小到大排列
//            return -this.name.compareTo(user.name);  //按照姓名从大到小排列
            int compare = -this.name.compareTo(user.name);  //按照姓名从大到小排列
            if(compare != 0){   //年龄从小到大排列
                return compare;
            }else{
                return Integer.compare(this.age,user.age);
            }
        } else {
            throw new RuntimeException("输入的类型不匹配");
        }
    }
}

```

#### 5-8、TreeSet的课后练习

![img](https://img-blog.csdnimg.cn/img_convert/bf48149ea63b1be479da1a19db027fb1.png)

1、MyDate类

```java
/**
 * MyDate类包含:
 * private成员变量year,month,day；并为每一个属性定义getter,  setter 方法；
 */
public class MyDate implements Comparable{
    private int year;
    private int month;
    private int day;

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        this.year = year;
    }

    public int getMonth() {
        return month;
    }

    public void setMonth(int month) {
        this.month = month;
    }

    public int getDay() {
        return day;
    }

    public void setDay(int day) {
        this.day = day;
    }

    public MyDate() {
    }

    public MyDate(int year, int month, int day) {
        this.year = year;
        this.month = month;
        this.day = day;
    }

    @Override
    public String toString() {
        return "MyDate{" +
                "year=" + year +
                ", month=" + month +
                ", day=" + day +
                '}';
    }

    @Override
    public int compareTo(Object o) {
        if(o instanceof MyDate){
            MyDate m = (MyDate)o;

            //比较年
            int minusYear = this.getYear() - m.getYear();
            if(minusYear != 0){
                return minusYear;
            }
            //比较月
            int minusMonth = this.getMonth() - m.getMonth();
            if(minusMonth != 0){
                return minusMonth;
            }
            //比较日
            return this.getDay() - m.getDay();
        }

        throw new RuntimeException("传入的数据类型不一致！");

    }
}
```

2、Employee类

```java
/**
 * 定义一个Employee类。
 * 该类包含：private成员变量name,age,birthday，
 * 其中birthday 为MyDate 类的对象；
 * 并为每一个属性定义getter, setter 方法；
 * 并重写toString 方法输出name, age, birthday
 */
public class Employee implements Comparable{
    private String name;
    private int age;
    private MyDate birthday;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public MyDate getBirthday() {
        return birthday;
    }

    public void setBirthday(MyDate birthday) {
        this.birthday = birthday;
    }

    public Employee() {
    }

    public Employee(String name, int age, MyDate birthday) {
        this.name = name;
        this.age = age;
        this.birthday = birthday;
    }

    @Override
    public String toString() {
        return "Employee{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", birthday=" + birthday +
                '}';
    }

    //按name排序
    @Override
    public int compareTo(Object o){
        if(o instanceof Employee){
            Employee e = (Employee)o;
            return this.name.compareTo(e.name);
        }
//        return 0;
        throw new RuntimeException("传入的数据类型不一致");
    }
}
```

3、测试类

```java
import org.junit.Test;

import java.util.Comparator;
import java.util.Iterator;
import java.util.TreeSet;

/**
 * 创建该类的5 个对象，并把这些对象放入TreeSet 集合中
 * （下一章：TreeSet 需使用泛型来定义）分别按以下两种方式
 * 对集合中的元素进行排序，并遍历输出：
 *
 * 1). 使Employee 实现Comparable 接口，并按name 排序
 * 2). 创建TreeSet 时传入Comparator对象，按生日日期的先后排序。
 */
public class EmployeeTest {

    //问题二：按生日日期的先后排序
    @Test
    public void test2(){
        TreeSet set = new TreeSet(new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                if(o1 instanceof Employee && o2 instanceof Employee){
                    Employee e1 = (Employee)o1;
                    Employee e2 = (Employee)o2;

                    MyDate b1 = e1.getBirthday();
                    MyDate b2 = e2.getBirthday();

                    //方式一：
//                    //比较年
//                    int minusYear = b1.getYear() - b2.getYear();
//                    if(minusYear != 0){
//                        return minusYear;
//                    }
//
//                    //比较月
//                    int minusMonth = b1.getMonth() - b2.getMonth();
//                    if(minusMonth != 0){
//                        return minusMonth;
//                    }
//
//                    //比较日
//                    return b1.getDay() - b2.getDay();

                    //方式二：
                    return b1.compareTo(b2);
                }
//                return 0;
                throw new RuntimeException("传入的数据类型不一致！");
            }
        });

        Employee e1 = new Employee("wangxianzhi",41,new MyDate(334,5,4));
        Employee e2 = new Employee("simaqian",43,new MyDate(-145,7,12));
        Employee e3 = new Employee("yanzhenqin",44,new MyDate(709,5,9));
        Employee e4 = new Employee("zhangqian",51,new MyDate(-179,8,12));
        Employee e5 = new Employee("quyuan",21,new MyDate(-340,12,4));

        set.add(e1);
        set.add(e2);
        set.add(e3);
        set.add(e4);
        set.add(e5);

        Iterator iterator = set.iterator();
        while (iterator.hasNext()){
            System.out.println(iterator.next());
        }
    }

    //问题一：使用自然排序
    @Test
    public void test(){
        TreeSet set = new TreeSet();

        Employee e1 = new Employee("wangxianzhi",41,new MyDate(334,5,4));
        Employee e2 = new Employee("simaqian",43,new MyDate(-145,7,12));
        Employee e3 = new Employee("yanzhenqin",44,new MyDate(709,5,9));
        Employee e4 = new Employee("zhangqian",51,new MyDate(-179,8,12));
        Employee e5 = new Employee("quyuan",21,new MyDate(-340,12,4));

        set.add(e1);
        set.add(e2);
        set.add(e3);
        set.add(e4);
        set.add(e5);

        Iterator iterator = set.iterator();
        while (iterator.hasNext()){
            System.out.println(iterator.next());
        }
    }
}

```

#### 5-9、Set课后两道面试题

练习：在List内去除重复数字值，要求尽量简单

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Collection;
import java.util.HashSet;
import java.util.List;

public class CollectionTest {

    //练习：在List内去除重复数字值，要求尽量简单
    public static List duplicateList(List list) {
        HashSet set = new HashSet();
        set.addAll(list);
        return new ArrayList(set);
    }
    @Test
    public void test2(){
        List list = new ArrayList();
        list.add(new Integer(1));
        list.add(new Integer(2));
        list.add(new Integer(2));
        list.add(new Integer(4));
        list.add(new Integer(4));
        List list2 = duplicateList(list);
        for (Object integer : list2) {
            System.out.println(integer);
        }
    }
}
```

2、面试题

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Collection;
import java.util.HashSet;
import java.util.List;

public class CollectionTest {

    @Test
    public void test3(){
        HashSet set = new HashSet();
        Person p1 = new Person(1001,"AA");
        Person p2 = new Person(1002,"BB");

        set.add(p1);
        set.add(p2);
        System.out.println(set);

        p1.name = "CC";
        set.remove(p1);
        System.out.println(set);
        set.add(new Person(1001,"CC"));
        System.out.println(set);
        set.add(new Person(1001,"AA"));
        System.out.println(set);

    }
}
```

person类：

```java
public class Person {

    int id;
    String name;

    public Person(int id, String name) {
        this.id = id;
        this.name = name;
    }

    public Person() {

    }

    @Override
    public String toString() {
        return "Person{" +
                "id=" + id +
                ", name='" + name + '\'' +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        Person person = (Person) o;

        if (id != person.id) return false;
        return name != null ? name.equals(person.name) : person.name == null;
    }

    @Override
    public int hashCode() {
        int result = id;
        result = 31 * result + (name != null ? name.hashCode() : 0);
        return result;
    }
}
```

### 6、Map接口

![img](https://img-blog.csdnimg.cn/img_convert/34101a405fcfc7c089f0165cb4c9545e.png)

#### 6-1、Map接口及其多个实现类的对比

```java
import org.junit.Test;

import java.util.HashMap;
import java.util.Map;

/**
 * 一、Map的实现类的结构：
 *  |----Map:双列数据，存储key-value对的数据   ---类似于高中的函数：y = f(x)
 *         |----HashMap:作为Map的主要实现类；线程不安全的，效率高；存储null的key和value
 *              |----LinkedHashMap:保证在遍历map元素时，可以按照添加的顺序实现遍历。
 *                      原因：在原有的HashMap底层结构基础上，添加了一对指针，指向前一个和后一个元素。
 *                      对于频繁的遍历操作，此类执行效率高于HashMap。
 *         |----TreeMap:保证按照添加的key-value对进行排序，实现排序遍历。此时考虑key的自然排序或定制排序
 *                      底层使用红黑树
 *         |----Hashtable:作为古老的实现类；线程安全的，效率低；不能存储null的key和value
 *              |----Properties:常用来处理配置文件。key和value都是String类型
 *
 *
 *      HashMap的底层：数组+链表  （jdk7及之前）
 *                    数组+链表+红黑树 （jdk 8）
 *
 *  面试题：
 *  1. HashMap的底层实现原理？
 *  2. HashMap 和 Hashtable的异同？
 *  3. CurrentHashMap 与 Hashtable的异同？（暂时不讲）
 *
 */
public class MapTest {
    @Test
    public void test(){
        Map map = new HashMap();
//        map = new Hashtable();
        map.put(null,123);
    }
}
```

#### 6-2、Map中存储的key-value的特点

Map与Collection并列存在。用于保存具有映射关系的数据:key-value
Map中的key和value都可以是任何引用类型的数据
Map 中的key 用Set来存放，不允许重复，即同一个Map 对象所对应的类，须重写hashCode()和equals()方法
常用String类作为Map的“键”
key和value之间存在单向一对一关系，即通过指定的key总能找到唯一的、确定的value
Map接口的常用实现类：HashMap、TreeMap、LinkedHashMap和Properties。其中，HashMap是Map接口使用频率最高的实现类
![img](https://img-blog.csdnimg.cn/img_convert/8be1971cf0f098a6512b9668871c3541.png)

```java
 /**
   *  二、Map结构的理解：
   *    Map中的key:无序的、不可重复的，使用Set存储所有的key  ---> key所在的类要重写equals()和hashCode() （以HashMap为例）
   *    Map中的value:无序的、可重复的，使用Collection存储所有的value --->value所在的类要重写equals()
   *    一个键值对：key-value构成了一个Entry对象。
   *    Map中的entry:无序的、不可重复的，使用Set存储所有的entry
   *
   */   
```

#### 6-3、Map实现类之一：HashMap

HashMap是Map接口使用频率最高的实现类。
允许使用null键和null值，与HashSet一样，不保证映射的顺序。
所有的key构成的集合是Set:无序的、不可重复的。所以，key所在的类要重写：equals()和hashCode()
所有的value构成的集合是Collection:无序的、可以重复的。所以，value所在的类要重写：equals()
一个key-value构成一个entry
所有的entry构成的集合是Set:无序的、不可重复的
HashMap判断两个key相等的标准是：两个key通过equals()方法返回true，hashCode值也相等。
HashMap判断两个value相等的标准是：两个value 通过equals()方法返回true。

#### 6-4、HashMap的底层实现原理

**JDK 7及以前版本：HashMap是数组+链表结构(即为链地址法)**

**JDK 8版本发布以后：HashMap是数组+链表+红黑树实现。**

![img](https://img-blog.csdnimg.cn/img_convert/58c89db281ee84d93098a4f043dd3856.png)

![img](https://img-blog.csdnimg.cn/img_convert/b2aebd46ed8d41111825cd15ac2a3be6.png)

HashMap源码中的重要常量

```java
/*
 *      DEFAULT_INITIAL_CAPACITY : HashMap的默认容量，16
 *      DEFAULT_LOAD_FACTOR：HashMap的默认加载因子：0.75
 *      threshold：扩容的临界值，=容量*填充因子：16 * 0.75 => 12
 *      TREEIFY_THRESHOLD：Bucket中链表长度大于该默认值，转化为红黑树:8
 *      MIN_TREEIFY_CAPACITY：桶中的Node被树化时最小的hash表容量:64
*/
```

##### 6-4-1、HashMap在JDK7中的底层实现原理

HashMap的内部存储结构其实是数组和链表的结合。当实例化一个HashMap时，系统会创建一个长度为Capacity的Entry数组，这个长度在哈希表中被称为容量(Capacity)，在这个数组中可以存放元素的位置我们称之为“桶”(bucket)，每个bucket都有自己的索引，系统可以根据索引快速的查找bucket中的元素。
每个bucket中存储一个元素，即一个Entry对象，但每一个Entry对象可以带一个引用变量，用于指向下一个元素，因此，在一个桶中，就有可能生成一个Entry链。而且新添加的元素作为链表的head。
添加元素的过程：
向HashMap中添加entry1(key，value)，需要首先计算entry1中key的哈希值(根据key所在类的hashCode()计算得到)，此哈希值经过处理以后，得到在底层Entry[]数组中要存储的位置i。
如果位置i上没有元素，则entry1直接添加成功。
如果位置i上已经存在entry2(或还有链表存在的entry3，entry4)，则需要通过循环的方法，依次比较entry1中key的hash值和其他的entry的hash值。
如果彼此hash值不同，则直接添加成功。
如果hash值相同，继续比较二者是否equals。如果返回值为true，则使用entry1的value去替换equals为true的entry的value。
如果遍历一遍以后，发现所有的equals返回都为false,则entry1仍可添加成功。entry1指向原有的entry元素。

```java
/*
 * 三、HashMap的底层实现原理？以jdk7为例说明：
 *    HashMap map = new HashMap():
 *    在实例化以后，底层创建了长度是16的一维数组Entry[] table。
 *    ...可能已经执行过多次put...
 *    map.put(key1,value1):
 *    首先，调用key1所在类的hashCode()计算key1哈希值，此哈希值经过某种算法计算以后，得到在Entry数组中的存放位置。
 *    如果此位置上的数据为空，此时的key1-value1添加成功。 ----情况1
 *    如果此位置上的数据不为空，(意味着此位置上存在一个或多个数据(以链表形式存在)),比较key1和已经存在的一个或多个数据
 *    的哈希值：
 *           如果key1的哈希值与已经存在的数据的哈希值都不相同，此时key1-value1添加成功。----情况2
 *           如果key1的哈希值和已经存在的某一个数据(key2-value2)的哈希值相同，继续比较：调用key1所在类的equals(key2)方法，比较：
 *                如果equals()返回false:此时key1-value1添加成功。----情况3
 *                如果equals()返回true:使用value1替换value2。
 *
 *   补充：关于情况2和情况3：此时key1-value1和原来的数据以链表的方式存储。
 *
 *   在不断的添加过程中，会涉及到扩容问题，当超出临界值(且要存放的位置非空)时，扩容。默认的扩容方式：扩容为原来容量的2倍，并将原有的数据复制过来。
 *
 */

/**
  * HashMap的扩容
  *     当HashMap中的元素越来越多的时候，hash冲突的几率也就越来越高，
  *     因为数组的长度是固定的。所以为了提高查询的效率，
  *     就要对HashMap的数组进行扩容，而在HashMap数组扩容之后，
  *     最消耗性能的点就出现了：原数组中的数据必须重新计算其在新数组中的位置，
  *     并放进去，这就是resize。
  *     
  * 那么HashMap什么时候进行扩容呢？
  *      当HashMap中的元素个数超过数组大小(数组总大小length,
  *      不是数组中个数size)*loadFactor时，就 会 进 行 数 组 扩 容，
  *      loadFactor的默认值(DEFAULT_LOAD_FACTOR)为0.75，这是一个折中的取值。
  *      也就是说，默认情况下，数组大小(DEFAULT_INITIAL_CAPACITY)为16，
  *      那么当HashMap中元素个数超过16*0.75=12（这个值就是代码中的threshold值，
  *      也叫做临界值）的时候，就把数组的大小扩展为2*16=32，即扩大一倍，
  *      然后重新计算每个元素在数组中的位置，而这是一个非常消耗性能的操作，
  *      所以如果我们已经预知HashMap中元素的个数，
  *      那么预设元素的个数能够有效的提高HashMap的性能。
  */

```

##### 6-4-2、HashMap在JDK8中的底层实现原理

HashMap的内部存储结构其实是数组+链表+红黑树的结合。当实例化一个HashMap时，会初始化initialCapacity和loadFactor，在put第一对映射关系时，系统会创建一个长度为initialCapacity的Node数组，这个长度在哈希表中被称为容量(Capacity)，在这个数组中可以存放元素的位置我们称之为“桶”(bucket)，每个bucket都有自己的索引，系统可以根据索引快速的查找bucket中的元素

每个bucket中存储一个元素，即一个Node对象，但每一个Node对象可以带一个引用变量next，用于指向下一个元素，因此，在一个桶中，就有可能生成一个Node链。也可能是一个一个TreeNode对象，每一个TreeNode对象可以有两个叶子结点left和right，因此，在一个桶中，就有可能生成一个TreeNode树。而新添加的元素作为链表的last，或树的叶子结点。

那么HashMap什么时候进行扩容和树形化呢？

当HashMap中的元素个数超过数组大小(数组总大小length,不是数组中个数size)*loadFactor时，就会进行数组扩容，loadFactor的默认值(DEFAULT_LOAD_FACTOR)为0.75，这是一个折中的取值。也就是说，默认情况下，数组大小(DEFAULT_INITIAL_CAPACITY)为16，那么当HashMap中元素个数超过16*0.75=12（这个值就是代码中的threshold值，也叫做临界值）的时候，就把数组的大小扩展为2*16=32，即扩大一倍，然后重新计算每个元素在数组中的位置，而这是一个非常消耗性能的操作，所以如果我们已经预知HashMap中元素的个数，那么预设元素的个数能够有效的提高HashMap的性能。

当HashMap中的其中一个链的对象个数如果达到了8个，此时如果capacity没有达到64，那么HashMap会先扩容解决，如果已经达到了64，那么这个链会变成红黑树，结点类型由Node变成TreeNode类型。当然，如果当映射关系被移除后，下次resize方法时判断树的结点个数低于6个，也会把红黑树再转为链表。

关于映射关系的key是否可以修改？answer：不要修改

映射关系存储到HashMap中会存储key的hash值，这样就不用在每次查找时重新计算每一个Entry或Node（TreeNode）的hash值了，因此如果已经put到Map中的映射关系，再修改key的属性，而这个属性又参与hashcode值的计算，那么会导致匹配不上。

```java
/* 总结：
 *   jdk8 相较于jdk7在底层实现方面的不同：
 *      1.new HashMap():底层没有创建一个长度为16的数组
 *      2.jdk 8底层的数组是：Node[],而非Entry[]
 *      3.首次调用put()方法时，底层创建长度为16的数组
 *      4.jdk7底层结构只有：数组+链表。jdk8中底层结构：数组+链表+红黑树。
 *         4.1形成链表时，七上八下（jdk7:新的元素指向旧的元素。jdk8：旧的元素指向新的元素）
 *         4.2当数组的某一个索引位置上的元素以链表形式存在的数据个数 > 8 且当前数组的长度 > 64时，此时此索引位置上的所数据改为使用红黑树存储。
 */
```

#### 6-5、LinkedHashMap的底层实现原理（了解）

LinkedHashMap是HashMap的子类

在HashMap存储结构的基础上，使用了一对双向链表来记录添加元素的顺序

与LinkedHashSet类似，LinkedHashMap可以维护Map 的迭代顺序：迭代顺序与Key-Value 对的插入顺序一致

HashMap中的内部类：Node
![img](https://img-blog.csdnimg.cn/img_convert/342cf58820c14e037baaadd31c600d80.png)

LinkedHashMap`中的内部类：`Entry

![img](https://img-blog.csdnimg.cn/img_convert/edbc291a09efb65428640308c90d7b8b.png)

```java
/*
 *  四、LinkedHashMap的底层实现原理（了解）
 *      源码中：
 *      static class Entry<K,V> extends HashMap.Node<K,V> {
 *            Entry<K,V> before, after;//能够记录添加的元素的先后顺序
 *            Entry(int hash, K key, V value, Node<K,V> next) {
 *               super(hash, key, value, next);
 *            }
 *        } 
 */
import org.junit.Test;

import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;

public class MapTest {

    @Test
    public void test2(){
        Map map = new HashMap();
        map = new LinkedHashMap();
        map.put(123,"AA");
        map.put(345,"BB");
        map.put(12,"CC");

        System.out.println(map);
    }
}
```

#### 6-6、Map中的常用方法1

```java
import org.junit.Test;

import java.util.*;
/**
 *  五、Map中定义的方法：
 *      添加、删除、修改操作：
 *      Object put(Object key,Object value)：将指定key-value添加到(或修改)当前map对象中
 *      void putAll(Map m):将m中的所有key-value对存放到当前map中
 *      Object remove(Object key)：移除指定key的key-value对，并返回value
 *      void clear()：清空当前map中的所有数据
 *      元素查询的操作：
 *      Object get(Object key)：获取指定key对应的value
 *      boolean containsKey(Object key)：是否包含指定的key
 *      boolean containsValue(Object value)：是否包含指定的value
 *      int size()：返回map中key-value对的个数
 *      boolean isEmpty()：判断当前map是否为空
 *      boolean equals(Object obj)：判断当前map和参数对象obj是否相等
 *      元视图操作的方法：
 *      Set keySet()：返回所有key构成的Set集合
 *      Collection values()：返回所有value构成的Collection集合
 *      Set entrySet()：返回所有key-value对构成的Set集合
 *
 */
public class MapTest {

    /**
     *  元素查询的操作：
     *  Object get(Object key)：获取指定key对应的value
     *  boolean containsKey(Object key)：是否包含指定的key
     *  boolean containsValue(Object value)：是否包含指定的value
     *  int size()：返回map中key-value对的个数
     *  boolean isEmpty()：判断当前map是否为空
     *  boolean equals(Object obj)：判断当前map和参数对象obj是否相等
     */
    @Test
    public void test4(){
        Map map = new HashMap();
        map.put("AA",123);
        map.put(45,123);
        map.put("BB",56);
        // Object get(Object key)
        System.out.println(map.get(45));
        //containsKey(Object key)
        boolean isExist = map.containsKey("BB");
        System.out.println(isExist);

        isExist = map.containsValue(123);
        System.out.println(isExist);

        map.clear();

        System.out.println(map.isEmpty());
    }

    /**
     * 添加、删除、修改操作：
     *  Object put(Object key,Object value)：将指定key-value添加到(或修改)当前map对象中
     *  void putAll(Map m):将m中的所有key-value对存放到当前map中
     *  Object remove(Object key)：移除指定key的key-value对，并返回value
     *  void clear()：清空当前map中的所有数据
     */
    @Test
    public void test3(){
        Map map = new HashMap();
        //添加
        map.put("AA",123);
        map.put(45,123);
        map.put("BB",56);
        //修改
        map.put("AA",87);

        System.out.println(map);

        Map map1 = new HashMap();
        map1.put("CC",123);
        map1.put("DD",456);
        map.putAll(map1);

        System.out.println(map);

        //remove(Object key)
        Object value = map.remove("CC");
        System.out.println(value);
        System.out.println(map);

        //clear()
        map.clear();//与map = null操作不同
        System.out.println(map.size());
        System.out.println(map);
    }
}
```

#### 6-7、Map中的常用方法2

```java
import org.junit.Test;

import java.util.*;
/**
 *  五、Map中定义的方法：
 *      添加、删除、修改操作：
 *      Object put(Object key,Object value)：将指定key-value添加到(或修改)当前map对象中
 *      void putAll(Map m):将m中的所有key-value对存放到当前map中
 *      Object remove(Object key)：移除指定key的key-value对，并返回value
 *      void clear()：清空当前map中的所有数据
 *      元素查询的操作：
 *      Object get(Object key)：获取指定key对应的value
 *      boolean containsKey(Object key)：是否包含指定的key
 *      boolean containsValue(Object value)：是否包含指定的value
 *      int size()：返回map中key-value对的个数
 *      boolean isEmpty()：判断当前map是否为空
 *      boolean equals(Object obj)：判断当前map和参数对象obj是否相等
 *      元视图操作的方法：
 *      Set keySet()：返回所有key构成的Set集合
 *      Collection values()：返回所有value构成的Collection集合
 *      Set entrySet()：返回所有key-value对构成的Set集合
 *
 * 总结：常用方法：
 *    添加：put(Object key,Object value)
 *    删除：remove(Object key)
 *    修改：put(Object key,Object value)
 *    查询：get(Object key)
 *    长度：size()
 *    遍历：keySet() / values() / entrySet()
 *
 *  面试题：
 *  1. HashMap的底层实现原理？
 *  2. HashMap 和 Hashtable的异同？
 *      1.HashMap与Hashtable都实现了Map接口。由于HashMap的非线程安全性，效率上可能高于Hashtable。Hashtable的方法是Synchronize的，而HashMap不是，在多个线程访问Hashtable时，不需要自己为它的方法实现同步，而HashMap 就必须为之提供外同步。
 *      2.HashMap允许将null作为一个entry的key或者value，而Hashtable不允许。
 *      3.HashMap把Hashtable的contains方法去掉了，改成containsvalue和containsKey。因为contains方法容易让人引起误解。
 *      4.Hashtable继承自Dictionary类，而HashMap是Java1.2引进的Map interface的一个实现。
 *      5.Hashtable和HashMap采用的hash/rehash算法都大概一样，所以性能不会有很大的差异。
 *
 *  3. CurrentHashMap 与 Hashtable的异同？（暂时不讲）
 *
 */
public class MapTest {

    /**
     *  元视图操作的方法：
     *  Set keySet()：返回所有key构成的Set集合
     *  Collection values()：返回所有value构成的Collection集合
     *  Set entrySet()：返回所有key-value对构成的Set集合
     */
    @Test
    public void test5(){
        Map map = new HashMap();
        map.put("AA",123);
        map.put(45,1234);
        map.put("BB",56);

        //遍历所有的key集：keySet()
        Set set = map.keySet();
        Iterator iterator = set.iterator();
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }
        System.out.println("*****************");

        //遍历所有的values集：values()
        Collection values = map.values();
        for(Object obj : values){
            System.out.println(obj);
        }
        System.out.println("***************");
        //遍历所有的key-values
        //方式一：
        Set entrySet = map.entrySet();
        Iterator iterator1 = entrySet.iterator();
        while (iterator1.hasNext()){
            Object obj = iterator1.next();
            //entrySet集合中的元素都是entry
            Map.Entry entry = (Map.Entry) obj;
            System.out.println(entry.getKey() + "---->" + entry.getValue());

        }
        System.out.println("/");

        //方式二：
        Set keySet = map.keySet();
        Iterator iterator2 = keySet.iterator();
        while(iterator2.hasNext()){
            Object key = iterator2.next();
            Object value = map.get(key);
            System.out.println(key + "=====" + value);
        }
    }
}
```

#### 6-8、TreeMap两种添加方式的使用

TreeMap存储Key-Value 对时，需要根据key-value对进行排序。TreeMap可以保证所有的Key-Value 对处于有序状态。
TreeSet底层使用红黑树结构存储数据
TreeMap的Key的排序：
自然排序：TreeMap的所有的Key 必须实现Comparable接口，而且所有的Key应该是同一个类的对象，否则将会抛出ClasssCastException
定制排序：创建TreeMap时，传入一个Comparator 对象，该对象负责对TreeMap中的所有key 进行排序。此时不需要Map 的Key实现Comparable 接口
TreeMap判断两个key相等的标准：两个key通过compareTo()方法或者compare()方法返回0。

1、User类

```java
public class User implements Comparable{
    private String name;
    private int age;

    public User() {
    }

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        System.out.println("User equals()....");
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        User user = (User) o;

        if (age != user.age) return false;
        return name != null ? name.equals(user.name) : user.name == null;
    }

    @Override
    public int hashCode() { //return name.hashCode() + age;
        int result = name != null ? name.hashCode() : 0;
        result = 31 * result + age;
        return result;
    }

    //按照姓名从大到小排列,年龄从小到大排列
    @Override
    public int compareTo(Object o) {
        if(o instanceof User){
            User user = (User)o;
//            return -this.name.compareTo(user.name);
            int compare = -this.name.compareTo(user.name);
            if(compare != 0){
                return compare;
            }else{
                return Integer.compare(this.age,user.age);
            }
        }else{
            throw new RuntimeException("输入的类型不匹配");
        }

    }
}
```

2、测试类

```java
import org.junit.Test;

import java.util.*;

public class TreeMapTest {

    /**
     * 向TreeMap中添加key-value，要求key必须是由同一个类创建的对象
     * 因为要按照key进行排序：自然排序 、定制排序
     */
    //自然排序
    @Test
    public void test(){
        TreeMap map = new TreeMap();
        User u1 = new User("Tom",23);
        User u2 = new User("Jerry",32);
        User u3 = new User("Jack",20);
        User u4 = new User("Rose",18);

        map.put(u1,98);
        map.put(u2,89);
        map.put(u3,76);
        map.put(u4,100);

        Set entrySet = map.entrySet();
        Iterator iterator1 = entrySet.iterator();
        while (iterator1.hasNext()){
            Object obj = iterator1.next();
            Map.Entry entry = (Map.Entry) obj;
            System.out.println(entry.getKey() + "---->" + entry.getValue());

        }
    }

    //定制排序
    @Test
    public void test2(){
        TreeMap map = new TreeMap(new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                if(o1 instanceof User && o2 instanceof User){
                    User u1 = (User)o1;
                    User u2 = (User)o2;
                    return Integer.compare(u1.getAge(),u2.getAge());
                }
                throw new RuntimeException("输入的类型不匹配！");
            }
        });
        User u1 = new User("Tom",23);
        User u2 = new User("Jerry",32);
        User u3 = new User("Jack",20);
        User u4 = new User("Rose",18);

        map.put(u1,98);
        map.put(u2,89);
        map.put(u3,76);
        map.put(u4,100);

        Set entrySet = map.entrySet();
        Iterator iterator1 = entrySet.iterator();
        while (iterator1.hasNext()){
            Object obj = iterator1.next();
            Map.Entry entry = (Map.Entry) obj;
            System.out.println(entry.getKey() + "---->" + entry.getValue());

        }
    }
}
```

#### 6-9、Hashtable

Hashtable是个古老的Map 实现类，JDK1.0就提供了。不同于HashMap，Hashtable是线程安全的。
Hashtable实现原理和HashMap相同，功能相同。底层都使用哈希表结构，查询速度快，很多情况下可以互用。
与HashMap不同，Hashtable不允许使用null 作为key和value
与HashMap一样，Hashtable也不能保证其中Key-Value 对的顺序
Hashtable判断两个key相等、两个value相等的标准，与HashMap一致。

#### 6-10、Properties处理属性文件

Properties 类是Hashtable的子类，该对象用于处理属性文件
由于属性文件里的key、value都是字符串类型，所以**Properties 里的key和value都是字符串类型**
存取数据时，建议使用setProperty(String key,Stringvalue)方法和getProperty(String key)方法

1、新建jdbc.properties文件
![img](https://img-blog.csdnimg.cn/img_convert/4800b141e7d9bb3c43211acd9f24b4e5.png)

![img](https://img-blog.csdnimg.cn/img_convert/e169a742c42b31bbd860df5cfd975025.png)

![img](https://img-blog.csdnimg.cn/img_convert/853471dde7dc490ea21e65190a65cb51.png)

2、编写源代码

```java
import java.io.FileInputStream;
import java.io.IOException;
import java.util.Properties;

public class PropertiesTest {
    //Properties:常用来处理配置文件。key和value都是String类型
    public static void main(String[] args){
        //快捷键：ALT+Shift+Z
        FileInputStream fis = null;
        try {
            Properties pros = new Properties();
            fis = new FileInputStream("jdbc.properties");
            pros.load(fis); //加载流对应文件

            String name = pros.getProperty("name");
            String password = pros.getProperty("password");

            System.out.println("name = " + name + ",password = " + password);
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if(fis != null){
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```

如果jdbc.properties文件中写入为中文；

防止jdbc.properties出现中文乱码，可根据如下解决：

![img](https://img-blog.csdnimg.cn/img_convert/d6e32450043ebfc6998bdbd1e1e6d815.png)

新建jdbc.properties

![img](https://img-blog.csdnimg.cn/img_convert/68dbda5f6415e90fd9033604e8403f7c.png)

### 7、Collections工具类

操作数组的工具类：Arrays
Collections 是一个操作Set、List和Map 等集合的工具类
Collections中提供了一系列静态的方法对集合元素进行排序、查询和修改等操作，还提供了对集合对象设置不可变、对集合对象实现同步控制等方法
排序操作：（均为static方法）
reverse(List)：反转List 中元素的顺序
shuffle(List)：对List集合元素进行随机排序
sort(List)：根据元素的自然顺序对指定List 集合元素按升序排序
sort(List，Comparator)：根据指定的Comparator 产生的顺序对List 集合元素进行排序
swap(List，int，int)：将指定list 集合中的i处元素和j 处元素进行交换

#### 7-1、Collections工具类常用方法的测试

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

/**
 * Collections:操作Collection、Map的工具类
 *
 * 面试题：Collection 和 Collections的区别？
 *       Collection是集合类的上级接口，继承于他的接口主要有Set 和List.
 *       Collections是针对集合类的一个帮助类，他提供一系列静态方法实现对各种集合的搜索、排序、线程安全化等操作.
 */
public class CollectionTest {
    /**
     * reverse(List)：反转 List 中元素的顺序
     * shuffle(List)：对 List 集合元素进行随机排序
     * sort(List)：根据元素的自然顺序对指定 List 集合元素按升序排序
     * sort(List，Comparator)：根据指定的 Comparator 产生的顺序对 List 集合元素进行排序
     * swap(List，int， int)：将指定 list 集合中的 i 处元素和 j 处元素进行交换
     *
     * Object max(Collection)：根据元素的自然顺序，返回给定集合中的最大元素
     * Object max(Collection，Comparator)：根据 Comparator 指定的顺序，返回给定集合中的最大元素
     * Object min(Collection)
     * Object min(Collection，Comparator)
     * int frequency(Collection，Object)：返回指定集合中指定元素的出现次数
     * void copy(List dest,List src)：将src中的内容复制到dest中
     * boolean replaceAll(List list，Object oldVal，Object newVal)：使用新值替换 List 对象的所有旧值
     *
     */

    @Test
    public void test(){
        List list = new ArrayList();
        list.add(123);
        list.add(43);
        list.add(765);
        list.add(765);
        list.add(765);
        list.add(-97);
        list.add(0);

        System.out.println(list);

//        Collections.reverse(list);
//        Collections.shuffle(list);
//        Collections.sort(list);
//        Collections.swap(list,1,2);
        int frequency = Collections.frequency(list, 123);

        System.out.println(list);
        System.out.println(frequency);
    }

    @Test
    public void test2(){
        List list = new ArrayList();
        list.add(123);
        list.add(43);
        list.add(765);
        list.add(-97);
        list.add(0);

        //报异常：IndexOutOfBoundsException("Source does not fit in dest")
//        List dest = new ArrayList();
//        Collections.copy(dest,list);
        //正确的：
        List dest = Arrays.asList(new Object[list.size()]);
        System.out.println(dest.size());//list.size();
        Collections.copy(dest,list);

        System.out.println(dest);

        /**
         * Collections 类中提供了多个 synchronizedXxx() 方法，
         * 该方法可使将指定集合包装成线程同步的集合，从而可以解决
         * 多线程并发访问集合时的线程安全问题
         */
        //返回的list1即为线程安全的List
        List list1 = Collections.synchronizedList(list);
    }
}
```

#### 7-2、补充：Enumeration(了解！！！)

![img](https://img-blog.csdnimg.cn/img_convert/0941872358abded0001ec9579776852f.png)

```java
Enumeration stringEnum = new StringTokenizer("a-b*c-d-e-g", "-");
    while(stringEnum.hasMoreElements()){
        Object obj= stringEnum.nextElement();System.out.println(obj); 
    }

```

## 15、泛型

### 1、为什么要有泛型

泛型：标签

#### 1-1、举例

- 中药店，每个抽屉外面贴着标签
- 超市购物架上很多瓶子，每个瓶子装的是什么，有标签。

#### 1-2、泛型的设计背景

集合容器类在设计阶段/声明阶段不能确定这个容器到底实际存的是什么类型的对象，所以在JDK1.5之前只能把元素类型设计为Object，JDK1.5之后使用泛型来解决。因为这个时候除了元素的类型不确定，其他的部分是确定的，例如关于这个元素如何保存，如何管理等是确定的，因此此时把元素的类型设计成一个参数，这个类型参数叫做泛型。Collection，List，ArrayList这个就是类型参数，即泛型。

#### 1-3、其他说明

所谓泛型，就是允许在定义类、接口时通过一个标识表示类中某个属性的类型或者是某个方法的返回值及参数类型。这个类型参数将在使用时（例如，继承或实现这个接口，用这个类型声明变量、创建对象时）确定（即传入实际的类型参数，也称为类型实参）。
从JDK1.5以后，Java引入了“参数化类型（Parameterizedtype）”的概念，允许我们在创建集合时再指定集合元素的类型，正如：List，这表明该List只能保存字符串类型的对象。
JDK1.5改写了集合框架中的全部接口和类，为这些接口、类增加了泛型支持，从而可以在声明集合变量、创建集合对象时传入类型实参。

#### 1-4、那么为什么要有泛型呢

**那么为什么要有泛型呢，直接Object不是也可以存储数据吗？**

> **1、解决元素存储的安全性问题，好比商品、药品标签，不会弄错。2.解决获取数据元素时，需要类型强制转换的问题，好比不用每回拿商品、药品都要辨别。**

![img](https://img-blog.csdnimg.cn/img_convert/e8b9c3de54e6610e42e08ea1a2d9f98a.png)

![img](https://img-blog.csdnimg.cn/img_convert/7bff707c9e87b7fafd21c1b57804fa7d.png)

**2、Java泛型可以保证如果程序在编译时没有发出警告，运行时就不会产生ClassCastException异常。同时，代码更加简洁、健壮。**

```java
import org.junit.Test;

import java.util.ArrayList;

/**
 * 泛型的使用
 * 1.jdk5.0新增的特征
 */
public class GenericTest {

    //在集合中使用泛型之前的情况：
    @Test
    public void test(){
        ArrayList list = new ArrayList();
        //需求：存放学生的成绩
        list.add(78);
        list.add(49);
        list.add(72);
        list.add(81);
        list.add(89);
        //问题一：类型不安全
//        list.add("Tom");

        for(Object score : list){
            //问题二：强转时可能出现类型转化异常
            int stuScore = (Integer)score;

            System.out.println(stuScore);
        }

    }

}
```

### 2、在集合中使用泛型

注意点：泛型的类型必须是类，不能是基本数据类型。需要用到基本数据类型的位置，拿包装类替换

#### 2-1、举例

```java
import org.junit.Test;

import java.util.*;

/**
 * 泛型的使用
 * 1.jdk5.0新增的特征
 *
 * 2.在集合中使用泛型：
 *  总结：
 *  ①集合接口或集合类在jdk5.0时都修改为带泛型的结构。
 *  ②在实例化集合类时，可以指明具体的泛型类型
 *  ③指明完以后，在集合类或接口中凡是定义类或接口时，内部结构（比如：方法、构造器、属性等）使用到类的泛型的位置，都指定为实例化的泛型类型。
 *    比如：add(E e)  --->实例化以后：add(Integer e)
 *  ④注意点：泛型的类型必须是类，不能是基本数据类型。需要用到基本数据类型的位置，拿包装类替换
 *  ⑤如果实例化时，没有指明泛型的类型。默认类型为java.lang.Object类型。
 *
 * 3.如何自定义泛型结构：泛型类、泛型接口；泛型方法。见 GenericTest1.java
 *
 */
public class GenericTest {

    //在集合中使用泛型的情况：以HashMap为例
    @Test
    public void test3(){
//        Map<String,Integer> map = new HashMap<String,Integer>();
        //jdk7新特性：类型推断
        Map<String,Integer> map = new HashMap<>();

        map.put("Tom",87);
        map.put("Tone",81);
        map.put("Jack",64);

//        map.put(123,"ABC");

        //泛型的嵌套
        Set<Map.Entry<String,Integer>> entry = map.entrySet();
        Iterator<Map.Entry<String, Integer>> iterator = entry.iterator();

        while(iterator.hasNext()){
            Map.Entry<String, Integer> e = iterator.next();
            String key = e.getKey();
            Integer value = e.getValue();
            System.out.println(key + "----" + value);
        }
    }

    //在集合中使用泛型的情况：以ArrayList为例
    @Test
    public void test2(){
        ArrayList<Integer> list = new ArrayList<Integer>();

        list.add(78);
        list.add(49);
        list.add(72);
        list.add(81);
        list.add(89);
        //编译时，就会进行类型检查，保证数据的安全
//        list.add("Tom");

        //方式一：
//        for(Integer score :list){
//            //避免了强转的操作
//            int stuScore = score;
//
//            System.out.println(stuScore);
//        }

        //方式二：
        Iterator<Integer> iterator = list.iterator();
        while(iterator.hasNext()){
            int stuScore = iterator.next();
            System.out.println(stuScore);
        }
    }
}
```

#### 2-2、练习

练习1

![img](https://img-blog.csdnimg.cn/img_convert/9b9fe485bf5138c0e1d75ba0023796b7.png)

1、MyDate类

```java
/**
 * MyDate类包含:
 * private成员变量year,month,day；并为每一个属性定义getter,  setter 方法；
 *
 */
public class MyDate implements Comparable<MyDate>{
    private int year;
    private int month;
    private int day;

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        this.year = year;
    }

    public int getMonth() {
        return month;
    }

    public void setMonth(int month) {
        this.month = month;
    }

    public int getDay() {
        return day;
    }

    public void setDay(int day) {
        this.day = day;
    }

    public MyDate() {
    }

    public MyDate(int year, int month, int day) {
        this.year = year;
        this.month = month;
        this.day = day;
    }

    @Override
    public String toString() {
        return "MyDate{" +
                "year=" + year +
                ", month=" + month +
                ", day=" + day +
                '}';
    }

//    @Override
//    public int compareTo(Object o) {
//        if(o instanceof MyDate){
//            MyDate m = (MyDate)o;
//
//            //比较年
//            int minusYear = this.getYear() - m.getYear();
//            if(minusYear != 0){
//                return minusYear;
//            }
//            //比较月
//            int minusMonth = this.getMonth() - m.getMonth();
//            if(minusMonth != 0){
//                return minusMonth;
//            }
//            //比较日
//            return this.getDay() - m.getDay();
//        }
//
//        throw new RuntimeException("传入的数据类型不一致！");
//
//    }

    @Override
    public int compareTo(MyDate m) {
        //比较年
        int minusYear = this.getYear() - m.getYear();
        if(minusYear != 0){
            return minusYear;
        }
        //比较月
        int minusMonth = this.getMonth() - m.getMonth();
        if(minusMonth != 0){
            return minusMonth;
        }
        //比较日
        return this.getDay() - m.getDay();
    }
}
```

2、Employee类

```java
/**
 * 定义一个Employee类。
 * 该类包含：private成员变量name,age,birthday，
 * 其中birthday 为MyDate 类的对象；
 * 并为每一个属性定义getter, setter 方法；
 * 并重写toString 方法输出name, age, birthday
 *
 */
public class Employee implements Comparable<Employee>{
    private String name;
    private int age;
    private MyDate birthday;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public MyDate getBirthday() {
        return birthday;
    }

    public void setBirthday(MyDate birthday) {
        this.birthday = birthday;
    }

    public Employee() {
    }

    public Employee(String name, int age, MyDate birthday) {
        this.name = name;
        this.age = age;
        this.birthday = birthday;
    }

    @Override
    public String toString() {
        return "Employee{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", birthday=" + birthday +
                '}';
    }

    //没有指明泛型时的写法
    //按name排序
//    @Override
//    public int compareTo(Object o){
//        if(o instanceof Employee){
//            Employee e = (Employee)o;
//            return this.name.compareTo(e.name);
//        }
        return 0;
//        throw new RuntimeException("传入的数据类型不一致");
//    }

    //指明泛型时的写法
    @Override
    public int compareTo(Employee o) {
        return this.name.compareTo(o.name);
    }
}
```

3、测试类

```java
import org.junit.Test;

import java.util.Comparator;
import java.util.Iterator;
import java.util.TreeSet;

/**
 * 创建该类的5 个对象，并把这些对象放入TreeSet 集合中
 * （下一章：TreeSet 需使用泛型来定义）分别按以下两种方式
 * 对集合中的元素进行排序，并遍历输出：
 *
 * 1). 使Employee 实现Comparable 接口，并按name 排序
 * 2). 创建TreeSet 时传入Comparator对象，按生日日期的先后排序。
 */
public class EmployeeTest {

    //问题二：按生日日期的先后排序
    @Test
    public void test2(){
        TreeSet<Employee> set = new TreeSet<>(new Comparator<Employee>() {
            //使用泛型以后的写法
            @Override
            public int compare(Employee o1, Employee o2) {
                MyDate b1 = o1.getBirthday();
                MyDate b2 = o2.getBirthday();

                return b1.compareTo(b2);
            }
            //使用泛型之前的写法
            //@Override
//            public int compare(Object o1, Object o2) {
//                if(o1 instanceof Employee && o2 instanceof Employee){
//                    Employee e1 = (Employee)o1;
//                    Employee e2 = (Employee)o2;
//
//                    MyDate b1 = e1.getBirthday();
//                    MyDate b2 = e2.getBirthday();
//                    //方式一：
                    //比较年
                    int minusYear = b1.getYear() - b2.getYear();
                    if(minusYear != 0){
                        return minusYear;
                    }
                    //比较月
                    int minusMonth = b1.getMonth() - b2.getMonth();
                    if(minusMonth != 0){
                        return minusMonth;
                    }
                    //比较日
                    return b1.getDay() - b2.getDay();
//
//                    //方式二：
//                    return b1.compareTo(b2);
//
//                }
                return 0;
//                throw new RuntimeException("传入的数据类型不一致！");
//            }
        });

        Employee e1 = new Employee("liudehua",55,new MyDate(1965,5,4));
        Employee e2 = new Employee("zhangxueyou",43,new MyDate(1987,5,4));
        Employee e3 = new Employee("guofucheng",44,new MyDate(1987,5,9));
        Employee e4 = new Employee("liming",51,new MyDate(1954,8,12));
        Employee e5 = new Employee("liangzhaowei",21,new MyDate(1978,12,4));

        set.add(e1);
        set.add(e2);
        set.add(e3);
        set.add(e4);
        set.add(e5);

        Iterator<Employee> iterator = set.iterator();
        while (iterator.hasNext()){
            System.out.println(iterator.next());
        }
    }

    //问题一：使用自然排序
    @Test
    public void test(){
        TreeSet<Employee> set = new TreeSet<Employee>();

        Employee e1 = new Employee("wangxianzhi",41,new MyDate(334,5,4));
        Employee e2 = new Employee("simaqian",43,new MyDate(-145,7,12));
        Employee e3 = new Employee("yanzhenqin",44,new MyDate(709,5,9));
        Employee e4 = new Employee("zhangqian",51,new MyDate(-179,8,12));
        Employee e5 = new Employee("quyuan",21,new MyDate(-340,12,4));

        set.add(e1);
        set.add(e2);
        set.add(e3);
        set.add(e4);
        set.add(e5);

        Iterator<Employee> iterator = set.iterator();
        while (iterator.hasNext()){
            Employee next = iterator.next();
            System.out.println(next);
        }
    }
}
```

### 3、自定义泛型结构

#### 3-1、自定义泛型类举例

1、OrderTest类

```java
/**
 * 自定义泛型类
 *
 */
public class OrderTest<T> {

    String orderName;
    int orderId;

    //类的内部结构就可以使用类的泛型
    T orderT;

    public OrderTest(){

    };

    public OrderTest(String orderName,int orderId,T orderT){
        this.orderName = orderName;
        this.orderId = orderId;
        this.orderT = orderT;
    }

    //如下的三个方法都不是泛型方法
    public T getOrderT(){
        return orderT;
    }

    public void setOrderT(T orderT){
        this.orderT = orderT;
    }

    @Override
    public String toString() {
        return "Order{" +
                "orderName='" + orderName + '\'' +
                ", orderId=" + orderId +
                ", orderT=" + orderT +
                '}';
    }
    
    //泛型方法：在方法中出现了泛型的结构，泛型参数与类的泛型参数没有任何关系。
    //换句话说，泛型方法所属的类是不是泛型类都没有关系。
    //泛型方法，可以声明为静态的。原因：泛型参数是在调用方法时确定的。并非在实例化类时确定。
    public static <E>  List<E> copyFromArrayToList(E[] arr){

        ArrayList<E> list = new ArrayList<>();

        for(E e : arr){
            list.add(e);
        }
        return list;

    }
}
```

2、SubOrder类

```java
public class SubOrder extends OrderTest<Integer>{   //SubOrder:不是泛型类
}
```

3、SubOrder1类

```java
public class SubOrder1<T> extends OrderTest<T> {//SubOrder1<T>:仍然是泛型类
}
```

4、GenericTest1类

```java
import org.junit.Test;

/**
 * 如何自定义泛型结构：泛型类、泛型接口；泛型方法。
 *
 * 1.关于自定义泛型类、泛型接口：
 */
public class GenericTest1 {

    @Test
    public void test(){
        /**
         * 如果定义了泛型类，实例化没有指明类的泛型，则认为此泛型类型为Object类型
         * 要求：如果大家定义了类是带泛型的，建议在实例化时要指明类的泛型。
         */
        OrderTest order = new OrderTest();
        order.setOrderT(123);
        order.setOrderT("ABC");

        //建议：实例化时指明类的泛型
        OrderTest<String> order1 = new OrderTest<String>("orderAA",1001,"order:AA");

        order1.setOrderT("AA:hello");
    }

    @Test
    public void test2(){
        SubOrder sub1 = new SubOrder();
        //由于子类在继承带泛型的父类时，指明了泛型类型。则实例化子类对象时，不再需要指明泛型。
        sub1.setOrderT(1122);

        SubOrder1<String> sub2 = new SubOrder1<>();
        sub2.setOrderT("order2...");
    }
}
```

#### 3-2、自定义泛型类泛型接口的注意点

注意点：

泛型类可能有多个参数，此时应将多个参数一起放在尖括号内。比如：<E1,E2,E3>

泛型类的构造器如下：public GenericClass(){}。而下面是错误的：public GenericClass(){}

实例化后，操作原来泛型位置的结构必须与指定的泛型类型一致。

泛型不同的引用不能相互赋值。尽管在编译时ArrayList和ArrayList是两种类型，但是，在运行时只有一个ArrayList被加载到JVM中。

泛型如果不指定，将被擦除，泛型对应的类型均按照Object处理，但不等价于Object。
经验：泛型要使用一路都用。要不用，一路都不要用。

如果泛型结构是一个接口或抽象类，则不可创建泛型类的对象。

jdk1.7，泛型的简化操作：ArrayList flist = new ArrayList<>();

泛型的指定中不能使用基本数据类型，可以使用包装类替换。

在类/接口上声明的泛型，在本类或本接口中即代表某种类型，可以作为非静态属性的类型、非静态方法的参数类型、非静态方法的返回值类型。但在静态方法中不能使用类的泛型。

异常类不能是泛型的：
//异常类不能声明为泛型类
//public class MyException<T> extends Exception{
//}

**代码演示：**

不能使用`new E[]`。但是可以：`E[] elements = (E[])new Object[capacity]`;参考：ArrayList源码中声明：Object[] elementData，而非泛型参数类型数组。

> 1、Person类

```java
public class Person {
}
```

> 2、OrderTest类

```
/**
 * 自定义泛型类
 */
public class OrderTest<T> {

    String orderName;
    int orderId;

    //类的内部结构就可以使用类的泛型
    T orderT;

    public OrderTest(){
        //编译不通过
//        T[] arr = new T[10];
        //编译通过
        T[] arr = (T[]) new Object[10];
    };

    public OrderTest(String orderName,int orderId,T orderT){
        this.orderName = orderName;
        this.orderId = orderId;
        this.orderT = orderT;
    }

    public T getOrderT(){
        return orderT;
    }

    public void setOrderT(T orderT){
        this.orderT = orderT;
    }

    @Override
    public String toString() {
        return "Order{" +
                "orderName='" + orderName + '\'' +
                ", orderId=" + orderId +
                ", orderT=" + orderT +
                '}';
    }

    //静态方法中不能使用类的泛型。
//    public static void show(T orderT){
//        System.out.println(orderT);
//    }

    public void show(){
        //编译不通过
//        try{
//
//
//        }catch(T t){
//
//        }
    }
}
```

3、GenericTest1类

```java
import org.junit.Test;

import java.util.ArrayList;

/**
 * 如何自定义泛型结构：泛型类、泛型接口；泛型方法。
 *
 * 1.关于自定义泛型类、泛型接口：
 *
 */
public class GenericTest1 {

    @Test
    public void test3(){
        ArrayList<String> list1 = null;
        ArrayList<Integer> list2 = new ArrayList<Integer>();
        //泛型不同的引用不能相互赋值。
        //list1 = list2;

        Person p1 = null;
        Person p2 = null;
        p1 = p2;
    }
}
```

> 4、在继承中使用泛型

1. 父类有泛型，子类可以选择保留泛型也可以选择指定泛型类型：
   - 子类不保留父类的泛型：按需实现
     - 没有类型擦除
     - 具体类型
   - 子类保留父类的泛型：泛型子类
     - 全部保留
     - 部分保留

```java
class Father<T1, T2> {}
// 子类不保留父类的泛型
// 1)没有类型擦除
class Son1 extends Father {// 等价于class Son extends Father<Object,Object>{}
}
// 2)具体类型
class Son2 extends Father<Integer, String> {}
// 子类保留父类的泛型
// 1)全部保留
class Son3<T1, T2> extends Father<T1, T2> {}
// 2)部分保留
class Son4<T2> extends Father<Integer, T2> {}
```

**结论：子类必须是“富二代”，子类除了指定或保留父类的泛型，还可以增加自己的泛型。**

#### 3-3、自定义泛型方法举例

说明：

方法，也可以被泛型化，不管此时定义在其中的类是不是泛型类。在泛型方法中可以定义泛型参数，此时，参数的类型就是传入数据的类型。

泛型方法的格式：

[访问权限] <泛型> 返回类型  方法名([泛型标识参数名称]) 抛出的异常
如：public static <E>  List<E> copyFromArrayToList(E[] arr)　throws  Exception{  }
1
2
代码演示：

1、OrderTest类

```java
import java.util.ArrayList;
import java.util.List;

/**
 * 自定义泛型类
 */
public class OrderTest<T> {

    /**
     * 泛型方法：在方法中出现了泛型的结构，泛型参数与类的泛型参数没有任何关系。
     * 换句话说，泛型方法所属的类是不是泛型类都没有关系。
     * 泛型方法，可以声明为静态的。原因：泛型参数是在调用方法时确定的。并非在实例化类时确定。
     */
    public static <E> List<E> copyFromArrayToList(E[] arr){

        ArrayList<E> list = new ArrayList<>();

        for(E e : arr){
            list.add(e);
        }
        return list;

    }
}
```

2、测试类

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.List;

/**
 * 如何自定义泛型结构：泛型类、泛型接口；泛型方法。
 *
 * 1.关于自定义泛型类、泛型接口：
 *
 */
public class GenericTest1 {

    //测试泛型方法
    @Test
    public void test4(){
        OrderTest<String> order = new OrderTest<>();
        Integer[] arr = new Integer[]{1,2,3,4};
        //泛型方法在调用时，指明泛型参数的类型。
        List<Integer> list = order.copyFromArrayToList(arr);

        System.out.println(list);
    }
}
```

3、SubOrder类

```java
import java.util.ArrayList;
import java.util.List;

public class SubOrder extends OrderTest<Integer>{   //SubOrder:不是泛型类
    
    public static <E> List<E> copyFromArrayToList(E[] arr){//静态的泛型方法

        ArrayList<E> list = new ArrayList<>();

        for(E e : arr){
            list.add(e);
        }
        return list;

    }
}
```

#### 3-4、举例泛型类和泛型方法的使用情境

1、DAO类

```java
import java.util.List;

public class DAO<T> { //表的共性操作的DAO

    //添加一条记录
    public void add(T t){

    }

    //删除一条记录
    public boolean remove(int index){

        return false;
    }

    //修改一条记录
    public void update(int index,T t){

    }

    //查询一条记录
    public T getIndex(int index){

        return null;
    }

    //查询多条记录
    public List<T> getForList(int index){

        return null;
    }

    //泛型方法
    //举例：获取表中一共有多少条记录？获取最大的员工入职时间？
    public <E> E getValue(){

        return null;
    }

}
```

2、Customer类

```java
public class Customer { //此类对应数据库中的customers表
}
```

3、CustomerDAO类

```java
public class CustomerDAO extends DAO<Customer>{//只能操作某一个表的DAO
}
```

4、Student类

```java
public class Student {
}

```

5、StudentDAO类

```java
public class StudentDAO extends DAO<Student> {//只能操作某一个表的DAO
}

```

6、DAOTest类

```java
import org.junit.Test;

import java.util.List;

public class DAOTest {

    @Test
    public void test(){
        CustomerDAO dao1 = new CustomerDAO();

        dao1.add(new Customer());
        List<Customer> list = dao1.getForList(10);


        StudentDAO dao2 = new StudentDAO();
        Student student = dao2.getIndex(1);
    }

}

```

### 4、泛型在继承上的体现【通配符】

```java
import org.junit.Test;

import java.util.AbstractList;
import java.util.ArrayList;
import java.util.List;

/**
 * 1.泛型在继承方面的体现
 *
 * 2.通配符的使用
 *
 */
public class GenericTest {

    /**
     * 1.泛型在继承方面的体现
     * 虽然类A是类B的父类，但是G<A> 和G<B>二者不具备子父类关系，二者是并列关系。
     * 补充：类A是类B的父类，A<G> 是 B<G> 的父类
     */
    @Test
    public void test(){

        Object obj = null;
        String str = null;
        obj = str;

        Object[] arr1 = null;
        String[] arr2 = null;
        arr1 = arr2;
        //编译不通过
//        Date date = new Date();
//        str = date;
        List<Object> list1 = null;
        List<String> list2 = new ArrayList<String>();
        //此时的list1和list2的类型不具有子父类关系
        //编译不通过
//        list1 = list2;
        /**
         * 反证法：
         *   假设list1 = list2;
         *      list1.add(123);导致混入非String的数据。出错。
         */
        show(list1);
        show2(list2);
    }

    public void show2(List<String> list){

    }

    public void show(List<Object> list){

    }

    @Test
    public void test2(){
        AbstractList<String> list1 = null;
        List<String> list2 = null;
        ArrayList<String> list3 = null;

        list1 = list3;
        list2 = list3;

        List<String> list4 = new ArrayList<>();
    }

}

```

### 5、通配符的使用

说明：

使用类型

通配符：？

比如：List<?> ，Map<?,?>
List<?>是List、List等各种泛型List的父类。
读取List<?>的对象list中的元素时，永远是安全的，因为不管list的真实类型是什么，它包含的都是Object。

写入list中的元素时，不行。因为我们不知道c的元素类型，我们不能向其中添加对象。

唯一的例外是null，它是所有类型的成员。

将任意元素加入到其中不是类型安全的：

- Collection<?> c = new ArrayList();
- c.add(new Object()); // 编译时错误因为我们不知道c的元素类型，我们不能向其中添加对象。add方法有类型参数E作为集合的元素类型。我们传给add的任何参数都必须是一个未知类型的子类。因为我们不知道那是什么类型，所以我们无法传任何东西进去。

1. **另一方面，我们可以调用get()方法并使用其返回值。返回值是一个未知的类型，但是我们知道，它总是一个Object**。

**代码演示：**

```java
import org.junit.Test;

import java.util.AbstractList;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

/**
 * 1.泛型在继承方面的体现
 * 2.通配符的使用
 */
public class GenericTest {

    /**
     * 2.通配符的使用
     * 通配符：？
     *
     * 类A是类B的父类，G<A>和G<B>是没有关系的，二者共同的父类是：G<?>
     */
    @Test
    public void test3(){
        List<Object> list1 = null;
        List<String> list2 = null;

        List<?> list = null;

        list = list1;
        list = list2;

        //编译通过
        print(list1);
        print(list2);
    }

    public void print(List<?> list){
        Iterator<?> iterator = list.iterator();
        while(iterator.hasNext()){
            Object obj = iterator.next();
            System.out.println(obj);
        }
    }
}
```

#### 5-1、使用通配符后数据的读取和写入要求

![img](https://img-blog.csdnimg.cn/img_convert/2fd8ff17cc7537df3bbbdc4709a78770.png)

```java
import org.junit.Test;

import java.util.AbstractList;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

/**
 * 1.泛型在继承方面的体现
 *
 * 2.通配符的使用
 */
public class GenericTest {

    /**
     * 2.通配符的使用
     * 通配符：？
     *
     * 类A是类B的父类，G<A>和G<B>是没有关系的，二者共同的父类是：G<?>
     */
    @Test
    public void test3(){
        List<Object> list1 = null;
        List<String> list2 = null;

        List<?> list = null;

        list = list1;
        list = list2;

        //编译通过
//        print(list1);
//        print(list2);

        List<String> list3 = new ArrayList<>();
        list3.add("AA");
        list3.add("BB");
        list3.add("CC");
        list = list3;
        //添加(写入)：对于List<?>就不能向其内部添加数据。
        //除了添加null之外。
//        list.add("DD");
//        list.add('?');

        list.add(null);

        //获取(读取)：允许读取数据，读取的数据类型为Object。
        Object o = list.get(0);
        System.out.println(o);
    }
}
```

#### 5-2、有限制条件的通配符的使用

说明：

<?>
允许所有泛型的引用调用

通配符指定上限上限

extends：使用时指定的类型必须是继承某个类，或者实现某个接口，即<=

通配符指定下限

下限super：使用时指定的类型不能小于操作的类，即>=

举例：

<?extends Number> (无穷小, Number]
只允许泛型为Number及Number子类的引用调用

<? super Number> [Number , 无穷大)
只允许泛型为Number及Number父类的引用调用

<? extends Comparable>
只允许泛型为实现Comparable接口的实现类的引用调用

代码演示：

1、Person类

```java
public class Person {
}
```

2、Student类

```java
public class Student extends Person{
}
```

3、测试类

```java
import org.junit.Test;

import java.util.AbstractList;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

/**
 * 1.泛型在继承方面的体现
 *
 * 2.通配符的使用
 */
public class GenericTest {

    /**
     * 3.有限制条件的通配符的使用。
     *
     * ? extends A:
     *      G<? extends A> 可以作为G<A>和G<B>的父类，其中B是A的子类
     *
     * ? super A:
     *      G<? super A> 可以作为G<A>和G<B>的父类，其中B是A的父类
     */
    @Test
    public void test4(){
        List<? extends Person> list1 = null;
        List<? super Person> list2 = null;

//        List<Student> list3 = null;
//        List<Student> list4 = null;
//        List<Student> list5 = null;

        List<Student> list3 = new ArrayList<Student>();
        List<Person> list4 = new ArrayList<Person>();
        List<Object> list5 = new ArrayList<Object>();

        list1 = list3;
        list1 = list4;
//        list1 = list5;

//        list2 = list3;
        list2 = list4;
        list2 = list5;

        //读取数据：
        list1 = list3;
        Person p = list1.get(0);
        //编译不通过
        //Student s = list1.get(0);

        list2 = list4;
        Object obj = list2.get(0);
        编译不通过
//        Person obj = list2.get(0);

        //写入数据：
        //编译不通过
//        list1.add(new Student());

        //编译通过
        list2.add(new Person());
        list2.add(new Student());
    }

}
```

### 6、泛型应用举例

#### 6-1、泛型嵌套

```java
public static void main(String[] args) {
        HashMap<String, ArrayList<Citizen>> map= new HashMap<String, ArrayList<Citizen>>();
        ArrayList<Citizen> list= new ArrayList<Citizen>();
        list.add(new Citizen("刘恺威"));
        list.add(new Citizen("杨幂"));
        list.add(new Citizen("小糯米"));
        map.put("刘恺威", list);
        Set<Entry<String, ArrayList<Citizen>>> entrySet= map.entrySet();
        Iterator<Entry<String, ArrayList<Citizen>>> iterator= entrySet.iterator();
        while(iterator.hasNext()) {
            Entry<String, ArrayList<Citizen>> entry= iterator.next();
            String key= entry.getKey();
            ArrayList<Citizen> value= entry.getValue();
            System.out.println("户主："+ key);
            System.out.println("家庭成员："+ value);
        }
    }
```

#### 6-2、实际案例

![img](https://img-blog.csdnimg.cn/img_convert/c7f67e4a87cd1527d1ea0d4389551d23.png)

```java
interface Info{		// 只有此接口的子类才是表示人的信息
}
class Contact implements Info{	// 表示联系方式
	private String address ;	// 联系地址
	private String telephone ;	// 联系方式
	private String zipcode ;	// 邮政编码
	public Contact(String address,String telephone,String zipcode){
		this.address = address;
		this.telephone = telephone;
		this.zipcode = zipcode;
	}
	public void setAddress(String address){
		this.address = address ;
	}
	public void setTelephone(String telephone){
		this.telephone = telephone ;
	}
	public void setZipcode(String zipcode){
		this.zipcode = zipcode;
	}
	public String getAddress(){
		return this.address ;
	}
	public String getTelephone(){
		return this.telephone ;
	}
	public String getZipcode(){
		return this.zipcode;
	}
	@Override
	public String toString() {
		return "Contact [address=" + address + ", telephone=" + telephone
				+ ", zipcode=" + zipcode + "]";
	}
}
class Introduction implements Info{
	private String name ;		// 姓名
	private String sex ;		// 性别
	private int age ;			// 年龄
	public Introduction(String name,String sex,int age){
		this.name = name;
		this.sex = sex;
		this.age = age;
	}
	public void setName(String name){
		this.name = name ;
	}
	public void setSex(String sex){
		this.sex = sex ;
	}
	public void setAge(int age){
		this.age = age ;
	}
	public String getName(){
		return this.name ;
	}
	public String getSex(){
		return this.sex ;
	}
	public int getAge(){
		return this.age ;
	}
	@Override
	public String toString() {
		return "Introduction [name=" + name + ", sex=" + sex + ", age=" + age
				+ "]";
	}
}
class Person<T extends Info>{
	private T info ;
	public Person(T info){		// 通过构造器设置信息属性内容
		this.info = info;
	}
	public void setInfo(T info){
		this.info = info ;
	}
	public T getInfo(){
		return info ;
	}
	@Override
	public String toString() {
		return "Person [info=" + info + "]";
	}
	
}
public class GenericPerson{
	public static void main(String args[]){
		Person<Contact> per = null ;		// 声明Person对象
		per = new Person<Contact>(new Contact("北京市","01088888888","102206")) ;
		System.out.println(per);
		
		Person<Introduction> per2 = null ;		// 声明Person对象
		per2 = new Person<Introduction>(new Introduction("李雷","男",24));
		System.out.println(per2) ;
	}
}
```

### 7、自定义泛型类练习

![img](https://img-blog.csdnimg.cn/img_convert/985fe52e0a8c525605fa4d8e3a2d32e4.png)

1、泛型类DAO

```java
import java.util.*;

/**
 * 定义个泛型类 DAO<T>，在其中定义一个Map 成员变量，Map 的键为 String 类型，值为 T 类型。
 *
 * 分别创建以下方法：
 * public void save(String id,T entity)： 保存 T 类型的对象到 Map 成员变量中
 * public T get(String id)：从 map 中获取 id 对应的对象
 * public void update(String id,T entity)：替换 map 中key为id的内容,改为 entity 对象
 * public List<T> list()：返回 map 中存放的所有 T 对象
 * public void delete(String id)：删除指定 id 对象
 */
public class DAO<T> {
    private Map<String,T> map = new HashMap<String,T>();
    //保存 T 类型的对象到 Map 成员变量中
    public void save(String id,T entity){
        map.put(id,entity);
    }
    //从 map 中获取 id 对应的对象
    public T get(String id){
        return map.get(id);
    }
    //替换 map 中key为id的内容,改为 entity 对象
    public void update(String id,T entity){
        if(map.containsKey(id)){
            map.put(id,entity);
        }
    }
    //返回 map 中存放的所有 T 对象
    public List<T> list(){
        //错误的：
//        Collection<T> values = map.values();
//        return (List<T>) values;
        //正确的：
        ArrayList<T> list = new ArrayList<>();
        Collection<T> values = map.values();
        for(T t : values){
            list.add(t);
        }
        return list;

    }
    //删除指定 id 对象
    public void delete(String id){
        map.remove(id);
    }
}
```

2、User类

```java
/**
 * 定义一个 User 类：
 * 该类包含：private成员变量（int类型） id，age；（String 类型）name。
 */
public class User {
    private int id;
    private int age;
    private String name;

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public User(int id, int age, String name) {

        this.id = id;
        this.age = age;
        this.name = name;
    }

    public User() {

    }

    @Override
    public String toString() {
        return "User{" +
                "id=" + id +
                ", age=" + age +
                ", name='" + name + '\'' +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        User user = (User) o;

        if (id != user.id) return false;
        if (age != user.age) return false;
        return name != null ? name.equals(user.name) : user.name == null;
    }

    @Override
    public int hashCode() {
        int result = id;
        result = 31 * result + age;
        result = 31 * result + (name != null ? name.hashCode() : 0);
        return result;
    }
}
```

3、测试类

```java
import java.util.List;

/**
 * 创建 DAO 类的对象， 分别调用其 save、get、update、list、delete
 * 方法来操作 User 对象，使用 Junit 单元测试类进行测试。
 */
public class DAOTest {
    public static void main(String[] args) {
        DAO<User> dao = new DAO<User>();

        dao.save("1001",new User(1001,34,"周杰伦"));
        dao.save("1002",new User(1002,20,"昆凌"));
        dao.save("1003",new User(1003,25,"蔡依林"));

        dao.update("1003",new User(1003,30,"方文山"));

        dao.delete("1002");

        List<User> list = dao.list();
//        System.out.println(list);
        list.forEach(System.out::println);
    }
}
```

## 16、IO流

### 1、File类的使用

#### 1-1、File类的实例化

java.io.File类：文件和文件目录路径的抽象表示形式，与平台无关
File 能新建、删除、重命名文件和目录，但File 不能访问文件内容本身。如果需要访问文件内容本身，则需要使用输入/输出流。
想要在Java程序中表示一个真实存在的文件或目录，那么必须有一个File对象，但是Java程序中的一个File对象，可能没有一个真实存在的文件或目录。
File对象可以作为参数传递给流的构造器

```java
import org.junit.Test;
import java.io.File;

/**
 * File类的使用
 *
 * 1. File类的一个对象，代表一个文件或一个文件目录(俗称：文件夹)
 * 2. File类声明在java.io包下
 *
 */
public class FileTest {
    /**
     * 1.如何创建file类的实例
     *      File(String filePath):以filePath为路径创建File对象，可以是绝对路径或者相对路径
     *      File(String parentPath,String childPath):以parentPath为父路径，childPath为子路径创建File对象。
     *      File(File parentFile,String childPath):根据一个父File对象和子文件路径创建File对象
     * 2.
     *   相对路径：相较于某个路径下，指明的路径。
     *   绝对路径：包含盘符在内的文件或文件目录的路径
     *
     * 3.路径分隔符
     *      windows:\\
     *      unix:/
     * 4.Java程序支持跨平台运行，因此路径分隔符要慎用。
     *
     * 5.为了解决这个隐患，File类提供了一个常量：
     *   public  static final String separator。
     *   根据操作系统，动态的提供分隔符。
     *
     * File file1= new File("d:\\Work\\info.txt");
     * File file2= new File("d:"+ File.separator+ "Work"+ File.separator+ "info.txt");
     * File file3= new File("d:/Work");
     *
     */
    @Test
    public void test(){
        //构造器1：
        File file1 = new File("hello.txt");//相对于当前module
        File file2 = new File("F:\\java\\Work2\\JavaSenior\\day08\\num.txt");

        System.out.println(file1);
        System.out.println(file2);

        //构造器2：
        File file3 = new File("D:\\workspace_idea1","JavaSenior");
        System.out.println(file3);

        //构造器3：
        File file4 = new File(file3,"hi.txt");
        System.out.println(file4);
    }

}
```

#### 1-2、File类的常用方法1

```java
import org.junit.Test;

import java.io.File;
import java.util.Date;

/**
 * File类的使用
 *
 * 1. File类的一个对象，代表一个文件或一个文件目录(俗称：文件夹)
 * 2. File类声明在java.io包下
 */
public class FileTest {

    /**
     * public String getAbsolutePath()：获取绝对路径
     * public String getPath() ：获取路径
     * public String getName() ：获取名称
     * public String getParent()：获取上层文件目录路径。若无，返回null
     * public long length() ：获取文件长度（即：字节数）。不能获取目录的长度。
     * public long lastModified() ：获取最后一次的修改时间，毫秒值
     *
     * 如下的两个方法适用于文件目录：
     * public String[] list() ：获取指定目录下的所有文件或者文件目录的名称数组
     * public File[] listFiles() ：获取指定目录下的所有文件或者文件目录的File数组
     */
    @Test
    public void test2(){
        File file = new File("Hello.txt");
        File file2 = new File("F:\\java\\Work2\\JavaSenior\\day08\\num.txt");

        System.out.println(file.getAbsolutePath());
        System.out.println(file.getPath());
        System.out.println(file.getName());
        System.out.println(file.getParent());
        System.out.println(file.length());
        System.out.println(new Date(file.lastModified()));

        System.out.println();

        System.out.println(file2.getAbsolutePath());
        System.out.println(file2.getPath());
        System.out.println(file2.getName());
        System.out.println(file2.getParent());
        System.out.println(file2.length());
        System.out.println(file2.lastModified());
    }

    @Test
    public void test3(){
        //文件需存在！！！
        File file = new File("F:\\java\\Work2\\JavaSenior");

        String[] list = file.list();
        for(String s : list){
            System.out.println(s);
        }

        System.out.println();

        File[] files = file.listFiles();
        for(File f : files){
            System.out.println(f);
        }
    }

    /**
     * File类的重命名功能
     *
     *  public boolean renameTo(File dest):把文件重命名为指定的文件路径
     *    比如：file1.renameTo(file2)为例：
     *         要想保证返回true,需要file1在硬盘中是存在的，且file2不能在硬盘中存在。
     */
    @Test
    public void test4(){
        File file1 = new File("hello.txt");
        File file2 = new File("D:\\book\\num.txt");

        boolean renameTo = file2.renameTo(file1);
        System.out.println(renameTo);
    }
}
```

#### 1-3、File类的常用方法2

![img](https://img-blog.csdnimg.cn/img_convert/e1cfd3ce0032867ebcb16dbcb5c06743.png)

```java
import org.junit.Test;

import java.io.File;
import java.io.IOException;
import java.util.Date;

/**
 * File类的使用
 *
 * 1. File类的一个对象，代表一个文件或一个文件目录(俗称：文件夹)
 * 2. File类声明在java.io包下
 * 3. File类中涉及到关于文件或文件目录的创建、删除、重命名、修改时间、文件大小等方法，
 *    并未涉及到写入或读取文件内容的操作。如果需要读取或写入文件内容，必须使用IO流来完成。
 * 4. 后续File类的对象常会作为参数传递到流的构造器中，指明读取或写入的"终点".
 */
public class FileTest {

    /**
     * public boolean isDirectory()：判断是否是文件目录
     * public boolean isFile() ：判断是否是文件
     * public boolean exists() ：判断是否存在
     * public boolean canRead() ：判断是否可读
     * public boolean canWrite() ：判断是否可写
     * public boolean isHidden() ：判断是否隐藏
     */
    @Test
    public void test5(){
        File file1 = new File("hello.txt");
        file1 = new File("hello1.txt");

        System.out.println(file1.isDirectory());
        System.out.println(file1.isFile());
        System.out.println(file1.exists());
        System.out.println(file1.canRead());
        System.out.println(file1.canWrite());
        System.out.println(file1.isHidden());

        System.out.println();

        File file2 = new File("D:\\book");
        file2 = new File("D:\\book1");
        System.out.println(file2.isDirectory());
        System.out.println(file2.isFile());
        System.out.println(file2.exists());
        System.out.println(file2.canRead());
        System.out.println(file2.canWrite());
        System.out.println(file2.isHidden());
    }

    /**
     * 创建硬盘中对应的文件或文件目录
     * public boolean createNewFile() ：创建文件。若文件存在，则不创建，返回false
     * public boolean mkdir() ：创建文件目录。如果此文件目录存在，就不创建了。如果此文件目录的上层目录不存在，也不创建。
     * public boolean mkdirs() ：创建文件目录。如果此文件目录存在，就不创建了。如果上层文件目录不存在，一并创建
     *
     *     删除磁盘中的文件或文件目录
     * public boolean delete()：删除文件或者文件夹
     *     删除注意事项：Java中的删除不走回收站。
     */
    @Test
    public void test6() throws IOException {
        File file1 = new File("hi.txt");
        if(!file1.exists()){
            //文件的创建
            file1.createNewFile();
            System.out.println("创建成功");
        }else{//文件存在
            file1.delete();
            System.out.println("删除成功");
        }
    }

    @Test
    public void test7(){
        //文件目录的创建
        File file1 = new File("d:\\io\\io1\\io3");

        boolean mkdir = file1.mkdir();
        if(mkdir){
            System.out.println("创建成功1");
        }

        File file2 = new File("d:\\io\\io1\\io4");

        boolean mkdir1 = file2.mkdirs();
        if(mkdir1){
            System.out.println("创建成功2");
        }
        //要想删除成功，io4文件目录下不能有子目录或文件
        File file3 = new File("D:\\io\\io1\\io4");
        file3 = new File("D:\\io\\io1");
        System.out.println(file3.delete());
    }
}
```

#### 1-4、课后练习

![img](https://img-blog.csdnimg.cn/img_convert/2dea5f971514e90f57600a5898d5b62d.png)

1、FileTest类

```java
import org.junit.Test;

import java.io.File;
import java.io.IOException;

/**
 * 1. 利用File构造器，new一个文件目录file
 *    1)在其中创建多个文件和目录
 *    2)编写方法，实现删除file中指定文件的操作
 */
public class FileTest {
    @Test
    public void test() throws IOException {
        File file = new File("D:\\io\\io1\\hello.txt");
        //创建一个与file同目录下的另外一个文件，文件名为：haha.txt
        File destFile = new File(file.getParent(),"haha.txt");
        boolean newFile = destFile.createNewFile();
        if(newFile){
            System.out.println("创建成功！");
        }
    }
}
```

2、FindJPGFileTest类

```java
import org.junit.Test;

import java.io.File;
import java.io.FilenameFilter;

/**
 * 2.判断指定目录下是否有后缀名为.jpg的文件，如果有，就输出该文件名称
 */
public class FindJPGFileTest {
    @Test
    public void test(){
        File srcFile = new File("d:\\code");

        String[] fileNames = srcFile.list();
        for(String fileName : fileNames){
            if(fileName.endsWith(".jpg")){
                System.out.println(fileName);
            }
        }
    }

    @Test
    public void test2(){
        File srcFile = new File("d:\\code");

        File[] listFiles = srcFile.listFiles();
        for(File file : listFiles){
            if(file.getName().endsWith(".jpg")){
                System.out.println(file.getAbsolutePath());
            }
        }
    }

    /**
     * File类提供了两个文件过滤器方法
     * public String[] list(FilenameFilter filter)
     * public File[] listFiles(FileFilter filter)
     */
    @Test
    public void test3(){
        File srcFile = new File("d:\\code");

        File[] subFiles = srcFile.listFiles(new FilenameFilter() {

            @Override
            public boolean accept(File dir, String name) {
                return name.endsWith(".jpg");
            }
        });

        for(File file : subFiles){
            System.out.println(file.getAbsolutePath());
        }
    }
}
```

3、ListFilesTest类

```java
import java.io.File;

/**
 * 3. 遍历指定目录所有文件名称，包括子文件目录中的文件。
 *      拓展1：并计算指定目录占用空间的大小
 *      拓展2：删除指定文件目录及其下的所有文件
 */
public class ListFilesTest {
    public static void main(String[] args) {
        // 递归:文件目录
        /** 打印出指定目录所有文件名称，包括子文件目录中的文件 */

        // 1.创建目录对象
        File dir = new File("E:\\teach\\01_javaSE\\_尚硅谷Java编程语言\\3_软件");

        // 2.打印目录的子文件
        printSubFile(dir);
    }

    public static void printSubFile(File dir) {
        // 打印目录的子文件
        File[] subfiles = dir.listFiles();

        for (File f : subfiles) {
            if (f.isDirectory()) {// 文件目录
                printSubFile(f);
            } else {// 文件
                System.out.println(f.getAbsolutePath());
            }

        }
    }

    // 方式二：循环实现
    // 列出file目录的下级内容，仅列出一级的话
    // 使用File类的String[] list()比较简单
    public void listSubFiles(File file) {
        if (file.isDirectory()) {
            String[] all = file.list();
            for (String s : all) {
                System.out.println(s);
            }
        } else {
            System.out.println(file + "是文件！");
        }
    }

    // 列出file目录的下级，如果它的下级还是目录，接着列出下级的下级，依次类推
    // 建议使用File类的File[] listFiles()
    public void listAllSubFiles(File file) {
        if (file.isFile()) {
            System.out.println(file);
        } else {
            File[] all = file.listFiles();
            // 如果all[i]是文件，直接打印
            // 如果all[i]是目录，接着再获取它的下一级
            for (File f : all) {
                listAllSubFiles(f);// 递归调用：自己调用自己就叫递归
            }
        }
    }

    // 拓展1：求指定目录所在空间的大小
    // 求任意一个目录的总大小
    public long getDirectorySize(File file) {
        // file是文件，那么直接返回file.length()
        // file是目录，把它的下一级的所有大小加起来就是它的总大小
        long size = 0;
        if (file.isFile()) {
            size += file.length();
        } else {
            File[] all = file.listFiles();// 获取file的下一级
            // 累加all[i]的大小
            for (File f : all) {
                size += getDirectorySize(f);// f的大小;
            }
        }
        return size;
    }

    // 拓展2：删除指定的目录
    public void deleteDirectory(File file) {
        // 如果file是文件，直接delete
        // 如果file是目录，先把它的下一级干掉，然后删除自己
        if (file.isDirectory()) {
            File[] all = file.listFiles();
            // 循环删除的是file的下一级
            for (File f : all) {// f代表file的每一个下级
                deleteDirectory(f);
            }
        }
        // 删除自己
        file.delete();
    }
}
```

### 2、IO流原理及流的分类

#### 2-1、IO流原理

I/O是Input/Output的缩写，I/O技术是非常实用的技术，用于处理设备之间的数据传输。如读/写文件，网络通讯等。
Java程序中，对于数据的输入/输出操作以“流(stream)”的方式进行。
java.io包下提供了各种“流”类和接口，用以获取不同种类的数据，并通过标准的方法输入或输出数据。
输入input：读取外部数据（磁盘、光盘等存储设备的数据）到程序（内存）中。
输出output：将程序（内存）数据输出到磁盘、光盘等存储设备中。
![img](https://img-blog.csdnimg.cn/img_convert/74982d54ff7df37618ef186ec7dad049.png)

#### 2-2、流的分类

按操作数据单位不同分为：字节流(8 bit)，字符流(16 bit)
按数据流的流向不同分为：输入流，输出流
按流的角色的不同分为：节点流，处理流
抽象基类	字节流	字符流

输入流	InputStream	Reader
输出流	OutputStream	Writer

Java的IO流共涉及40多个类，实际上非常规则，都是从如下4个抽象基类派生的。
由这四个类派生出来的子类名称都是以其父类名作为子类名后缀。
![img](https://img-blog.csdnimg.cn/img_convert/23f558de081b9a9a2a5da93fdc1989df.png)

#### 2-3、IO流体系

![img](https://img-blog.csdnimg.cn/img_convert/2cece5577c55fc427b9942a42e577fe4.png)

### 3、节点流(或文件流)

#### 3-1、FileReader读入数据的基本操作

1、读取文件【四个步骤】

1、建立一个流对象，将已存在的一个文件加载进流。

```java
FileReaderfr= new FileReader(new File(“Test.txt”));
```

2、创建一个临时存放数据的数组。

```java
char[] ch= new char[1024];
```

3、调用流对象的读取方法将流中的数据读入到数组中。

```java
	fr.read(ch);
```

4、复制资源

```java
	fr.close();
```

```java
import org.junit.Test;

import java.io.File;
import java.io.FileReader;
import java.io.IOException;

/**
 * 一、流的分类：
 * 1.操作数据单位：字节流、字符流
 * 2.数据的流向：输入流、输出流
 * 3.流的角色：节点流、处理流
 *
 * 二、流的体系结构
 * 抽象基类         节点流（或文件流）                               缓冲流（处理流的一种）
 * InputStream     FileInputStream   (read(byte[] buffer))        BufferedInputStream (read(byte[] buffer))
 * OutputStream    FileOutputStream  (write(byte[] buffer,0,len)  BufferedOutputStream (write(byte[] buffer,0,len) / flush()
 * Reader          FileReader (read(char[] cbuf))                 BufferedReader (read(char[] cbuf) / readLine())
 * Writer          FileWriter (write(char[] cbuf,0,len)           BufferedWriter (write(char[] cbuf,0,len) / flush()
 */
public class FileReaderWriterTest {
    public static void main(String[] args) {
        File file = new File("hello.txt");//相较于当前工程
        System.out.println(file.getAbsolutePath());

        File file1 = new File("day09\\hello.txt");
        System.out.println(file1.getAbsolutePath());
    }

    /**
     * 将day09下的hello.txt文件内容读入程序中，并输出到控制台
     *
     * 说明点：
     *     1. read()的理解：返回读入的一个字符。如果达到文件末尾，返回-1
     *     2. 异常的处理：为了保证流资源一定可以执行关闭操作。需要使用try-catch-finally处理
     *     3. 读入的文件一定要存在，否则就会报FileNotFoundException。
     *
     */
    @Test
    public void test(){
        FileReader fr = null;
        try {
            //实例化File对象，指明要操作的文件
            File file = new File("hello.txt");//相较于当前的Module
            //2.提供具体的流
            fr = new FileReader(file);

            //3.数据的读入过程
            //read():返回读入的一个字符。如果达到文件末尾，返回-1.
            //方式一：
//        int data = fr.read();
//        while(data != -1){
//            System.out.print((char) data);
//            data = fr.read();
//        }

            //方式二：语法上针对于方式一的修改
            int data;
            while((data = fr.read()) != -1){
                System.out.print((char) data);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            //4.流的关闭操作
//            try {
//                if(fr != null)
//                    fr.close();
//            } catch (IOException e) {
//                e.printStackTrace();
//            }

            //或
            if(fr != null){
                try {
                    fr.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }

        }
    }
}
```

#### 3-2、FileReader中使用read(char[] cbuf)读入数据

```java
import org.junit.Test;
import java.io.File;
import java.io.FileReader;
import java.io.IOException;

public class FileReaderWriterTest {

    //对read()操作升级：使用read的重载方法
    @Test
    public void test2(){
        FileReader fr = null;
        try {
            //1.File类的实例化
            File file = new File("hello.txt");

            //2.FileReader流的实例化
            fr = new FileReader(file);

            //3.读入的操作
            //read(char[] cbuf):返回每次读入cbuf数组中的字符的个数。如果达到文件末尾，返回-1
            char[] cbuf = new char[5];
            int len;
            fr.read(cbuf);
            while((len = fr.read(cbuf)) != -1){
                //方式一：
                //错误的写法
//                for(int i = 0;i < cbuf.length;i++){
//                    System.out.print(cbuf[i]);
//                }
                //正确的写法
//                for(int i = 0;i < len;i++){
//                    System.out.print(cbuf[i]);
//                }

                //方式二：
                //错误的写法,对应着方式一的错误的写法
//                String str = new String(cbuf);
//                System.out.print(str);
                //正确的写法
                String str = new String(cbuf,0,len);
                System.out.print(str);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            if(fr != null){
                //4.资源的关闭
                try {
                    fr.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
        }

    }

}

```

#### 3-3、FileWriter写出数据的操作

> 1、写入文件

1、 创建流对象，建立数据存放文件

```java
    FileWriterfw= new FileWriter(new File(“Test.txt”));
```

2、调用流对象的写入方法，将数据写入流

```java
  fw.write(“atguigu-songhongkang”);
```

3、关闭流资源，并将流中的数据清空到文件中。

```java
    fw.close();
```

```java
import org.junit.Test;
import java.io.*;

public class FileReaderWriterTest {

    /**
     * 从内存中写出数据到硬盘的文件里。
     *
     * 说明：
     * 1.输出操作，对应的File可以不存在的。并不会报异常
     * 2.
     *   File对应的硬盘中的文件如果不存在，在输出的过程中，会自动创建此文件。
     *   File对应的硬盘中的文件如果存在：
     *       如果流使用的构造器是：FileWriter(file,false) / FileWriter(file):对原有文件的覆盖
     *       如果流使用的构造器是：FileWriter(file,true):不会对原有文件覆盖，而是在原有文件基础上追加内容
     */
    @Test
    public void test3(){        
        FileWriter fw = null;
        try {
            //1.提供File类的对象，指明写出到的文件
            File file = new File("hello1.txt");

            //2.提供FileWriter的对象，用于数据的写出
            fw = new FileWriter(file,false);

            //3.写出的操作
            fw.write("I have a dream!\n");
            fw.write("you need to have a dream!");
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //4.流资源的关闭
            if(fw != null){

                try {
                    fw.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```

#### 3-4、使用FileReader和FileWriter实现文本文件的复制

```java
import org.junit.Test;
import java.io.*;

public class FileReaderWriterTest {

    @Test
    public void test4() {
        FileReader fr = null;
        FileWriter fw = null;
        try {
            //1.创建File类的对象，指明读入和写出的文件
            File srcFile = new File("hello1.txt");
            File srcFile2 = new File("hello2..txt");

            //不能使用字符流来处理图片等字节数据
//            File srcFile = new File("爱情与友情.jpg");
//            File srcFile2 = new File("爱情与友情1.jpg");

            //2.创建输入流和输出流的对象
            fr = new FileReader(srcFile);
            fw = new FileWriter(srcFile2);

            //3.数据的读入和写出操作
            char[] cbuf = new char[5];
            int len;//记录每次读入到cbuf数组中的字符的个数
            while((len = fr.read(cbuf)) != -1){
                //每次写出len个字符
                fw.write(cbuf,0,len);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //4.关闭流资源
            //方式一：
//            try {
//                if(fw != null)
//                    fw.close();
//            } catch (IOException e) {
//                e.printStackTrace();
//            }finally{
//                try {
//                    if(fr != null)
//                        fr.close();
//                } catch (IOException e) {
//                    e.printStackTrace();
//                }
//            }
            //方式二：
            try {
                if(fw != null)
                    fw.close();
            } catch (IOException e) {
                e.printStackTrace();
            }

            try {
                if(fr != null)
                    fr.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

#### 3-5、使用FileInputStream不能读取文本文件的测试

```java
import org.junit.Test;

import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;

/**
 * 测试FileInputStream和FileOutputStream的使用
 *
 * 结论：
 *    1. 对于文本文件(.txt,.java,.c,.cpp)，使用字符流处理
 *    2. 对于非文本文件(.jpg,.mp3,.mp4,.avi,.doc,.ppt,...)，使用字节流处理
 */
public class FileIOPutTest {
    //使用字节流FileInputStream处理文本文件，可能出现乱码。
    @Test
    public void testFileInputStream(){
        FileInputStream fis = null;
        try {
            //1.造文件
            File file = new File("hello.txt");

            //2.造流
            fis = new FileInputStream(file);

            //3.读数据
            byte[] buffer = new byte[5];
            int len;//记录每次读取的字节的个数
            while((len = fis.read(buffer)) != -1){
                String str = new String(buffer,0,len);
                System.out.print(str);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            if(fis != null) {
                //4.关闭资源
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```

#### 3-6、使用FileInputStream和FileOutputStream读写非文本文件

```java
import org.junit.Test;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class FileIOPutTest {

    /**
     * 实现对图片的复制操作
     */
    @Test
    public void testFileInputOutputStream()  {
        FileInputStream fis = null;
        FileOutputStream fos = null;
        try {
            //1.造文件
            File srcFile = new File("爱情与友情.jpg");
            File destFile = new File("爱情与友情2.jpg");

            //2.造流
            fis = new FileInputStream(srcFile);
            fos = new FileOutputStream(destFile);

            //3.复制的过程
            byte[] buffer = new byte[5];
            int len;
            //4.读数据
            while((len = fis.read(buffer)) != -1){
                fos.write(buffer,0,len);
            }
            System.out.println("复制成功");
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if(fos != null){
                //5.关闭资源
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(fis != null){
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
        }

    }
}
```

#### 3-7、使用FileInputStream和FileOutputStream复制文件的方法测试

```java
import org.junit.Test;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class FileIOPutTest {

    //指定路径下文件的复制
    public void copyFile(String srcPath,String destPath){
        FileInputStream fis = null;
        FileOutputStream fos = null;
        try {
            //
            File srcFile = new File(srcPath);
            File destFile = new File(destPath);

            //
            fis = new FileInputStream(srcFile);
            fos = new FileOutputStream(destFile);

            //复制的过程
            byte[] buffer = new byte[1024];
            int len;
            while((len = fis.read(buffer)) != -1){
                fos.write(buffer,0,len);
            }

        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if(fos != null){
                //
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(fis != null){
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
        }
    }

    @Test
    public void testCopyFile(){

        long start = System.currentTimeMillis();

//        String srcPath = "C:\\Users\\29433\\Desktop\\164.jpg";
//        String destPath = "C:\\Users\\29433\\Desktop\\164.jpg";

        String srcPath = "hello.txt";
        String destPath = "hello3.txt";

        copyFile(srcPath,destPath);

        long end = System.currentTimeMillis();

        System.out.println("复制操作花费的时间为：" + (end - start));//1
    }
}
```

### 4、缓冲流

为了提高数据读写的速度，Java API提供了带缓冲功能的流类，在使用这些流类时，会创建一个内部缓冲区数组，缺省使用8192个字节(8Kb)的缓冲区。

![img](https://img-blog.csdnimg.cn/img_convert/b127ea9bd12c05a70b88033ee70bf2f3.png)

缓冲流要“套接”在相应的节点流之上，根据数据操作单位可以把缓冲流分为：

BufferedInputStream和BufferedOutputStream
BufferedReader和BufferedWriter
当读取数据时，数据按块读入缓冲区，其后的读操作则直接访问缓冲区

当使用BufferedInputStream读取字节文件时，BufferedInputStream会一次性从文件中读取8192个(8Kb)，存在缓冲区中，直到缓冲区装满了，才重新从文件中读取下一个8192个字节数组。

向流中写入字节时，不会直接写到文件，先写到缓冲区中直到缓冲区写满，BufferedOutputStream才会把缓冲区中的数据一次性写到文件里。使用方法flush()可以强制将缓冲区的内容全部写入输出流

关闭流的顺序和打开流的顺序相反。只要关闭最外层流即可，关闭最外层流也会相应关闭内层节点流

flush()方法的使用：手动将buffer中内容写入文件

如果是带缓冲区的流对象的close()方法，不但会关闭流，还会在关闭流之前刷新缓冲区，关闭后不能再写出。
![img](https://img-blog.csdnimg.cn/img_convert/7ce79819b9685ffc2bae685bec83b0f1.png)

#### 4-1、缓冲流(字节型)实现非文本文件的复制

```java
import org.junit.Test;

import java.io.*;

/**
 * 处理流之一：缓冲流的使用
 *
 *  1.缓冲流：
 *  BufferedInputStream
 *  BufferedOutputStream
 *  BufferedReader
 *  BufferedWriter
 */
public class BufferedTest {

    /**
     * 实现非文本文件的复制
     */
    @Test
    public void BufferedStreamTest(){
        BufferedInputStream bis = null;
        BufferedOutputStream bos = null;

        try {
            //1.造文件
            File srcFile = new File("爱情与友情.jpg");
            File destFile = new File("爱情与友情3.jpg");
            //2.造流
            //2.1 造节点流
            FileInputStream fis = new FileInputStream((srcFile));
            FileOutputStream fos = new FileOutputStream(destFile);
            //2.2 造缓冲流
            bis = new BufferedInputStream(fis);
            bos = new BufferedOutputStream(fos);

            //3.复制的细节：读取、写入
            byte[] buffer = new byte[10];
            int len;
            while((len = bis.read(buffer)) != -1){
                bos.write(buffer,0,len);
//                bos.flush();//刷新缓冲区
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //4.资源关闭
            //要求：先关闭外层的流，再关闭内层的流
            if(bos != null){
                try {
                    bos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
            if(bis != null){
                try {
                    bis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            //说明：关闭外层流的同时，内层流也会自动的进行关闭。关于内层流的关闭，我们可以省略.
//        fos.close();
//        fis.close();
        }
    }
}
```

#### 4-2、缓冲流与节点流读写速度对比

```java
import org.junit.Test;
import java.io.*;
/**
 * 处理流之一：缓冲流的使用
 *
 *  1.缓冲流：
 *  BufferedInputStream
 *  BufferedOutputStream
 *  BufferedReader
 *  BufferedWriter
 *
 *  2.作用：提供流的读取、写入的速度
 *    提高读写速度的原因：内部提供了一个缓冲区
 *
 *  3. 处理流，就是“套接”在已有的流的基础上。
 *
 */
public class BufferedTest {

    //实现文件复制的方法
    public void copyFileWithBuffered(String srcPath,String destPath){
        BufferedInputStream bis = null;
        BufferedOutputStream bos = null;

        try {
            //1.造文件
            File srcFile = new File(srcPath);
            File destFile = new File(destPath);
            //2.造流
            //2.1 造节点流
            FileInputStream fis = new FileInputStream((srcFile));
            FileOutputStream fos = new FileOutputStream(destFile);
            //2.2 造缓冲流
            bis = new BufferedInputStream(fis);
            bos = new BufferedOutputStream(fos);

            //3.复制的细节：读取、写入
            byte[] buffer = new byte[1024];
            int len;
            while((len = bis.read(buffer)) != -1){
                bos.write(buffer,0,len);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //4.资源关闭
            //要求：先关闭外层的流，再关闭内层的流
            if(bos != null){
                try {
                    bos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
            if(bis != null){
                try {
                    bis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
            //说明：关闭外层流的同时，内层流也会自动的进行关闭。关于内层流的关闭，我们可以省略.
//        fos.close();
//        fis.close();
        }
    }

    @Test
    public void testCopyFileWithBuffered(){
        long start = System.currentTimeMillis();

        String srcPath = "C:\\Users\\29433\\Desktop\\book.flv";
        String destPath = "C:\\Users\\29433\\Desktop\\book1.flv";


        copyFileWithBuffered(srcPath,destPath);


        long end = System.currentTimeMillis();

        System.out.println("复制操作花费的时间为：" + (end - start));//1
    }

}
```

![img](https://img-blog.csdnimg.cn/img_convert/a6629278090d40d2322f85459e710eee.png)

#### 4-3、缓冲流(字符型)实现文本文件的复制

```java
import org.junit.Test;
import java.io.*;

public class BufferedTest {
  /**
     * 使用BufferedReader和BufferedWriter实现文本文件的复制
     */
    @Test
    public void test4(){
        BufferedReader br = null;
        BufferedWriter bw = null;
        try {
            //创建文件和相应的流
            br = new BufferedReader(new FileReader(new File("dbcp.txt")));
            bw = new BufferedWriter(new FileWriter(new File("dbcp1.txt")));

            //读写操作
            //方式一：使用char[]数组
//            char[] cbuf = new char[1024];
//            int len;
//            while((len = br.read(cbuf)) != -1){
//                bw.write(cbuf,0,len);
//    //            bw.flush();
//            }

            //方式二：使用String
            String data;
            while((data = br.readLine()) != null){
                //方法一：
//                bw.write(data + "\n");//data中不包含换行符
                //方法二：
                bw.write(data);//data中不包含换行符
                bw.newLine();//提供换行的操作
            }

        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //关闭资源
            if(bw != null){

                try {
                    bw.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(br != null){
                try {
                    br.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```

![img](https://img-blog.csdnimg.cn/img_convert/3c19bb7c87f1659a1aab43ea29cd1673.png)

#### 4-4、缓冲流课后练习

![img](https://img-blog.csdnimg.cn/img_convert/90531fa8b1e38303434349792a7eeaac.png)

1、练习2

```java
package git;

import org.junit.Test;

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class PicTest {

    //图片的加密
    @Test
    public void test() {
        FileInputStream fis = null;
        FileOutputStream fos = null;
        try {
            fis = new FileInputStream("爱情与友情.jpg");
            fos = new FileOutputStream("爱情与友情secret.jpg");

            byte[] buffer = new byte[20];
            int len;
            while ((len = fis.read(buffer)) != -1) {
                //字节数组进行修改
                //错误的
                //            for(byte b : buffer){
                //                b = (byte) (b ^ 5);
                //            }

                //正确的
                for (int i = 0; i < len; i++) {
                    buffer[i] = (byte) (buffer[i] ^ 5);
                }

                fos.write(buffer, 0, len);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fos != null) {
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }

    }

    //图片的解密
    @Test
    public void test2() {

        FileInputStream fis = null;
        FileOutputStream fos = null;
        try {
            fis = new FileInputStream("爱情与友情secret.jpg");
            fos = new FileOutputStream("爱情与友情4.jpg");

            byte[] buffer = new byte[20];
            int len;
            while ((len = fis.read(buffer)) != -1) {
                //字节数组进行修改
                //错误的
                //            for(byte b : buffer){
                //                b = (byte) (b ^ 5);
                //            }
               
                //正确的
                for (int i = 0; i < len; i++) {
                    buffer[i] = (byte) (buffer[i] ^ 5);
                }

                fos.write(buffer, 0, len);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fos != null) {
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
     
    }
}
```

2、练习3

```java
import org.junit.Test;

import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import java.util.Set;

/**
 * 练习3:获取文本上字符出现的次数,把数据写入文件
 *
 * 思路：
 * 1.遍历文本每一个字符
 * 2.字符出现的次数存在Map中
 *
 * Map<Character,Integer> map = new HashMap<Character,Integer>();
 * map.put('a',18);
 * map.put('你',2);
 *
 * 3.把map中的数据写入文件
 */
public class WordCount {

    /**
     * 说明：如果使用单元测试，文件相对路径为当前module
     *     如果使用main()测试，文件相对路径为当前工程
     */
    @Test
    public void testWordCount() {
        FileReader fr = null;
        BufferedWriter bw = null;
        try {
            //1.创建Map集合
            Map<Character, Integer> map = new HashMap<Character, Integer>();

            //2.遍历每一个字符,每一个字符出现的次数放到map中
            fr = new FileReader("dbcp.txt");
            int c = 0;
            while ((c = fr.read()) != -1) {
                //int 还原 char
                char ch = (char) c;
                // 判断char是否在map中第一次出现
                if (map.get(ch) == null) {
                    map.put(ch, 1);
                } else {
                    map.put(ch, map.get(ch) + 1);
                }
            }

            //3.把map中数据存在文件count.txt
            //3.1 创建Writer
            bw = new BufferedWriter(new FileWriter("wordcount.txt"));

            //3.2 遍历map,再写入数据
            Set<Map.Entry<Character, Integer>> entrySet = map.entrySet();
            for (Map.Entry<Character, Integer> entry : entrySet) {
                switch (entry.getKey()) {
                    case ' ':
                        bw.write("空格=" + entry.getValue());
                        break;
                    case '\t'://\t表示tab 键字符
                        bw.write("tab键=" + entry.getValue());
                        break;
                    case '\r'://
                        bw.write("回车=" + entry.getValue());
                        break;
                    case '\n'://
                        bw.write("换行=" + entry.getValue());
                        break;
                    default:
                        bw.write(entry.getKey() + "=" + entry.getValue());
                        break;
                }
                bw.newLine();
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //4.关流
            if (fr != null) {
                try {
                    fr.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
            if (bw != null) {
                try {
                    bw.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
        }
    }
}

```

### 5、转换流

#### 5-1、转换流概述与InputStreamReader的使用

转换流提供了在字节流和字符流之间的转换
Java API提供了两个转换流：
InputStreamReader：将InputStream转换为Reader
实现将字节的输入流按指定字符集转换为字符的输入流。
需要和InputStream“套接”。
构造器
public InputStreamReader(InputStreamin)
public InputSreamReader(InputStreamin,StringcharsetName)
如：Reader isr= new InputStreamReader(System.in,”gbk”);
OutputStreamWriter：将Writer转换为OutputStream
实现将字符的输出流按指定字符集转换为字节的输出流。
需要和OutputStream“套接”。
构造器
public OutputStreamWriter(OutputStreamout)
public OutputSreamWriter(OutputStreamout,StringcharsetName)
字节流中的数据都是字符时，转成字符流操作更高效。
很多时候我们使用转换流来处理文件乱码问题。实现编码和解码的功能。
![img](https://img-blog.csdnimg.cn/img_convert/4dfa85f71b54ed2d8e3a43371933b7fb.png)

```java
import org.junit.Test;

import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStreamReader;

/**
 * 处理流之二：转换流的使用
 * 1.转换流：属于字符流
 *      InputStreamReader：将一个字节的输入流转换为字符的输入流
 *      OutputStreamWriter：将一个字符的输出流转换为字节的输出流
 *
 * 2.作用：提供字节流与字符流之间的转换
 *
 * 3.解码：字节、字节数组  --->字符数组、字符串
 *   编码：字符数组、字符串 ---> 字节、字节数组
 *
 * 4.字符集
 */
public class InputStreamReaderTest {

    /**
     * 此时处理异常的话，仍然应该使用try-catch-finally
     * InputStreamReader的使用，实现字节的输入流到字符的输入流的转换
     */
    @Test
    public void test() throws IOException {

        FileInputStream fis = new FileInputStream("dbcp.txt");
//        InputStreamReader isr = new InputStreamReader(fis);//使用系统默认的字符集
        //参数2指明了字符集，具体使用哪个字符集，取决于文件dbcp.txt保存时使用的字符集
        InputStreamReader isr = new InputStreamReader(fis,"UTF-8");//使用系统默认的字符集

        char[] cbuf = new char[20];
        int len;
        while((len = isr.read(cbuf)) != -1){
            String str = new String(cbuf,0,len);
            System.out.print(str);
        }

        isr.close();
    }

}
```

#### 5-2、转换流实现文件读入与写出

```java
import org.junit.Test;

import java.io.*;

/**
 * 处理流之二：转换流的使用
 * 1.转换流：属于字符流
 *      InputStreamReader：将一个字节的输入流转换为字符的输入流
 *      OutputStreamWriter：将一个字符的输出流转换为字节的输出流
 *
 * 2.作用：提供字节流与字符流之间的转换
 *
 * 3.解码：字节、字节数组  --->字符数组、字符串
 *   编码：字符数组、字符串 ---> 字节、字节数组
 *
 * 4.字符集
 */
public class InputStreamReaderTest {
    /**
     * 此时处理异常的话，仍然应该使用try-catch-finally
     * 综合使用InputStreamReader和OutputStreamWriter
     */
    @Test
    public void test2() throws IOException {
        //1.造文件、造流
        File file1 = new File("dbcp.txt");
        File file2 = new File("dbcp_gbk.txt");

        FileInputStream fis = new FileInputStream(file1);
        FileOutputStream fos = new FileOutputStream(file2);

        InputStreamReader isr = new InputStreamReader(fis,"utf-8");
        OutputStreamWriter osw = new OutputStreamWriter(fos,"gbk");

        //2.读写过程
        char[] cbuf = new char[20];
        int len;
        while((len = isr.read(cbuf)) != -1){
            osw.write(cbuf,0,len);
        }

        //3.关闭资源
        isr.close();
        osw.close();
    }
}
```

#### 5-3、多种字符编码集的说明

> 1、编码表的由来

计算机只能识别二进制数据，早期由来是电信号。为了方便应用计算机，让它可以识别各个国家的文字。就将各个国家的文字用数字来表示，并一一对应，形成一张表。这就是编码表。

> 2、常见的编码表

```java
/**
  * 4.字符集
  *  ASCII：美国标准信息交换码。
  *     用一个字节的7位可以表示。
  *  ISO8859-1：拉丁码表。欧洲码表
  *     用一个字节的8位表示。
  *  GB2312：中国的中文编码表。最多两个字节编码所有字符
  *  GBK：中国的中文编码表升级，融合了更多的中文文字符号。最多两个字节编码
  *  Unicode：国际标准码，融合了目前人类使用的所有字符。为每个字符分配唯一的字符码。所有的文字都用两个字节来表示。
  *  UTF-8：变长的编码方式，可用1-4个字节来表示一个字符。
  */
```

说明：

Unicode不完美，这里就有三个问题，
一个是，我们已经知道，英文字母只用一个字节表示就够了，
第二个问题是如何才能区别Unicode和ASCII？计算机怎么知道两个字节表示一个符号，而不是分别表示两个符号呢？
第三个，如果和GBK等双字节编码方式一样，用最高位是1或0表示两个字节和一个字节，就少了很多值无法用于表示字符，不够表示所有字符。Unicode在很长一段时间内无法推广，直到互联网的出现。
面向传输的众多UTF（UCS Transfer Format）标准出现了，顾名思义，**UTF-8就是每次8个位传输数据，而UTF-16就是每次16个位。**这是为传输而设计的编码，并使编码无国界，这样就可以显示全世界上所有文化的字符了。
Unicode只是定义了一个庞大的、全球通用的字符集，并为每个字符规定了唯一确定的编号，具体存储成什么样的字节流，取决于字符编码方案。推荐的Unicode编码是UTF-8和UTF-16。

![img](https://img-blog.csdnimg.cn/img_convert/b886d2a72df648a1e6bd5ffcf2db9dc3.png)

![img](https://img-blog.csdnimg.cn/img_convert/35ad9abbbf83b4ea957ce978bac16873.png)

### 6、标准输入、输出流

System.in和System.out分别代表了系统标准的输入和输出设备
默认输入设备是：键盘，输出设备是：显示器
System.in的类型是InputStream
System.out的类型是PrintStream，其是OutputStream的子类FilterOutputStream的子类
重定向：通过System类的setIn，setOut方法对默认设备进行改变。
public static void setIn(InputStreamin)
public static void setOut(PrintStreamout)

```java
import org.junit.Test;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

/**
 * 其他流的使用
 * 1.标准的输入、输出流
 * 2.打印流
 * 3.数据流
 */
public class OtherStreamTest {

    /**
     * 1.标准的输入、输出流
     *   1.1
     *     System.in:标准的输入流，默认从键盘输入
     *     System.out:标准的输出流，默认从控制台输出
     *   1.2
     *     System类的setIn(InputStream is) / setOut(PrintStream ps)方式重新指定输入和输出的流。
     *
     *   1.3练习：
     *     从键盘输入字符串，要求将读取到的整行字符串转成大写输出。然后继续进行输入操作，
     *     直至当输入“e”或者“exit”时，退出程序。
     *
     *   方法一：使用Scanner实现，调用next()返回一个字符串
     *   方法二：使用System.in实现。System.in  --->  转换流 ---> BufferedReader的readLine()
     */
    @Test
    public void test(){
        BufferedReader br = null;
        try {
            InputStreamReader isr = new InputStreamReader(System.in);
            br = new BufferedReader(isr);

            while (true) {
                System.out.println("请输入字符串：");
                String data = br.readLine();
                if ("e".equalsIgnoreCase(data) || "exit".equalsIgnoreCase(data)) {
                    System.out.println("程序结束");
                    break;
                }

                String upperCase = data.toUpperCase();
                System.out.println(upperCase);

            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (br != null) {
                try {
                    br.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
        }
    }
}
```

### 7、打印流

实现将基本数据类型的数据格式转化为字符串输出
打印流：PrintStream和PrintWriter
提供了一系列重载的print()和println()方法，用于多种数据类型的输出
PrintStream和PrintWriter的输出不会抛出IOException异常
PrintStream和PrintWriter有自动flush功能
PrintStream 打印的所有字符都使用平台的默认字符编码转换为字节。在需要写入字符而不是写入字节的情况下，应该使用PrintWriter 类。
System.out返回的是PrintStream的实例

```java
import org.junit.Test;
import java.io.*;

public class OtherStreamTest {

    /**
     * 2. 打印流：PrintStream 和PrintWriter
     *  2.1 提供了一系列重载的print() 和 println()
     *  2.2 练习：
     */
    @Test
    public void test2(){
        PrintStream ps = null;
        try {
            FileOutputStream fos = new FileOutputStream(new File("D:\\IO\\text.txt"));
            // 创建打印输出流,设置为自动刷新模式(写入换行符或字节 '\n' 时都会刷新输出缓冲区)
            ps = new PrintStream(fos, true);
            if (ps != null) {// 把标准输出流(控制台输出)改成文件
                System.setOut(ps);
            }

            for (int i = 0; i <= 255; i++) { // 输出ASCII字符
                System.out.print((char) i);
                if (i % 50 == 0) { // 每50个数据一行
                    System.out.println(); // 换行
                }
            }

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } finally {
            if (ps != null) {
                ps.close();
            }
        }
    }
}
```

### 8、数据流

为了方便地操作Java语言的基本数据类型和String的数据，可以使用数据流。

数据流有两个类：(用于读取和写出基本数据类型、String类的数据）

DataInputStream和DataOutputStream
分别“套接”在InputStream和OutputStream子类的流上
DataInputStream中的方法

boolean readBoolean()	byte readByte()
char readChar()	float readFloat()
double readDouble()	short readShort()
long readLong()	int readInt()
String readUTF()	void readFully(byte[s] b)

- DataOutputStream中的方法
  - 将上述的方法的read改为相应的write即可。

```java
import org.junit.Test;
import java.io.*;

public class OtherStreamTest {    
   /**
     * 3.数据流
     *   3.1 DataInputStream 和 DataOutputStream
     *   3.2 作用：用于读取或写出基本数据类型的变量或字符串
     *
     *   练习：将内存中的字符串、基本数据类型的变量写出到文件中。
     *
     *   注意：处理异常的话，仍然应该使用try-catch-finally.
     */
    @Test
    public void test3() throws IOException {
        //1.
        DataOutputStream dos = new DataOutputStream(new FileOutputStream("data.txt"));
        //2.
        dos.writeUTF("刘刚");
        dos.flush();//刷新操作，将内存中的数据写入文件
        dos.writeInt(23);
        dos.flush();
        dos.writeBoolean(true);
        dos.flush();
        //3.
        dos.close();
    }

    /**
     * 将文件中存储的基本数据类型变量和字符串读取到内存中，保存在变量中。
     *
     * 注意点：读取不同类型的数据的顺序要与当初写入文件时，保存的数据的顺序一致！
     */
    @Test
    public void test4() throws IOException {
        //1.
        DataInputStream dis = new DataInputStream(new FileInputStream("data.txt"));
        //2.
        String name = dis.readUTF();
        int age = dis.readInt();
        boolean isMale = dis.readBoolean();

        System.out.println("name = " + name);
        System.out.println("age = " + age);
        System.out.println("isMale = " + isMale);

        //3.
        dis.close();

    }
}
```

### 9、对象流

#### 9 -1、对象序列化机制的理解

ObjectInputStream和OjbectOutputSteam
用于存储和读取基本数据类型数据或对象的处理流。它的强大之处就是可以把Java中的对象写入到数据源中，也能把对象从数据源中还原回来。
序列化：用ObjectOutputStream类保存基本类型数据或对象的机制
反序列化：用ObjectInputStream类读取基本类型数据或对象的机制
ObjectOutputStream和ObjectInputStream不能序列化static和transient修饰的成员变量
对象序列化机制允许把内存中的Java对象转换成平台无关的二进制流，从而允许把这种二进制流持久地保存在磁盘上，或通过网络将这种二进制流传输到另一个网络节点。//当其它程序获取了这种二进制流，就可以恢复成原来的Java对象
序列化的好处在于可将任何实现了Serializable接口的对象转化为字节数据，使其在保存和传输时可被还原
序列化是RMI（Remote Method Invoke –远程方法调用）过程的参数和返回值都必须实现的机制，而RMI 是JavaEE的基础。因此序列化机制是JavaEE平台的基础
如果需要让某个对象支持序列化机制，则必须让对象所属的类及其属性是可序列化的，为了让某个类是可序列化的，该类必须实现如下两个接口之一。否则，会抛出NotSerializableException异常
Serializable
Externalizable

#### 9-2、对象流序列化与反序列化字符串操作

```java
import org.junit.Test;

import java.io.*;

/**
 * 对象流的使用
 * 1.ObjectInputStream 和 ObjectOutputStream
 * 2.作用：用于存储和读取基本数据类型数据或对象的处理流。它的强大之处就是可以把Java中的对象写入到数据源中，也能把对象从数据源中还原回来。
 */
public class ObjectTest {

    /**
     * 序列化过程：将内存中的java对象保存到磁盘中或通过网络传输出去
     * 使用ObjectOutputStream实现
     */
    @Test
    public void test(){
        ObjectOutputStream oos = null;
        try {
            //创造流
            oos = new ObjectOutputStream(new FileOutputStream("object.dat"));
            //制造对象
            oos.writeObject(new String("秦始皇陵欢迎你"));

            //刷新操作
            oos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if(oos != null){
                //3.关闭流
                try {
                    oos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    /**
     * 反序列化：将磁盘文件中的对象还原为内存中的一个java对象
     * 使用ObjectInputStream来实现
     */
    @Test
    public void test2(){
        ObjectInputStream ois = null;
        try {
            ois = new ObjectInputStream(new FileInputStream("object.dat"));

            Object obj = ois.readObject();
            String str = (String) obj;

            System.out.println(str);
        } catch (IOException e) {
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } finally {
            if(ois != null){
                try {
                    ois.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

}
```

#### 9-3、自定义类实现序列化与反序列化操作

若某个类实现了Serializable接口，该类的对象就是可序列化的：

创建一个ObjectOutputStream
调用ObjectOutputStream对象的writeObject(对象) 方法输出可序列化对象
注意写出一次，操作flush()一次
反序列化

创建一个ObjectInputStream对象调用readObject() 方法读取流中的对象
强调：如果某个类的属性不是基本数据类型或String 类型，而是另一个引用类型，那么这个引用类型必须是可序列化的，否则拥有该类型的Field 的类也不能序列化

1、Person类

```java
import java.io.Serializable;

/**
 * Person需要满足如下的要求，方可序列化
 * 1.需要实现接口：Serializable
 */
public class Person implements Serializable {
    public static final long serialVersionUID = 475463534532L;

    private String name;
    private int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

2、测试类

```java
import org.junit.Test;

import java.io.*;

/**
 * 对象流的使用
 * 1.ObjectInputStream 和 ObjectOutputStream
 * 2.作用：用于存储和读取基本数据类型数据或对象的处理流。它的强大之处就是可以把Java中的对象写入到数据源中，也能把对象从数据源中还原回来。
 *
 * 3.要想一个java对象是可序列化的，需要满足相应的要求。见Person.java
 *
 * 4.序列化机制：
 * 对象序列化机制允许把内存中的Java对象转换成平台无关的二进制流，从而允许把这种
 * 二进制流持久地保存在磁盘上，或通过网络将这种二进制流传输到另一个网络节点。
 * 当其它程序获取了这种二进制流，就可以恢复成原来的Java对象。
 *
 */
public class ObjectTest {

    /**
     * 序列化过程：将内存中的java对象保存到磁盘中或通过网络传输出去
     * 使用ObjectOutputStream实现
     */
    @Test
    public void test(){
        ObjectOutputStream oos = null;
        try {
            //创造流
            oos = new ObjectOutputStream(new FileOutputStream("object.dat"));
            //制造对象
            oos.writeObject(new String("秦始皇陵欢迎你"));
            //刷新操作
            oos.flush();

            oos.writeObject(new Person("李时珍",65));
            oos.flush();


        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if(oos != null){
                //3.关闭流
                try {
                    oos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    /**
     * 反序列化：将磁盘文件中的对象还原为内存中的一个java对象
     * 使用ObjectInputStream来实现
     */
    @Test
    public void test2(){
        ObjectInputStream ois = null;
        try {
            ois = new ObjectInputStream(new FileInputStream("object.dat"));

            Object obj = ois.readObject();
            String str = (String) obj;

            Person p = (Person) ois.readObject();

            System.out.println(str);
            System.out.println(p);
        } catch (IOException e) {
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } finally {
            if(ois != null){
                try {
                    ois.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

}
```

#### 9-4、serialVersionUID的理解

凡是实现Serializable接口的类都有一个表示序列化版本标识符的静态变量：
private static final long serialVersionUID;
serialVersionUID用来表明类的不同版本间的兼容性。简言之，其目的是以序列化对象进行版本控制，有关各版本反序列化时是否兼容。
如果类没有显示定义这个静态常量，它的值是Java运行时环境根据类的内部细节自动生成的。若类的实例变量做了修改，serialVersionUID可能发生变化。故建议，显式声明。
简单来说，Java的序列化机制是通过在运行时判断类的serialVersionUID来验证版本一致性的。在进行反序列化时，JVM会把传来的字节流中的serialVersionUID与本地相应实体类的serialVersionUID进行比较，如果相同就认为是一致的，可以进行反序列化，否则就会出现序列化版本不一致的异常。(InvalidCastException)
1、Person类

```java
import java.io.Serializable;

/**
 * Person需要满足如下的要求，方可序列化
 * 1.需要实现接口：Serializable
 * 2.当前类提供一个全局常量：serialVersionUID
 * 3.除了当前Person类需要实现Serializable接口之外，还必须保证其内部所有属性
 *   也必须是可序列化的。（默认情况下，基本数据类型可序列化）
 *
 *
 * 补充：ObjectOutputStream和ObjectInputStream不能序列化static和transient修饰的成员变量
 */
public class Person implements Serializable {
    public static final long serialVersionUID = 475463534532L;

    private String name;
    private int age;
    private int id;

    public Person() {
    }

    public Person(String name, int age, int id) {
        this.name = name;
        this.age = age;
        this.id = id;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", id=" + id +
                '}';
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

2、测试类

```java
import org.junit.Test;

import java.io.*;

/**
 * 对象流的使用
 * 1.ObjectInputStream 和 ObjectOutputStream
 * 2.作用：用于存储和读取基本数据类型数据或对象的处理流。它的强大之处就是可以把Java中的对象写入到数据源中，也能把对象从数据源中还原回来。
 *
 * 3.要想一个java对象是可序列化的，需要满足相应的要求。见Person.java
 *
 * 4.序列化机制：
 * 对象序列化机制允许把内存中的Java对象转换成平台无关的二进制流，从而允许把这种
 * 二进制流持久地保存在磁盘上，或通过网络将这种二进制流传输到另一个网络节点。
 * 当其它程序获取了这种二进制流，就可以恢复成原来的Java对象。
 *
 */
public class ObjectTest {

    /**
     * 序列化过程：将内存中的java对象保存到磁盘中或通过网络传输出去
     * 使用ObjectOutputStream实现
     */
    @Test
    public void test(){
        ObjectOutputStream oos = null;
        try {
            //创造流
            oos = new ObjectOutputStream(new FileOutputStream("object.dat"));
            //制造对象
            oos.writeObject(new String("秦始皇陵欢迎你"));
            //刷新操作
            oos.flush();

            oos.writeObject(new Person("李时珍",65,0));
            oos.flush();


        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if(oos != null){
                //3.关闭流
                try {
                    oos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    /**
     * 反序列化：将磁盘文件中的对象还原为内存中的一个java对象
     * 使用ObjectInputStream来实现
     */
    @Test
    public void test2(){
        ObjectInputStream ois = null;
        try {
            ois = new ObjectInputStream(new FileInputStream("object.dat"));

            Object obj = ois.readObject();
            String str = (String) obj;

            Person p = (Person) ois.readObject();

            System.out.println(str);
            System.out.println(p);
        } catch (IOException e) {
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } finally {
            if(ois != null){
                try {
                    ois.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

}
```

#### 9-5、自定义类可序列化的其它要求

1、Person类

```java
import java.io.Serializable;

/**
 * Person需要满足如下的要求，方可序列化
 * 1.需要实现接口：Serializable
 * 2.当前类提供一个全局常量：serialVersionUID
 * 3.除了当前Person类需要实现Serializable接口之外，还必须保证其内部所有属性
 *   也必须是可序列化的。（默认情况下，基本数据类型可序列化）
 *
 *
 * 补充：ObjectOutputStream和ObjectInputStream不能序列化static和transient修饰的成员变量
 *
 */
public class Person implements Serializable{

    public static final long serialVersionUID = 475463534532L;

    private String name;
    private int age;
    private int id;
    private Account acct;

    public Person(String name, int age, int id) {
        this.name = name;
        this.age = age;
        this.id = id;
    }

    public Person(String name, int age, int id, Account acct) {
        this.name = name;
        this.age = age;
        this.id = id;
        this.acct = acct;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", id=" + id +
                ", acct=" + acct +
                '}';
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public Person(String name, int age) {

        this.name = name;
        this.age = age;
    }

    public Person() {

    }
}

class Account implements Serializable{
    public static final long serialVersionUID = 4754534532L;
    private double balance;

    @Override
    public String toString() {
        return "Account{" +
                "balance=" + balance +
                '}';
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    public Account(double balance) {

        this.balance = balance;
    }
}
```

2、测试类

```java
import org.junit.Test;

import java.io.*;

/**
 * 对象流的使用
 * 1.ObjectInputStream 和 ObjectOutputStream
 * 2.作用：用于存储和读取基本数据类型数据或对象的处理流。它的强大之处就是可以把Java中的对象写入到数据源中，也能把对象从数据源中还原回来。
 *
 * 3.要想一个java对象是可序列化的，需要满足相应的要求。见Person.java
 *
 * 4.序列化机制：
 * 对象序列化机制允许把内存中的Java对象转换成平台无关的二进制流，从而允许把这种
 * 二进制流持久地保存在磁盘上，或通过网络将这种二进制流传输到另一个网络节点。
 * 当其它程序获取了这种二进制流，就可以恢复成原来的Java对象。
 */
public class ObjectTest {

    /**
     * 序列化过程：将内存中的java对象保存到磁盘中或通过网络传输出去
     * 使用ObjectOutputStream实现
     */
    @Test
    public void test(){
        ObjectOutputStream oos = null;
        try {
            //创造流
            oos = new ObjectOutputStream(new FileOutputStream("object.dat"));
            //制造对象
            oos.writeObject(new String("秦始皇陵欢迎你"));
            //刷新操作
            oos.flush();

            oos.writeObject(new Person("李时珍",65));
            oos.flush();

            oos.writeObject(new Person("张学良",23,1001,new Account(5000)));
            oos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if(oos != null){
                //3.关闭流
                try {
                    oos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    /**
     * 反序列化：将磁盘文件中的对象还原为内存中的一个java对象
     * 使用ObjectInputStream来实现
     */
    @Test
    public void test2(){
        ObjectInputStream ois = null;
        try {
            ois = new ObjectInputStream(new FileInputStream("object.dat"));

            Object obj = ois.readObject();
            String str = (String) obj;

            Person p = (Person) ois.readObject();

            System.out.println(str);
            System.out.println(p);
        } catch (IOException e) {
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } finally {
            if(ois != null){
                try {
                    ois.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

}
```

### 10、随机存取文件流

RandomAccessFile 声明在java.io包下，但直接继承于java.lang.Object类。并且它实现了DataInput、DataOutput这两个接口，也就意味着这个类既可以读也可以写。
RandomAccessFile 类支持“随机访问” 的方式，程序可以直接跳到文件的任意地方来读、写文件
支持只访问文件的部分内容
可以向已存在的文件后追加内容
RandomAccessFile 对象包含一个记录指针，用以标示当前读写处的位置。RandomAccessFile类对象可以自由移动记录指针：
long getFilePointer()：获取文件记录指针的当前位置
void seek(long pos)：将文件记录指针定位到pos位置
构造器
public RandomAccessFile(Filefile, Stringmode)
public RandomAccessFile(Stringname, Stringmode)
创建RandomAccessFile类实例需要指定一个mode 参数，该参数指定RandomAccessFile的访问模式：
r: 以只读方式打开
rw：打开以便读取和写入
rwd:打开以便读取和写入；同步文件内容的更新
rws:打开以便读取和写入；同步文件内容和元数据的更新
如果模式为只读r。则不会创建文件，而是会去读取一个已经存在的文件，如果读取的文件不存在则会出现异常。如果模式为rw读写。如果文件不存在则会去创建文件，如果存在则不会创建。

#### 10-1、RandomAccessFile实现数据的读写操作

```java
import org.junit.Test;

import java.io.File;
import java.io.IOException;
import java.io.RandomAccessFile;

/**
 * RandomAccessFile的使用
 * 1.RandomAccessFile直接继承于java.lang.Object类，实现了DataInput和DataOutput接口
 * 2.RandomAccessFile既可以作为一个输入流，又可以作为一个输出流
 * 3.如果RandomAccessFile作为输出流时，写出到的文件如果不存在，则在执行过程中自动创建。
 *   如果写出到的文件存在，则会对原有文件内容进行覆盖。（默认情况下，从头覆盖）
 */
public class RandomAccessFileTest {

    @Test
    public void test(){

        RandomAccessFile raf1 = null;
        RandomAccessFile raf2 = null;
        try {
            raf1 = new RandomAccessFile(new File("爱情与友情.jpg"),"r");
            raf2 = new RandomAccessFile(new File("爱情与友情1.jpg"),"rw");

            byte[] buffer = new byte[1024];
            int len;
            while((len = raf1.read(buffer)) != -1){
                raf2.write(buffer,0,len);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if(raf1 != null){
                try {
                    raf1.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
            if(raf2 != null){
                try {
                    raf2.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }

    }

    @Test
    public void test2() throws IOException {

        RandomAccessFile raf1 = new RandomAccessFile("hello.txt","rw");

        raf1.write("xyz".getBytes());

        raf1.close();

    }

}
```

#### 10-2、RandomAccessFile实现数据的插入操作

```java
import org.junit.Test;

import java.io.File;
import java.io.IOException;
import java.io.RandomAccessFile;

/**
 * RandomAccessFile的使用
 * 1.RandomAccessFile直接继承于java.lang.Object类，实现了DataInput和DataOutput接口
 * 2.RandomAccessFile既可以作为一个输入流，又可以作为一个输出流
 * 3.如果RandomAccessFile作为输出流时，写出到的文件如果不存在，则在执行过程中自动创建。
 *   如果写出到的文件存在，则会对原有文件内容进行覆盖。（默认情况下，从头覆盖）
 *
 * 4.可以通过相关的操作，实现RandomAccessFile“插入”数据的效果
 */
public class RandomAccessFileTest {

    /**
     * 使用RandomAccessFile实现数据的插入效果
     */
    @Test
    public void test3() throws IOException {
        RandomAccessFile raf1 = new RandomAccessFile("hello.txt","rw");

        raf1.seek(3);//将指针调到角标为3的位置
        //保存指针3后面的所有数据到StringBuilder中
        StringBuilder builder = new StringBuilder((int) new File("hello.txt").length());
        byte[] buffer = new byte[20];
        int len;
        while((len = raf1.read(buffer)) != -1){
            builder.append(new String(buffer,0,len)) ;
        }
        //调回指针，写入“xyz”
        raf1.seek(3);
        raf1.write("xyz".getBytes());

        //将StringBuilder中的数据写入到文件中
        raf1.write(builder.toString().getBytes());

        raf1.close();

        //思考：将StringBuilder替换为ByteArrayOutputStream
    }

}
```

### 11、NIO.2中Path、Paths、Files类的使用

Java NIO (New IO，Non-Blocking IO)是从Java 1.4版本开始引入的一套新的IO API，可以替代标准的Java IO API。NIO与原来的IO有同样的作用和目的，但是使用的方式完全不同，NIO支持面向缓冲区的(IO是面向流的)、基于通道的IO操作。NIO将以更加高效的方式进行文件的读写操作。

Java API中提供了两套NIO，一套是针对标准输入输出NIO，另一套就是网络编程NIO。

|-----java.nio.channels.Channel
    |-----FileChannel:处理本地文件
    |-----SocketChannel：TCP网络编程的客户端的Channel
    |-----ServerSocketChannel:TCP网络编程的服务器端的Channel
    |-----DatagramChannel：UDP网络编程中发送端和接收端的Channel
随着JDK 7 的发布，Java对NIO进行了极大的扩展，增强了对文件处理和文件系统特性的支持，以至于我们称他们为NIO.2。因为NIO 提供的一些功能，NIO已经成为文件处理中越来越重要的部分。

早期的Java只提供了一个File类来访问文件系统，但File类的功能比较有限，所提供的方法性能也不高。而且，大多数方法在出错时仅返回失败，并不会提供异常信息。

NIO. 2为了弥补这种不足，引入了Path接口，代表一个平台无关的平台路径，描述了目录结构中文件的位置。Path可以看成是File类的升级版本，实际引用的资源也可以不存在。

在以前IO操作都是这样写的:

```java
import java.io.File;

File file = new File(“index.html”);
```

但在Java7 中，我们可以这样写：

```java
import java.nio.file.Path;
import java.nio.file.Paths;
Path path = Paths.get(“index.html”);
```

同时，NIO.2在java.nio.file包下还提供了Files、Paths工具类，Files包含了大量静态的工具方法来操作文件；Paths则包含了两个返回Path的静态工厂方法。

Paths类提供的静态get()方法用来获取Path对象：

static Pathget(String first, String … more) : 用于将多个字符串串连成路径
static Path get(URI uri): 返回指定uri对应的Path路径
1、Path接口
![img](https://img-blog.csdnimg.cn/img_convert/6b9b053461f8e826c26a05b5165f0554.png)

2、Files 类

![img](https://img-blog.csdnimg.cn/img_convert/136c25b4e21abb2636a8e2da960c62d1.png)

![img](https://img-blog.csdnimg.cn/img_convert/8982f1154c6cb449ecf5695d8f1142cf.png)

## 17、网络编程

### 1、网络编程概述

Java是Internet 上的语言，它从语言级上提供了对网络应用程序的支持，程序员能够很容易开发常见的网络应用程序。

Java提供的网络类库，可以实现无痛的网络连接，联网的底层细节被隐藏在Java 的本机安装系统里，由JVM 进行控制。并且Java 实现了一个跨平台的网络库，程序员面对的是一个统一的网络编程环境。

计算机网络：

把分布在不同地理区域的计算机与专门的外部设备用通信线路互连成一个规模大、功能强的网络系统，从而使众多的计算机可以方便地互相传递信息、共享硬件、软件、数据信息等资源。

网络编程的目的：

直接或间接地通过网络协议与其它计算机实现数据交换，进行通讯。

网络编程中有两个主要的问题：

如何准确地定位网络上一台或多台主机；定位主机上的特定的应用
找到主机后如何可靠高效地进行数据传输

### 2、网络通信要素概述

- 通信双方地址
  - IP
  - 端口号
- 一定的规则（即：网络通信协议。有两套参考模型）
  - OSI参考模型：模型过于理想化，未能在因特网上进行广泛推广
  - TCP/IP参考模型(或TCP/IP协议)：事实上的国际标准。
- 网络通信协议

![img](https://img-blog.csdnimg.cn/img_convert/09bdce6b569fe3cf80206cc704dbf7cb.png)

![img](https://img-blog.csdnimg.cn/img_convert/e769997523201f9fa4f83e501931e6e1.png)

```java
/**
 * 一、网络编程中有两个主要的问题：
 * 1.如何准确地定位网络上一台或多台主机；定位主机上的特定的应用
 * 2.找到主机后如何可靠高效地进行数据传输
 *
 * 二、网络编程中的两个要素：
 * 1.对应问题一：IP和端口号
 * 2.对应问题二：提供网络通信协议：TCP/IP参考模型（应用层、传输层、网络层、物理+数据链路层）
 */
```

### 3、通信要素1 ：IP和端口号

#### 3-1、IP的理解与InetAddress类的实例化

IP 地址：InetAddress
唯一的标识Internet 上的计算机（通信实体）
本地回环地址(hostAddress)：127.0.0.1 主机名(hostName)：localhost
IP地址分类方式1：IPV4和IPV6
IPV4：4个字节组成，4个0-255。大概42亿，30亿都在北美，亚洲4亿。2011年初已经用尽。以点分十进制表示，如192.168.0.1
IPV6：128位（16个字节），写成8个无符号整数，每个整数用四个十六进制位表示，数之间用冒号（：）分开，如：3ffe:3201:1401:1280:c8ff:fe4d:db39:1984
IP地址分类方式2：公网地址(万维网使用)和私有地址(局域网使用)。192.168.开头的就是私有地址，范围即为192.168.0.0–192.168.255.255，专门为组织机构内部使用
特点：不易记忆
Internet上的主机有两种方式表示地址：
域名(hostName)：www.atguigu.com
IP地址(hostAddress)：202.108.35.210
InetAddress类主要表示IP地址，两个子类：Inet4Address、Inet6Address。
InetAddress类对象含有一个Internet主机地址的域名和IP地址：www.atguigu.com和202.108.35.210。
域名容易记忆，当在连接网络时输入一个主机的域名后，域名服务器(DNS)负责将域名转化成IP地址，这样才能和主机建立连接。-------域名解析

![img](https://img-blog.csdnimg.cn/img_convert/f0b20fc08bb3bd5b0aaff6131b11b428.png)

```java
import java.net.InetAddress;
import java.net.UnknownHostException;

/**
 * 一、网络编程中有两个主要的问题：
 * 1.如何准确地定位网络上一台或多台主机；定位主机上的特定的应用
 * 2.找到主机后如何可靠高效地进行数据传输
 *
 * 二、网络编程中的两个要素：
 * 1.对应问题一：IP和端口号
 * 2.对应问题二：提供网络通信协议：TCP/IP参考模型（应用层、传输层、网络层、物理+数据链路层）
 *
 *
 * 三、通信要素一：IP和端口号
 *
 * 1. IP:唯一的标识 Internet 上的计算机（通信实体）
 * 2. 在Java中使用InetAddress类代表IP
 * 3. IP分类：IPv4 和 IPv6 ; 万维网 和 局域网
 * 4. 域名:   www.baidu.com   www.mi.com  www.sina.com  www.jd.com
 *            www.vip.com
 * 5. 本地回路地址：127.0.0.1 对应着：localhost
 *
 * 6. 如何实例化InetAddress:两个方法：getByName(String host) 、 getLocalHost()
 *        两个常用方法：getHostName() / getHostAddress()
 *
  * 7. 端口号：正在计算机上运行的进程。
 * 要求：不同的进程有不同的端口号
 * 范围：被规定为一个 16 位的整数 0~65535。
 *
 * 8. 端口号与IP地址的组合得出一个网络套接字：Socket
 */
public class InetAddressTest {
    public static void main(String[] args) {

        try {
            //File file = new File("hello.txt");
            InetAddress inet1 = InetAddress.getByName("192.168.10.14");

            System.out.println(inet1);

            InetAddress inet2 = InetAddress.getByName("www.atguigu.com");
            System.out.println(inet2);

            InetAddress inet3 = InetAddress.getByName("127.0.0.1");
            System.out.println(inet3);

            //获取本地ip
            InetAddress inet4 = InetAddress.getLocalHost();
            System.out.println(inet4);

            //getHostName()
            System.out.println(inet2.getHostName());
            //getHostAddress()
            System.out.println(inet2.getHostAddress());

        } catch (UnknownHostException e) {
            e.printStackTrace();
        }
    }
}
```

#### 3-2、端口号的理解

端口号标识正在计算机上运行的进程（程序）
不同的进程有不同的端口号
被规定为一个16 位的整数0~65535。
端口分类：
公认端口：0~1023。被预先定义的服务通信占用（如：HTTP占用端口80，FTP占用端口21，Telnet占用端口23）
注册端口：1024~49151。分配给用户进程或应用程序。（如：Tomcat占用端口8080，MySQL占用端口3306，Oracle占用端口1521等）。
动态/私有端口：49152~65535。
端口号与IP地址的组合得出一个网络套接字：Socket。
![img](https://img-blog.csdnimg.cn/img_convert/cdbda7a9127a6319dcd57cc16be48849.png)

### 4、通信要素2：网络协议

网络通信协议

计算机网络中实现通信必须有一些约定，即通信协议，对速率、传输代码、代码结构、传输控制步骤、出错控制等制定标准。

问题：网络协议太复杂

计算机网络通信涉及内容很多，比如指定源地址和目标地址，加密解密，压缩解压缩，差错控制，流量控制，路由控制，如何实现如此复杂的网络协议呢？

通信协议分层的思想

在制定协议时，把复杂成份分解成一些简单的成份，再将它们复合起来。最常用的复合方式是层次方式，即同层间可以通信、上一层可以调用下一层，而与再下一层不发生关系。各层互不影响，利于系统的开发和扩展。

#### 4-1、TCP和UDP网络通信协议的对比

传输层协议中有两个非常重要的协议：
传输控制协议TCP(Transmission Control Protocol)
用户数据报协议UDP(User Datagram Protocol)。
TCP/IP 以其两个主要协议：传输控制协议(TCP)和网络互联协议(IP)而得名，实际上是一组协议，包括多个具有不同功能且互为关联的协议。
IP(Internet Protocol)协议是网络层的主要协议，支持网间互连的数据通信。
TCP/IP协议模型从更实用的角度出发，形成了高效的四层体系结构，即物理链路层、IP层、传输层和应用层。
TCP协议：
使用TCP协议前，须先建立TCP连接，形成传输数据通道
传输前，采用“三次握手”方式，点对点通信，是可靠的
TCP协议进行通信的两个应用进程：客户端、服务端。
在连接中可进行大数据量的传输传输完毕，需释放已建立的连接，效率低
UDP协议：
将数据、源、目的封装成数据包，不需要建立连接
每个数据报的大小限制在64K内
发送不管对方是否准备好，接收方收到也不确认，故是不可靠的
可以广播发送
发送数据结束时无需释放资源，开销小，速度快
![img](https://img-blog.csdnimg.cn/img_convert/e028a11c223c41376e42a0cecd7dc505.png)

![img](https://img-blog.csdnimg.cn/img_convert/3125b3b4a4431912fa787bbeaea342b6.png)

### 5、TCP网络编程

1、例题1

```java
import org.junit.Test;

import java.io.ByteArrayOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.InetAddress;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * 实现TCP的网络编程
 * 例子1：客户端发送信息给服务端，服务端将数据显示在控制台上
 */
public class TCPTest {

    //客户端
    @Test
    public void client()  {
        Socket socket = null;
        OutputStream os = null;
        try {
            //1.创建Socket对象，指明服务器端的ip和端口号
            InetAddress inet = InetAddress.getByName("192.168.14.100");
            socket = new Socket(inet,8899);
            //2.获取一个输出流，用于输出数据
            os = socket.getOutputStream();
            //3.写出数据的操作
            os.write("你好，我是客户端HH".getBytes());
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //4.资源的关闭
            if(os != null){
                try {
                    os.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(socket != null){
                try {
                    socket.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
        }
    }
    //服务端
    @Test
    public void server()  {

        ServerSocket ss = null;
        Socket socket = null;
        InputStream is = null;
        ByteArrayOutputStream baos = null;
        try {
            //1.创建服务器端的ServerSocket，指明自己的端口号
            ss = new ServerSocket(8899);
            //2.调用accept()表示接收来自于客户端的socket
            socket = ss.accept();
            //3.获取输入流
            is = socket.getInputStream();

            //不建议这样写，可能会有乱码
//        byte[] buffer = new byte[1024];
//        int len;
//        while((len = is.read(buffer)) != -1){
//            String str = new String(buffer,0,len);
//            System.out.print(str);
//        }
            //4.读取输入流中的数据
            baos = new ByteArrayOutputStream();
            byte[] buffer = new byte[5];
            int len;
            while((len = is.read(buffer)) != -1){
                baos.write(buffer,0,len);
            }

            System.out.println(baos.toString());

            System.out.println("收到了来自于：" + socket.getInetAddress().getHostAddress() + "的数据");

        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if(baos != null){
                //5.关闭资源
                try {
                    baos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(is != null){
                try {
                    is.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(socket != null){
                try {
                    socket.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(ss != null){
                try {
                    ss.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```

2、例题2

```java
import org.junit.Test;

import java.io.*;
import java.net.InetAddress;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * 实现TCP的网络编程
 * 例题2：客户端发送文件给服务端，服务端将文件保存在本地。
 *
 * @author subei
 * @create 2020-05-16 17:05
 */
public class TCPTest2 {

    /**
     * 这里涉及到的异常，应该使用try-catch-finally处理
     * @throws IOException
     */
    @Test
    public void test() throws IOException {
        Socket socket = new Socket(InetAddress.getByName("127.0.0.1"),9090);
        OutputStream os = socket.getOutputStream();
        FileInputStream fis = new FileInputStream(new File("164.jpg"));
        byte[] buffer = new byte[1024];
        int len;
        while((len = fis.read(buffer)) != -1){
            os.write(buffer,0,len);
        }
        fis.close();
        os.close();
        socket.close();
    }

    /**
     * 这里涉及到的异常，应该使用try-catch-finally处理
     * @throws IOException
     */
    @Test
    public void test2() throws IOException {
        ServerSocket ss = new ServerSocket(9090);
        Socket socket = ss.accept();
        InputStream is = socket.getInputStream();
        FileOutputStream fos = new FileOutputStream(new File("1641.jpg"));
        byte[] buffer = new byte[1024];
        int len;
        while((len = is.read(buffer)) != -1){
            fos.write(buffer,0,len);
        }
        fos.close();
        is.close();
        socket.close();
        ss.close();
    }
}
```

3、例题3

```java
import org.junit.Test;

import java.io.*;
import java.net.InetAddress;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * 实现TCP的网络编程
 * 例题3：从客户端发送文件给服务端，服务端保存到本地。并返回“发送成功”给客户端。
 * 并关闭相应的连接。
 *
 */
public class TCPTest3 {
    /**
     * 这里涉及到的异常，应该使用try-catch-finally处理
     * @throws IOException
     */
    @Test
    public void test() throws IOException {
        Socket socket = new Socket(InetAddress.getByName("127.0.0.1"),9090);
        OutputStream os = socket.getOutputStream();
        FileInputStream fis = new FileInputStream(new File("164.jpg"));
        byte[] buffer = new byte[1024];
        int len;
        while((len = fis.read(buffer)) != -1){
            os.write(buffer,0,len);
        }
        //关闭数据的输出
        socket.shutdownOutput();

        //5.接收来自于服务器端的数据，并显示到控制台上
        InputStream is = socket.getInputStream();
        ByteArrayOutputStream baos = new ByteArrayOutputStream();
        byte[] bufferr = new byte[20];
        int len1;
        while((len1 = is.read(buffer)) != -1){
            baos.write(buffer,0,len1);
        }
        System.out.println(baos.toString());

        fis.close();
        os.close();
        socket.close();
        baos.close();
    }

    /**
     * 这里涉及到的异常，应该使用try-catch-finally处理
     * @throws IOException
     */
    @Test
    public void test2() throws IOException {
        ServerSocket ss = new ServerSocket(9090);
        Socket socket = ss.accept();
        InputStream is = socket.getInputStream();
        FileOutputStream fos = new FileOutputStream(new File("1642.jpg"));
        byte[] buffer = new byte[1024];
        int len;
        while((len = is.read(buffer)) != -1){
            fos.write(buffer,0,len);
        }

        System.out.println("图片传输完成");

        //6.服务器端给予客户端反馈
        OutputStream os = socket.getOutputStream();
        os.write("你好，照片我已收到，风景不错！".getBytes());

        fos.close();
        is.close();
        socket.close();
        ss.close();
        os.close();
    }
}
```

### 6、UDP网络编程

类DatagramSocket和DatagramPacket实现了基于UDP 协议网络程序。
UDP数据报通过数据报套接字DatagramSocket发送和接收，系统不保证UDP数据报一定能够安全送到目的地，也不能确定什么时候可以抵达。
DatagramPacket 对象封装了UDP数据报，在数据报中包含了发送端的IP地址和端口号以及接收端的IP地址和端口号。
UDP协议中每个数据报都给出了完整的地址信息，因此无须建立发送方和接收方的连接。如同发快递包裹一样。
流程：
DatagramSocket与DatagramPacket
建立发送端，接收端
建立数据包
调用Socket的发送、接收方法
关闭Socket
1、发送端与接收端是两个独立的运行程序

```java
import org.junit.Test;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;

/**
 * UDPd协议的网络编程
 */
public class UDPTest {

    //发送端
    @Test
    public void sender() throws IOException {
        DatagramSocket socket = new DatagramSocket();

        String str = "我是UDP发送端";
        byte[] data = str.getBytes();
        InetAddress inet = InetAddress.getLocalHost();
        DatagramPacket packet = new DatagramPacket(data,0,data.length,inet,9090);

        socket.send(packet);
        socket.close();
    }

    //接收端
    @Test
    public void receiver() throws IOException {
        DatagramSocket socket = new DatagramSocket(9090);

        byte[] buffer = new byte[100];
        DatagramPacket packet = new DatagramPacket(buffer,0,buffer.length);

        socket.receive(packet);

        System.out.println(new String(packet.getData(),0,packet.getLength()));

        socket.close();
    }
}
```

### 7、URL编程

#### 7-1、URL的理解与实例化

```java
import java.net.MalformedURLException;
import java.net.URL;

/**
 * URL网络编程
 * 1.URL:统一资源定位符，对应着互联网的某一资源地址
 * 2.格式：
 *  http://127.0.0.1:8080/work/164.jpg?username=subei
 *  协议   主机名    端口号  资源地址           参数列表
 */
public class URLTest {
    public static void main(String[] args) {
        try {
            URL url = new URL("http://127.0.0.1:8080/work/164.jpg?username=subei");

//            public String getProtocol(  )     获取该URL的协议名
            System.out.println(url.getProtocol());
//            public String getHost(  )           获取该URL的主机名
            System.out.println(url.getHost());
//            public String getPort(  )            获取该URL的端口号
            System.out.println(url.getPort());
//            public String getPath(  )           获取该URL的文件路径
            System.out.println(url.getPath());
//            public String getFile(  )             获取该URL的文件名
            System.out.println(url.getFile());
//            public String getQuery(   )        获取该URL的查询名
            System.out.println(url.getQuery());
        } catch (MalformedURLException e) {
            e.printStackTrace();
        }
    }
}
```

#### 7-2、URL网络编程实现Tomcat服务端数据下载

```java
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;

public class URLTest1 {
    public static void main(String[] args) {
        HttpURLConnection urlConnection = null;
        InputStream is = null;
        FileOutputStream fos = null;
        try {
            URL url = new URL("http://127.0.0.1:8080/work/164.jpg");

            urlConnection = (HttpURLConnection) url.openConnection();

            urlConnection.connect();

            is = urlConnection.getInputStream();
            fos = new FileOutputStream("day10\\1643.jpg");

            byte[] buffer = new byte[1024];
            int len;
            while((len = is.read(buffer)) != -1){
                fos.write(buffer,0,len);
            }

            System.out.println("下载完成");
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //关闭资源
            if(is != null){
                try {
                    is.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(fos != null){
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(urlConnection != null){
                urlConnection.disconnect();
            }
        }
    }
}
```

![img](https://img-blog.csdnimg.cn/img_convert/f091c15d075f01e4fb5ec42cf120dfd1.png)

#### 7-3、URI、URL和URN的区别

URI，是uniform resource identifier，统一资源标识符，用来唯一的标识一个资源。而URL是uniform resource locator，统一资源定位符，它是一种具体的URI，即URL可以用来标识一个资源，而且还指明了如何locate这个资源。而URN，uniform resource name，统一资源命名，是通过名字来标识资源，比如mailto:java-net@java.sun.com。也就是说，URI是以一种抽象的，高层次概念定义统一资源标识，而URL和URN则是具体的资源标识的方式。URL和URN都是一种URI。
在Java的URI中，一个URI实例可以代表绝对的，也可以是相对的，只要它符合URI的语法规则。而URL类则不仅符合语义，还包含了定位该资源的信息，因此它不能是相对的。
![img](https://img-blog.csdnimg.cn/img_convert/4356b4b9d4f98d5fd163bbedd4bcc840.png)

## 18、反射与动态代理

### 1、java反射机制概述

Reflection（反射）是被视为动态语言的关键，反射机制允许程序在执行期借助于Reflection API取得任何类的内部信息，并能直接操作任意对象的内部属性及方法。

加载完类之后，在堆内存的方法区中就产生了一个Class类型的对象（一个类只有一个Class对象），这个对象就包含了完整的类的结构信息。我们可以通过这个对象看到类的结构。这个对象就像一面镜子，透过这个镜子看到类的结构，所以，我们形象的称之为：反射。

![img](https://img-blog.csdnimg.cn/img_convert/55a0434a0a4bf6209c9daf4ba81a3808.png)

1、动态语言

是一类在运行时可以改变其结构的语言：例如新的函数、对象、甚至代码可以被引进，已有的函数可以被删除或是其他结构上的变化。通俗点说就是在运行时代码可以根据某些条件改变自身结构。主要动态语言：Object-C、C#、JavaScript、PHP、Python、Erlang。

2、静态语言

与动态语言相对应的，运行时结构不可变的语言就是静态语言。如Java、C、C++。

Java不是动态语言，但Java可以称之为“准动态语言”。即Java有一定的动态性，我们可以利用反射机制、字节码操作获得类似动态语言的特性。Java的动态性让编程的时候更加灵活！
Java反射机制提供的功能
在运行时判断任意一个对象所属的类
在运行时构造任意一个类的对象
在运行时判断任意一个类所具有的成员变量和方法
在运行时获取泛型信息
在运行时调用任意一个对象的成员变量和方法
在运行时处理注解
生成动态代理
反射相关的主要API
java.lang.Class:代表一个类
java.lang.reflect.Method:代表类的方法
java.lang.reflect.Field:代表类的成员变量
java.lang.reflect.Constructor:代表类的构造器
测试类

```java
import org.junit.Test;

public class ReflectionTest {

    //反射之前，对于Person的操作
    @Test
    public void test(){

        //1.创建类的对象
        Person p1 = new Person("jay",21);

        //2.调用对象,调用其内部的属性和方法
        p1.age = 15;
        System.out.println(p1.toString());

        p1.show();

        //在Person类的外部，不可以通过Person类的对象调用其内部私有的结构。
        //比如：name、showNation以及私有的构造器。
        
    }
}
```

Person类

```java
package github;

public class Person {
    private String name;
    public int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    private Person(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    public void show(){
        System.out.println("你好，我是🔔");
    }

    private String showNation(String nation){
        System.out.println("喷子实在太多了！！！" + nation);
        return nation;
    }
}
```

#### 1-1、使用反射，实现同上的操作

```java
import org.junit.Test;

import java.lang.reflect.Constructor;
import java.lang.reflect.Field;
import java.lang.reflect.InvocationTargetException;
import java.lang.reflect.Method;

public class ReflectionTest {

    //反射之后 ，堆与Person的操作
    @Test
    public void test2() throws NoSuchMethodException, IllegalAccessException, InvocationTargetException, InstantiationException, NoSuchFieldException {
        Class clazz = Person.class;
        //1.通过反射，创建Person类的对象
        Constructor cons = clazz.getConstructor(String.class,int.class);
        Object obj = cons.newInstance("Jon",18);
        Person p = (Person) obj;
        System.out.println(p.toString());
        //2.通过反射，调用对象指定的属性和方法
        //调用属性
        Field age = clazz.getDeclaredField("age");
        age.set(p,10);
        System.out.println(p.toString());

        //调用方法
        Method show = clazz.getDeclaredMethod("show");
        show.invoke(p);

    }
}
```

#### 1-2、反射的强大：调用类的私有结构

```java
import org.junit.Test;

import java.lang.reflect.Constructor;
import java.lang.reflect.Field;
import java.lang.reflect.Method;

public class ReflectionTest {
     //反射之后 ，堆与Person的操作
    @Test
    public void test2() throws Exception{
        Class clazz = Person.class;
        //1.通过反射，创建Person类的对象
        Constructor cons = clazz.getConstructor(String.class,int.class);
        Object obj = cons.newInstance("Jon",18);
        Person p = (Person) obj;
        System.out.println(p.toString());
        //2.通过反射，调用对象指定的属性和方法
        //调用属性
        Field age = clazz.getDeclaredField("age");
        age.set(p,10);
        System.out.println(p.toString());

        //调用方法
        Method show = clazz.getDeclaredMethod("show");
        show.invoke(p);

        System.out.println("+++++++++++++++++++++++++");

        //通过反射，是可以调用Person类的私有结构的。比如：私有的构造器、方法、属性
        //调用私有的构造器
        Constructor cons2 = clazz.getDeclaredConstructor(String.class);
        cons2.setAccessible(true);
        Person p1 = (Person) cons2.newInstance("kalo");
        System.out.println(p1);

        //调用私有的属性
        Field name = clazz.getDeclaredField("name");
        name.setAccessible(true);
        name.set(p1,"Taoyao");
        System.out.println(p1);

        //调用私有的方法
        Method showNation = clazz.getDeclaredMethod("LiNin", String.class);
        showNation.setAccessible(true);
        String nation = (String) showNation.invoke(p1,"FaceBook");
        //相当于String nation = p1.showNation("FaceBook")
        System.out.println(nation);
    }

    /**
     * 疑问1：通过直接new的方式或反射的方式都可以调用公共的结构，开发中到底用那个？
     * 建议：直接new的方式。
     * 什么时候会使用：反射的方式。 反射的特征：动态性
     * 疑问2：反射机制与面向对象中的封装性是不是矛盾的？如何看待两个技术？
     * 不矛盾。
     */
}
```

### 2、理解Class类并获取Class实例

#### 2-1、Class类的理解

```java
    /**
     * 关于java.lang.Class类的理解
     * 1.类的加载过程：
     * 程序经过Javac.exe命令后，会生成一个或多个字节码文件(.class结尾)。
     * 接着我们使用java.exe命令对某个字节码文件进行解释运行。相当于将某个字节码文件
     * 加载到内存中。此过程就称为类的加载。加载到内存中的类，我们就称为运行时类，此
     * 运行时类，就作为Class的一个实例。
     *
     * 2.换句话说，Class的实例就对应着一个运行时类。
     */

```

**Class类的常用方法**

![img](https://img-blog.csdnimg.cn/img_convert/941872063b3bec2022dbd43330c8bf27.png)

#### 2-2、获取Class实例的4种方式

```java
import org.junit.Test;

import java.lang.annotation.ElementType;
import java.lang.reflect.Constructor;
import java.lang.reflect.Field;
import java.lang.reflect.Method;

public class ReflectionTest {

    /**
     * 2.换句话说，Class的实例就对应着一个运行时类。
     * 3.加载到内存中的运行时类，会缓存一定的时间。在此时间之内，我们可以通过不同的方式
     * 来获取此运行时类。
     */


    @Test
    public void test3() throws ClassNotFoundException {
        //方式一：
        Class c1 = Person.class;
        System.out.println(c1);

        //方式二：通过运行时类的对象,调用getClass()
        Person p1 = new Person();
        Class c2 = p1.getClass();
        System.out.println(c2);

        //方式三：调用Class的静态方法：forName(String classPath)
        Class c3 = Class.forName("www.gh110.com");
//        c3 = Class.forName("www.123.com");
        System.out.println(c3);

        System.out.println(c1 == c2);
        System.out.println(c1 == c3);

        //方式四：使用类的加载器：ClassLoader  (了解)
        ClassLoader classLoader = ReflectionTest.class.getClassLoader();
        Class c4 = classLoader.loadClass("www.gh110.com");
        System.out.println(c4);

        System.out.println(c1 == c4);
    }
}
```

#### 2-3、Class实例对应的结构的说明

1、哪些类型可以有Class对象？

（1）class：外部类，成员(成员内部类，静态内部类)，局部内部类，匿名内部类
（2）interface：接口
（3）[]：数组
（4）enum：枚举
（5）annotation：注解@interface
（6）primitivetype：基本数据类型
（7）void

```java
import org.junit.Test;
import java.lang.annotation.ElementType;
import java.lang.reflect.Constructor;
import java.lang.reflect.Field;
import java.lang.reflect.Method;

public class ReflectionTest {

    //万事万物皆对象？对象.xxx,File,URL,反射,前端、数据库操作

    /**
     * Class实例可以是哪些结构的说明：
     */
    @Test
    public void test4() {
        Class s1 = Object.class;
        Class s2 = Comparable.class;
        Class s3 = String[].class;
        Class s4 = int[][].class;
        Class s5 = ElementType.class;
        Class s6 = Override.class;
        Class s7 = int.class;
        Class s8 = void.class;
        Class s9 = Class.class;

        int[] a = new int[10];
        int[] b = new int[100];
        Class s10 = a.getClass();
        Class s11 = b.getClass();
        // 只要数组的元素类型与维度一样，就是同一个Class
        System.out.println(s10 == s11);
    }

}
```

### 3、类的加载与classloader的理解

#### 3-1、了解：类的加载过程

当程序主动使用某个类时，如果该类还未被加载到内存中，则系统会通过如下三个步骤来对该类进行初始化。

![img](https://img-blog.csdnimg.cn/img_convert/0f45e6c982ae6c53515790215cfec860.png)

说明

加载：将class文件字节码内容加载到内存中，并将这些静态数据转换成方法区的运行时数据结构，然后生成一个代表这个类的java.lang.Class对象，作为方法区中类数据的访问入口（即引用地址）。所有需要访问和使用类数据只能通过这个Class对象。这个加载的过程需要类加载器参与。
链接：将Java类的二进制代码合并到JVM的运行状态之中的过程。
验证：确保加载的类信息符合JVM规范，例如：以cafe开头，没有安全方面的问题
准备：正式为类变量（static）分配内存并设置类变量默认初始值的阶段，这些内存都将在方法区中进行分配。
解析：虚拟机常量池内的符号引用（常量名）替换为直接引用（地址）的过程。
初始化：
执行类构造器()方法的过程。类构造器()方法是由编译期自动收集类中所有类变量的赋值动作和静态代码块中的语句合并产生的。（类构造器是构造类信息的，不是构造该类对象的构造器）。
当初始化一个类的时候，如果发现其父类还没有进行初始化，则需要先触发其父类的初始化。
虚拟机会保证一个类的()方法在多线程环境中被正确加锁和同步。
![img](https://img-blog.csdnimg.cn/img_convert/677c93ba3d381c6c4437bca902487651.png)

#### 3-2、了解：什么时候会发生类初始化？

类的主动引用（一定会发生类的初始化）
当虚拟机启动，先初始化main方法所在的类
new一个类的对象
调用类的静态成员（除了final常量）和静态方法
使用java.lang.reflect包的方法对类进行反射调用
当初始化一个类，如果其父类没有被初始化，则先会初始化它的父类
类的被动引用（不会发生类的初始化）
当访问一个静态域时，只有真正声明这个域的类才会被初始化
当通过子类引用父类的静态变量，不会导致子类初始化
通过数组定义类引用，不会触发此类的初始化
引用常量不会触发此类的初始化（常量在链接阶段就存入调用类的常量池中了）

#### 3-3、ClassLoader的理解

![img](https://img-blog.csdnimg.cn/img_convert/654a1a2058923c641257caeecb770801.png)

类加载器的作用：
类加载的作用：将class文件字节码内容加载到内存中，并将这些静态数据转换成方法区的运行时数据结构，然后在堆中生成一个代表这个类的java.lang.Class对象，作为方法区中类数据的访问入口。
类缓存：标准的JavaSE类加载器可以按要求查找类，但一旦某个类被加载到类加载器中，它将维持加载（缓存）一段时间。不过JVM垃圾回收机制可以回收这些Class对象。
类加载器作用是用来把类(class)装载进内存的。JVM 规范定义了如下类型的类的加载器。
![img](https://img-blog.csdnimg.cn/img_convert/84f83993bd4897effb32bdd0435505e3.png)

```java
import org.junit.Test;

/**
 * 了解类的加载器
 *
 */
public class ClassLoaderTest {
    
    @Test
    public void test1(){
        //对于自定义类，使用系统类加载器进行加载
        ClassLoader classLoader = ClassLoaderTest.class.getClassLoader();
        System.out.println(classLoader);
        //调用系统类加载器的getParent()：获取扩展类加载器
        ClassLoader classLoader1 = classLoader.getParent();
        System.out.println(classLoader1);
        //调用扩展类加载器的getParent()：无法获取引导类加载器
        //引导类加载器主要负责加载java的核心类库，无法加载自定义类的。
        ClassLoader classLoader2 = classLoader1.getParent();
        System.out.println(classLoader2);

        ClassLoader classLoader3 = String.class.getClassLoader();
        System.out.println(classLoader3);
    }
}
```

#### 3-4、使用ClassLoader加载配置文件

![img](https://img-blog.csdnimg.cn/img_convert/5336c0084c21e5078a7f07abef5433a7.png)

```java
import org.junit.Test;

import java.io.InputStream;
import java.util.Properties;

/**
 * 了解类的加载器
 */
public class ClassLoaderTest {

    /**
     * Properties：用来读取配置文件。
     * @throws Exception
     */
    @Test
    public void test2() throws Exception {
        Properties pros = new Properties();
        //此时的文件默认在当前的module下。
        //读取配置文件的方式一：
//        FileInputStream fis = new FileInputStream("jdbc.properties");
//        pros.load(fis);

        //读取配置文件的方式二：使用ClassLoader
        //配置文件默认识别为：当前module的src下
        ClassLoader classLoader = ClassLoaderTest.class.getClassLoader();
        InputStream is = classLoader.getResourceAsStream("jdbc1.properties");
        pros.load(is);

        String user = pros.getProperty("user");
        String password = pros.getProperty("password");
        System.out.println("user = " + user + ",password = " + password);
    }
}
```

### 4、通过反射，创建运行时类的对象

```java
import org.junit.Test;

/**
 * 通过发射创建对应的运行时类的对象
 */
public class NewInstanceTest {

    @Test
    public void test() throws Exception {
        Class<Person> clazz = Person.class;
        /**
         * newInstance():调用此方法，创建对应的运行时类的对象。内部调用了运行时类的空参的构造器。
         *
         * 要想此方法正常的创建运行时类的对象，要求：
         * 1.运行时类必须提供空参的构造器
         * 2.空参的构造器的访问权限得够。通常，设置为public。
         *
         * 在javabean中要求提供一个public的空参构造器。原因：
         * 1.便于通过反射，创建运行时类的对象
         * 2.便于子类继承此运行时类时，默认调用super()时，保证父类有此构造器
         */
        Person obj = clazz.newInstance();
        System.out.println(obj);
    }
}
```

#### 4-1、举例体会反射的动态性

```java
import org.junit.Test;
import java.util.Random;

/**
 * 通过发射创建对应的运行时类的对象
 */
public class NewInstanceTest {

    @Test
    public void test2(){
        for(int i = 0;i < 100;i++){
            int num = new Random().nextInt(3);//0,1,2
            String classPath = "";
            switch(num){
                case 0:
                    classPath = "java.util.Date";
                    break;
                case 1:
                    classPath = "java.lang.Object";
                    break;
                case 2:
                    classPath = "www.java.Person";
                    break;
            }
            try {
                Object obj = getInstance(classPath);
                System.out.println(obj);
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }

    /**
     * 创建一个指定类的对象。
     * classPath:指定类的全类名
     *
     * @param classPath
     * @return
     * @throws Exception
     */
    public Object getInstance(String classPath) throws Exception {
        Class clazz =  Class.forName(classPath);
        return clazz.newInstance();
    }
}
```

### 5、获取运行时类的完整结构

#### 5-1、提供结构丰富Person类

1、Person类

```java
@MyAnnotation(value="java")
public class Person extends Creature<String> implements Comparable<String>,MyInterface{

    private String name;
    int age;
    public int id;

    public Person() {
    }

    @MyAnnotation(value="C++")
    Person(String name){
        this.name = name;
    }

    private Person(String name,int age){
        this.name = name;
        this.age = age;
    }

    @MyAnnotation
    private String show(String nation){
        System.out.println("我来自" + nation + "星系");
        return nation;
    }

    @Override
    public void info() {
        System.out.println("火星喷子");
    }

    public String display(String play){
        return play;
    }

    @Override
    public int compareTo(String o) {
        return 0;
    }
}

```

2、Creature类

```java
import java.io.Serializable;

public abstract class Creature <T> implements Serializable {
    private char gender;
    public double weight;

    private void breath(){
        System.out.println("太阳系");
    }

    public void eat(){
        System.out.println("银河系");
    }
}
```

3、MyInterface

```java
public interface MyInterface {
    void info();
}
```

4、MyAnnotation

```java
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

import static java.lang.annotation.ElementType.*;

@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})
@Retention(RetentionPolicy.RUNTIME)
public @interface MyAnnotation {
    String value() default "hello world";
}
```

#### 5-2、获取运行时类的属性结构及其内部结构

1、Person类

```java
package github2;

@MyAnnotation(value="java")
public class Person extends Creature<String> implements Comparable<String>,MyInterface{

    private String name;
    int age;
    public int id;

    public Person() {
    }

    @MyAnnotation(value="C++")
    Person(String name){
        this.name = name;
    }

    private Person(String name,int age){
        this.name = name;
        this.age = age;
    }

    @MyAnnotation
    private String show(String nation){
        System.out.println("我来自" + nation + "星系");
        return nation;
    }

    @Override
    public void info() {
        System.out.println("火星喷子");
    }

    public String display(String play){
        return play;
    }

    @Override
    public int compareTo(String o) {
        return 0;
    }
}
```

2、测试类

```java
import github2.Person;
import org.junit.Test;

import java.lang.reflect.Field;
import java.lang.reflect.Modifier;

/**
 * 获取当前运行时类的属性结构
 */
public class FieldTest {

    @Test
    public void test(){
        Class clazz = Person.class;
        //获取属性结构
        //getFields():获取当前运行时类及其父类中声明为public访问权限的属性
        Field[] fields = clazz.getFields();
        for(Field f : fields){
            System.out.println(f);
        }
        System.out.println("++++++++++++++++++");
        //getDeclaredFields():获取当前运行时类中声明的所有属性。（不包含父类中声明的属性）
        Field[] declaredFields = clazz.getDeclaredFields();
        for(Field f : declaredFields){
            System.out.println(f);
        }
    }

    //权限修饰符  数据类型 变量名
    @Test
    public void test2(){
        Class clazz = Person.class;
        Field[] declaredFields = clazz.getDeclaredFields();
        for(Field f : declaredFields){
            //1.权限修饰符
            int modifier = f.getModifiers();
            System.out.print(Modifier.toString(modifier) + "\t");
            System.out.println("+++++++++++++++++++++++++++");
            //2.数据类型
            Class type = f.getType();
            System.out.print(type.getName() + "\t");
            System.out.println("***************************");
            //3.变量名
            String fName = f.getName();
            System.out.print(fName);
        }
    }
}
```

#### 5-3、获取运行时类的方法结构

1、Person类

```java
package github2;

@MyAnnotation(value="java")
public class Person extends Creature<String> implements Comparable<String>,MyInterface{

    private String name;
    int age;
    public int id;

    public Person() {
    }

    @MyAnnotation(value="C++")
    Person(String name){
        this.name = name;
    }

    private Person(String name,int age){
        this.name = name;
        this.age = age;
    }

    @MyAnnotation
    private String show(String nation){
        System.out.println("我来自" + nation + "星系");
        return nation;
    }

    @Override
    public void info() {
        System.out.println("火星喷子");
    }

    public String display(String play){
        return play;
    }

    @Override
    public int compareTo(String o) {
        return 0;
    }
}
```

2、测试类

```java
package github3;

import github2.Person;
import org.junit.Test;

import java.lang.reflect.Method;

/**
 * 获取运行时类的方法结构
 */
public class MythodTest {
    @Test
    public void test(){
        Class clazz = Person.class;
        //getMethods():获取当前运行时类及其所有父类中声明为public权限的方法
        Method[] methods = clazz.getMethods();
        for(Method m : methods){
            System.out.println(m + "****");
        }
        System.out.println("++++++++++++++++++++++++++++");
        //getDeclaredMethods():获取当前运行时类中声明的所有方法。（不包含父类中声明的方法）
        Method[] declaredMethods = clazz.getDeclaredMethods();
        for(Method m : declaredMethods){
            System.out.println(m);
        }
    }
}
```

#### 5-4、获取运行时类的方法的内部结构

1、Person类

```java
@MyAnnotation(value="java")
public class Person extends Creature<String> implements Comparable<String>,MyInterface{

    private String name;
    int age;
    public int id;

    public Person() {
    }

    @MyAnnotation(value="C++")
    Person(String name){
        this.name = name;
    }

    private Person(String name,int age){
        this.name = name;
        this.age = age;
    }

    @MyAnnotation
    private String show(String nation){
        System.out.println("我来自" + nation + "星系");
        return nation;
    }

    @Override
    public void info() {
        System.out.println("火星喷子");
    }

    public String display(String interests,int age) throws Exception{
        return interests + age;
    }

    @Override
    public int compareTo(String o) {
        return 0;
    }
    
    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", id=" + id +
                '}';
    }
}

```

2、测试类

```java
package github3;

import github2.Person;
import org.junit.Test;

import java.lang.annotation.Annotation;
import java.lang.reflect.Method;
import java.lang.reflect.Modifier;

/**
 * 获取运行时类的方法结构
 */
public class MythodTest {

    /**
     * @Xxxx
     * 权限修饰符  返回值类型  方法名(参数类型1 形参名1,...) throws XxxException{}
     */
    @Test
    public void test2() {
        Class clazz = Person.class;
        Method[] declaredMethods = clazz.getDeclaredMethods();
        for (Method m : declaredMethods) {
            //1.获取方法声明的注解
            Annotation[] annos = m.getAnnotations();
            for (Annotation a : annos) {
                System.out.println(a + "KKKK");
            }

            //2.权限修饰符
            System.out.print(Modifier.toString(m.getModifiers()) + "\t");

            //3.返回值类型
            System.out.print(m.getReturnType().getName() + "\t");

            //4.方法名
            System.out.print(m.getName());
            System.out.print("(");
            //5.形参列表
            Class[] pTs = m.getParameterTypes();
            if(!(pTs == null && pTs.length == 0)){
                for(int i = 0;i < pTs.length;i++){
                    if(i == pTs.length - 1){
                        System.out.print(pTs[i].getName() + " args_" + i);
                        break;
                    }
                    System.out.print(pTs[i].getName() + " args_" + i + ",");
                }
            }
            System.out.print(")");

            //6.抛出的异常
            Class[] eTs = m.getExceptionTypes();
            if(eTs.length > 0){
                System.out.print("throws ");
                for(int i = 0;i < eTs.length;i++){
                    if(i == eTs.length - 1){
                        System.out.print(eTs[i].getName());
                        break;
                    }
                    System.out.print(eTs[i].getName() + ",");
                }
            }
            System.out.println("TQA");
        }
    }

}
```

#### 5-5、获取运行时类的构造器结构

```java
package github3;

import github2.Person;
import org.junit.Test;

import java.lang.reflect.Constructor;

public class OtherTest {
    /**
     * 获取构造器的结构
     */
    @Test
    public void test(){
        Class clazz = Person.class;
        //getConstructors():获取当前运行时类中声明为public的构造器
        Constructor[] constructors = clazz.getConstructors();
        for(Constructor c : constructors){
            System.out.println(c);
        }
        System.out.println("************************");
        //getDeclaredConstructors():获取当前运行时类中声明的所有的构造器
        Constructor[] declaredConstructors = clazz.getDeclaredConstructors();
        for(Constructor c : declaredConstructors){
            System.out.println(c);
        }
    }
}
```

#### 5-6、获取运行时类的父类及父类的泛型

```java
package github3;

import github2.Person;
import org.junit.Test;

import java.lang.reflect.Constructor;
import java.lang.reflect.ParameterizedType;
import java.lang.reflect.Type;

public class OtherTest {
    /**
     * 获取运行时类的父类
     */
    @Test
    public void test2(){
        Class clazz = Person.class;
        Class superclass = clazz.getSuperclass();
        System.out.println(superclass);
    }

    /**
     * 获取运行时类的带泛型的父类
     */
    @Test
    public void test3(){
        Class clazz = Person.class;
        Type genericSuperclass = clazz.getGenericSuperclass();
        System.out.println(genericSuperclass);
    }

    /**
     * 获取运行时类的带泛型的父类的泛型
     */
    @Test
    public void test4(){
        Class clazz = Person.class;
        Type genericSuperclass = clazz.getGenericSuperclass();
        ParameterizedType paramType = (ParameterizedType) genericSuperclass;
        //获取泛型类型
        Type[] actualTypeArguments = paramType.getActualTypeArguments();
//        System.out.println(actualTypeArguments[0].getTypeName());
        System.out.println(((Class)actualTypeArguments[0]).getName());
    }
}
```

#### 5-7、获取运行时类的接口、所在包、注解等

```java
package github3;

import github2.Person;
import org.junit.Test;

import java.lang.annotation.Annotation;
import java.lang.reflect.Constructor;
import java.lang.reflect.ParameterizedType;
import java.lang.reflect.Type;

public class OtherTest {
    /**
     * 获取运行时类实现的接口
     */
    @Test
    public void test5(){
        Class clazz = Person.class;

        Class[] interfaces = clazz.getInterfaces();
        for(Class c : interfaces){
            System.out.println(c);
        }
        System.out.println("++++++++++++++++++++++");
       
        //获取运行时类的父类实现的接口
        Class[] interfaces1 = clazz.getSuperclass().getInterfaces();
        for(Class c : interfaces1){
            System.out.println(c);
        }
    }

    /**
     * 获取运行时类所在的包
     */
    @Test
    public void test6(){
        Class clazz = Person.class;
        Package pack = clazz.getPackage();
        System.out.println(pack);
    }

    /**
     * 获取运行时类声明的注解
     */
    @Test
    public void test7(){
        Class clazz = Person.class;
        Annotation[] annotations = clazz.getAnnotations();
        for(Annotation annos : annotations){
            System.out.println(annos);
        }
    }
}
```

### 6、调用运行时类的指定结构

#### 6-1、调用运行时类中的指定属性

1、Person类

```java
package github2;

@MyAnnotation(value="java")
public class Person extends Creature<String> implements Comparable<String>,MyInterface{

    private String name;
    int age;
    public int id;

    public Person() {
    }

    @MyAnnotation(value="C++")
    Person(String name){
        this.name = name;
    }

    private Person(String name,int age){
        this.name = name;
        this.age = age;
    }

    @MyAnnotation
    private String show(String nation){
        System.out.println("我来自" + nation + "星系");
        return nation;
    }

    @Override
    public void info() {
        System.out.println("火星喷子");
    }

    public String display(String interests,int age) throws Exception{
        return interests + age;
    }

    @Override
    public int compareTo(String o) {
        return 0;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", id=" + id +
                '}';
    }
}
```

2、测试类

```java
package github3;

import github2.Person;
import org.junit.Test;

import java.lang.reflect.Field;

/**
 * 调用运行时类中指定的结构：属性、方法、构造器
 */
public class ReflectionTest {
    /**
     * 不需要掌握
     */
    @Test
    public void testField() throws Exception {
        Class clazz = Person.class;

        //创建运行时类的对象
        Person p = (Person) clazz.newInstance();

        //获取指定的属性：要求运行时类中属性声明为public
        //通常不采用此方法
        Field id = clazz.getField("id");

        //设置当前属性的值
        //set():参数1：指明设置哪个对象的属性   参数2：将此属性值设置为多少
        id.set(p,1001);

        //获取当前属性的值
        //get():参数1：获取哪个对象的当前属性值
        int pId = (int) id.get(p);
        System.out.println(pId);
    }

    /**
     * 如何操作运行时类中的指定的属性 -- 需要掌握
     */
    @Test
    public void testField1() throws Exception {
        Class clazz = Person.class;

        //创建运行时类的对象
        Person p = (Person) clazz.newInstance();

        //1. getDeclaredField(String fieldName):获取运行时类中指定变量名的属性
        Field name = clazz.getDeclaredField("name");

        //2.保证当前属性是可访问的
        name.setAccessible(true);

        //3.获取、设置指定对象的此属性值
        name.set(p,"Jam");
        System.out.println(name.get(p));
    }
}
```

#### 6-2、调用运行时类中的指定方法

```java
package github3;

import github2.Person;
import org.junit.Test;

import java.lang.reflect.Constructor;
import java.lang.reflect.Field;
import java.lang.reflect.Method;

/**
 * 调用运行时类中指定的结构：属性、方法、构造器
 */
public class ReflectionTest {
    /**
     * 如何操作运行时类中的指定的方法 -- 需要掌握
     */
    @Test
    public void testMethod() throws Exception {
        Class clazz = Person.class;
        //创建运行时类的对象
        Person p = (Person) clazz.newInstance();

        //1.获取指定的某个方法
        //getDeclaredMethod():参数1 ：指明获取的方法的名称  参数2：指明获取的方法的形参列表
        Method show = clazz.getDeclaredMethod("show", String.class);

        //2.保证当前方法是可访问的
        show.setAccessible(true);

        //3.调用方法的invoke():参数1：方法的调用者  参数2：给方法形参赋值的实参
        //invoke()的返回值即为对应类中调用的方法的返回值。
        Object returnValue = show.invoke(p,"CCA"); //String nation = p.show("CCA");
        System.out.println(returnValue);

        System.out.println("+++++++++如何调用静态方法+++++++++++");

//    private static void showDesc()

        Method showDesc = clazz.getDeclaredMethod("showDown");
        showDesc.setAccessible(true);
        //如果调用的运行时类中的方法没有返回值，则此invoke()返回null
//    Object returnVal = showDesc.invoke(null);
        Object returnVal = showDesc.invoke(Person.class);
        System.out.println(returnVal);//null
    }
}
```

#### 6-3、调用运行时类中的指定构造器

```java
import github2.Person;
import org.junit.Test;

import java.lang.reflect.Constructor;
import java.lang.reflect.Field;
import java.lang.reflect.Method;

/**
 * 调用运行时类中指定的结构：属性、方法、构造器
 */
public class ReflectionTest {

    /**
     * 如何调用运行时类中的指定的构造器
     */
    @Test
    public void testConstructor() throws Exception {
        Class clazz = Person.class;

        //private Person(String name)
        //1.获取指定的构造器
        //getDeclaredConstructor():参数：指明构造器的参数列表
        Constructor constructor = clazz.getDeclaredConstructor(String.class);

        //2.保证此构造器是可访问的
        constructor.setAccessible(true);

        //3.调用此构造器创建运行时类的对象
        Person per = (Person) constructor.newInstance("Tom");
        System.out.println(per);
    }
}
```

### 7、反射的应用：动态代理

#### 7-1、代理模式与动态代理

代理设计模式的原理:

使用一个代理将对象包装起来, 然后用该代理对象取代原始对象。任何对原始对象的调用都要通过代理。代理对象决定是否以及何时将方法调用转到原始对象上。

之前为大家讲解过代理机制的操作，属于静态代理，特征是代理类和目标对象的类都是在编译期间确定下来，不利于程序的扩展。同时，每一个代理类只能为一个接口服务，这样一来程序开发中必然产生过多的代理。最好可以通过一个代理类完成全部的代理功能。

动态代理是指客户通过代理类来调用其它对象的方法，并且是在程序运行时根据需要动态创建目标类的代理对象。

动态代理使用场合:

调试
远程方法调用
动态代理相比于静态代理的优点：

抽象角色中（接口）声明的所有方法都被转移到调用处理器一个集中的方法中处理，这样，我们可以更加灵活和统一的处理众多的方法。

#### 7-2、静态代理举例

```java
/**
 * 静态代理举例
 *
 * 特点：代理类和被代理类在编译期间，就确定下来了。
 */
interface ClothFactory{
    void produceCloth();
}

//代理类
class PersonTest implements ClothFactory{
    private ClothFactory factory;//用被代理类对象进行实例化

    public PersonTest(ClothFactory factory){
        this.factory = factory;
    }

    @Override
    public void produceCloth() {
        System.out.println("造纸厂开始做一些准备工作");

        factory.produceCloth();

        System.out.println("造纸厂做一些后续收尾工作");
    }
}

//被代理类
class NeckTest implements ClothFactory{

    @Override
    public void produceCloth() {
        System.out.println("造纸厂计划生产一批卫生纸");
    }
}

public class StaticProxyTest {
    public static void main(String[] args) {
        //创建被代理类的对象
        ClothFactory word = new NeckTest();

        //创建代理类的对象
        ClothFactory proxyPaperFactory = new PersonTest(word);

        proxyPaperFactory.produceCloth();
    }
}
```

#### 7-3、动态代理举例

```java
import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;

/**
 * 动态代理举例
 */
interface Moon{
    String getBelief();

    void Object(String Moon);
}

//被代理类
class Venus implements Moon{


    @Override
    public String getBelief() {
        return "The only planet in the solar system without a magnetic field.";
    }

    @Override
    public void Object(String MinMoon) {
        System.out.println("周围有很多" + MinMoon);
    }
}

/**
 * 要想实现动态代理，需要解决的问题？
 * 问题一：如何根据加载到内存中的被代理类，动态的创建一个代理类及其对象。
 * 问题二：当通过代理类的对象调用方法a时，如何动态的去调用被代理类中的同名方法a。
 */
class BookTest{

    //调用此方法，返回一个代理类的对象。解决问题一
    public static Object getProxyInstance(Object obj){//obj:被代理类的对象
        DeskTest hander = new DeskTest();
        hander.bind(obj);
        return Proxy.newProxyInstance(obj.getClass().getClassLoader(),obj.getClass().getInterfaces(),hander);
    }
}

class DeskTest implements InvocationHandler{

    private Object obj;//需要使用被代理类的对象进行赋值

    public void bind(Object obj){
        this.obj = obj;
    }

    //当我们通过代理类的对象，调用方法a时，就会自动的调用如下的方法：invoke()
    //将被代理类要执行的方法a的功能就声明在invoke()中
    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {

        //method:即为代理类对象调用的方法，此方法也就作为了被代理类对象要调用的方法
        //obj:被代理类的对象
        Object returnValue = method.invoke(obj,args);

        //上述方法的返回值就作为当前类中的invoke()的返回值。
        return returnValue;
    }
}

public class ProductTest {
    public static void main(String[] args) {
        Venus superMan = new Venus();
        //NumTest:代理类的对象
        Moon NumTest = (Moon) BookTest.getProxyInstance(superMan);
        //当通过代理类对象调用方法时，会自动的调用被代理类中同名的方法
        String belief = NumTest.getBelief();
        System.out.println(belief);
        NumTest.Object("四川大巴山");

        System.out.println("+++++++++++++++++++");

        NeckTest fox = new NeckTest();
        ClothFactory ween = (ClothFactory) BookTest.getProxyInstance(fox);

        ween.produceCloth();
    }
}

```

#### 7-4、AOP与动态代理的举例

前面介绍的Proxy和InvocationHandler，很难看出这种动态代理的优势，下面介绍一种更实用的动态代理机制

![img](https://img-blog.csdnimg.cn/img_convert/350951efa715010e9f67c825a8c2644c.png)

![img](https://img-blog.csdnimg.cn/img_convert/a930618a732073ac70b4310cec4ce67c.png)

改进后的说明：代码段1、代码段2、代码段3和深色代码段分离开了，但代码段1、2、3又和一个特定的方法A耦合了！最理想的效果是：代码块1、2、3既可以执行方法A，又无须在程序中以硬编码的方式直接调用深色代码的方法。
使用Proxy生成一个动态代理时，往往并不会凭空产生一个动态代理，这样没有太大的意义。通常都是为指定的目标对象生成动态代理
这种动态代理在AOP中被称为AOP代理，AOP代理可代替目标对象，AOP代理包含了目标对象的全部方法。但AOP代理中的方法与目标对象的方法存在差异：AOP代理里的方法可以在执行目标方法之前、之后插入一些通用处理。
![img](https://img-blog.csdnimg.cn/img_convert/416543ffb785658f84566304c824bf80.png)

举例

```java
/**
 * 静态代理举例
 *
 * 特点：代理类和被代理类在编译期间，就确定下来了。
 */
interface ClothFactory{
    void produceCloth();
}

//代理类
class PersonTest implements ClothFactory{
    private ClothFactory factory;//用被代理类对象进行实例化

    public PersonTest(ClothFactory factory){
        this.factory = factory;
    }

    @Override
    public void produceCloth() {
        System.out.println("造纸厂开始做一些准备工作");

        factory.produceCloth();

        System.out.println("造纸厂做一些后续收尾工作");
    }
}

//被代理类
class NeckTest implements ClothFactory{

    @Override
    public void produceCloth() {
        System.out.println("造纸厂计划生产一批卫生纸");
    }
}

public class StaticProxyTest {
    public static void main(String[] args) {
        //创建被代理类的对象
        ClothFactory word = new NeckTest();

        //创建代理类的对象
        ClothFactory proxyPaperFactory = new PersonTest(word);

        proxyPaperFactory.produceCloth();
    }
}
```

测试类

```java
package github4;

import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;

/**
 * 动态代理举例
 */
interface Moon{
    String getBelief();

    void Object(String Moon);
}

//被代理类
class Venus implements Moon{


    @Override
    public String getBelief() {
        return "The only planet in the solar system without a magnetic field.";
    }

    @Override
    public void Object(String MinMoon) {
        System.out.println("周围有很多" + MinMoon);
    }
}

/**
 * 要想实现动态代理，需要解决的问题？
 * 问题一：如何根据加载到内存中的被代理类，动态的创建一个代理类及其对象。
 * 问题二：当通过代理类的对象调用方法a时，如何动态的去调用被代理类中的同名方法a。
 */
class BookTest{

    //调用此方法，返回一个代理类的对象。解决问题一
    public static Object getProxyInstance(Object obj){//obj:被代理类的对象
        DeskTest hander = new DeskTest();
        hander.bind(obj);
        return Proxy.newProxyInstance(obj.getClass().getClassLoader(),obj.getClass().getInterfaces(),hander);
    }
}

class DeskTest implements InvocationHandler{

    private Object obj;//需要使用被代理类的对象进行赋值

    public void bind(Object obj){
        this.obj = obj;
    }

    //当我们通过代理类的对象，调用方法a时，就会自动的调用如下的方法：invoke()
    //将被代理类要执行的方法a的功能就声明在invoke()中
    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        SunTest util = new SunTest();
        util.Star();

        //method:即为代理类对象调用的方法，此方法也就作为了被代理类对象要调用的方法
        //obj:被代理类的对象
        Object returnValue = method.invoke(obj,args);

        util.Star2();

        //上述方法的返回值就作为当前类中的invoke()的返回值。
        return returnValue;
    }
}

class SunTest{

    public void Star(){
        System.out.println("====================通用方法一====================");

    }

    public void Star2(){
        System.out.println("====================通用方法二====================");
    }

}

public class ProductTest {
    public static void main(String[] args) {
        Venus superMan = new Venus();
        //NumTest:代理类的对象
        Moon NumTest = (Moon) BookTest.getProxyInstance(superMan);
        //当通过代理类对象调用方法时，会自动的调用被代理类中同名的方法
        String belief = NumTest.getBelief();
        System.out.println(belief);
        NumTest.Object("四川大巴山");

        System.out.println("+++++++++++++++++++");

        NeckTest fox = new NeckTest();
        ClothFactory ween = (ClothFactory) BookTest.getProxyInstance(fox);

        ween.produceCloth();
    }
}

```

## 19、Java8新特性

### 1、Java8概述

- Java 8 (又称为jdk 1.8) 是Java 语言开发的一个主要版本。
- Java 8 是oracle公司于2014年3月发布，可以看成是自Java 5 以来最具革命性的版本。Java 8为Java语言、编译器、类库、开发工具与JVM带来了大量新特性。

![img](https://img-blog.csdnimg.cn/img_convert/873337fa3d817235541f830b76bfc87e.png)

### 2、Java8新特性的好处

- 速度更快
- 代码更少(增加了新的语法：Lambda 表达式)
- 强大的Stream API
- 便于并行
- 最大化减少空指针异常：Optional
- Nashorn引擎，允许在JVM上运行JS应用

### 3、并行流与串行流

并行流就是把一个内容分成多个数据块，并用不同的线程分别处理每个数据块的流。相比较串行的流，并行的流可以很大程度上提高程序的执行效率。

Java 8 中将并行进行了优化，我们可以很容易的对数据进行并行操作。Stream API 可以声明性地通过parallel() 与sequential() 在并行流与顺序流之间进行切换。

### 4、Lambda表达式

Lambda 是一个匿名函数，我们可以把Lambda [表达式](https://so.csdn.net/so/search?q=表达式&spm=1001.2101.3001.7020)理解为是一段可以传递的代码（将代码像数据一样进行传递）。使用它可以写出更简洁、更灵活的代码。作为一种更紧凑的代码风格，使Java的语言表达能力得到了提升。

#### 4-1、Lambda表达式使用举例

```java
import org.junit.Test;

import java.util.Comparator;

/**
 * Lambda表达式的使用举例
 */
public class LambdaTest {
    @Test
    public void test(){
        Runnable r1 = new Runnable() {
            @Override
            public void run() {
                System.out.println("长安欢迎您");
            }
        };
        r1.run();

        System.out.println("+++++++++++++++++++++++++|");

        Runnable r2 = () -> System.out.println("长安欢迎您");

        r2.run();
    }

    @Test
    public void test2(){
        Comparator<Integer> c1 = new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return Integer.compare(o1,o2);
            }
        };
        int compare1 = c1.compare(8,16);
        System.out.println(compare1);

        System.out.println("+++++++++++++++++++++++");

        //Lambda表达式的写法
        Comparator<Integer> c2 = (o1,o2) -> Integer.compare(o1,o2);

        int compare2 = c2.compare(28,35);
        System.out.println(compare2);

        System.out.println("+++++++++++++++++++++++++++");
        //方法引用
        Comparator<Integer> c3 = Integer :: compare;

        int compare3 = c3.compare(28,35);
        System.out.println(compare3);
    }
}
```

#### 4-2、Lambda表达式语法的使用1

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.function.Consumer;

/**
 * Lambda表达式的使用
 *
 * 1.举例： (o1,o2) -> Integer.compare(o1,o2);
 * 2.格式：
 *      -> :lambda操作符 或 箭头操作符
 *      ->左边：lambda形参列表 （其实就是接口中的抽象方法的形参列表）
 *      ->右边：lambda体 （其实就是重写的抽象方法的方法体）
 *
 * 3.Lambda表达式的使用：（分为6种情况介绍）
 */
public class LambdaTest1 {

    //语法格式一：无参，无返回值
    @Test
    public void test(){
        Runnable r1 = new Runnable() {
            @Override
            public void run() {
                System.out.println("长安欢迎您");
            }
        };
        r1.run();

        System.out.println("+++++++++++++++++++++++++|");

        Runnable r2 = () -> System.out.println("长安欢迎您");

        r2.run();
    }

    //语法格式二：Lambda 需要一个参数，但是没有返回值。
    @Test
    public void test2(){
        Consumer<String> con = new Consumer<String>() {
            @Override
            public void accept(String s) {
                System.out.println(s);
            }
        };
        con.accept("善与恶的区别是什么？");

        System.out.println("+++++++++++++++++++");

        Consumer<String> c1 = (String s) -> {
            System.out.println(s);
        };
        c1.accept("先天人性无善恶,后天人性有善恶。");
    }

    //语法格式三：数据类型可以省略，因为可由编译器推断得出，称为“类型推断”
    @Test
    public void test3(){
        Consumer<String> c1 = (String s) -> {
            System.out.println(s);
        };
        c1.accept("先天人性无善恶,后天人性有善恶。");

        System.out.println("---------------------");

        Consumer<String> c2 = (s) -> {
            System.out.println(s);
        };
        c2.accept("如果没有邪恶的话我们怎么会知道人世间的那些善良呢？");
    }

    @Test
    public void test4(){
        ArrayList<String> list = new ArrayList<>();//类型推断

        int[] arr = {1,2,3};//类型推断
    }
}
```

#### 4-3、Lambda表达式语法的使用2

```java
import org.junit.Test;

import java.util.Comparator;
import java.util.function.Consumer;

/**
 * Lambda表达式的使用
 *
 * 1.举例： (o1,o2) -> Integer.compare(o1,o2);
 * 2.格式：
 *      -> :lambda操作符 或 箭头操作符
 *      ->左边：lambda形参列表 （其实就是接口中的抽象方法的形参列表）
 *      ->右边：lambda体 （其实就是重写的抽象方法的方法体）
 *
 * 3.Lambda表达式的使用：（分为6种情况介绍）
 *
 *    总结：
 *    ->左边：lambda形参列表的参数类型可以省略(类型推断)；如果lambda形参列表只有一个参数，其一对()也可以省略
 *    ->右边：lambda体应该使用一对{}包裹；如果lambda体只有一条执行语句（可能是return语句），省略这一对{}和return关键字
 */
public class LambdaTest1 {

    //语法格式四：Lambda若只需要一个参数时，参数的小括号可以省略
    @Test
    public void test5(){
        Consumer<String> c1 = (s) -> {
            System.out.println(s);
        };
        c1.accept("先天人性无善恶,后天人性有善恶。");

        System.out.println("---------------------");

        Consumer<String> c2 = s -> {
            System.out.println(s);
        };
        c2.accept("如果没有邪恶的话我们怎么会知道人世间的那些善良呢？");
    }

    //语法格式五：Lambda需要两个或以上的参数，多条执行语句，并且可以有返回值
    @Test
    public void test6(){
        Comparator<Integer> c1 = new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                System.out.println(o1);
                System.out.println(o2);
                return o1.compareTo(o2);
            }
        };
        System.out.println(c1.compare(15,23));

        System.out.println("\\\\\\\\\\\\\\\\\\\\\\\\\\");

        Comparator<Integer> com2 = (o1,o2) -> {
            System.out.println(o1);
            System.out.println(o2);
            return o1.compareTo(o2);
        };
        System.out.println(com2.compare(16,8));
    }

    //语法格式六：当Lambda体只有一条语句时，return与大括号若有，都可以省略
    @Test
    public void test7(){
        Comparator<Integer> c1 = (o1,o2) -> {
            return o1.compareTo(o2);
        };

        System.out.println(c1.compare(16,8));

        System.out.println("\\\\\\\\\\\\\\\\\\\\\\\\\\");

        Comparator<Integer> c2 = (o1,o2) -> o1.compareTo(o2);

        System.out.println(c2.compare(17,24));
    }

    @Test
    public void test8(){
        Consumer<String> c1 = s -> {
            System.out.println(s);
        };
        c1.accept("先天人性无善恶,后天人性有善恶。");

        System.out.println("---------------------");

        Consumer<String> c2 = s -> System.out.println(s);

        c2.accept("如果没有邪恶的话我们怎么会知道人世间的那些善良呢？");
    }
}
```

### 5、函数式(Functional)接口

#### 5-1、函数式接口的介绍

```java
/*
 * 4.Lambda表达式的本质：作为函数式接口的实例
 *
 * 5. 如果一个接口中，只声明了一个抽象方法，则此接口就称为函数式接口。我们可以在一个接口上使用 @FunctionalInterface 注解，
 *   这样做可以检查它是否是一个函数式接口。
 *
 */

/**
 * 自定义函数式接口
 */
public interface MyInterFace {

    void method();

//    void method2();
    
}
```

在java.util.function包下定义了Java 8 的丰富的函数式接口
Java从诞生日起就是一直倡导“一切皆对象”，在Java里面面向对象(OOP)编程是一切。但是随着python、scala等语言的兴起和新技术的挑战，Java不得不做出调整以便支持更加广泛的技术要求，也即java不但可以支持OOP还可以支持OOF（面向函数编程）
在函数式编程语言当中，函数被当做一等公民对待。在将函数作为一等公民的编程语言中，Lambda表达式的类型是函数。但是在Java8中，有所不同。在Java8中，Lambda表达式是对象，而不是函数，它们必须依附于一类特别的对象类型——函数式接口。
简单的说，在Java8中，Lambda表达式就是一个函数式接口的实例。这就是Lambda表达式和函数式接口的关系。也就是说，只要一个对象是函数式接口的实例，那么该对象就可以用Lambda表达式来表示。
所以以前用匿名实现类表示的现在都可以用Lambda表达式来写。

#### 5-2、Java内置的函数式接口介绍及使用举例


BiPredicate<T,U>	T,U	boolean	包含方法为：booleantest(Tt,Uu)
ToIntFunction	T	int	计算int值的函数
ToLongFunction	T	long	计算long值的函数
ToDoubleFunction	T	double	计算double值的函数
IntFunction	int	R	参数为int类型的函数
LongFunction	long	R	参数为long类型的函数
DoubleFunction	double	R	参数为double类型的函数

| 函数式接口                         | 参数类型 | 返回类型 | 用途                                                         |
| ---------------------------------- | -------- | -------- | ------------------------------------------------------------ |
| `Consumer` 消费型接口              | T        | void     | 对类型为T的对象应用操作，包含方法：void accept(T t)          |
| `Supplier` 供给型接口              | 无       | T        | 返回类型为T的对象，包含方法：T get()                         |
| `Function<T, R>`函数型接口         | T        | R        | 对类型为T的对象应用操作，并返回结果。结果是R类型的对象。包含方法：R apply(T t) |
| `Predicate`断定型接口              | T        | boolean  | 确定类型为T的对象是否满足某约束，并返回boolean 值。包含方法：boolean test(T t) |
| `BiFunction<T,U,R>`                | T, U     | R        | 对类型为T,U参数应用操作，返回R类型的结果。包含方法为：Rapply(T t,U u); |
| `UnaryOperator`(Function子接口)    | T        | T        | 对类型为T的对象进行一元运算，并返回T类型的结果。包含方法为：Tapply(T t); |
| `BinaryOperator`(BiFunction子接口) | T,T      | T        | 对类型为T的对象进行二元运算，并返回T类型的结果。包含方法为：Tapply(T t1,T t2); |
| `BiConsumer<T,U>`                  | T,U      | void     | 对类型为T,U参数应用操作。包含方法为：`voidaccept(Tt,Uu)`     |
| `BiPredicate<T,U>`                 | T,U      | boolean  | 包含方法为：`booleantest(Tt,Uu)`                             |
| `ToIntFunction`                    | T        | int      | 计算`int`值的函数                                            |
| `ToLongFunction`                   | T        | long     | 计算`long`值的函数                                           |
| `ToDoubleFunction`                 | T        | double   | 计算`double`值的函数                                         |
| `IntFunction`                      | int      | R        | 参数为`int`类型的函数                                        |
| `LongFunction`                     | long     | R        | 参数为`long`类型的函数                                       |
| `DoubleFunction`                   | double   | R        | 参数为`double`类型的函数                                     |

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.function.Consumer;
import java.util.function.Predicate;

/**
 * java内置的4大核心函数式接口
 *
 * 消费型接口 Consumer<T>     void accept(T t)
 * 供给型接口 Supplier<T>     T get()
 * 函数型接口 Function<T,R>   R apply(T t)
 * 断定型接口 Predicate<T>    boolean test(T t)
 */
public class LambdaTest2 {

    public void happyTime(double money, Consumer<Double> con) {
        con.accept(money);
    }

    @Test
    public void test(){
        happyTime(30, new Consumer<Double>() {
            @Override
            public void accept(Double aDouble) {
                System.out.println("熬夜太累了，点个外卖，价格为：" + aDouble);
            }
        });
        System.out.println("+++++++++++++++++++++++++");

        //Lambda表达式写法
        happyTime(20,money -> System.out.println("熬夜太累了，吃口麻辣烫，价格为：" + money));
    }

    //根据给定的规则，过滤集合中的字符串。此规则由Predicate的方法决定
    public List<String> filterString(List<String> list, Predicate<String> pre){

        ArrayList<String> filterList = new ArrayList<>();
        for(String s : list){
            if(pre.test(s)){
                filterList.add(s);
            }
        }
        return filterList;

    }

    @Test
    public void test2(){
        List<String> list = Arrays.asList("长安","上京","江南","渝州","凉州","兖州");

        List<String> filterStrs = filterString(list, new Predicate<String>() {
            @Override
            public boolean test(String s) {
                return s.contains("州");
            }
        });

        System.out.println(filterStrs);

        List<String> filterStrs1 = filterString(list,s -> s.contains("州"));
        System.out.println(filterStrs1);
    }
}
```

### 6、方法引用与构造器引用

当要传递给Lambda体的操作，已经有实现的方法了，可以使用方法引用！
方法引用可以看做是Lambda表达式深层次的表达。换句话说，方法引用就是Lambda表达式，也就是函数式接口的一个实例，通过方法的名字来指向一个方法，可以认为是Lambda表达式的一个语法糖。
要求：实现接口的抽象方法的参数列表和返回值类型，必须与方法引用的方法的参数列表和返回值类型保持一致！
格式：使用操作符“::” 将类(或对象) 与方法名分隔开来。
如下三种主要使用情况：
对象::实例方法名
类::静态方法名
类::实例方法名

#### 6-1、方法引用的使用情况1

1、Employee类

```java
public class Employee {

	private int id;
	private String name;
	private int age;
	private double salary;

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public double getSalary() {
		return salary;
	}

	public void setSalary(double salary) {
		this.salary = salary;
	}

	public Employee() {
		System.out.println("Employee().....");
	}

	public Employee(int id) {
		this.id = id;
		System.out.println("Employee(int id).....");
	}

	public Employee(int id, String name) {
		this.id = id;
		this.name = name;
	}

	public Employee(int id, String name, int age, double salary) {

		this.id = id;
		this.name = name;
		this.age = age;
		this.salary = salary;
	}

	@Override
	public String toString() {
		return "Employee{" + "id=" + id + ", name='" + name + '\'' + ", age=" + age + ", salary=" + salary + '}';
	}

	@Override
	public boolean equals(Object o) {
		if (this == o)
			return true;
		if (o == null || getClass() != o.getClass())
			return false;

		Employee employee = (Employee) o;

		if (id != employee.id)
			return false;
		if (age != employee.age)
			return false;
		if (Double.compare(employee.salary, salary) != 0)
			return false;
		return name != null ? name.equals(employee.name) : employee.name == null;
	}

	@Override
	public int hashCode() {
		int result;
		long temp;
		result = id;
		result = 31 * result + (name != null ? name.hashCode() : 0);
		result = 31 * result + age;
		temp = Double.doubleToLongBits(salary);
		result = 31 * result + (int) (temp ^ (temp >>> 32));
		return result;
	}
}
```

2、测试类

```java
import org.junit.Test;

import java.io.PrintStream;
import java.util.Comparator;
import java.util.function.BiPredicate;
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Supplier;

/**
 * 方法引用的使用
 *
 * 1.使用情境：当要传递给Lambda体的操作，已经有实现的方法了，可以使用方法引用！
 *
 * 2.方法引用，本质上就是Lambda表达式，而Lambda表达式作为函数式接口的实例。所以
 *   方法引用，也是函数式接口的实例。
 *
 * 3. 使用格式：  类(或对象) :: 方法名
 *
 * 4. 具体分为如下的三种情况：
 *    情况1     对象 :: 非静态方法
 *    情况2     类 :: 静态方法
 *
 *    情况3     类 :: 非静态方法
 *
 * 5. 方法引用使用的要求：要求接口中的抽象方法的形参列表和返回值类型与方法引用的方法的
 *    形参列表和返回值类型相同！（针对于情况1和情况2）
 */
public class MethodRefTest {
    
    // 情况一：对象 :: 实例方法
    //Consumer中的void accept(T t)
    //PrintStream中的void println(T t)
    @Test
    public void test() {
        Consumer<String> c1 = str -> System.out.println(str);
        c1.accept("兖州");

        System.out.println("+++++++++++++");
        PrintStream ps = System.out;
        Consumer<String> c2 = ps::println;
        c2.accept("xian");
    }

    //Supplier中的T get()
    //Employee中的String getName()
    @Test
    public void test2() {
        Employee emp = new Employee(004,"Nice",19,4200);

        Supplier<String> sk1 = () -> emp.getName();
        System.out.println(sk1.get());

        System.out.println("*******************");
        Supplier<String> sk2 = emp::getName;
        System.out.println(sk2.get());
    }
}
```

#### 6-2、方法引用的使用情况2

1、Employee类——同上

2、测试类

```java
import org.junit.Test;
import java.util.Comparator;
import java.util.function.Function;

public class MethodRefTest {

    // 情况二：类 :: 静态方法
    //Comparator中的int compare(T t1,T t2)
    //Integer中的int compare(T t1,T t2)
    @Test
    public void test3() {
        Comparator<Integer> com1 = (t1, t2) -> Integer.compare(t1,t2);
        System.out.println(com1.compare(21,20));

        System.out.println("+++++++++++++++");

        Comparator<Integer> com2 = Integer::compare;
        System.out.println(com2.compare(15,7));
    }

    //Function中的R apply(T t)
    //Math中的Long round(Double d)
    @Test
    public void test4() {
        Function<Double,Long> func = new Function<Double, Long>() {
            @Override
            public Long apply(Double d) {
                return Math.round(d);
            }
        };

        System.out.println("++++++++++++++++++");

        Function<Double,Long> func1 = d -> Math.round(d);
        System.out.println(func1.apply(14.1));

        System.out.println("++++++++++++++++++");

        Function<Double,Long> func2 = Math::round;
        System.out.println(func2.apply(17.4));
    }
}
```

#### 6-3、方法引用的使用情况3

1、Employee类——同上

2、测试类

```java
import org.junit.Test;

import java.util.Comparator;
import java.util.function.BiPredicate;
import java.util.function.Function;

public class MethodRefTest {

    // 情况三：类 :: 实例方法  (有难度)
    // Comparator中的int comapre(T t1,T t2)
    // String中的int t1.compareTo(t2)
    @Test
    public void test5() {
        Comparator<String> com1 = (s1,s2) -> s1.compareTo(s2);
        System.out.println(com1.compare("abc","abd"));

        System.out.println("++++++++++++++++");

        Comparator<String> com2 = String :: compareTo;
        System.out.println(com2.compare("abd","abm"));
    }

    //BiPredicate中的boolean test(T t1, T t2);
    //String中的boolean t1.equals(t2)
    @Test
    public void test6() {
        BiPredicate<String,String> pre1 = (s1, s2) -> s1.equals(s2);
        System.out.println(pre1.test("MON","MON"));

        System.out.println("++++++++++++++++++++");
        
        BiPredicate<String,String> pre2 = String :: equals;
        System.out.println(pre2.test("MON","MON"));
    }

    // Function中的R apply(T t)
    // Employee中的String getName();
    @Test
    public void test7() {
        Employee employee = new Employee(007, "Ton", 21, 8000);

        Function<Employee,String> func1 = e -> e.getName();
        System.out.println(func1.apply(employee));

        System.out.println("++++++++++++++++++++++++");

        Function<Employee,String> f2 = Employee::getName;
        System.out.println(f2.apply(employee));
    }
}
```

#### 6-4、构造器引用与数组引用的使用

格式：ClassName::new

与函数式接口相结合，自动与函数式接口中方法兼容。

可以把构造器引用赋值给定义的方法，要求构造器参数列表要与接口中抽象方法的参数列表一致！且方法的返回值即为构造器对应类的对象。

1、Employee类——同上

2、测试类

```java
import org.junit.Test;

import java.util.Arrays;
import java.util.function.BiFunction;
import java.util.function.Function;
import java.util.function.Supplier;

/**
 * 一、构造器引用
 *      和方法引用类似，函数式接口的抽象方法的形参列表和构造器的形参列表一致。
 *      抽象方法的返回值类型即为构造器所属的类的类型
 *
 * 二、数组引用
 *     可以把数组看做是一个特殊的类，则写法与构造器引用一致。 
 */
public class MethodRefTest {

    //构造器引用
    //Supplier中的T get()
    //Employee的空参构造器：Employee()
    @Test
    public void test() {
        Supplier<Employee> sup = new Supplier<Employee>() {
            @Override
            public Employee get() {
                return new Employee();
            }
        };
        System.out.println("+++++++++++++++++++");

        Supplier<Employee> sk1 = () -> new Employee();
        System.out.println(sk1.get());

        System.out.println("+++++++++++++++++++");

        Supplier<Employee> sk2 = Employee::new;
        System.out.println(sk2.get());
    }

    //Function中的R apply(T t)
    @Test
    public void test2() {
        Function<Integer, Employee> f1 = id -> new Employee(id);
        Employee employee = f1.apply(7793);
        System.out.println(employee);

        System.out.println("+++++++++++++++++++");

        Function<Integer, Employee> f2 = Employee::new;
        Employee employee1 = f2.apply(4545);
        System.out.println(employee1);
    }

    //BiFunction中的R apply(T t,U u)
    @Test
    public void test3() {
        BiFunction<Integer, String, Employee> f1 = (id, name) -> new Employee(id, name);
        System.out.println(f1.apply(2513, "Fruk"));

        System.out.println("*******************");

        BiFunction<Integer, String, Employee> f2 = Employee::new;
        System.out.println(f2.apply(9526, "Bon"));
    }

    //数组引用
    //Function中的R apply(T t)
    @Test
    public void test4() {
        Function<Integer, String[]> f1 = length -> new String[length];
        String[] arr1 = f1.apply(7);
        System.out.println(Arrays.toString(arr1));

        System.out.println("+++++++++++++++++++");

        Function<Integer, String[]> f2 = String[]::new;
        String[] arr2 = f2.apply(9);
        System.out.println(Arrays.toString(arr2));
    }
}
```

### 7、强大的StreamAPI

#### 7-1、Stream API的概述

Java8中有两大最为重要的改变。第一个是Lambda 表达式；另外一个则是Stream API。
Stream API ( java.util.stream)把真正的函数式编程风格引入到Java中。这是目前为止对Java类库最好的补充，因为Stream API可以极大提供Java程序员的生产力，让程序员写出高效率、干净、简洁的代码。
Stream 是Java8 中处理集合的关键抽象概念，它可以指定你希望对集合进行的操作，可以执行非常复杂的查找、过滤和映射数据等操作。使用Stream API 对集合数据进行操作，就类似于使用SQL 执行的数据库查询。也可以使用Stream API 来并行执行操作。简言之，Stream API 提供了一种高效且易于使用的处理数据的方式。
为什么要使用Stream API
实际开发中，项目中多数数据源都来自于Mysql，Oracle等。但现在数据源可以更多了，有MongDB，Radis等，而这些NoSQL的数据就需要Java层面去处理。
Stream 和Collection 集合的区别：Collection 是一种静态的内存数据结构，而Stream 是有关计算的。前者是主要面向内存，存储在内存中，后者主要是面向CPU，通过CPU 实现计算。

```java
/**
 * 1.Stream关注的是对数据的运算，与CPU打交道
 *   集合关注的是数据的存储，与内存打交道
 *
 * 2.
 * ①Stream 自己不会存储元素。
 * ②Stream 不会改变源对象。相反，他们会返回一个持有结果的新Stream。
 * ③Stream 操作是延迟执行的。这意味着他们会等到需要结果的时候才执行
 *
 * 3.Stream 执行流程
 * ① Stream的实例化
 * ② 一系列的中间操作（过滤、映射、...)
 * ③ 终止操作
 *
 * 4.说明：
 * 4.1 一个中间操作链，对数据源的数据进行处理
 * 4.2 一旦执行终止操作，就执行中间操作链，并产生结果。之后，不会再被使用
 */
```

![img](https://img-blog.csdnimg.cn/img_convert/c4f4c62e55b8182fa7c99cd15a0d7de0.png)

#### 7-2、Stream的实例化

1、EmployeeData类

```java
import java.util.ArrayList;
import java.util.List;
/**
 * 提供用于测试的数据
 */
public class EmployeeData {
	
	public static List<Employee> getEmployees(){
		List<Employee> list = new ArrayList<>();
		
		list.add(new Employee(1001, "马化腾", 34, 6000.38));
		list.add(new Employee(1002, "马云", 12, 9876.12));
		list.add(new Employee(1003, "刘强东", 33, 3000.82));
		list.add(new Employee(1004, "雷军", 26, 7657.37));
		list.add(new Employee(1005, "李彦宏", 65, 5555.32));
		list.add(new Employee(1006, "比尔盖茨", 42, 9500.43));
		list.add(new Employee(1007, "任正非", 26, 4333.32));
		list.add(new Employee(1008, "扎克伯格", 35, 2500.32));
		
		return list;
	}	
}
```

2、Employee类

```java
public class Employee {

	private int id;
	private String name;
	private int age;
	private double salary;

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public double getSalary() {
		return salary;
	}

	public void setSalary(double salary) {
		this.salary = salary;
	}

	public Employee() {
		System.out.println("Employee().....");
	}

	public Employee(int id) {
		this.id = id;
		System.out.println("Employee(int id).....");
	}

	public Employee(int id, String name) {
		this.id = id;
		this.name = name;
	}

	public Employee(int id, String name, int age, double salary) {

		this.id = id;
		this.name = name;
		this.age = age;
		this.salary = salary;
	}

	@Override
	public String toString() {
		return "Employee{" + "id=" + id + ", name='" + name + '\'' + ", age=" + age + ", salary=" + salary + '}';
	}

	@Override
	public boolean equals(Object o) {
		if (this == o)
			return true;
		if (o == null || getClass() != o.getClass())
			return false;

		Employee employee = (Employee) o;

		if (id != employee.id)
			return false;
		if (age != employee.age)
			return false;
		if (Double.compare(employee.salary, salary) != 0)
			return false;
		return name != null ? name.equals(employee.name) : employee.name == null;
	}

	@Override
	public int hashCode() {
		int result;
		long temp;
		result = id;
		result = 31 * result + (name != null ? name.hashCode() : 0);
		result = 31 * result + age;
		temp = Double.doubleToLongBits(salary);
		result = 31 * result + (int) (temp ^ (temp >>> 32));
		return result;
	}
}
```

3、测试类

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.Arrays;
import java.util.List;
import java.util.stream.IntStream;
import java.util.stream.Stream;

/**
 * 测试Stream的实例化
 */
public class StreamAPITest {

    //创建 Stream方式一：通过集合
    @Test
    public void test(){
        List<Employee> employees = EmployeeData.getEmployees();

//        default Stream<E> stream() : 返回一个顺序流
        Stream<Employee> stream = employees.stream();

//        default Stream<E> parallelStream() : 返回一个并行流
        Stream<Employee> parallelStream = employees.parallelStream();
    }

    //创建 Stream方式二：通过数组
    @Test
    public void test2(){
        int[] arr = new int[]{1,2,3,4,5,6};
        //调用Arrays类的static <T> Stream<T> stream(T[] array): 返回一个流
        IntStream stream = Arrays.stream(arr);

        Employee e1 = new Employee(1001,"Hom");
        Employee e2 = new Employee(1002,"Nut");
        Employee[] arr1 = new Employee[]{e1,e2};

        Stream<Employee> stream1 = Arrays.stream(arr1);
    }
    //创建 Stream方式三：通过Stream的of()
    @Test
    public void test3(){
        Stream<Integer> stream = Stream.of(1, 2, 3, 4, 5, 6);
    }

    //创建 Stream方式四：创建无限流
    @Test
    public void test4(){
//      迭代
//      public static<T> Stream<T> iterate(final T seed, final UnaryOperator<T> f)
        //遍历前10个偶数
        Stream.iterate(0, t -> t + 2).limit(10).forEach(System.out::println);

//      生成
//      public static<T> Stream<T> generate(Supplier<T> s)
        Stream.generate(Math::random).limit(10).forEach(System.out::println);
    }
}
```

#### 7-3、Stream的中间操作：筛选与切片

多个中间操作可以连接起来形成一个流水线，除非流水线上触发终止操作，否则中间操作不会执行任何的处理！而在终止操作时一次性全部处理，称为“惰性求值”。

| 方法                  | 描述                                                         |
| --------------------- | ------------------------------------------------------------ |
| `filter(Predicate p)` | 接收Lambda ，从流中排除某些元素                              |
| `distinct()`          | 筛选，通过流所生成元素的hashCode() 和equals() 去除重复元素   |
| `limit(long maxSize)` | 截断流，使其元素不超过给定数量                               |
| `skip(long n)`        | 跳过元素，返回一个扔掉了前n 个元素的流。若流中元素不足n 个，则返回一个空流。与`limit(n)`互补 |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.List;
import java.util.stream.Stream;

/**
 * 测试Stream的中间操作
 */
public class StreamAPITest2 {

    //1-筛选与切片
    @Test
    public void test(){
        List<Employee> list = EmployeeData.getEmployees();
//        filter(Predicate p)——接收 Lambda ， 从流中排除某些元素。
        Stream<Employee> stream = list.stream();
        //练习：查询员工表中薪资大于7000的员工信息
        stream.filter(e -> e.getSalary() > 7000).forEach(System.out::println);

        System.out.println("+++++++++++++++++++++++");
//        limit(n)——截断流，使其元素不超过给定数量。
        list.stream().limit(3).forEach(System.out::println);
        System.out.println("+++++++++++++++++++++++");

//        skip(n) —— 跳过元素，返回一个扔掉了前 n 个元素的流。若流中元素不足 n 个，则返回一个空流。与 limit(n) 互补
        list.stream().skip(3).forEach(System.out::println);

        System.out.println("+++++++++++++++++++++++");
//        distinct()——筛选，通过流所生成元素的 hashCode() 和 equals() 去除重复元素

        list.add(new Employee(1013,"李飞",42,8500));
        list.add(new Employee(1013,"李飞",41,8200));
        list.add(new Employee(1013,"李飞",28,6000));
        list.add(new Employee(1013,"李飞",39,7800));
        list.add(new Employee(1013,"李飞",40,8000));

//        System.out.println(list);

        list.stream().distinct().forEach(System.out::println);
    }
}
```

#### 7-4、Stream的中间操作：映射

| 方法                              | 描述                                                         |
| --------------------------------- | ------------------------------------------------------------ |
| `map(Function f)`                 | 接收一个函数作为参数，该函数会被应用到每个元素上，并将其映射成一个新的元素。 |
| `mapToDouble(ToDoubleFunction f)` | 接收一个函数作为参数，该函数会被应用到每个元素上，产生一个新的DoubleStream。 |
| `mapToInt(ToIntFunction f)`       | 接收一个函数作为参数，该函数会被应用到每个元素上，产生一个新的IntStream。 |
| `mapToLong(ToLongFunction f)`     | 接收一个函数作为参数，该函数会被应用到每个元素上，产生一个新的LongStream。 |
| `flatMap(Function f)`             | 接收一个函数作为参数，将流中的每个值都换成另一个流，然后把所有流连接成一个流 |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Stream;

/**
 * 测试Stream的中间操作
 */
public class StreamAPITest2 {

    //2-映射
    @Test
    public void test2(){
//        map(Function f)——接收一个函数作为参数，将元素转换成其他形式或提取信息，该函数会被应用到每个元素上，并将其映射成一个新的元素。
        List<String> list = Arrays.asList("aa", "bb", "cc", "dd");
        list.stream().map(str -> str.toUpperCase()).forEach(System.out::println);

//        练习1：获取员工姓名长度大于3的员工的姓名。
        List<Employee> employees = EmployeeData.getEmployees();
        Stream<String> namesStream = employees.stream().map(Employee::getName);
        namesStream.filter(name -> name.length() > 3).forEach(System.out::println);
        System.out.println();

        //练习2：
        Stream<Stream<Character>> streamStream = list.stream().map(StreamAPITest2::fromStringToStream);
        
        streamStream.forEach(s ->{
            s.forEach(System.out::println);
        });
        System.out.println("++++++++++++++++++++++");
//        flatMap(Function f)——接收一个函数作为参数，将流中的每个值都换成另一个流，然后把所有流连接成一个流。
        Stream<Character> characterStream = list.stream().flatMap(StreamAPITest2::fromStringToStream);
        
        characterStream.forEach(System.out::println);
    }

    //将字符串中的多个字符构成的集合转换为对应的Stream的实例
    public static Stream<Character> fromStringToStream(String str){//aa
        ArrayList<Character> list = new ArrayList<>();
        for(Character c : str.toCharArray()){
            list.add(c);
        }
        return list.stream();
    }

    @Test
    public void test3(){
        ArrayList list1 = new ArrayList();
        list1.add(25);
        list1.add(33);
        list1.add(14);

        ArrayList list2 = new ArrayList();
        list2.add(51);
        list2.add(23);
        list2.add(61);

//        list1.add(list2);
        list1.addAll(list2);
        System.out.println(list1);
    }
}、
```

#### 7-5、Stream的中间操作：排序

| 方法                     | 描述                               |
| ------------------------ | ---------------------------------- |
| `sorted()`               | 产生一个新流，其中按自然顺序排序   |
| `sorted(Comparator com)` | 产生一个新流，其中按比较器顺序排序 |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Stream;

/**
 * 测试Stream的中间操作
 */
public class StreamAPITest2 {

    //3-排序
    @Test
    public void test4(){
//        sorted()——自然排序
        List<Integer> list = Arrays.asList(25,45,36,12,85,64,72,-95,4);
        list.stream().sorted().forEach(System.out::println);
        //抛异常，原因:Employee没有实现Comparable接口
//        List<Employee> employees = EmployeeData.getEmployees();
//        employees.stream().sorted().forEach(System.out::println);


//        sorted(Comparator com)——定制排序

        List<Employee> employees = EmployeeData.getEmployees();
        employees.stream().sorted( (e1,e2) -> {

            int ageValue = Integer.compare(e1.getAge(),e2.getAge());
            if(ageValue != 0){
                return ageValue;
            }else{
                return -Double.compare(e1.getSalary(),e2.getSalary());
            }

        }).forEach(System.out::println);
    }
}
```

#### 7-6、Stream的终止操作：匹配与查找

- 终端操作会从流的流水线生成结果。其结果可以是任何不是流的值，例如：List、Integer，甚至是void 。
- 流进行了终止操作后，不能再次使用。

| 方法                     | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| `allMatch(Predicate p)`  | 检查是否匹配所有元素                                         |
| `anyMatch(Predicate p)`  | 检查是否至少匹配一个元素                                     |
| `noneMatch(Predicate p)` | 检查是否没有匹配所有元素                                     |
| `findFirst()`            | 返回第一个元素                                               |
| `findAny()`              | 返回当前流中的任意元素                                       |
| `count()`                | 返回流中元素总数                                             |
| `max(Comparator c)`      | 返回流中最大值                                               |
| `min(Comparator c)`      | 返回流中最小值                                               |
| `forEach(Consumer c)`    | 内部迭代(使用Collection 接口需要用户去做迭代，称为外部迭代。相反，Stream API 使用内部迭代——它帮你把迭代做了) |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.List;
import java.util.Optional;
import java.util.stream.Stream;

public class StreamAPITest3 {
    //1-匹配与查找
    @Test
    public void test(){
        List<Employee> employees = EmployeeData.getEmployees();

//        allMatch(Predicate p)——检查是否匹配所有元素。
//          练习：是否所有的员工的年龄都大于18
        boolean allMatch = employees.stream().allMatch(e -> e.getAge() > 23);
        System.out.println(allMatch);

//        anyMatch(Predicate p)——检查是否至少匹配一个元素。
//         练习：是否存在员工的工资大于 10000
        boolean anyMatch = employees.stream().anyMatch(e -> e.getSalary() > 9000);
        System.out.println(anyMatch);

//        noneMatch(Predicate p)——检查是否没有匹配的元素。
//          练习：是否存在员工姓“马”
        boolean noneMatch = employees.stream().noneMatch(e -> e.getName().startsWith("马"));
        System.out.println(noneMatch);
        
//        findFirst——返回第一个元素
        Optional<Employee> employee = employees.stream().findFirst();
        System.out.println(employee);
        
//        findAny——返回当前流中的任意元素
        Optional<Employee> employee1 = employees.parallelStream().findAny();
        System.out.println(employee1);
    }

    @Test
    public void test2(){
        List<Employee> employees = EmployeeData.getEmployees();
        
        // count——返回流中元素的总个数
        long count = employees.stream().filter(e -> e.getSalary() > 4500).count();
        System.out.println(count);
        
//        max(Comparator c)——返回流中最大值
//        练习：返回最高的工资：
        Stream<Double> salaryStream = employees.stream().map(e -> e.getSalary());
        Optional<Double> maxSalary = salaryStream.max(Double::compare);
        System.out.println(maxSalary);
        
//        min(Comparator c)——返回流中最小值
//        练习：返回最低工资的员工
        Optional<Employee> employee = employees.stream().min((e1, e2) -> Double.compare(e1.getSalary(), e2.getSalary()));
        System.out.println(employee);
        System.out.println();
        
//        forEach(Consumer c)——内部迭代
        employees.stream().forEach(System.out::println);

        //使用集合的遍历操作
        employees.forEach(System.out::println);
    }
}
```

#### 7-7、Stream的终止操作：归约

| 方法                                                         | 描述                                          |
| ------------------------------------------------------------ | --------------------------------------------- |
| `reduce(T iden, BinaryOperator b)`                           | 可以将流中元素反复结合起来，得到一个值。返回T |
| `reduce(BinaryOperator b)`可以将流中元素反复结合起来，得到一个值。返回Optional |                                               |

备注：map 和reduce 的连接通常称为map-reduce 模式，因Google 用它来进行网络搜索而出名。

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.Arrays;
import java.util.List;
import java.util.Optional;
import java.util.stream.Stream;

public class StreamAPITest3 {

    //2-归约
    @Test
    public void test3(){
//        reduce(T identity, BinaryOperator)——可以将流中元素反复结合起来，得到一个值。返回 T
//        练习1：计算1-10的自然数的和
        List<Integer> list = Arrays.asList(72,25,32,34,43,56,81,15,29,71);
        Integer sum = list.stream().reduce(0, Integer::sum);
        System.out.println(sum);

//        reduce(BinaryOperator) ——可以将流中元素反复结合起来，得到一个值。返回 Optional<T>
//        练习2：计算公司所有员工工资的总和
        List<Employee> employees = EmployeeData.getEmployees();
        Stream<Double> salaryStream = employees.stream().map(Employee::getSalary);
//        Optional<Double> sumMoney = salaryStream.reduce(Double::sum);
        Optional<Double> sumMoney = salaryStream.reduce((d1,d2) -> d1 + d2);
        System.out.println(sumMoney.get());
    }
}
```

#### 7-8、Stream的终止操作：收集

| 方法                   | 描述                                                         |
| ---------------------- | ------------------------------------------------------------ |
| `collect(Collector c)` | 将流转换为其他形式。接收一个Collector接口的实现，用于给Stream中元素做汇总的方法 |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.Arrays;
import java.util.List;
import java.util.Optional;
import java.util.Set;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class StreamAPITest3 {

    //3-收集
    @Test
    public void test4() {
//        collect(Collector c)——将流转换为其他形式。接收一个 Collector接口的实现，用于给Stream中元素做汇总的方法
//        练习1：查找工资大于6000的员工，结果返回为一个List或Set

        List<Employee> employees = EmployeeData.getEmployees();
        List<Employee> employeeList = employees.stream().filter(e -> e.getSalary() > 6000).collect(Collectors.toList());

        employeeList.forEach(System.out::println);
        
        System.out.println("++++++++++++++++++");
        
        Set<Employee> employeeSet = employees.stream().filter(e -> e.getSalary() > 6000).collect(Collectors.toSet());

        employeeSet.forEach(System.out::println);
    }
}
```

`Collector` 接口中方法的实现决定了如何对流执行收集的操作(如收集到`List、Set、Map`)。

`Collectors`实用类提供了很多静态方法，可以方便地创建常见收集器实例，具体方法与实例如下表：

![img](https://img-blog.csdnimg.cn/img_convert/bd29b1fd138291421630d2d542675cf7.png)

![img](https://img-blog.csdnimg.cn/img_convert/0d4c3b7ce571549e8940d8c9e8192df1.png)

### 8、Optional类

#### 8-1、Optional类的介绍

到目前为止，臭名昭著的空指针异常是导致Java应用程序失败的最常见原因。以前，为了解决空指针异常，Google公司著名的Guava项目引入了Optional类，Guava通过使用检查空值的方式来防止代码污染，它鼓励程序员写更干净的代码。受到Google Guava的启发，Optional类已经成为Java 8类库的一部分。

Optional 类(java.util.Optional) 是一个容器类，它可以保存类型T的值，代表这个值存在。或者仅仅保存null，表示这个值不存在。原来用null 表示一个值不存在，现在Optional 可以更好的表达这个概念。并且可以避免空指针异常。
Optional类的Javadoc描述如下：这是一个可以为null的容器对象。如果值存在则isPresent()方法会返回true，调用get()方法会返回该对象。
Optional提供很多有用的方法，这样我们就不用显式进行空值检测。
创建Optional类对象的方法：
Optional.of(T t): 创建一个Optional 实例，t必须非空；
Optional.empty() : 创建一个空的Optional 实例
Optional.ofNullable(T t)：t可以为null
判断Optional容器中是否包含对象：
boolean isPresent() : 判断是否包含对象
void ifPresent(Consumer<? super T> consumer) ：如果有值，就执行Consumer接口的实现代码，并且该值会作为参数传给它。
获取Optional容器的对象：
T get(): 如果调用对象包含值，返回该值，否则抛异常
T orElse(T other) ：如果有值则将其返回，否则返回指定的other对象。
T orElseGet(Supplier<? extends T> other) ：如果有值则将其返回，否则返回由Supplier接口实现提供的对象。
T orElseThrow(Supplier<? extends X> exceptionSupplier) ：如果有值则将其返回，否则抛出由Supplier接口实现提供的异常。
1、Boy类

```java
public class Boy {
    private Girl girl;

    public Boy() {
    }

    public Boy(Girl girl) {
        this.girl = girl;
    }

    public Girl getGirl() {
        return girl;
    }

    public void setGirl(Girl girl) {
        this.girl = girl;
    }

    @Override
    public String toString() {
        return "Boy{" +
                "girl=" + girl +
                '}';
    }
}
```

2、Girl类

```java
public class Girl {
    private String name;

    public Girl() {
    }

    public Girl(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Girl{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

3、测试类

```java
import org.junit.Test;
import java.util.Optional;

/**
 * Optional类：为了在程序中避免出现空指针异常而创建的。
 *
 * 常用的方法：ofNullable(T t)
 *           orElse(T t)
 */
public class OptionalTest {
    /**
     * Optional.of(T t) : 创建一个 Optional 实例，t必须非空；
     * Optional.empty() : 创建一个空的 Optional 实例
     * Optional.ofNullable(T t)：t可以为null
     */
    @Test
    public void test(){
        Girl girl = new Girl();
//        girl = null;
        //of(T t):保证t是非空的
        Optional<Girl> optionalGirl = Optional.of(girl);
    }

    @Test
    public void test2(){
        Girl girl = new Girl();
//        girl = null;
        //ofNullable(T t)：t可以为null
        Optional<Girl> optionalGirl = Optional.ofNullable(girl);
        System.out.println(optionalGirl);
        //orElse(T t1):如果单前的Optional内部封装的t是非空的，则返回内部的t.
        //如果内部的t是空的，则返回orElse()方法中的参数t1.
        Girl girl1 = optionalGirl.orElse(new Girl(""));
        System.out.println(girl1);
    }
}
```

#### 8-2、Optional类应用举例

1、测试类

```java
import org.junit.Test;
import java.util.Optional;

/**
 * Optional类：为了在程序中避免出现空指针异常而创建的。
 *
 * 常用的方法：ofNullable(T t)
 *           orElse(T t)
 */
public class OptionalTest {

    @Test
    public void test3(){
        Boy boy = new Boy();
        boy = null;
        String girlName = getGirlName(boy);
        System.out.println(girlName);
    }

    private String getGirlName(Boy boy) {
        return boy.getGirl().getName();
    }

    //优化以后的getGirlName():
    public String getGirlName1(Boy boy){
        if(boy != null){
            Girl girl = boy.getGirl();
            if(girl != null){
                return girl.getName();
            }
        }
        return null;
    }

    @Test
    public void test4(){
        Boy boy = new Boy();
        boy = null;
        String girlName = getGirlName1(boy);
        System.out.println(girlName);
    }

    //使用Optional类的getGirlName():
    public String getGirlName2(Boy boy){

        Optional<Boy> boyOptional = Optional.ofNullable(boy);
        //此时的boy1一定非空
        Boy boy1 = boyOptional.orElse(new Boy(new Girl("朱淑贞")));

        Girl girl = boy1.getGirl();

        Optional<Girl> girlOptional = Optional.ofNullable(girl);
        //girl1一定非空
        Girl girl1 = girlOptional.orElse(new Girl("阿青"));

        return girl1.getName();
    }

    @Test
    public void test5(){
        Boy boy = null;
        boy = new Boy();
        boy = new Boy(new Girl("李清照"));
        String girlName = getGirlName2(boy);
        System.out.println(girlName);
    }
}

```

