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

12、三子棋游戏
文件1 game.h头文件
#define ROW 3
#define COL 3
//上述ROW COL可改为任意数
#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<string.h>
#include<math.h>
#include<stdlib.h>//srand
#include<time.h>//time
void InitBoard(char board[ROW][COL], int row, int col);
void DisplayBoard(char board[ROW][COL], int row, int col);
void PlayerMove(char board[ROW][COL], int row, int col);
void ComputerMove(char board[ROW][COL], int row, int col);
//玩家*  电脑#   平局Q    继续C
char IsWin(char board[ROW][COL], int row, int col);

文件2 game.c
#include "game.h"
void InitBoard(char board[ROW][COL], int row, int col)
{
	int i = 0;
	int j = 0;
	for (i = 0; i < row; i++)
	{
		for (j = 0; j < col; j++)
		{
			board[i][j] = ' ';
		}
	}
}

void DisplayBoard(char board[ROW][COL], int row, int col)
{
	int i = 0;
	for (i = 0; i < row; i++)
	{
		int j = 0;
		for (j = 0; j < col; j++)
		{
			printf(" %c ", board[i][j]);
			if (j < col - 1)
			{
				printf("|");
			}
		}
		printf("\n");
		if (i < row - 1)
		{
			for (j = 0; j < col; j++)
			{
				printf("---");
				if (j < col - 1)
				{
					printf("|");
				}
			}
		}
		printf("\n");
	}
}
/* |   |
---|---|---
   |   |
---|---|---
   |   |*/

void PlayerMove(char board[ROW][COL], int row, int col)
{
	int x, y;
	printf("玩家走:>\n");
	while (1)
	{
		printf("请输入坐标>:");
		scanf("%d%d", &x, &y);
		if ((x >= 1 && x <= row) && (y >= 1 && y <= col))
		{
			if (board[x - 1][y - 1] == ' ')
			{
				board[x - 1][y - 1] = '*';
				break;
			}
			else
			{
				printf("该坐标已被占用\n");
			}
		}
		else
		{
			printf("输入的坐标不合法！\n");
		}
	}
}

void ComputerMove(char board[ROW][COL], int row, int col)
{
	int x, y;
	printf("电脑走:>\n");
	while (1)
	{
		x = rand() % row;
		y = rand() % col;
		if (board[x][y] == ' ')
		{
			board[x][y] = '#';
			break;
		}
	}
}

int IsFull(char board[ROW][COL], int row, int col)
{
	int i, j;
	for (i = 0; i < row; i++)
	{
		for (j = 0; j < col; j++)
		{
			if (board[i][j] == ' ')
			{
				return 0;
			}
		}
	}
	return 1;
}

char IsWin(char board[ROW][COL], int row, int col)
{
	int i = 0;
	int j = 0; 
//判断每行
	for (i = 0; i < row; i++)
	{
		for (j = 0; j < col; j++)
		{
			if ((board[i][j] != board[i][0]) || (board[i][j] == ' '))
			{
				break;
			}
		}
		if (j == col)
		{
			return board[i][0];
		}
	}
//判断每列
	for (j = 0; j < col; j++)
	{
		for (i = 0; i < row; i++)
		{
			if ((board[i][j] != board[0][j]) || (board[i][j] == ' '))
			{
				break;
			}
		}
		if (i == row)
		{
			return board[0][j];
		}
	}
//判断斜向对角
	for (i = 0; i < row; i++)
	{
		if ((board[i][i] != board[0][0]) || (board[i][i] == ' '))
		{
			break;
		}
	}
	if (i == row)
	{
		return board[0][0];
	}

	for (i = 0; i < row; i++)
	{
		if ((board[i][row - 1 - i] != board[0][row - 1]) || (board[i][row - 1 - i] == ' '))
		{
			break;
		}
	}
	if (i == row)
	{
		return board[0][row - 1];
	}
//判断是否平局
	if (1 == IsFull(board, ROW, COL))
	{
		return 'Q';
	}
	else
	{
		return 'C';
	}
}

文件3 test.c
//三子棋游戏
#include "game.h"
void menu()
{
	printf("############################\n");
	printf("#######1.play  0.exit#######\n");
	printf("############################\n");
}

void game()
{
    /* |   |
	---|---|---
       |   |
	---|---|---
	   |   |*/
	char ret = 0;
	char board[ROW][COL] = { 0 };
	srand((unsigned int)time(NULL));
	InitBoard(board, ROW, COL);//初始化数组
	DisplayBoard(board, ROW, COL);//打印出棋盘
	
	while (1)
	{
		PlayerMove(board,ROW,COL);
		DisplayBoard(board, ROW, COL);
		ret=IsWin(board, ROW, COL);
		if (ret != 'C')
		{
			break;
		}
		ComputerMove(board, ROW, COL);
		DisplayBoard(board, ROW, COL);
		ret=IsWin(board, ROW, COL);
		if (ret != 'C')
		{
			break;
		}
	}

	if (ret == '*')
	{
		printf("玩家赢！\n");
	}
	else if (ret == '#')
	{
		printf("电脑赢！\n");
	}
	else
	{
		printf("平局！\n");
	}
}

void test()
{
	int input = 0;
	//使用do while 代码至少进行一次，适合游戏菜单部分，巧用input
	do
	{
		menu();
		printf("请选择是否游戏(1/0):>");
		scanf("%d", &input);
		switch (input)
		{
		case 1:
			printf("开始游戏！\n");
			game();
			break;
		case 0:
			printf("退出游戏！\n");
			break;
		default:
			printf("输入错误，请重新输入！\n");
			break;
		}
	} while (input);
}
//主函数在此
int main()
{
	test();
	return 0;
}

13、扫雷游戏
文件1 game.h
#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<string.h>
#include<math.h>
#include<stdlib.h>//srand
#include<time.h>//time

#define ROW 9
#define COL 9
#define ROWS ROW+2
#define COLS COL+2
#define easy_count 10

void InitBoard(char board[ROWS][COLS], int rows, int cols,char set);
void DisplayBoard(char board[ROWS][COLS], int row, int col);
void SetMine(char board[ROWS][COLS], int row, int col);
void FindMine(char mine[ROWS][COLS], char show[ROWS][COLS], int row, int col);

文件2 game.c
#include "game.h"

void InitBoard(char board[ROWS][COLS], int rows, int cols,char set)
{
	int i, j;
	for (i = 0; i < rows;i++)
	{
		for (j = 0; j < cols; j++)
		{
			board[i][j] = set;
		}
	}
}

void DisplayBoard(char board[ROWS][COLS], int row, int col)
{
	int i, j;
	for (i = 0; i <= row; i++)
	{
		printf("%d ", i);
	}
	printf("\n");
	for (i = 1; i <= row; i++)
	{
		printf("%d ",i);
		for (j = 1; j <= col; j++)
		{
			printf("%c ", board[i][j]);
		}
		printf("\n");
	}
}

void SetMine(char board[ROWS][COLS], int row, int col)
{
	int count = easy_count;
	while (count)
	{
		int x = rand() % row + 1;//1-9
		int y = rand() % col + 1;
		if (board[x][y] == '0')
		{
			board[x][y] = '1';
			count--;
		}
	}
}

int get_mine_count(char mine[ROWS][COLS], int x, int y)
{
	return (mine[x - 1][y - 1] +
		mine[x - 1][y] +
		mine[x - 1][y + 1] +
		mine[x][y - 1] +
		mine[x][y + 1] +
		mine[x + 1][y - 1] +
		mine[x + 1][y] +
		mine[x + 1][y + 1] - 8 * '0');
}


void FindMine(char mine[ROWS][COLS], char show[ROWS][COLS], int row, int col)
{
	int x, y;
	int win = 0;
	while (win<row * col - easy_count)
	{
		printf("请输入坐标:>");
		scanf("%d%d", &x, &y);
		if (x >= 1 && x <= row && y >= 1 && y <= col)
		{
			if (mine[x][y] == '1')
			{
				printf("很遗憾，你被炸死了！\n");
				DisplayBoard(mine, ROW, COL);
				break;
			}
			else
			{
				int count = get_mine_count(mine, x, y);
				show[x][y] = count + '0';
				DisplayBoard(show, ROW, COL);
				win++;
			}
		}
		else
		{
			printf("输入不合法，请重新输入！\n");
		}
	}
	if (win == row * col - easy_count)
	{
		printf("排雷成功\n");
	}
}

文件3 test.c
#include "game.h"

void game()
{
	printf("扫雷游戏开始！\n");
	//雷信息储存
	//1.布置好的雷的信息
	char mine[ROWS][COLS] = { 0 };
	//2.排查出的雷的信息
	char show[ROWS][COLS] = { 0 };
	InitBoard(mine, ROWS, COLS,'0');
	InitBoard(show, ROWS, COLS,'*');
	DisplayBoard(mine, ROW, COL);
	printf("\n");
	DisplayBoard(show, ROW, COL);
	SetMine(mine, ROW, COL);
	//DisplayBoard(mine, ROW, COL);
	FindMine(mine,show,ROW,COL);
}

void menu()
{
	printf("############################\n");
	printf("#######1.play  0.exit#######\n");
	printf("############################\n");
}

void test()
{
	int input = 0;
	srand((unsigned int)time(NULL));
	do
	{
	menu();
	printf("请选择:>");
	scanf("%d", &input);
	//对scanf的内容作出判断
	switch (input)
	{
	case 1:
		printf("开始游戏！\n");
		game();
		break;
	case 0:
		printf("结束游戏程序！\n");
		break;
	default:
		printf("选择输入错误，请重新输入！\n");
	}
	} while (input);
}

int main()
{
	test();
	return 0;
}

14、转置字符串
void reverse(char arr[6])
{
	char tmp = arr[0];
	int len = sizeof(arr)/sizeof(arr[0]);
	len = strlen(arr);
	arr[0] = arr[len - 1];
	arr[len - 1] = '\0';
	if (strlen(arr + 1) >= 2)
	{
		reverse(arr + 1);
	}
	arr[len - 1] = tmp;
}
int main()
{
	char arr[6] = "hello";
	reverse(arr);
	printf("%s\n", arr);
	return 0;
}

15、计算m的n次方
double calculate(int m, int n)
{
	if (0 == n)
	{
		return 1;
	}
	else if (n >= 1)
	{
		return m * calculate(m, n - 1);
	}
	else
	{
		return 1.0 / calculate(m, -n);
	}
}
int main()
{
	int m, n;
	scanf("%d%d", &m, &n);
	double ret = calculate(m, n);
	printf("ret=%lf\n", ret);
	return 0;
}

16、my_strcpy的最优解
char* my_strcpy(char* dest, const char* src)
{
	char* ret = dest;
	assert(dest != NULL);//保证了指针的有效性
	assert(src != NULL);
	while (*dest++ = *src++)
	{
		;
	}
	return ret;
}
int main()
{
	char arr1[] = "######";
	char arr2[] = "bit";
	printf("%s\n", my_strcpy(arr1, arr2));
	return 0;
}

17、打印*号问题
int main()
{
	int n;
	do
	{
		printf("Enter n>:");
		scanf("%d", &n);
	} while ((n%2==0)&&(n<0));
	for (int i = 1; i <= n; i += 2)
	{
		for (int j = 1; j <= (n - i) / 2; j++)
		{
			printf(" ");
		}
		for (int j = 1; j <= i; j++)
		{
			printf("*");
		}
		printf("\n");
	}
	for (int i = n-2; i >=1; i -= 2)
	{
		for (int j = 1; j <= (n - i) / 2; j++)
		{
			printf(" ");
		}
		for (int j = 1; j <= i; j++)
		{
			printf("*");
		}
		printf("\n");
	}
	return 0;
}

18、搬砖问题
int main()
{
	int n, men, children, women,count;
	printf("Enter n>:");
	scanf("%d", &n);
	count = 0;
	for (men = 0; men <= n / 3; men++)
	{
		for (women = 0; women <= n / 2; women++)
		{
			children = n - men - women;
			if ((men * 3 + women * 2 + children) == n)
			{
				printf("men=%d,women=%d,children=%d\n", men, women, children);
				count++;
			}
		}
	}
	return 0;
}

19、找零钱问题
int main()
{
	int money, flag;
	int n1, n2, n5;
	printf("Enter money>:");
	scanf("%d", &money);
	flag = 0;
	for (n5 = money / 5; (n5 >= 0) && (1 == flag);n5--)
	{
		for (n2 = (money - n5 * 5) / 2; (n2 >= 0) && (1 == flag); n2--)
		{
			for (n1 = money - n5 * 5 - n2 * 2; (n1 >= 0) && (1 == flag); n1--)

			{
				if (n1 + n2 * 2 + n5 * 5 == money)
				{
					flag = 1;
					printf;
				}
			}
		}
	}
	return 0;
}

20、
