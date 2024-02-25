# Introduction to Pointer 
## A pointer is an independent valriable used to stores menory address of another variable as its value
   ## <data type>* name --> declar pointer 
    data type of poiner to same data type of val
    **void can point any data types(bult-in)**
    operater & used together pointer valriable to get the menory address
    ex:
    ```
    #include <stdio.h>
    int main(){
        int val1 = 15;
        int* prtint = &val1;
        float val2 = 3.14;
        float* ptrf = &val2;
        prinft ("%p ", &prtint);
        printf("%p ", &prtf);
        return 0;
    }
    ```
    operater * used with pointer variable to get the value what pointer point to variable
    ```
     #include <stdio.h>
    int main(){
        int val1 = 15;
        int* prtint = &val1;
        prinft ("%p ", &prtint);
        printf("%n ", *ptrint);
        return 0;
    }
    ```
### A pointer can stores multiple memory addresses
## Pointer application
### Passing Arguments by reference:
    ```
    void change_val(int* a, int*b){
        int termp = *a;
        *a = *b;
        *b = termp;
    }
    int main(){
        int a = 15;
        int b = 12;
        change_val(&a, &b);
        printf("%d %d", a,b);
        return 0;
    }
    ```
### Accessing array elements
    ```
    #include <stdio.h>
    int main(){
        int array = {4, 6, 7, 8, 12};
        printf("%d ", array[2]); // day la cach thong thuong
        printf("%d ", *(array + 2)); //in gia tri tai vi tri thu 2 cua array 
                                     // array la 1 con tro voi dia chi cua no la dia chi phan tu dau tien trong mang
        return 0;
    }
    ```
    
## Dynamic array and pointer 
   
