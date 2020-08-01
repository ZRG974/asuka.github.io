//关于 数组 指针 函数（const int ）

#include <stdio.h>

int sum (int ar[],int n);
int sam (int const ar[],int n);

int main() {
	
int ch[5]={1,2,3,4,5,};
int *sh=&ch[0]; 	// int *sh=ch;

//int rh=ch; 错误 

int num=0; 
int *rh=&num;
 

int n;
	
for(n=0;n<5;n++){
		printf("%3d",ch[n]);
	
}
putchar('\n');
for(n=0;n<5;n++){
		printf("%3d",sh[n]);
	
}
putchar('\n');
	
printf("%d\n",sum(ch,5));  		//printf("%d\n",sum(&ch[0],5));

printf("%d\n",sam(sh,5));  	//Error ld returned 1 exit status 
	
for(n=0;n<5;n++){
		printf("%3d",ch[n]);
	
}
putchar('\n');


printf("%d\n",sum(sh,5));		//证明 sh指针仍指向 ch数组（sh与ch相同？） ，所以输出为ch数组递增后的结果 

printf("%d\n",sum(rh,5));		//可运行 


	return 0;
}



  int sum(int *ar,int n)		// int sum(int ar[],int n)
  {
  	int i;
  	int total =0;
  	for (i=0;i<n;i++){
  		total +=ar[i]++;  		//wrong 破坏了原数组的值 
  	}
  	return total;1
  }
  
  
   int sam(const int ar[],int n)	//const int 保护原数组的值 
  {
  	int i;
  	int total =0;
  	for (i=0;i<n;i++){
  		total +=ar[i]; 		 //total +=ar[i]++; 编译不通过 
  	}
  	return total;
  }
