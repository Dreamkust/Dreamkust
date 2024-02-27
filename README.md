#include <stdio.h>
#include <malloc.h>

int MaximumElementNumber (const int *, int);
int ProductBetweenTwoZero(const int *, int);
int Conversion(const int *, int);
int Length(const int*, int);

int main()
{
    int choice = 0;
    int length = 0;
    printf ("Welcome, enter the length of your array: \n");
    scanf ("%d", &length);
    int *array=(int *) malloc (length * sizeof(int));
    printf ("Now input your numbers : \n");
    for (int i = 0; i < length; i++)
    {
        scanf ("%d", &array[i]);
    }

    printf ("If you want to see index of maximum element, enter 1: \n");
    printf("If you want to see Product between two zero equal, enter 2: \n");
    printf("If you want to see Conversion numbers by index, enter 3: \n" );
    printf("If you want to see maximum length of zero chain, enter 4: \n");
    scanf ("%d", &choice);
    if (choice == 1)
    {
        int res = MaximumElementNumber (array, length);
        printf ("Index maximum element equal: %d\n", res);
    }
    else if (choice == 2)
    {
        int res = ProductBetweenTwoZero(array, length);
        printf("Product between two zero equal: %d\n", res);
    }
    else if (choice == 3)
    {
        Conversion(array,length);
    }
    else
    {
        int res = Length(array,length);
        printf("maximum length of zero chain equals: %d", res);
    }
    return 0;

}

int MaximumElementNumber (const int *array, int length)
{
    int maxElement = array[0];
    int res = 0;
    for (int i = 1; i < length; ++i)
    {
        if (array[i] > maxElement)
        {
            maxElement = array[i];
            res = i;
        }
    }
    return res;
}

int ProductBetweenTwoZero (const int *array, int length)
{
    int res = 1;
    int zeros[1];
    int k = 0;
    for(int i = 0; i < length; ++i)
    {
        if (array[i] == 0)
        {
            zeros[k] = i;
            k += 1;
        }
    }
    if(k < 2) {
        printf("Not enough zeros in the array.\n");
        return 0;
    }
    else
    {
        int a = zeros[0];
        a += 1;
        int b = zeros[1];
        for(int i = a; i < b; ++i)
        {
            res *= array[i];
        }
    }
    return res;
}
int Conversion(const int *array, int lenght)
{
    int k1 = 0;
    int k2 = 0;
    int kk1 = 0;
    int kk2 = 0;
    int k = 0;
    for(int i = 0; i < lenght; i++) {

        if (i % 2 == 0)
        {
          k1+= 1;
        }
        else
        {
            k2 += 1;
        }
    }
    int chet[k1];
    int nechet[k2];
    for(int i = 0; i < lenght; i++) {

        if (i % 2 == 0)
        {
            chet[kk1] = array[i];
            kk1+=1;
        }
        else
        {
            nechet[kk2] = array[i];
            kk2+=1;
        }
    }
    int newmas[lenght];
    for(int i = 0; i < k2; i++)
    {
        newmas[i] = nechet[i];
    }
    for(int i = k2; i < lenght; i++)
    {
        newmas[i] = chet[k];
        k += 1;
    }
    printf("Your array: [");
    for(int i = 0; i < lenght; i++){
        printf("%d ",newmas[i]);
    }
    printf("]");
}

int Length(const int *array, int length){
    int res = 0;
    int max = 0;
    for(int i = 0; i < length; i++){
        if (array[i] == 0)
        {
            res += 1;
            if(res > max)
            {
             max = res;
            }
        }
        else
        {
            res = 0;
        }
    }
    return max;
}
