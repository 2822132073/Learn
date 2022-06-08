# C语言



[TOC]

## 考试需要注意的问题

### 相关细节

1. 注意`if`,`for`,`while`相关语句后面的`;`和`{}`,以防弄错执行范围
2. 字符`0`ascii码为48,`A`是65,`a`是`97`
3. `while(s(++len))`求的是字符串长度,也就是`strlen`的作用(字符串不包含`\0`的长度)
4. `while(s(len++))`求的是字符串包含`\0`共有多少字符
5. 二维数组定义`a[2][4]`为两行四列
6. 宏可以写在文件任意位置(就算在main函数里面都可以)
7. `do..while..`循环: 循环体和条件表达式执行次数一样
8. `while`循环: 条件表达式比循环体执行次数多一次
9. `p=NULL`,`p=0`,`p='\0'`三者等价
10. 不能将字符串直接赋值给命名字符数组,只能在初始时进行赋值
11. 两个字符串数组之间不能直接赋值,需要借助`strcpy(dest, src);`
12. 位运算的对象只能是整型和**字符型**
13. 符号常量相当于定义一个宏
14. `printf("%d,%d", b, b = b + 2);`执行结果为`4,4`,因为`printf`执行表达式的顺序是从左到右
15. 注意strlen返回的字符串的长度不包括结束符`\0`,指针变量的占用4字节
16. C语言两个`%`,打印结果为一个`%`,`printf("%%");`的输出结果为`%`
17. `scanf`在输入字符串时,以空格作为分隔符,`gets`输入字符串时以回车符作为结束符
18. 数组为指针常量,不可以进行修改
19. 整形变量在没有初始化初值的情况下,它的值是随机的
20. `EOF`的值是`-1`,`EOF`必须在文本文件中才能出现
21. `sizeof`是不是函数,是一个表达式,`sizeof(数组名)`返回数组所有元素占有的内存空间字节数,`sizeof(指针)`返回指针占用大小
22. `int x=y=1`,是错的,需要对y进行进行定义才可以进行赋值
23. `printf`的`%md` 中的m是规定十进制数的最小宽度
24. 就算是返回类型是`void`,函数也可以使用`return`,只不过不能在后面加认识东西 就像: `return;`
25. `0`按位取反的值为`-1`
26. C语言默认是左对齐 但是在添加宽度后就变成右对齐
27. 强制类型转换应该使用括号将数据类型括起来,例如: `(int)x;`
28. 各种`循环`,`判断`语句,还有`{}`都属于一个单独的作用域
29. 数组类型的形参都会退化为指针
30. 字符常量的值不能超过255
31. 当函数的返回值省略的时候,函数的返回值默认为int类型

> 下列函数正确:
>
> ```c
> void fun(){
> 	static int a=0;
> 	if(1)static int a=1;  //两个a不是同一个变量,此函数输出结果为:0
> 	printf("%d\n",a);
> }
> ```
>
> 这个也是正确的:
>
> ```c
> void fun(){
> 	static int a=0;
>  {static int a=1;}  //和上面的结果相同,输出0
> 	printf("%d\n",a);
> }
> ```
>
> 下列函数编译错误:
>
> ```c
> void fun(){
> 	static int a=0;
>      static int a=1;  //在同一个作用域重新定义了一遍a,编译报错
> 	printf("%d\n",a);
> }
> 
> ```
>
> 下面可以提现函数作用的作用
>
> ```c
> void fun(){
> 	static int a=0;
> 	{
> 		static int a=1;
> 		a+=2;
> 		printf("in: a=%d ",a);
> 	}
> 	a++;
> 	printf("out: a=%d\n",a);
> }
> 
> void main()
> {
> 	int i;
> 	for(i=0;i<3;i++)
> 		fun();
>  }
> 
> ```
>
> 输出结果:
>
> ```c
> in: a=3 out: a=1
> in: a=5 out: a=2
> in: a=7 out: a=3
> ```
>
> 

### printf相关知识点

1. `printf("%d,%d", b, b = b + 2);`执行结果为`4,4`,因为`printf`执行表达式的顺序是从左到右
2. C语言两个`%`,打印结果为一个`%`,`printf("%%");`的输出结果为`%`
3. `printf`的`%md` 中的m是规定十进制数的最小宽度
4. `printf`默认右对齐,需要左对齐需要在前面加上`-`
5. %\[标志][最小宽度]\[.精度][类型长度]类型,在printf中的长度为最小宽度,也就是说,如果如果实际位数比这个大,就会全部显示



### scanf相关知识点

1. `scanf("%3d",&n);`*设置域宽为3,如果输入1234,那么n的值为123*
2. `scanf("%3d%3d",&a,&b)`;*//当输入为：1234567时，将123赋给a，456赋给b。*
3. `scanf("%d %*d %d",&a,&b);`,*//1 2 3时，1赋给 a ，2舍弃，3赋给 b 。*
4. `scanf("%3d%*2d%3d%3d",&n1,&n2,&n3);`*//输入123456789,n1为123,n2为678,n3为9*
5. `scanf`不可以指定小数位宽
6. scanf在输入字符串时,遇到空格结束输入而不是遇到回车











### 相关简答题

#### C语言中什么是算数运算？什么是关系运算？什么是逻辑运算？

> 1.算术运算就是指加减乘除和整数的模运算（即取余数运算）。
>
> 2.关系运算就是比较运算，将两个数值进行比较，判断其比较结果是否符合给定的条件。
>
> 3.逻辑运算指两个条件进行运算，有逻辑与、逻辑或、逻辑非三种。













### 编程

#### 最大公约数和最小公倍数

> **最大公因数**，也称最大公约数、最大公因子，指两个或多个整数共有约数中最大的一个；**最小公倍数**是指两个或多个整数公有的倍数叫做它们的公倍数，其中除0以外最小的一个公倍数就叫做这几个整数的最小公倍数。最小公倍数=两整数的乘积÷最大公约数 ， 所以怎么求最大公约数是关键。

```c
#include<stdio.h>
void main()
{
	int num1=4,num2=8,temp,n1=num1,n2=num2;
	while(num2!=0){
		temp = num1%num2;
		num1=num2;
		num2=temp;
	}
	printf("最大公约数: %d 最小公倍数: %d\n",num1,n1*n2/num1);
}
```

```c
//最大公约数
int gcd(int a,int b){
	int temp;
	while(b!=0){
		temp=a%b;
		a=b;
		b=temp;
	}
	return a;
}
//最小公倍数
int lcm(int a,int b){
	return a*b/gcd(a,b);
}
```



#### 闰年

> 1. 非整百年：能被4整除的为闰年。（如2004年就是闰年,2100年不是闰年）
> 2. 整百年：能被400整除的是闰年。(如2000年是闰年，1900年不是闰年)

```c
#include<stdio.h>
void main()
{
	int year=2000;
	for(;year<3000;year++){
		if(year%400==0||year%4==0&&year%100!=0){
			printf("%d YES\n",year);
		}
	}
}
```

#### 斐波那契数列

> f(n) = f(n-1) + f(n-2)

```c
#include<stdio.h>

int Fibonacci(int n){
	if(n==0)return 0;
	else if(n==1){return 1;}
	else  return Fibonacci(n-1)+Fibonacci(n-2);
}

void main()
{
	int n=5;
	printf("%d\n",Fibonacci(n));
}
```

#### 素数(质数)

> 大于1的[自然数](https://baike.baidu.com/item/自然数/385394)中，除了1和它本身以外不再有其他[因数](https://baike.baidu.com/item/因数/9539111)的自然数。

```c
bool isPrime(int n){
	int i;
	for(i=2;i<n;i++){
		if(n%i==0)return false;
	}
	return true;
}
```



#### 复制字符串

```c
void copyString(char *s1,char *s2){
	int i=0;
	while((s1[i]=s2[i])!='\0')i++;
}
```



#### 冒泡排序

```c
void main()
{
	int a[10]={-1,2,5,2,8,99,2,51,5,90},i,j,temp;
	for(i=0;i<10-1;i++){
		for(j=0;j<10-1-i;j++){
			if(a[j]>a[j+1]){
				temp=a[j];
				a[j]=a[j+1];
				a[j+1]=temp;
			}
		}
	}
	for(i=0;i<10;i++){
		printf("%d ",a[i]);
	}
}
```



#### 倒叙输出

```c
```



#### 连接字符串

```c
//将s2的字符放到s1后面去
void connectString(char *s1,char *s2){
	while(*(++s1)!='\0');
	while((*s1++=*s2++)!='\0');
}
```

#### 反转二维数组(行列反转)

```c
void reversal(int a[3][3]){
	int i,j,temp;
	for(i=0;i<3;i++){
		for(j=i+i;j<3;j++){
			temp=a[i][j];
			a[i][j]=a[j][i];
			a[j][i]=temp;
		}
	}
}
```

#### 反序存放字符串

```c
void reversal_string(char *s){
	int len=0,i;
	char c;
	while(s[++len]!='\0');
	for(i=0;i<len/2;i++){
		c=s[len-i-1];
		s[len-i-1]=s[i];
		s[i]=c;
	}
```

#### 寻找最长单词

````c
int longestWord(char *s){
	int max_len=0,len=0;
	while(*s!='\0'){
		if(*s!=' ' && *s !='\0')
			len++;
		else{
			printf("len=%d\n",len);
			if(max_len<len)max_len=len;
			len=0;
		}
		s++;
	}
	return max_len;
}

````



#### 统计各种字符个数,并且在函数中输出

```c
void statistics(char *s){
	int en=0,num=0,blank=0,other=0;
	while(*s!='\0'){
		if(*s>='a' && *s<='z' || *s>='A' && *s <='Z')en++;
		else if(*s>='0'&&*s<='9')num++;
		else if(*s==' ')blank++;
		else other++;
		s++;
	}
	printf("letter=%d number=%d blank=%d other=%d\n",en,num,blank,other);
}
```



#### 插入空格

```c
void insertBlank(int n){
	char s[10];
	int i=6;
	s[i+1]='\0';
	while(i>=0){
		if(i%2==0){
			s[i--]='0'+n%10;
			n=n/10;
		}else{
			s[i--]=' ';
		}	
	}
	printf("%s\n",s);
}
```



#### 将s1中的元音字符复制到s2中

```c
void copyVowel(char *s1,char *s2){
	int i=0;
	while(*s1!='\0'){
		if(*s1=='a' ||*s1=='e' ||*s1=='i' || *s1=='o'||*s1=='u'){
			s2[i++]=*s1;
		}
		s1++;
	}
	s2[i]='\0';
	printf("%s\n",s2);
}
```

#### 选择法排序

```c
//选择法排序
void choiceSort(int n[10],int len){
	int i,j,k,temp;
	for(i=0;i<len-1;i++){ //10个数字需要进行9次扫描,不需要扫描10次,9次扫描后,最后一定是最大的数
		k=i;     
		for(j=i+1;j<len;j++){  //每次都需要比较到最后一位
			if(n[k]>n[j])k=j;   //将数组中最小的数存储在k中  
		}
		temp=n[k];  //将最小的值向前移动
		n[k]=n[i];
		n[i]=temp;
	}	
}


```

#### 对角线元素之和

```c
//对角线元素之和
int diagonalSum(int a[3][3]){
	int i,sum=0;
	for(i=0;i<3;i++){
		sum+=a[i][i];
	}
	return sum;
}
```

#### 插入数字

```c
//按照数组规律插入数组,len为当前数组有多少个有效数字,insertNumber为要插入的数字
void insert(int a[10],int len,int insertNumber){
	int i,t1,t2=insertNumber,index;
	for(i=0;i<len;i++){
		if(a[i]<=insertNumber && a[i+1]>=insertNumber){ //找到要插入的位置
			index=i+1;  
			break;
		}
	}
	for(i=index;i<len+1;i++){  //将数组数字向后移动
		t1=a[i];
		a[i]=t2;
		t2=t1;
	}
}
```

#### 杨辉三角

```c
//row为需要打印的行数,如果row>10,需要增加传入数组的大小
void  pascalTriangle(int a[10][10],int row){  
	int i,j;
	for(i=0;i<row;i++){
		a[i][0]=a[i][i]=1;
		for(j=1;j<i;j++){
			a[i][j]=a[i-1][j]+a[i-1][j-1];
		}
	}
	for(i=0;i<row;i++){
		for(j=0;j<row;j++){
			if(a[i][j]>=1){
				printf("%d   ",a[i][j]);
			}

		}
				printf("\n");
	}
}


```



#### 寻找鞍点

> 鞍点是行上最大，列上最小的元素

```c

void fun(int a[3][4],int row,int line){
	int i,j,point_r,point_l,flag;
	for(i=0;i<row;i++){
		point_r=i;   
		point_l=0;
		flag=1;
		for(j=1;j<line;j++){   //找出行中最大数字的坐标
			if(a[i][point_l]<a[i][j])point_l=j;
		}
		for(j=1;j<row;j++){   //再看这个数是不是这列中的最小的,不是的话修改flag的值
			if(a[point_r][point_l]>a[j][point_l]){
				flag=0;
				break;
			}
		}
		if(flag==1){
			printf("row=%d line=%d\n",point_r,point_l);
			break;
		}else if(flag!=1 && i==row-1){
			printf("No!!!!\n");
		}
	}
}
```



#### 二分法

```c
//二分法,len为长度,n为查找的数字,返回下标
int dichotomy(int a[],int len,int n){
	int L,R,mid;
	L=0;
	R=len-1;
	mid=len/2;
	while(L<=R){
		if(a[mid]==n){
			return mid;
		}else if(a[mid]<n){
			L=mid+1;
		}else if(a[mid]>n){
			R=mid-1;
		}
		mid=(L+R)/2;
	}
}
```



#### 密码与原文相互转换

```c
//密码与译文之间的转换
void encode(char *plaintText,char *cipherText){
	while(*plaintText!='\0'){
		if(*plaintText>='a' && *plaintText<='z'){
			*cipherText='a'+(26-(*plaintText-'a'+1));
		}else if(*plaintText >= 'A' && *plaintText<='Z'){
			*cipherText='A'+(26-(*plaintText-'A'+1));
		}else{
			*cipherText=*plaintText;
		}
		cipherText++;
		plaintText++;
	}
	*cipherText='\0';
}

//明文与密码相互转换
void decode(char *cipherText,char *plaintText){
	while(*cipherText!='\0'){
		if(*cipherText>='a' && *cipherText<='z'){
			*plaintText='a'+('z'-*cipherText);
		}else if(*cipherText >= 'A' && *cipherText<='Z'){
			*plaintText='A'+('Z'-*cipherText);
		}else{
			*plaintText=*cipherText;
		}
		cipherText++;
		plaintText++;
	}
	*plaintText='\0';
}

```



#### 字符串比较函数

```c
int strcmp(char *s1,char * s2){
	while(*s1!='\0' && *s2!='\0'){
		if(*s1==*s2){
			s1++;
			s2++;
		}else{
			return *s1-*s2;
		}
	}
	return 0;
}
```

#### 课本137,第5题

```c
int fun(int n){
	int sum=0,a=2,pre=0,i;
	for(i=1;i<=n;i++){
		pre=pre*10+2;
		sum+=pre;
	}
	return sum;
}
```



#### 完数

> 一个数因子之和等于这个数
>
> 因子:A能被B整除,A就是B的因子,例如: 15的因子有1,3,5

```c
#include<stdio.h>
void main()
{
	int n,i,j=0,factor[1000]={0},sum=0;
	for(i=1;i<=1000;i++){
		for(n=1;n<i;n++){  //找出i的因子
			if(i%n==0){
				factor[j++]=n; 
				sum+=n;  //将这些因数相加
			}
		}
		if(sum==i){
			printf("完数: %d 因子为: ",sum);
			for(n=0;n<j;n++){
				if(factor[n]>0){
					printf("%d,",factor[n]);
				}
			}
			printf("\n");
		}
		j=0;
		sum=0;
	}
}
```



#### 水仙花数

> 水仙花数是三位数,其各位数字的立方相加等于该数本身

```c
#include<stdio.h>
void main()
{
	int i,j,k,sum;
	for(i=1;i<=9;i++){
		for(j=0;j<=9;j++){
			for(k=0;k<=9;k++){
				if(i*i*i+j*j*j+k*k*k==i*100+j*10+k){
					printf("%d\n",i*100+j*10+k);
				}
			}
		}
	}

}
```



#### 阶乘的相加

> 例如n为5
>
> 就是 1+1x2+1x2x3+1x2x3x4+1x2x3x4x5

```c
int factorial(int n){
	int i,temp=1,sum=1;
	for(i=2;i<=n;i++){
		temp*=i;
		sum+=temp;
		printf("%d %d\n",sum,temp);
	}
	return sum;
}
```



#### P138_11

> 一球从100米高度自由落下，每次落地后反弹回原来高度的一半，再落下，求它第10次落地时，共经过多少米，？第十次反弹多高？

```c
void main()
{
	float height=100.0;
	float meter=100.0;
	int n=2;
	for(;n<=10;n++){
		meter += height/2*2;
		height /=2;
	}
	printf("height=%f meter=%f\n",height,meter);
}
```

#### 冒泡

```c
	for(i=0;i<m-1;i++){
		for(j=0;j<m-1-i;j++){
			if(b[j]>b[j+1]){
				n=b[j+1];
				b[j+1]=b[j];
				b[j]=n;
			}
		}
	}
```



#### 猴子吃桃问题

```c

int monkeyEatPeach(int i){
	if(i==10){
		return 1;
	}else{
		return 2*(monkeyEatPeach(i+1)+1);
	}
}


void main()
{
	int i,n=1,sum=n;
	for(i=10;i>=2;i--){
		n=(n+1)*2;
		sum+=n;
		printf("%d %d\n",i,n);
	}
	printf("%d\n",monkeyEatPeach(1));
}
```











## C语言中符号

| 符号 | 名称                                                         |
| ---- | ------------------------------------------------------------ |
| *    | 在定义变量时,是一个说明符,在对指针变量进行引用时为`间址运算符` |
|      |                                                              |
|      |                                                              |



## 常量的各种表达

### 常量

#### 十进制

> 这种常量只能出现 0～9 的数字，且可带正、负号。例如：0 1 364 28 -34

#### 八进制

> 这种常量是以数字 0 开头的八进制数字串。其中数字为 0～7。例如：0111(十进制 73) 011(十进制 9) 0123(十进制 83)

#### 十六进制

> 这种常量是以 0x或 0X开头的十六进制数字串。其中每个数字可以是 0～9、a～f或 A～F 中的数字或英文字母。例如：0x11(十进制 17) 0Xa5(十进制 165) 0x5a(十进制 90)

### 浮点数

#### 十进制小数

> 十进制小数形式为包含一个小数点的十进制数字串。
>
> 此类实型常量小数点前或后**可以没有数字，但不能同时没有数字**。例如：3.14159, .89, 56.0, 78., -3.0, 0.0

#### 指数形式

> 指数形式的格式由两部分组成：十进制小数形式或十进制整型常量部分和指数部分。
>
> 其中指数部分是在 e 或 E(相当于数学中幂底数 10)后跟整数阶码(即可带符号的整数指数)。例如：1e15 //表示数值 1×10150.35e+1 //表示数值 0.35×10178e-1 //表示数值 78×10-1
>
> 下面是不正确的实型常量。e15 //缺少十进制小数部分0.35e //缺少阶码78e-1.2 //不是整数阶码

### 字符

#### 字符常量

> 单撇号括起来的单个字符，如 'a'、'D'、'？'、'$'

#### 字符串常量

> 字符串常量是用“双撇号”括起来的多个字符的序列，如"How are you"、"I love you"、"你好"。当然，只要是“双撇号”括起来的，就算只有一个字符也叫字符串，如"a"。字符常量 'a'与字符串常量"a"是不同的。

## 相关库函数

### 字符处理函数(ctype.h)

#### int isalnum(int c)

> 该函数检查所传的字符是否是字母和数字。

#### int isalpha(int c)

> 该函数检查所传的字符是否是字母。

#### int islower(int c)

> 该函数检查所传的字符是否是小写字母。

#### int isspace(int c)

> 该函数检查所传的字符是否是空白字符。

#### int isxdigit(int c)

> 该函数检查所传的字符是否是十六进制数字。

#### int tolower(int c)

> 该函数把大写字母转换为小写字母。

#### int toupper(int c)

> 该函数把小写字母转换为大写字母。













### 数学处理函数(math.h)

#### 

### 字符串处理库函数(string.h)

#### char *strcpy(char *str1, const char *str2);

> 把字符串str2(包括'\0')拷贝到字符串str1当中，并返回str1

#### char *strncpy(char *str1, const char *str2, size_t count);

> 把字符串str2中最多count个字符拷贝到字符串str1中，并返回str1。如果str2中少于count个字符，那么就用'\0'来填充，直到满足count个字符为止。

#### char *strcat(char *str1, const char *str2);

> 把str2(包括'\0')拷贝到str1的尾部(连接)，并返回str1。其中终止原str1的'\0'被str2的第一个字符覆盖。

#### char *strncat(char *str1, const char *str2, size_t count);

> 把str2中最多count个字符连接到str1的尾部，并以'\0'终止str1，返回str1。其中终止原str1的'\0'被str2的第一个字符覆盖。
> 注意，最大拷贝字符数是count+1。

#### int strcmp(const char *str1, const char *str2);

> 按字典顺序比较两个字符串，返回整数值的意义如下：
> 小于0，str1小于str2；
> 等于0，str1等于str2；
> 大于0，str1大于str2；

#### int strncmp(const char *str1, const char *str2, size_t count);

> 同strcmp，除了最多比较count个字符。根据比较结果返回的整数值如下：
> 小于0，str1小于str2；
> 等于0，str1等于str2；
> 大于0，str1大于str2；

#### char *strchr(const char *str, int ch);

> 返回指向字符串str中字符ch第一次出现的位置的指针，如果str中不包含ch，则返回NULL。

#### char *strrchr(const char *str, int ch);

> 返回指向字符串str中字符ch最后一次出现的位置的指针，如果str中不包含ch，则返回NULL。



## break continue

### break

> 直接退出本次循环,用在`循环`语句和`switch`

```c
#include<stdio.h>
#include <stdio.h>
void main(){
	int i;
	printf("A ");
	for(i=0;i<10;i++){
		printf("%d ",i);
		break;
		printf("B ");
	}
	printf("C\n");
}
```

> A 0 C

### continue

> 跳过本次循环`continue`下面的语句,直接进行下面的语句

```c
#include<stdio.h>
#include <stdio.h>
void main(){
	int i;
	printf("A ");
	for(i=0;i<10;i++){
		printf("%d ",i);
		continue;
		printf("B ");
	}
	printf("C\n");
}

```

> A 0 1 2 3 4 5 6 7 8 9 C







































## 100题

### 统计在所输入的50个实数中有多少个正数、多少个负数、多少个零。

```c
#include<stdio.h>
void main()
{
	int pos_n=0,neg_n=0,zero=0,i,n;
	for(i=0;i<50;i++){
		scanf("%d",&n);
		if(n>0){
			pos_n++;
		}else if(n<0){
			neg_n++;
		}else if(n==0){
			zero++;
		}
	}
	printf("positive number=%d\nnegative number=%d\nzero=%d\n",pos_n,neg_n,zero);
}
```



### 计算并输出方程X2+Y2=1989的所有整数解。

```c
#include<stdio.h>
void main()
{
	int x,y,n=0;
	while((n*n)<=1989){
		n++;
	}
	for(x=-n;x<n;x++){
		for(y=-45;y<n;y++){
			if((x*x+y*y)==1989){
				printf("x=%d y=%d\n",x,y);
			}
		}
	}
}

```



### 输入一个10进制正整数，然后输出它所对应的八进制、十六进制数。

```c
#include<stdio.h>
void main()
{
	int n,o,h,oct[8],index=0;
	char hex[8];
	scanf("%d",&n);
	o=h=n;
	while(o>0){
		oct[index++]=o%8;
		o/=8;
	}
	index--;
	printf("八进制: ");
	for(;index>=0;index--){
		printf("%d",oct[index]);
	}
	printf("\n");
	index=0;
	while(h>0){
		n=h%16;
		hex[index++]=(n>9)?'a'+(n-9-1):'0'+n;
		h/=16;
	}
	index--;
	printf("十六进制: ");
	for(;index>=0;index--){
		printf("%c",hex[index]);
	}
	printf("\n");
}
```

### 一个数如恰好等于它的因子之和，这个数就称为“完数”。编程序找出1000以内的所有完数，并输出其因子（6是一个"完数"，它的因子是1,2,3）

```c
#include<stdio.h>
void main()
{
	int n,i,j=0,factor[1000]={0},sum=0;
	for(i=1;i<=1000;i++){
		for(n=1;n<i;n++){
			if(i%n==0){
				factor[j++]=n;
				sum+=n;
			}
		}
		if(sum==i){
			printf("完数: %d 因子为: ",sum);
			for(n=0;n<j;n++){
				if(factor[n]>0){
					printf("%d,",factor[n]);
				}
			}
			printf("\n");
		}
		j=0;
		sum=0;
	}
}
```



### 输入一个正整数，输出它的所有质数因子（如180的质数因子为 2、2、3、3、5）。

```c
#include<stdio.h>


bool isPrime(int n){
	int i;
	for(i=2;i<n;i++){
		if(n%i==0){return false;}
	}
	return true;
}
void main()
{
	int i,n;
	scanf("%d",&n);
	i=2;
	while(n>0){
		if( n%i==0 && isPrime(i) ){
            printf("%d ",i);
            n/=i;
        }
		else i++;
	}
}

```





### 输入20个整数存入一数组，输出其中能被数组中其它元素整除的那些数组元素

```c
#include<stdio.h>
#define N 20
void main()
{
	int i,n,a[N];
	for(i=0;i<N;i++){
		scanf("%d",&a[i]);
	}
	printf("\n");
	for(i=0;i<N;i++){
		for(n=0;n<N;n++){
			if(n!=i && a[i]>a[n] && a[i]%a[n]==0 ){
				printf("%d\n",a[i]);
				break;
			}
		}
	}
}
```



### 输入两个数组（数组元素个数自定），输出在两个数组中都出现的元素（如a[5]={2,3,4,5,6}，b[6]={3,5,7,9,10,-1}，则输出3、5）。

```c
#include<stdio.h>
#define N 5
#define M 6
void main()
{
	int a[N]={2,3,4,5,6},b[M]={3,5,7,9,10,-1},i,j;
	for(i=0;i<N;i++){
		for(j=0;j<M;j++){
			if(a[i]==b[j])printf("%d ",a[i]);
		}
	}

}

```



### 将字符数组S2中的全部字符拷贝到字符数组S1中（不用strcpy函数）。

```c
#include<stdio.h>
void main()
{
	char s1[10]="123123",s2[10];
	int i=0;
	while((s2[i]=s1[i])!='\0')i++;
	printf("%s\n",s2);
}
```



### 输入两个数组（数组元素个数自定），输出在两个数组中都不出现的元素（如a[5]={2,3,4,5,6}，b[6]={3,5,7,9,10,-1}，则输出2、4、6、3、7、9、10、-1）。

```c
#include<stdio.h>
#define N 5
#define M 6
void main()
{
	int a[N]={2,3,4,5,6},b[M]={3,5,7,9,10,-1},e,i,j;
	for(i=0;i<N;i++){
		e=1;
		for(j=0;j<M;j++){
			if(a[i]==b[j]){e=0;break;}

		}
		if(e)printf("%d,",a[i]);
	}
	for(i=0;i<M;i++){
		e=1;
		for(j=0;j<N;j++){
			if(b[i]==a[j]){e=0;break;}
		}
		if(e)printf("%d,",b[i]);
	}

}
```



### 给定年份year，判别该年份是否闰年（定义一个宏以判别该年份是否闰年）。

```c
#include<stdio.h>
#define LEAP_YEAR(y) y%400==0||y%4==0&&y%100!=0
void main()
{
	int i;
	for(i=1000;i<=2000;i++){
		if(LEAP_YEAR(i)){
			printf("%d\n",i);
		}
	}
}
```



### 输入一行小写字母后，将字母变成其下一字母（a变成b、b变成c、c变成d、…、x变成y、y变成z、z变成a）输出

```c
#include<stdio.h>
void main()
{
	int i=0;
	char string[10];
	scanf("%s",string);
	while(string[i]!='\0'){
		string[i]=(string[i]-97+1)%26+'a';
		i++;
	}
	printf("%s\n",string);
}
```



### 编写一个函数，处理n行、n列的二维数组：将每一行的元素同除以该行上绝对值最大的元素。

```c
#include<stdio.h>
#include<math.h>
void main()
{
	int a[3][4]={{1,-5,2,3},{3,5,-6,7},{9,8,10,-3}},max[4],i,j;
	for(i=0;i<3;i++){
		max[i]=a[i][0];
		for(j=1;j<4;j++){
			if(abs(max[i])<abs(a[i][j]))max[i]=a[i][j];
		}
	}
//	for(i=0;i<3;i++){printf("%d ",max[i]);}
	for(i=0;i<3;i++){
		for(j=0;j<4;j++){
			a[i][j]/=max[i];
		}
	}
	for(i=0;i<3;i++){
		for(j=0;j<4;j++){
			printf("%d ",a[i][j]);
		}
		printf("\n");
	}
}
```



### 编写函数，求任意阶多项式 a0+a1X+a2X2+...+anXn 的值并返回多项式的值。

```c

```



### 设计一个函数，使给出一个数的原码，能得到该数的补码。

```c
```













## 在转义字符后的数字一般表示八进制

> 所有的ASCII码都可以用"\"加数字（一般是8进制数字）来表示,还可以使用十六进制

```c
#include <stdio.h>
void main(){
    char c1='\110';
    printf("%c\n",c1);
}
```

输出

> H



## 在使用scanf对字符变量时,空格算作一个字符

```c
#include <stdio.h>
void main(){
    char c1,c2,c3;
    scanf("%c%c%c",&c1,&c2,&c3);
    printf("%d %d %d\n",c1,c2,c3,n1,n2);
}
```

输入: `A B`

输出:`65 32 66`











## C程序设计习题

### 程序设计和C语言

#### 第一题

> 链接：https://www.nowcoder.com/questionTerminal/aef2eb45d73f4cbb996c22efddb08188?orderByHotValue=1&mutiTagIds=569&page=1&onlyReference=false
> 来源：牛客网
>
> 程序是一组计算机能够识别和执行的指令。一个特定的指令序列用来完成一定的功能。 
>
>   程序设计是给出解决特定问题程序的过程，是软件构造活动中的重要组成部分。程序设计往往以某种程序设计语言为工具，给出这种语言下的程序。程序设计过程应当包括分析、设计、编码、测试、排错等不同阶段。

#### 第二题

> 为什么需要计算机语言：计算机语言解决了人和计算机交流是的语言问题，使得计算机和人都能识别
>
> 高级语言有哪些特点：
>
> 1.  高级语言的数据结构要比汇编和机器语言丰富；
> 2. 高级语言与具体机器结构的关联没有汇编以及机器语言密切；
> 3. 高级语言更接近自然语言更容易掌握；
> 4. 高级语言编写的程序要经过编译或解释计算机才能执行;

#### 第三题

> #### (1)源程序,目标程序,可执行程序。
>
>  源程序：指未编译的按照一定的程序设计语言规范书写的文本文件，是一系列人类可读的计算机语言指令
>
>  目标程序：为源程序经编译可直接被计算机运行的机器码集合，在计算机文件上以.obj作扩展名
>
>  可执行程序：将所有编译后得到的目标模块连接装配起来，在与函数库相连接成为一个整体，生成一个可供计算机执行的目标程序，成为可执行程序
>
> #### (2)程序编辑,程序编译,程序连接。
>
> 程序编辑：上机输入或者编辑源程序。
>
> 程序编译：
>
> - 先用C提供的“预处理器”，对程序中的预处理指令进行编译预处理
> - 对源程序进行语法检查， 判断是否有语法错误，直到没有语法错误未知
> - 编译程序自动把源程序转换为二进制形式的目标程序
>
> 程序连接：将所有编译后得到的目标模块连接装配起来，在与函数库相连接成为一个整体的过程称之为程序连接
>
> #### (3)程序,程序模块,程序文件。
>
> 程序：一组计算机能识别和执行的指令，运行于电子计算机上，满足人们某种需求的信息化工具
>
> 程序模块：可由汇编程序、编译程序、装入程序或翻译程序作为一个整体来处理的一级独立的、可识别的程序指令
>
> 程序文件：程序的文件称为程序文件，程序文件存储的是程序，包括源程序和可执行程序
>
> #### (4)函数,主函数，被调用函数,库函数。
>
> 函数：将一段经常需要使用的代码封装起来，在需要使用时可以直接调用，来完成一定功能
>
> 主函数：又称main函数，是程序执行的起点
>
> 被调用函数：由一个函数调用另一个函数，则称第二个函数为被调用函数
>
> 库函数：一般是指编译器提供的可在c源程序中调用的函数。可分为两类，一类是c语言标准规定的库函数，一类是编译器特定的库函数
>
> ##### (5)程序调试,程序测试。
>
> 程序调试：是将编制的程序投入实际运行前，用手工或编译程序等方法进行测试，修正语法错误和逻辑错误的过程
>
> 程序测试：是指对一个完成了全部或部分功能、模块的计算机程序在正式使用前的检测，以确保该程序能按预定的方式正确地运行

#### 第六题

```c
#include <stdio.h>
#define MAX(x,y) (x>y?x:y)
void main(){
	int i,j,k;
	scanf("%d%d%d",&i,&j,&k);
	printf("%d\n",MAX(i,MAX(j,k)));
}
```



### 算法

#### 第8题

```c
#include <stdio.h>
void main(){
	int year=1900;
	for(;year<=2000;year++){
		if(year%4==0&&year%100!=1 || year%400==0){
			printf("%d\n",year);
		}
	}
}

```





```c
#include <stdio.h>
void main(){
	int  i,a[10],max=0;
	for(i=0;i<10;i++){
		scanf("%d",a+i);
	}
	for(i=0;i<10;i++){
		max=max<a[i]?a[i]:max;
	}
	printf("max=%d\n",max);
}

```



### 顺序程序设计

#### 第一题

```c
#include <stdio.h>
void main(){
	double r=0.07,p=1.0+r;
	int n=10,i;
	for(i=1;i<n;i++){
		p*=(1+r);
	}
	printf("p=%lf\n",p);
}

```

#### 第二题

```c
#include <stdio.h>
#include <math.h>
void main(){
	double r,p;
	int n,i;


//一次存5年
	r=0.03;
	n=5;
	p=1000*(1+r*n);
	printf("p=%lf\n",p);
//先存2年,再存3年
	r=0.021;
	n=2;
	p=1000*(1+r*n);
	r=0.0275;
	n=3;
	p=p*(1+r*n);
	printf("p=%lf\n",p);
//先存三年,再存两年
	r=0.0275;
	n=3;
	p=1000*(1+r*n);
	r=0.021;
	n=2;
	p=p*(1+r*n);
	printf("p=%lf\n",p);
//连续
	r=0.015;
	n=5;
	p=1000*pow((1+r),n);
	printf("p=%lf\n",p);
//灵活
	r=0.0035;
	n=5;
	p=1000*pow((1+r/4),4*n);
	printf("p=%lf\n",p);
}

```













### 1.有1、2、3、4个数字，能组成多少个互不相同且无重复数字的三位数？都是多少？

```c
#include <stdio.h>
void main(){
	int i,j,k;
	for(i=1;i<=5;i++){
		for(j=1;j<=5;j++){
			for(k=1;k<=5;k++){
				if(i!=j&&j!=k&&k!=i){
					printf("%d%d%d\n",i,j,k);

				}
			}
		}
	}
}
```



### 3.一个整数，它加上100后是一个完全平方数，再加上168又是一个完全平方数，请问该数是多少？



```c
    
```







p84 1

```c
#include <stdio.h>
void main(){
	int weight;
	double cost=0.0;
	scanf("%d",&weight);
	if(weight>=100){
		cost = weight*0.05;
	}else{
		cost = 5 + 0.02 * (weight - 100);
	}
	printf("%lf\n",cost);
}
```



p84 9

```c
#include <stdio.h>
#include <math.h>
void main(){
	int n,i,j=0,count=0;
	scanf("%d",&n);
	int n1=n;
	while(n1!=0){
		count++;
		n1=n1/10;
	}
	for(i=0;i<count;i++){
		j+=(n%10)*(int)pow(10,count-1-i);
		n=n/10;
	}
	printf("%d\n",j);

}
```



p113 1

```c
#include <stdio.h>
#include <math.h>
void main(){
	int m,n,i,sum=1;
	printf("m=\n");
	scanf("%d",&m);
	printf("n=\n");
	scanf("%d",&n);
	for(i=2;i<=m+n;i++){
		sum *= i;
	}
	printf("%d\n",sum);
}
```

p113 2

```c
#include <stdio.h>
#include <math.h>
void main(){
	int i;
	for(i=1;i<=100;i++){
		if(i%7!=0) printf("%d\n",i);
	}
}
```

p113 3

```c
#include <stdio.h>
void main(){
	int i,sum,max;
	sum=0;
	i=0;
	while(sum<=1000){
		max = i;
		i++;
		sum+=i;
	}
	printf("%d \n",max);
}
```

p113 4

```c
#include <stdio.h>
void main(){
	int i,max,a[20];
	max = 0;
	for(i=0;i<20;i++){
		scanf("%d",a+i);
	}
	for(i=0;i<20;i++){
		if(max<*(a+i)) max=*(a+i);
	}
	printf("%d \n",max);
}
```

p113 5

```c
#include <stdio.h>
void main(){
	int i,j;
	for(i=0;i<4;i++){
		for(j=0;j<3-i;j++){
			printf(" ");
		}
		for(j=0;j<1+(2*i);j++){
			printf("*");
		}
		for(j=0;j<3-i;j++){
			printf(" ");
		}
		printf("\n");
	}
	for(i=2;i>=0;i--){
		for(j=0;j<3-i;j++){
			printf(" ");
		}
		for(j=0;j<1+(2*i);j++){
			printf("*");
		}
		for(j=0;j<3-i;j++){
			printf(" ");
		}
		printf("\n");
	}
	for(i=1;i<=5;i++){
		for(j=0;j<5-i;j++){
			printf(" ");
		}
		for(j=i;j>0;j--){
			printf("%d",j);
		}
		printf("\n");
	}
}
```

p113 7

```c
#include <stdio.h>
#include <math.h>
void main(){
	int i,sum,n,j;
	sum=0;
	for(i=100;i<1000;i++){
		n=i;
		sum = 0;
		for(j=0;j<3;j++){
			sum += pow(n%10,3);
			n=n/10;
		}
		if(i==sum){
			printf("%d\n",i);
		}
	}
}
```



p113 8

```c
#include <stdio.h>
#include <math.h>
void main(){
	float length=100.0;
	int i=0;
	while(length>=1.0){
		i++;
		length/=2;
	}
	printf("%d ",i);
}
```



p113 9

```c
#include <stdio.h>
#include <math.h>
void main(){
	int i,j,k,count=0;
	for(i=0;i<=100;i++){
		for(j=0;j<=50;j++){
			for(k=0;k<=20;k++){
				if(i+2*j+5*k==100){
					printf("1: %d 2:%d 5:%d \n",i,j,k);
					count++;
				}
			}
		}
	}
	printf("%d\n",count);
}
```









p113 11

```c
#include <stdio.h>
#include <math.h>
void main(){
	int i=0;
	double hight,sum=100.0;
	hight = 100.0;
	for(i=0;i<10;i++){
		hight /= 2;
		sum += hight*2;

	}
	printf("%lf %lf\n",sum,hight);
}
```





p113 11

```c
#include <stdio.h>
#include <math.h>
void main(){
	int i;
	double sum=0,pre=0.000001;
	for(i=0;i<64;i++){
		sum += pre;
		pre *= 2;
	}
	printf("%lf",sum/5);
}
```





p113 12

```c
#include <stdio.h>
#include <math.h>
void main(){
	int i,j,count=0;
	for(i=0;i<15;i++){
		for(j=0;j<15;j++){
			if(i!=j){
				count++;
			}
		}
	}
	printf("%d\n",count);
}
```



p113 13

```c
#include <stdio.h>
#include <math.h>
void main(){
	double sum=0.0;
	int i,n=0;
	for(i=1;i<=3;i++){
		n += i;
		sum += 1.0/n;
		printf("%d\n",n);
	}
	printf("%lf",sum);
}
```



p150 1

```c
#include <stdio.h>
#include <math.h>
void main(){
	int i,fibonacci[20]={1,1};
	for(i=2;i<20;i++){
		fibonacci[i]=fibonacci[i-1]+fibonacci[i-2];
	}
	for(i=0;i<20;i++){
		if(fibonacci[i]%2==0){
			printf("%d ",fibonacci[i]);
		}
	}
}
```

p150 2

```c
#include <stdio.h>
#include <math.h>
#define N 6
void main(){
	int n[N]={1,5,7,13,15,19},temp,i;
	for(i=0;i<N/2;i++){
		temp = n[i];
		n[i] = n[N-i-1];
		n[N-i-1] = temp;
	}
	for(i=0;i<N;i++){
		printf("%d ",n[i]);
	}
}
```





p150 3

```c
#include <stdio.h>
#include <math.h>
void main(){
	int n[6]={23,25,30,33,40,47},sum=0,i,p,min,average=0;
	for(i=0;i<6;i++){
		sum += n[i];
	}
	average = sum/6;
	min=n[0];
	p=0;
	for(i=0;i<6;i++){
		if(min>abs(average-n[i])){
			min = abs(average-n[i]);
			p=i;
		}
	}

	printf("%d %d\n",average,n[p]);
}
```

p184 5

```c
int fun(int n,int *sum){
	if(n==3){
		return (*sum)+1*2*3;
	}else{
		*sum += n*(n-1)*(n-2);
		return fun(n-1,sum);
	}

}
```



p184 6

```c
#include <stdio.h>
#include <math.h>

int max(int n1,int n2){ //最大公约数
	int i;
	for(i=(n1>n2?n2:n1);i>1;i--){
		if(n1%i==0&&n2%i==0){
			return i;
		}
	}
}


int min(int n1,int n2){
	int i;
	for(i=2;i<(n1>n2?n2:n1);i++){
		if(n1%i==0&&n2%i==0){
			return i;
		}
	}
}
void main(){
	printf("%d\n",min(15,6));

}
```

p184 7

```c
int fun(int x,int n,int *sum){
	if(n==1){
		return (*sum)*x;
	}else{
		*sum *= x;
		return fun(x,n-1,sum);
	}
}
```



p184 8

```c
int fun(int n,int *sum){
	int i;
	if(n==1){
		return *sum+1;
	}else{
		for(i=1;i<=n;i++){*sum+=i;}
		return fun(n-1,sum);
	}
}
```



p220 1

```c
void swap(int *a,int *b){
	int temp;
	temp = *a;
	*a = *b;
	*b = temp;
}
```



p220 3

```c
#include <stdio.h>
#include <math.h>

int* max(int *a,int *b){
	return *a>*b?a:b;
}

int* min(int *a,int *b){
	return *a<*b?a:b;
}

void main(){
	int i,j,k,*p1,*p2,*p3;
	scanf("%d %d %d",&i,&j,&k);
	p1=max(max(&i,&j),&k);
	p2=max(min(&i,&j),min(&j,&k));
	p3=min(min(&i,&j),&k);
	printf("%d %d %d\n",*p1,*p2,*p3);

}
```



p2204

```c
void huiwen(char *s,int n){
	int i=0,j;
	while(s[i++]!=0);
	j=i-2;
	for(i=0;i<n/2;){
		if(s[i++]==s[j--]){
		}else{
			printf("no");
			return;
		}
	}
	printf("yes");
}
```

p220 5

```c
#include <stdio.h>

bool scanf_plus(int *i,int length,int *n){
	int j,k;
	scanf("%d",&k);
	for(j=0;j<length;j++){
		if(i[j]==k){
			return false;
		}
	}
	*n = k;
	return true;
}


void main(){
	int l[10]={0};
	int n,i;
	int count = 0;
	bool b;
	while(count < 10){
		b = scanf_plus(l,10,&n);
		if(b==true){
			l[count++]=n;
		}else{
			printf("数组内有重复数字!\n");
		}
		for(i=0;i<count;i++){
			printf("%d ",l[i]);
		}
        printf("\n");
	}

}
```



p220 6

```c
#include <stdio.h>
#include <math.h>
#include <string.h>

void input_array(int *a,int length){
	int i;
	for(i=0;i<length;i++){
		scanf("%d",a+i);
	}
}

void copy_array(int *a,int *b,int length){
	int i;
	for(i=0;i<length;i++){
		b[i]=a[i];
	}
}


void main(){
	int a[10],b[10],i;
	input_array(a,10);
	copy_array(a,b,10);
	for(i=0;i<10;i++){
		printf("%d ",b[i]);
	}
	printf("\n");
	for(i=0;i<10;i++){
		printf("%d ",a[i]);
	}
}
```



p220 7

```c
#include <stdio.h>
void char_sort(char *c,int length){
	int i,j;
	char r;
	for(i=0;i<length;i++){
		for(j=i+1;j<length;j++){
			if(c[i]<c[j]){
				r=c[i];
				c[i]=c[j];
				c[j]=r;
			}
		}
	}
	for(i=0;i<10;i++){
		printf("%c ",c[i]);
	}
}


void main(){
	char c[10]={'c','j','e','d','a','i','h','b','f','g'};
	char_sort(c,10);
}
```



p220 9

```c
int str_len(char *c){
	int len=0;
	if(c==NULL){
		return 0;
	}
	while(c[++len]!='\0');
	return len;
	
}
```





## 反转100>=n>1000

```c
#include <stdio.h>
#include <math.h>
void main(){
	int n,i,j=0;
	scanf("%d",&n);
	if(n>=100 && n<1000){
		for(i=0;i<3;i++){
			j+=(n%10)*(int)pow(10,2-i);
			n=n/10;
		}
	}
	printf("%d\n",j);
}
```

```c
#include <stdio.h>
void main(){
	int n,j=0;
	scanf("%d",&n);
	if(n>=100 && n<1000){
		j+=n%10*100;
		n=n/10;
		j+=n%10*10;
		n=n/10;
		j+=n%10;
	}
	printf("%d\n",j);
}
```

