# hello-world
My first repository,I'm Yucx from PRC.

#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<string.h>
#include<math.h>
#include<stdlib.h>
#include<time.h>

一、判断年龄
int main()
{
	int age = 20;
	if (age < 18)
		printf("未成年\n");
	else
		printf("成年了\n");
	return 0;
}
int main()
{
    int age = 0;
    scanf("%d", &age);
    if (age < 18)
        printf("少年\n");
    else if (age >= 18 && age < 30)
        printf("青年\n");
    else if (age >= 30 && age < 50)   
        printf("中年\n");   
    else if (age >= 50 && age < 80)    
        printf("老年\n");   
    else  
        printf("老寿星\n");
    return 0;
}

二、判断输出1-100之间的奇数
way1
int main()
{
	int i = 1;
	int a = 0;
	while (i < 101)
	{
		if (1 == i % 2)
		{
			printf("%d\n", i);
			a++;
		}
		i++;
	}
	printf("奇数共有%d个\n", a);
	return 0;
}
way2
int main()
{
	int i = 1;
	while (i < 101)
	{
		printf("%d ", i);
		i += 2;
	}
	return 0;
}

三、生成随机数的方式
int main()
{
	srand((unsigned int)time(NULL));
	int ret=rand();
	printf("%d\n", ret);
	return 0;
}
应用：玩猜数字游戏
//猜数字游戏
void menu()
{
	printf("***********************************\n");
	printf("***     1.play      0.exit      ***\n");
	printf("***********************************\n");
}
void game()
{
	int ret=rand()%100+1;
	int guess = 0;
	//用时间戳来设置随机数的生成起点
	//time_t time(time_t *timer)
	while (1)
	{
		printf("请输入数字>:");
		scanf("%d", &guess);
		if (guess < ret)
		{
			printf("猜小了！\n");
		}
		else if (guess > ret)
		{
			printf("猜大了！\n");
		}
		else
		{
			printf("恭喜你，猜对了！！！\n");
			break;
		}
	}
	
	
}
//时间戳 当前计算机时间减去计算机起始时间1970.1.1 0：0：0的秒数
int main()
{
	int input = 0;
	srand((unsigned int)time(NULL));
	do 
	{
		menu();
		printf("请选择:>");
		scanf("%d", &input);
		switch (input)
		{
		case 1:
			game();
			break;
		case 0:
			printf("退出游戏，程序结束！\n");
			break;
		default:
			printf("选择错误\n");
			break;
		}
	} while (input);
	return 0;
}

四、打印9*9乘法表
int main()
{
	int i = 0;
	int j = 0;
	for (i = 1; i <= 9; i++)
	{
		for (j = 1; j <= i; j++)
		{
			printf("%d*%d=%-2d ", i, j, i * j);//-2d左对齐  2d右对齐
		}
		printf("\n");
	}
	return 0;
}

五、二分查找
int main()
{
	int k = 0;
	printf("请输入待查找的目标：");
	scanf("%d", &k);
	int arr[] = { 1,2,3,4,5,6,7,8,9,10 };
	int i = 0;
	int sz = sizeof(arr) / sizeof(arr[0]);
	int j = sz - 1;
	int m = (i + j)/2;
	while (i <= j)
	{
		m = (i + j) / 2;
		if (arr[m] < k)
		{
			i = m + 1;
		}
		else if (arr[m] > k)
		{
			j = m - 1;
		}
		else
		{
			printf("找到了目标，下标为：%d", m);
			break;
		}
	}
	if (i > j)
	{
		printf("找不到目标");
	}
	return 0;
}

六、交换两个数（应用到传址函数）
void swap(int* x, int* y)
{
	int temp = *x;
	*x = *y;
	*y = temp;
}
int main()
{
	int i = 1;
	int j = 2;
	printf("i=%d j=%d\n", i, j);
	swap(&i, &j);
	printf("i=%d j=%d\n", i, j);
	return 0;
}

递归的简单应用
7、依次打印数字
void print(unsigned int n)
{
	if (n > 9)
	{
		print(n / 10);
	}
	printf("%d ", n % 10);
}
int main()
{
	unsigned int num = 0;
	printf("请输入要打印的数>:");
	scanf("%d", &num);
	print(num);
	return 0;
}

8、模拟strlen函数的功能
int my_strlen(char* str)
{
	if (*str != '\0')
		return (1 + my_strlen(str + 1));
	else
		return 0;
}
//int my_strlen(char* str)//模拟实现strlen
//{
//	int count = 0;
//	while(*str != '\0')
//	{
//		count++;
//		str++;
//	}
//	return count;
//}
int main()
{
	char arr[] = "bit"; //b i t \0
	//int len = strlen(arr);
	int len = my_strlen(arr);//arr是数组，传过去首元素的地址
	printf("len=%d\n", len);
	return 0;
}

9、汉诺塔问题
int tow(int n)
{
	int ret = 1;
	if (n > 1)
	{
		ret = tow(n - 1) * 2 + 1;
	}
	return ret;
}
int main()
{
	int n = 0;
	printf("请输入汉诺塔的阶数>:");
	scanf("%d", &n);
	int ret = tow(n);
	printf("需移动的次数为：%d\n",ret);
	return 0;
}

10、青蛙跳台阶问题
int frog(int n)
{
	if (n<2)
	{
		return 1;
	}
	else
	{
		return (frog(n - 1) + frog(n - 2));
	}
}
int main()
{
	int n = 0;
	printf("请输入青蛙跳跃的台阶数>:");
	scanf("%d", &n);
	int ret = frog(n);
	printf("青蛙共有%d种跳法\n",ret);
	return 0;
}

11、冒泡排序
void bubble_sort(int arr[], int sz)
{
	int i, j, flag;
	for (i = 0; i < sz - 1; i++)
	{
		flag = 1;
		for (j = 0; j < sz - 1 - i; j++)
		{
			if (arr[j] > arr[j + 1])
			{
				int temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
				flag = 0;
			}
		}
		if (1 == flag)
		{
			break;
		}
	}
}
int main()
{
	int arr[] = { 7,8,9,0,2,3,1,4,5,6 };
	int sz = sizeof(arr) / sizeof(arr[0]);
	int i = 0;
	bubble_sort(arr, sz);
	for (i = 0; i < sz; i++)
	{
		printf("%d ", arr[i]);
	}
	

	return 0;
}
