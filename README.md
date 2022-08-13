# hello-world
My first repository Yucx

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
