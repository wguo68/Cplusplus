
[教小白精通编程](http://xuepro.xcguan.net)

系列课程之

##  现代c++11/14/17教程之1--c++程序结构
 
 严禁未经作者同意，转载请注明出处，否则将追究法律责任！

### 1. 最简单的C++程序：

```c
int main() {
   return 0;
} 
```

C++程序是有一些所谓的“函数”构成的，每个C++程序都包含唯一的叫做"main"的主函数。

一个函数包含4个部分：

   * 返回类型: 说明这个函数执行后返回的结果值的数据类型。如上面的程序通过关键字“return”返回结果值0.            return的中文是“返回”的意思.

   * 函数名: 这个函数的名字

   * 参数列表: 由(和）括起来的一系列形参（以后会介绍）。

   * 函数体: 由{和}括起来的程序语句。   

**函数的格式**是：
 
 ```   
     返回类型  函数名(参数列表)
     {
        函数体
     }
```

补充说明：main函数的返回值是返回给操作系统，返回0通常表示没有错误，返回其他非0的整数通常表示是不同的错误代码，不同操作系统对返回的整数代码表示的错误有不同的规定。

2. 程序注释：为了方便他人阅读程序或自己今后回顾程序，可以在程序中添加一些对程序进行说明的文字，称为“注释”.

注释本身不是代码，仅仅是对程序代码的说明。完全可以删除注释，不影响程序任何功能，但良好的程序应该添加一些注释方便阅读理解。

注释主要分为： 多行注释和单行注释


* 多行注释（也称为块注释）：  以“/*”开头，以“*/”结尾。它们之间的一行或多行文字都是程序注释。

* 单行注释: 用“//”开头，其后的同一行的文字都是注释。

如上述代码可以添加如下注释：

```cpp
/*
   这是多行注释   
   这是我的第一个c++程序
   this is my sirst c++program
   作者: hwdong
   修改日期：2018-01-27
*/

int main() {   // main函数是程序的入口，程序总是从这里执行
   return 0;   // 程序结束，返回整数0
              //C++的程序语句都以分号';'结尾。
}
```

**注意**:块注释不能嵌套，即其中不能再出现"/*"或"*/"。

```cpp
/*
   块注释不能嵌套,不能在块注释中间包含/*或*/
   作者: hwdong
   修改日期：2018-01-27
*/
```

### 3. 输入输出、名字空间

```cpp 
#include <iostream>
int main() {   
  std::cout<<"hello world";
  return 0;  
}
```

执行这个程序，会在控制台窗口输出字符串“hello world”。

**3.1） 标准输入输出和cout**


可以用C++"标准输入输出流库"的功能进行程序的输入输出。

比如其中定义了一个表示控制台窗口的对象(也叫做变量)cout，
可以用**输出流运算符"<<"**向cout输出信息，比如输出一个字符串：

```c
 cout<<"hello world";
```
   用双引号括起来的一系列字符在C++中称为“字符串”。

**3.2) 名字空间**

C++中的所有对象、函数等都属于某个名字空间。

     
C++为了防止出现“名字冲突”（比如不同的程序库都用了同一个名字，
如果想同时使用这个库的同名名字会发生冲突），可以规定名字属于某个特定的“名字空间”，从而避免了名字冲突。

比如2个不同班级都有一个叫做“张伟”的学生，我们可以用
“数学1601班”的“张伟” 和“计算机1702班”的“张伟”来区分它们。

其中标准名字空间std是C++标准库中的所有对象、函数等的名字空间。
   std::cout表示这是 "名字空间std"的"cout"。
 
 "std::"称为“名字限定”，即限定cout是属于名字空间std中的名字。
 
如果某个名字如函数"main"没有明确说明名字空间，那个它就属于一个全局名字空间。

全局名字空间中的“东东”不需要名字限定！

再如"std::endl"是标准名字空间std中的某个名字"endl"，它是一个“换行字符”，"输出运算符<<"对这个符号会执行一个换行的动作，即从新的一行开始新的输出。

```cpp
#include <iostream>
int main() {   
  std::cout<<"hello world"<<std::endl;
  return 0;  
}
```

除了名字限定，也可以通过**"using namespace"**引入整个名字标准名字空间std的所有名字

```cpp
  using namespace std;
```

一旦引入所有名字，其后的程序语句就不需要对std中的名字如cout进行名字限定了。上述程序可以写成

```cpp
#include <iostream>
using namespace std;  //引入整个标准名字空间std中所有名字
int main() {   
  cout<<"hello world"<<endl;
  return 0;  
}
```

此外，我们还可以用关键字“using”引入单个名字，如"using std::cout"。
```cpp
#include <iostream>
using std::cout;
int main() {   
  cout<<"hello world"<<std::endl; //endl必须名字限定
  return 0;  
}
```

我们看到输出运算符"<<"可以连续使用，这是因为std::cout <<"hello world"的结果仍然是"std::cout"，所以可以继续使用"<<"

### 4. 宏定义#define：
用于给一个数值或字符串等起一个名字。

先看下面的计算圆面积和周长的程序：

```cpp
#include <iostream>
int main() {
  std::cout << 3.14*2.5*2.5 << std::endl;
  //..
  std::cout << 2*3.14*2.5 << std::endl;
        //...
  std::cout << 3.14*4.3*4.3 << std::endl;
  return 0; //程序返回整数0 
}
```

其中圆周率值用3.14表示，但如果后来觉得需要换用其他精度的如3.1415926作为圆周率，那么就需要在程序中搜索出所有的圆周率3.14并用3.1415926替换掉.

```cpp
#include <iostream>
int main() {
  std::cout << 3.1415926*2.5*2.5 << std::endl;
  //..
  std::cout << 2*3.1415926*2.5 << std::endl;
        //...
  std::cout << 3.1415926*4.3*4.3 << std::endl;
  return 0; //程序返回整数0 
}
```

假如很多地方用到圆周率，都需要这样找到它们然后替换。
一个更好的办法是给表示圆周率的数值起一个名字，如下所示：

```cpp
#include <iostream>
#define PI 3.14 //PI就是宏常量。 #define就是宏定义指令
int main() {
  std::cout << PI*2.5*2.5 << std::endl;
  //..
  std::cout << 2*PI*2.5 << std::endl;
        //...
  std::cout << PI*4.3*4.3 << std::endl;
  return 0; //程序返回整数0 
}
```

其中"#define PI 3.14"称为**宏定义**，即定义了一个叫做"PI"的宏，它实际就是数值"3.14"的名字。程序中用到3.14的地方就可以用PI来代替。

宏定义PI提高了程序的阅读性。更主要的是：如果今后需要更改圆周率，只要修改"#define PI 3.14"为"#define PI 3.1415926"即可，程序中其他地方无需修改。

```cpp
#include <iostream>
#define PI 3.1415926 //PI就是宏常量。 #define就是宏定义指令
int main() {
  std::cout << PI*2.5*2.5 << std::endl;
  //..
  std::cout << 2*PI*2.5 << std::endl;
  //...
  std::cout << PI*4.3*4.3 << std::endl;
  return 0; //程序返回整数0 
}
```

### 5. 变量： 命令的内存块
   
 数据需要存放在内存中并起一个名字，才能根据名字去访问这个内存块。

 C++中有不同类型的数据，数据必须说明它是什么类型。

 通过定义**变量**(也称为**对象**) 的方式可以申请到一块特定类型的内存块。

比如：

```cpp   
    int i;      //定义了一个叫做i的int型(int整数类型)的变量(对象)
    double r;   //定义了一个叫做r的double型(double浮点实数类型)的变量(对象)
    double area;  //定义了一个叫做area的double型的变量(对象)
```

看一个完成的使用“变量”的例子：

```cpp
#include <iostream>
#define PI 3.14159 
int main() {
  double r; // r是double类型的变量，double是浮点实数类型
  r = 2.5;
  std::cout << PI*r*r << std::endl;
  //...
  std::cout << 2*PI*r << std::endl;
  return 0; 
}
```

### 6. 标准输入流对象cin

输入输出标准流库<iostream>还定义了叫做"cin"的输入流对象，
它代表键盘对象，可以从cin中输入数据到某个程序变量(对象)中。

```cpp
   double r; 
   std::cin>>r; //等待用户从键盘输入一个实数给变量r。其中">>"是输入流运算符
```      

看一个完成的使用“cin”和输入流运算符">>"的例子：

```cpp
#include <iostream>
#define PI 3.14159 //PI就是宏常量。 #define就是宏定义指令
int main() {
  double r; 
  std::cin>>r;   //等待用户从键盘输入一个实数给变量r。
  std::cout << PI*r*r << std::endl;
  //..
  std::cout << 2*PI*r << std::endl;
  return 0; 
}
```

### 7. 输出运算符<<和输入运算符>>
    
输出运算符"<<"可以串起来使用。

```cpp   
  std::cout << PI*r*r << std::endl;    
```

这是因为"std::cout <<PI*r*r"的结果仍然是"std::cout"，所以可以继续使用"<<"

输入运算符>>也是一样的，比如：

```cpp
#include <iostream>
int main() {
        std::cout <<"请输入2个整数："<< std::endl;
  int a,b; 
  std::cin>>a>>b;   //等待用户从键盘输入2个整数，输入2个整数时，可以用空格或回车隔开它们。
  
  std::cout << a << "+" << b << "=:" <<a+b << std::endl;
  return 0; 
}
```

### 总结：

本文介绍了下列概念：简单的C++程序、程序注释、输入输出、名字空间、宏定义#define、变量-命令的内存块、标准输入流对象cin、输出运算符<<和输入运算符>>

### 练习：

1.  写1个程序，输出下面的图形：
```
                1

             2     3

          4     5    6
```

2.  写一个程序计算体积： cube(立方体), sphere(球), cone(圆锥).

         Cube Volume = side^3 

         Sphere Volume = (4/3) * pi * radius^3 

         Cone Volume = pi * radius^2 * (height/3) 

     要求图形参数如radius等从键盘输入。

```cpp
#include<iostream>
int main(){           

    double cubeSide，sphereRadius， coneRadius ，coneHeigh，  //图形的参数

    volCube, volSphere, volCone = 0;       //体积变量的初始值为0

   //补充你的代码

   return 0;

}
```

### 编程环境：

1. [CodeBlocks编译C/C++程序](https://weibo.com/tv/v/Fp8Pn6hQp?fid=1034:beb66bf53fa5e71e7b41ef375b8d1542)

2. [VS2017编译C++程序](https://weibo.com/tv/v/Fp8Pn6hQp?fid=1034:beb66bf53fa5e71e7b41ef375b8d1542)

3. [sublime配置MinGW搭建C/C++编程环境，并解决控制台汉字输出乱码问题](http://v.youku.com/v_show/id_XMzExNzMwNDM2NA==.html)  ​​​​


关注微博"[教小白精通编程](https://weibo.com/6196175626/profile?topnav=1&wvr=6)".  加入QQ群：101132160 ​​​ 享受直接的辅导！