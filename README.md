# Resizable Array
#include <stddef.h>
#include "array.h"



//typedef struct{
//    int *array;
//    int size;
//}Array;

Array a;

//创建数组
Array array_create(int intt_size)
{
    Array a;
    a.size = intt_size;
    a.array = (int *)malloc(sizeof(int)*intt_size);
    return a;
}
//释放内存
void array_free(Array *a)
{
    free(a->array);
    a->array = NULL;
    a->size  = 0;

}
//封装，得到数组大小
int array_size(const Array *a)
{
    return a->size;
}
//访问成员,返回指针方便赋值改变
int * array_at(Array *a,int index)
{
    return &(a->array[index]);
}
//改变大小
void array_inflate(Array *a,int more_size)
{
    int *p= (int *)malloc((a->size + more_size)*sizeof(int));
    int i;
    for(i=0; i<a->size; i++)
    {
        p[i] = a->array[i];
    }
    free(a->array);
    a->array = p;
    a->size += more_size;
}

int main(int argc, char const *argv[])
{
    Array a = array_create(100);
    printf("%d\n", array_size(&a));
    *array_at(&a,0) = 12;
    printf("%d\n", *array_at(&a,0));
    int n,cnt=0;
    while(1)
    {
        scanf("%d",array_at(&a,cnt++));
    }


    return 0;
}


