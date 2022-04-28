# Performance-Evaluation
Performance Evaluation

## Populating an Array using random() function

```C
#include <stdio.h>
#include <stdlib.h>
int main()
{

    long *data;
    long num=100000, j;
    data = (long *)malloc(sizeof(long)*num);
    if(data != NULL)
    {
        for(j = 0; j < num; j++)
        {
            data[j] = rand()%100;
        }
    }

    for(j = 0; j < num; j++)
    {
        printf("%ld\n",data[j]);
    }
    
    free(data);
    return 0;

}

```

## Estimating the Time Taken to Complete execution of a program block

```C
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

float timedifference_msec(struct timeval t0, struct timeval t1)
{
    return (t1.tv_sec - t0.tv_sec) * 1000.0f + (t1.tv_usec - t0.tv_usec) / 1000.0f;
}

int main(void)
{
   struct timeval t0;
   struct timeval t1;
   float elapsed;
   
   long *data;
   long num=100000000, j;
   data = (long *)malloc(sizeof(long)*num);

   gettimeofday(&t0, NULL);
   if(data != NULL)
    {
        for(j = 0; j < num; j++)
        {
            data[j] = rand()%100;
        }
    }
   gettimeofday(&t1, NULL);

   elapsed = timedifference_msec(t0, t1);

   printf("Code executed in %f milliseconds.\n", elapsed);

   return 0;
}
```
