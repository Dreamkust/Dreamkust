#include <stdio.h>
int MaximumElementNumber(const int*, int);

int main()
{
int choice = 0;
int length = 0;
printf("Добро пожаловать, введите длину вашего массива: \n");
scanf("%d", &length);
int array[length];
printf("А теперь, заполните его числами: ");
for(int i = 0; i < length; i++) {
scanf("%d", &array[i]);
}

printf("Чтобы найти номер максимального элемента в массива, введите 1");
scanf("%d",&choice);
if(choice == 1)
{
int res = MaximumElementNumber(array, length);
printf("Индекс максимального элемента: %d", res);
}
return 0;
}

int MaximumElementNumber(const int* array, int length)
{
int maxElement = array[0];
int res = 0;
for(int i = 1; i < length; ++i)
{
if(array[i] > maxElement)
{
maxElement = array[i];
res = i;
}
}
return res;
}
