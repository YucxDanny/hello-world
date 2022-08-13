# hello-world
My first repository Yucx


int main()
{
	int age = 20;
	if (age < 18)
		printf("未成年\n");
	else
		printf("成年了");
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
