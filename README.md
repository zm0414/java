### 1.Java语言特点

1. Java语言是面向对象的OOP
2. Java语言是跨平台性的
3. Java是解释型的 .class装载到jvm

| .java  |   源文件   |
| :----: | :--------: |
| javac  |    编译    |
| .class | 字节码文件 |
|  java  |    结果    |

1. 源文件的基本组成是class，应用程序的执行入口是main
2. Java语言区分大小写
3. **一个源文件最多只能一个public**，每一个class编译后对应一个.class

### 2.基础知识

1. 转义字符\t   \r  \n
2. javadoc标签  @author @version @see @param
3. Java代码规范 

![image-20210719151529509](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210719151529509.png)

```
//行尾风格
public static void main(String[] args){
	System.out.println("hello");
}
//次行风格
public static void main(String[] args)
{
	System.out.println("hello");
}
```

1. dos指令  相对路径 绝对路径

   | cd .. |    上一级目录    |
   | :---: | :--------------: |
   | cd \  |      根目录      |
   |  md   |       新建       |
   |  rd   |       删除       |
   | tree  | 查看所有子集目录 |
   |  cls  |       清屏       |
   | echo  |     输入内容     |
   | move  |    剪切 移动     |

#### 1.变量

三个基本要素（类型 名称 值）

```
int i = 10;
```

1. 变量先声明，后使用

#### 2.数据类型

![image-20210719155426553](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210719155426553.png)

#### 3.字符串

单个字符 char 'a' '\t' '周' 96=>输出96代表的字符a

​	byte short char三者运算时，首先转换为int类型。

多个字符 string->基本数据类型  <u>parse</u> 

```
String a = '123';
int num1 = Integer.parseInt(a);
double num2 = Double.parseDouble(a);
...
```

#### 4.运算符Relationoperator Logicloperator Assignoperator

```
a % b = a - (int)a / b * b 
&& 短路与 如果第一个条件为false，第二个不做判断
int result = a > b ? a++ : b++;
if (a > b){
	a++;
}else {
	b++;
}
```

### 5.标识符规则和规范

![image-20210719174308921](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210719174308921.png)

![image-20210719174541319](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210719174541319.png)

### 6.输入

```
  import java.util.Scanner;
  public class Input{
  	public static void main(String[] args){
  		Scanner myscanner = new Scanner(System.in);
  		System.out.println("输入姓名：");
  		String name = myscanner.next(); //接受用户输入的字符串
  		System.out.println("name" + name);
  	}
  }
  nextInt 接受用户输入int
  	int age = myscanner.nextInt();
  nextDouble 接受用户输入double
  	double sal = myscanner.nextDouble();
  next 接受用户输入char
  	char sex = myscanner.next().charAt(0);
  ```

### 7.**进制**

![image-20210719180313179](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210719180313179.png)

```
int n1 = 0b1010;
int n2 = 1010;
int n3 = 01010;
int n4 = ox10101;
```

> **二进制转为八进制**11010101-> 011 010 101 ->3 2 5 -> 0325

​	将二进制每三位为一组，转成对应的八进制数

> **二进制转为十六进制**11010101 -> 1101 0101 -> 13 5 -> 0xD5

​	将二进制每四位一组，转成对应的十六进制数

> **进制转成十进制**

$$
0b1101 -> 1x2^3 + 1x2^2+1x2^0 -> 8+4+1 = 13
$$

$$
23->2 x 8^1 + 3 x 8^0->2x8+3x1 = 19
$$

$$
0xD2 ->13x16^1+2x16^0 ->208+2=210
$$

![image-20210719184208569](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210719184208569.png)

计算机运算都是以**补码**方式进行运算

我们查看是看原码
### 8.位运算Bitoperator

```
public static void main(String[] args){
	1.先得到2的补码----》
	  2的原码00000000 00000000 00000000 00000010
	  2的补码00000000 00000000 00000000 00000010
	2.得到3的补码 ----》
	  3的原码00000000 00000000 00000000 00000011
	  3的补码00000000 00000000 00000000 00000011
	3.进行按位与 全为1就是1   ----》得到补码码
	        00000000 00000000 00000000 0000010
	4.转换为原码 正数三码合一 
	        0000000 00000000 00000000 00000010=2
	System.out.println(2&3);
	
	System.out.println(~-2);   
	1.-2的原码10000000 00000000 00000000 00000010
	2.-2的反码11111111 11111111 11111111 11111101
	3.-2的补码11111111 11111111 11111111 11111110
	4.~ 操作  00000000 00000000 00000000 00000001
	5.计算原码 00000000 00000000 00000000 00000001=1
	
	System.out.println(~2);
	1.2的补码 00000000 00000000 00000000 00000010
	2.~ 操作  11111111 11111111 11111111 11111101
	3.计算反码 11111111 11111111 11111111 11111100
	4.计算原码 10000000 00000000 00000000 00000011=-3
}
```

![image-20210719193707629](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210719193707629.png)

```
int a = 1 >> 2 ----- 00000001 =>00000000 1 / 2 / 2
int b = 1 << 2 ----- 00000010 =>00001000 1 * 2 * 2
15 >> 2 ------------ 15 / 2 / 2 =>7 / 2 =>3
```

### 9.顺序控制结构

多分支可以没有else

```
if (){
	代码块;
	代码块;
	......
}
import java.util.Scanner;
class test{
	public static void main(String[] args){
		Scanner scanner = new Scanner(System.in);
		System.out.println("输入分数");
		int score = scanner.nextInt();
		if (score > 90){
			System.out.println("优秀");
		} else if(score > 80){
			System.out.println("良好");
		} else if(score > 70){
			System.out.println("及格");
		} else {
			System.out.println("不及格");
		}
	}
}
```

```
//双分支
if (){
	...
}
else {
	...
}

//多分支
if (){
	...
}else if(){
	...
	}if(){
	
	}
	...
	else {

}
```

```
import java.util.*;
public static void main(Strings[] args){
	Scanner scanner = new Scanner(System.in);
	double a = scanner.nextDouble();
	double b = scanner.nextDouble();
	if (a > 10.0 && b < 20.0){
		System.out.println(a+b);
	}
}

class exercise02{
	public static void main(Strings[] args){
		Scanner scanner = new Scanner(System.in);
		int a = scanner.nextInt();
		int b = scanner.nextInt();
		int c = a + b;
		if (c % 3 == 0 && c % 5 ==0){
			System.out.println("ok");
		}else {
			System.out.println("no");
		}
	}
}

class exercise03{
	public static void main(Strings[] args){
		Scanner scanner = new Scanner(System.in);
		int year = scanner.nextInt();
		if (( year % 4 == 0 && year % 100 != 0) || year % 400 == 0){
			System.out.println("yes");
		}else {
			System.out.println("no");
		}
	}
}
```

```
if (){
	if (){
		...
	}else {
		...
	}
}else {
	...
}
```

```
switch(表达式){
	case 常量1:
		...
		break;
	case 常量2:
		...
		break;
	...
	default:
		...
}
```

switch 表达式数据类型和case后的常量类型一致，或者能自动转换类型

**switch(表达式)表达式返回值必须是byte,short,,int,char,enum,String**

![image-20210720005158614](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210720005158614.png)

### 10.循环控制for while do..while

```
for (循环变量初始化;循环条件;循环变量迭代){
	循环操作;
}

循环条件初始化
for (;循环条件;){
	循环操作；
	循环变量迭代；
}
```

循环条件是返回一个布尔值的表达式

循环初始值可以有多条初始化语句，用逗号隔开int i = 0,int j = 0

```
while (循环条件){
	循环体；
	循环变量迭代；
}
```

循环条件返回一个布尔值，**while先判断后执行**

```
循环变量初始化;
do {
	循环体；
	循环变量迭代；
}while(循环条件)；

int i = 1;
		do {
			System.out.println(i);
			i++;
		}while(i <= 10);
```

**do..while先执行后判断**

~~金字塔问题~~

```
Scanner scanner = new Scanner(System.in);
		System.out.println("金字塔问题 输入层数");
		int number = scanner.nextInt();
		int i = 1;
		for (;i <= number ; i++) {
			
			for (int k = 1; k <= number-i;k++) {
				System.out.print(" ");
			}
			
			for (int j = 1; j <= 2 * i - 1;j++) {
				if (j == 1 || j == 2 * i - 1 || i == number)
				System.out.print("*");
				else System.out.print(" ");
			}
			System.out.println(" ");
		}
```

### 11.跳转生成控制break continue return

```
Math.random()    0.0<= <1

String name = "哈哈";
if (name.equals("哈哈")){------》"哈哈".equals(name)
	System.out.println("equals");
	break;
}
int i =1;
		while (i <= 4) {
			i ++;
			if (i == 3) {
				break;
			}System.out.println("i="+ i);
		}
-------------i=2 -----------------------	

continue 结束本次循环，继续下次循环
int i =1;
		while (i <= 4) {
			i ++;
			if (i == 3) {
				continue;
			}System.out.println("i="+ i);
		}
-------------i=2 i=4 i=5----------------

return表示跳出方法，如果在main中，就是跳出程序
```

### 12.数组array--引用类型

1. 存放多个同一类型的数据

2. 用length得到数组长度

3. 使用方式

   ```
   数据类型[] 数组名 = new 数据类型[大小] 
   int[] array = new int[5];
   int array[] = new int[5];--------array[0]=1;
   
   int[] array;          //声明数组
   array = new int[5];   //分配内存空间
   
   int array[] = {1,3,6,3,5};  //静态初始化
   ```

   4.数组属引用类型，数组型数据是对象(object);

   5.声明数组---------》分配空间-----------》赋值，默认为0

```
int[] array = {2,4,6};
for (int i = 0;i < array.length;i++){
	System.out.println(array[i]);
}
```

****

基本数据类型赋值为值拷贝

**数组默认是引用传递，赋的值是地址**

```
//实现空间独立------- 声明新数组，分配新空间地址
int arr1[] = {1,2,3};
		int arr2[] = new int[arr1.length];
		for(int i = 0;i< arr1.length;i++) {
			arr2[i] = arr1[i];
		}
		arr2[2] = 30;
		System.out.println(arr1[2]);
```

### 13.排序

冒泡排序

![image-20210720235412688](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210720235412688.png)

![image-20210721000117513](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210721000117513.png)

顺序查找 二分查找

**二维数组**

```
int[] array[] ---------->int[][] array
int[][] arr = {{},
			   {},
			   {}};
 for (int i = 0; i < arr.length ;i++){
 	for(int j = 0 ; j < arr[i].length ; j ++){
 		System.out.print(arr[i][j]);
 	}
 	System.out.println("");
 }
 
 int[][] arr = new int[2][3];
 
 int[][] arr;
 arr = new int[2][3];
```

![image-20210721003930707](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210721003930707.png)

![image-20210721004255977](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210721004255977.png)

### 13.类

![image-20210722003702963](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210722003702963.png)

1.方法步骤

```
    //方法返回类型 boolean
    //方法名称 isOdd
    //方法形参 (int number)
    //方法体 判断 if
```

