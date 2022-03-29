# C语言



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

