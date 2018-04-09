
"[教小白精通编程](https://weibo.com/6196175626/profile?topnav=1&wvr=6)"系列课程之

##  “C++11/14课程”实验 
 
 严禁未经作者同意，转载请注明出处，否则将追究法律责任！

### C++实验一：C++程序结构

1. 写一个程序，输入2个整数，输出它们的商。

2. 写1个程序，输入2个整数，输出它们之间的所有整数。注意：输入的2个整数a,b，可能是a<=b，也可能是a>b

3.  写1个程序，输出下面的图形：
```
               *

             *    *

          *    *     *
```
4.  写一个程序计算体积： cube(立方体), sphere(球), cone(圆锥).
 
  Cube Volume = side^3 

  Sphere Volume = (4/3) * pi * radius^3 

  Cone Volume = pi * radius^2 * (height/3) 


```cpp
#include<iostream>

int main(){          

    double cubeSide,sphereRadius,coneRadius,coneHeigh, //图形的参数

    volCube, volSphere, volCone = 0;       //体积变量


    //补充你的代码
    //...
    return 0;

}
```


5. 写一个程序，从键盘输入一个正整数，判断它是否是质数。

### C++实验二：变量和类型

1.

写一个程序，按照类似下列格式，输出你的操作系统中各种常用内在类型的变量占用内存大小。结果形如：

```
 bool:            1个字节

 int:                4个字节

 ...
```


2. 理解并运行下列程序，看看结果是否符合你的预期，为什么？

```cpp
  unsigned u = 10, u2 = 42;

  std::cout << u2 - u << std::endl;

  std::cout << u - u2 << std::endl; 

  int i = 10, i2 = 42;

  std::cout << i2 - i << std::endl;

  std::cout << i - i2 << std::endl;

  std::cout << i - u << std::endl;

  std::cout << u - i << std::endl; 





  for (unsigned u = 10; u >= 0; --u)

     std::cout << u << std::endl;
```


3. 说明下列程序的结果 ，为什么？


```cpp
#include <string>

#include <iostream>

using namespace std;

int a;

string str;

int main(){
    int b;

    string str2 ,str3(”hello”);

    cout<<a<<‘\t’<<b<<‘\n’;

    cout<<str<<‘\t’<<str2<<‘\t’<<str3<<endl;  

}
```


4. 理解并运行下列程序，体会变量的定义及不同初始化方式

```cpp
#include <iostream>
using namespace std;
int main() {
    double d;
    double d1{3.5};
    double d2 = {3.5};
    double d3 = 3.5;
    double d4(3.5); 

    int i;
    int i1{3.5};
    int i2 = {3.5};
    int i3 = 3.5;
    int i4(3.5);  

    std::cout<<d<<std::endl;

    std::cout<<d1<<std::endl;

    std::cout<<d2<<std::endl;

    std::cout<<d3<<std::endl;

    std::cout<<d4<<std::endl;
       

    std::cout<<i<<std::endl;

    std::cout<<i1<<std::endl;
    std::cout<<i2<<std::endl;

    std::cout<<i3<<std::endl;
  
    std::cout<<i4<<std::endl;
     
    auto a = 3.5;      

    auto a1 = {3.5} 
    auto a2 = i2+d2/2;

    std::cout<<a<<std::endl;

    std::cout<<a1<<std::endl;

    std::cout<<a2<<std::endl;

}
```




5.说明下列程序的编译运行结果 ，为什么？如果用auto定义这些变量，结果又是什么？

```
int main(){
    char ch = 255 ,ch1 = 125;
    short a = 23.45, b = {23.45},c= 70000LLU,d{70000LU} ;

    cout<<ch<<'\t'<<ch1<<'\n';
    cout<<a<<'\t'<<b<<‘'\t' <<c<<'\t'<<d<<'\n';

    cout<<"type(ch):"<<typeid(ch).name()<<'\t'
          <<“type(ch1):”<<typeid(ch1).name()<<‘\n’


    cout<<"type(a):"<<typeid(a).name()<<'\t'
          <<"type(b):"<<typeid(b).name()<<'\t'
        <<"type(c):"<<typeid(c).name()<<'\t';
         <<"type(d):"<<typeid(d).name()<<'\n';

}
```

6. 一元二次方程求根：从键盘输入方程的系数(假设判别式>=0)，输出其方程的2个根

![](https://mmbiz.qpic.cn/mmbiz_jpg/SZ5H2qlR0knQBCibdYHW4seovpqV17viaXS4sKovyJC6ASx5hTCSvzfJ6acbwG1LAoOgIKr2a0TA4vYt74ibiaiaN6A/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)



7. 理解并运行下列程序

```cpp
#include <cmath>

#include <iostream>

#include <typeinfo>

using namespace std;

int main() {

  auto b = true; // a bool

  auto ch{'x'}; // a char

  auto i = 123; // an int

  auto d{1.2}; // a double

  auto z = sqrt(d); // z 是sqrt(d)的返回类型

  cout << typeid(b).name() << endl;
  cout << typeid(ch).name() << endl;
  cout << typeid(i).name() << endl;
  cout << typeid(d).name() << endl;
  cout << typeid(z).name() << endl;
}
```


8. 编译下列程序，理解编译错误的原因

```cpp
#include <iostream>

using namespace std;

int main {

  double val = 7.9;
  int val2 = 1025;
  int x2 = val; 
  char c2 = val2; 
  int x3{ val }; 
  char c3{ val2 };
  char c4{ 24 }; 
  char c5{ 264 };     

  int x4{ 2.0 };           

}
```


### C++实验三：引用


1. 下列程序有哪些编译错误？为什么？纠正错误并运行程序

```cpp
#include <iostream>

using namespace std;

int main() {
   int i;
   const int ci;
   int &r;
   int &r1 = i;

   int &r2 = 7;
   int &r3 = ci;
   int &r4 = 2*i+1;
   double d = 3.14; 
   int &r5 = d; 
   extern int &r6;
   int b=3;
   r1 = b; 
   int r  =b;
   r1 = 5;
   cout << a << '\t' << r <<endl;

   
   //const和引用的结合

   const int &r7 = i;
   cosnt int &r8 = 7
   const int &r9 = ci;
   cosnt int &r10 = 2*i+1;
   const int &r11  =d;


   i = r7;
   r1 = r7;
   r7 = r1;         

}
```


2. 引用经常用作函数的形参，表示该形参是实际参数的别名。体会下列函数的区别


```cpp
void swap(int x, int y){
   int t = x; x = y; y = t;
} 

void Swap(int &x, int &y){
   int t = x; x = y; y = t;
} 


int main(){
   int a = 3,b = 4;
   swap(a,b);
   std::cout<<a<<'\t'<<b<<std::endl;
   Swap(a,b);
   std::cout<<a<<'\t'<<b<<std::endl;
}
```


3. 下列函数返回一个数组的最小值的下标，修改这个函数，使得可以既返回最小值的下标也返回最大值的下标。


```cpp
 typedef double T;

int min_index(T *a,int n){

  if(n<=0) return -1;



  T min_value = a[0];

  int index = 0;



  for(int i = 1; i<n;i++){

    if(a[i]<min_value){

      min_value = a[i];

      index = i;

    }

  }

  return index;

}
```
       


```cpp
int main(){
  T arr[] = {23.5, 3.7, 15.2, 27.67, 39.99, 1.01, 13.33};

  for(int i = 0 ; i<7 ;i++)
       std::cout<<arr[i]<<'\t';

  std::cout<<std::endl;

  int index，index_ma;//分别表示最小值和最大值的下标

  //补充你的代码

  //...?...

  
  std::cout<<"  最小值的下标是："<< index <<std::endl;
  std::cout<<"  最大值的下标是："<<index_ma <<std::endl;
}
```

### C++实验四： 指针和数组
1. 理解并运行下列程序

// T *  就是 “T的指针类型”

// T * p 就是 “T的指针类型”的变量p

int main(){

  int ival = 1024;

  int *pi = &ival;

  int **ppi = &pi; // "int **" 即使 "(int *) *"就是  "int的指针的指针类型"



  std::cout<<"*pi=:"<<*pi<<std::endl; //*pi 就是ival

  std::cout<<"*ppi=:"<<*ppi<<std::endl; //*ppi 就是pi

  std::cout<<"**ppi=:"<<**ppi<<std::endl; //**ppi 就是ival

  std::cout<<"ppi=:"<<ppi<<std::endl; //ppi 就是pi的地址

  std::cout<<"&pi=:"<<&pi<<std::endl; //&pi 就是pi的地址



}



2. 理解并运行求C风格字符串(最后有结束字符的字符数组)长度的函数。

```cpp
#include <iostream>

#include <cstring>  //C语言字符串处理函数头文件

int StrLen(const char *s){
  const char *p = s;
  while(*p!='\0')     p++;
  return p-s;
}

int strLen(const char *s){
  int i = 0 ;
  while(s[i]!='\0')     i++;
  return i;
}


int main(){

  const char * str = "hello world";  
  // char str[] = {'h','e','l','l','o',...'d','\0'};

  int len = strlen(str); //C语言自带的求字符串长度函数strlen

  std::cout<<len<<std::endl;
  len = strLen(str);
  std::cout<<len<<std::endl;

  len = StrLen(str);
  std::cout<<len<<std::endl;
}
```




3. 编写比较2个C风格字符串的大小的函数strCmp，模仿C语言自带的比较大小函数strcmp.

```cpp
 /*strcmp(s1,s2)

 s1 = {'h','e','\0'}
 s2 = {'h','e','l','l','\0'}

 s1 = {'h','e','l','l','\0'}
 s2 = {'h','e','\0'}
*/

// s[i] :   *(s+i)

int strCmp(const char *s1,const char *s2){

    //你的代码

    // ...

}



int main(){
  char s1[] = {'h','e','\0'};

  char s2[] = {'h','e','l','l','\0'};

  int ret = StrCmp(s1,s2);
  if(ret<0)
    std::cout<<s1<<"<"<<s2<<std::endl;
  else if(ret==0)
    std::cout<<s1<<"=="<<s2<<std::endl;
  else 
    std::cout<<s1<<">"<<s2<<std::endl;

}
```


4. 估计下列代码运行结果是什么？有什么错误？运行改程序，验证你的判断。


```cpp
int main(){

     int i,arr[5];
     int *p = &i;
     *p = 6;

     std::cout<<i<<std::endl; 

     int *q = arr;
     std::cout<<arr[0]<<'\t'<<*q<<std::endl;

     *(p+2) = 20;
     *(q+2) = 20;

     std::cout<<p[q]<<'\t'<<q[2]<<std::endl;

     for(int i = 0 ; i<=5;i++)
       q[i] = i*10;

    for(int i = 0 ; i<=5;i++)
       std::cout<<p[i]<<std::endl;

    for(int *s = q; s!= (arr+5) ; s++)
       std::cout<<*s<<std::endl;

    std::cout<<*(p-1)<<'\t'<<*(q-1)<<std::endl;
}
```
5. 阅读编译下列程序，说明编译错误的原因。

并体会语法规则
```
不能用“一个const对象的指针或引用” 初始化或赋值给" non-const对象的指针或引用"

但可以用“一个non-const对象的指针或引用” 初始化或赋值给" const对象的指针或引用"
```

```cpp
int main(){ 
  int i;
  const int ci= 7;
  cosnt int ci2 = i*i;

  const int &cr = i;
  const int &cr1 = ci;
  const int &cr2 = 7;
  const int &cr3 = i*i+1;


  int &r = i;
  int &r1 = ci;
  int &r2 = 7;
  int &r3 = i*i+1;


  const int *pc = &i;
  const int *pc1 = &ci;

  int *const cp = &i;
  int *const cip = &ci;

  int *p = &i;
  int *p1 = &ci;
  
  int j;
  cp = &j; 
  pc = &j;  
  *cp  = 4;
  std::cout<<i<<std::endl;
  return 0;
}
```


2. 假设行数从键盘输入，打印输出如下的金字塔。

```cpp

        *
      * * *
    * * * * *
  * * * * * * *
* * * * * * * * *

 //添加你的代码
   ?
 int main(){
    int rows;
    std::cin>>rows;

    for(int i ; i<?; ?){
    	//输出第i行

    	//1）输出一定量的空白

    	for(int space; space< ?;space++)
    	    ?

    	//2)输出2*i-1 个星号

    	    ？

    	//输出换行

    	std::cout<<endl     
    }
}
```

3. 从键盘输入两个字符串给 string 类型的变量，输出这两个字符串的长度和两个字符串拼
接后的新字符串。

### 实验2: 变量与基本类型

1. 用typeid和sizeof检查一个类型或表达式的类型和占用内存大小。
对你知道的每种基本数据类型，分别针对类型或表达式调用者2个函数，如
```cpp
   int n;
   std::cout<<typeid( n ).name()
       <<" "<<sizeof(n)<<" "<<sizeof(int)<<endl ; // 打印：int 4 4

   std::cout<<typeid( 8.1 ).name() 
    <<" "<<sizeof(8.1)<<" "<<sizeof(double)<<endl ; // 打印：double 4 4

```
并编写一个模仿[C语言的输出输入输出基本类型](http://xuepro.xcguan.net/2017/10/30/C%E7%A8%8B%E5%BA%8F%E5%AE%9E%E4%BE%8B1-%E8%BE%93%E5%85%A5%E8%BE%93%E5%87%BA%E6%89%80%E6%9C%89%E5%9F%BA%E6%9C%AC%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B/)的C++程序。

2. 看看下列程序片段的编译器语法错误时什么？并说明理由

```cpp
void f{		
	double d = 2.3,d1(2.3);
	long double d2{2.3},d3 = {2.3}; 	
	int i{d},i2(s2); 
}

void f2{
    int &refVal4 = 10; 
	double dval = 3.14;
	int &refVal5 = dval; 
}

void f3(){
    int i = 0;
	int *const p1 = &i; 
	const int ci = 42; 
	const int *p2 = &ci; 
	const int *const p3 = p2; 
	const int &r = ci; 
	i = ci; 
	p2 = p3; 

	int *p = p3; 
	p2 = p3;
	p2 = &i; 
	int &r = ci; 
	const int &r2 = i; 
}

void f4(){
  int &a;
  auto i = 0, *p = &i; 
  auto sz = 0, pi = 3.14; 
}
```

### 实验3 :自定义类型

3.在下列程序基础上按照你自己的想法重写编写Sales_data及其使用程序，完成你想完成的功能。并修改成将struct Sales_data放在单独的头文件中，main函数文件#include这个头文件。

```cpp
#include <iostream>
#include <string>
struct Sales_data{
	std::string bookNo;
	unsigned units_sold = 0;
	double revenue = 0.0;
};
int main() {
	Sales_data data1, data2;
	double price = 0; // 每本书价格，用于计算总销售额revenue

					  // 读入数据到data1 和 data2

	std::cin >> data1.bookNo >> data1.units_sold >> price;
	data1.revenue = data1.units_sold * price;
	std::cin >> data2.bookNo >> data2.units_sold >> price;
	data2.revenue = data2.units_sold * price;

	// 相同则合并，不相同则单独输出

	if (data1.bookNo == data2.bookNo) {
		unsigned totalCnt = data1.units_sold + data2.units_sold;
		double totalRevenue = data1.revenue + data2.revenue;		

		std::cout << data1.bookNo << " " << totalCnt
			<< " " << totalRevenue << " ";
		if (totalCnt != 0)
			std::cout << totalRevenue / totalCnt << std::endl;
		else
			std::cout << "(no sales)" << std::endl;
		return 0; // indicate success

	}
	else { 
		std::cerr << "Data must refer to the same ISBN"
			<< std::endl;
		return -1; 
	}
}

```
 
### 实验4 :string、vector和迭代器

要求在遍历时，采用下标运算符、Range for、和迭代器三种方式。并尽可能使用auto或decltype

1. 理解并改正下列程序的错误,并运行之。
```cpp
void f2() {
	string s("hello world");
	if (!s.empty()) 
		s[0] = toupper(s[0]); //首字母都转变成大写字母
	
	for (int i = 0; i<=s.size(); i++) //此处有错
		cout << s[i];	
	
	//将每个字母都转变成大写字母
	for (auto c : s2)   //此处有错
		c = toupper(c); 
						
	cout << s2 << endl;
}
```



2. 实现一个管理销售数据的程序，在头文件
Sales_Item.h中定义2个数据类型：商品单价和销售项
struct Item_Price{
	string name;
	double price;
};
struct Sales_Item{
	string name;
	unsigned num = 0;
	double revenue = 0.0;
};

然后其中用2个vector向量:
```cpp
    vector<Item_Price> Item_Prices; //所有商品价格
    vector<Sales_Item> Sales_Items; //所有销售数据
```
表示程序的主要数据结构，并实现添加一个销售项、查询某商品价格、查询某商品的销售情况、统计总销售额、输出总商品目录，输出总销售单等功能。
```cpp
//添加相关头文件等...
   ？
int main(){
    vector<Item_Price> Item_Prices; //所有商品价格
    vector<Sales_Item> Sales_Items;
    char cmd; //命令字符
    while(cin>>cmd){
    	if(cmd=='a'||cmd=='A'){//添加销售项目

            ？
    	}
        //其他命令
    	?
    }
}
```

### 实验5 : 数组、指针和迭代器

1. 将下列程序的下标运算符访问方式修改成 Range for和指针访问方式。并尽可能使用auto或decltype
```cpp
/* C++ Program - Multiply Two Matrices */
		
#include<iostream.h>
#include<conio.h>
void main()
{
	clrscr();
	int mat1[3][3], mat2[3][3], mat3[3][3], sum=0, i, j, k;
	cout<<"Enter first matrix element (3*3) : ";
	for(i=0; i<3; i++)
	{
		for(j=0; j<3; j++)
		{
			cin>>mat1[i][j];
		}
	}
	cout<<"Enter second matrix element (3*3) : ";
	for(i=0; i<3; i++)
	{
		for(j=0; j<3; j++)
		{
			cin>>mat2[i][j];
		}
	}
	cout<<"Multiplying two matrices...\n";
	for(i=0; i<3; i++)
	{
		for(j=0; j<3; j++)
		{
			sum=0;
			for(k=0; k<3; k++)
			{
				sum = sum + mat1[i][k] * mat2[k][j];
			}
			mat3[i][j] = sum;
		}
	}
	cout<<"\nMultiplication of two Matrices : \n";
	for(i=0; i<3; i++)
	{
		for(j=0; j<3; j++)
		{
			cout<<mat3[i][j]<<" ";
		}
		cout<<"\n";
	}
	getch();
}
```


### 实验6 : 表达式

1. 运行下面的程序，说明结果为什么是错的？
```cpp
#include <iostream>
 
int main(){
    double d1(100 - 99.99); // should equal 0.01

    double d2(10 - 9.99); // should equal 0.01
 
    if (d1 == d2)
        std::cout << "d1 == d2" << "\n";
    else if (d1 > d2)
        std::cout << "d1 > d2" << "\n";
    else if (d1 < d2)
        std::cout << "d1 < d2" << "\n";
    
    return 0;
}
```
2. 运行并理解下面不同的比较2个数字几乎相等的方法

```cpp

#include <cmath>
 
bool approximatelyEqual(double a, double b, double epsilon){
    return fabs(a - b) <= ( (fabs(a) < fabs(b) ? fabs(b) : fabs(a)) * epsilon);
}

bool approximatelyEqualAbsRel(double a, double b, double absEpsilon, double relEpsilon)
{
    // Check if the numbers are really close -- needed when comparing numbers near zero.
    double diff = fabs(a - b);
    if (diff <= absEpsilon)
        return true;
 
    // Otherwise fall back to Knuth's algorithm
    return diff <= ( (fabs(a) < fabs(b) ? fabs(b) : fabs(a)) * relEpsilon);
}

#include <iostream>
int main()
{
    // a is really close to 1.0, but has rounding errors

    double a = 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1;
 
    std::cout << approximatelyEqual(a, 1.0, 1e-8) << "\n";  

     // compare "almost 1.0" to 1.0

    std::cout << approximatelyEqual(a-1.0, 0.0, 1e-8) << "\n";

    // compare "almost 0.0" to 0.0

    std::cout << approximatelyEqualAbsRel(a-1.0, 0.0, 1e-12, 1e-8) << "\n"; // compare "almost 0.0" to 0.0


}
```

3. 在农夫过河问题的检测物体是否在北岸的函数基础上，编写判断一个状态是否是安全状态？

```cpp
  bool farmerLocation(int state){
  	 return state&0x08!=0; //true表示农夫在北岸，false表示在南岸
  }
```
### 实验7: 语句

1. 理解下列程序，并输入各种可能性测试程序执行情况
```cpp
#include <iostream>
 
int main(){
    int i = 2;
    switch (i) {
        case 1: std::cout << "1";
        case 2: std::cout << "2";   //execution starts at this case label
        case 3: std::cout << "3";
        case 4:
        case 5: std::cout << "45";
                break;              //execution of subsequent statements is terminated
        case 6: std::cout << "6";
    }
 
    std::cout << '\n';
 
    switch (i) {
        case 4: std::cout << "a";
        default: std::cout << "d"; //there are no applicable constant_expressions 
                                   //therefore default is executed
    } 
    std::cout << '\n';
 
    switch (i) {
        case 4: std::cout << "a";  //nothing is executed
    }
}
```

2. 运行并理解程序
```cpp
#include <iostream>
int main(){
    int x;
    for( ; ; ){
        std::cout << "Enter 0 to stop" << endl;
        std::cin >> x;
        if (x == 0){
            break;
    	}
    	else if(x>0) continue;
    	std::cout << "你输入了一个负数！" << endl;
    }
    return 0;
}
```

### 实验8 : 函数

1. 编写一个函数，输出2个整数之间的所有整数。并在主程序里测试这个函数。
```cpp
 void Print(int a, int b){

 }

 int main(){
 	int x,y;
 	while(std::cin>>x){
 		if(std::cin>>y{
        //调用Print函数

        ?
 		}
 		else break;
 }
 ```

2. 编写最大公约数的函数并测试它


3. 编写swap函数，用于交换两个形参的值，分别用传值(包括传指针)和传引用方式将实参传给形参，对不同类型(如int,double,string等)编写相应的重载函数，并编写主函数测试这两个函数。


### 实验9 : 类

1. 实现一个较为完整的Date类并测试

2. 实现一个较为完整的Complex类并测试,尽量重载算术运算符。

2. 实现一个表示数学向量的类Vector2，并测试通常的数学向量运算，
如：查询其x或y分量、计算长度、1个向量的数乘、2个向量的加/减/点积/叉积等。并测试它。


## C++习题

### C++概述
1. 补充下列“闰年判断”程序：输入年份year，判断是否是闰年，若不是，输出NO，否则输出YES。（判断闰年的标准是：1、年份能被4整除而不能被100整除; 2、年份能被400整除）

```cpp
   ?
 int main(){
    int year;
    std::cin>>year;
    if(?){ 
      std::cout<<year<<" 是闰年"<<endl;
    }
    else std::cout<<year<<" 不是闰年"<<endl;
```
2. 用非递归方法计算如下递归函数的值（斐波拉契）：
  f(1)=1
  f(2)=1
  f(n)=f(n-1)+f(n-2) n>2

3. 有一分段函数如下，请编写程序，输入x值，输出y值。
![](http://dl2.iteye.com/upload/attachment/0118/2993/b247c5ea-12b2-3e47-89c8-29e8f97be24d.jpg)

4. 编程实现：从键盘输入一系列整数，求它们的最大值并输出
 

### 变量与基本类型
1. 下面这个程序执行后会有什么结果或问题:
```cpp
 #define SIZE 255
 int main(){
   unsigned char A[SIZE],i;
   for (i=0;i<=SIZE;i++)
      A[ i ]=i;
}
```


