# Introduction Liked_list 
    when using Array, you will encounter problems:
        Fixed array length
        Consecutive elements(both an advantage and a disavantage) in case the is enough menory needed for an Array and they are not consecutive, the array cannot be used.
        Inserting, editing, or deleting an element in array will affect all remaining elements(except when that element is at the end of the array)
        -----> To solve the problem of fixing array length, they create dynamic array. But if the number of elements in the hard array is too large , copying data to the dynamic array takes a lot of time 
        ***Linked_list was born to solve these problems.  
## what is Linked_list?
    Linked_list is an array not consecutive, with an elements is a node, a linked list consists of nodes where each node contains a data field and a reference(link) to the next node in the list.
    + The consecutive elements are connected by pointers.
    + The size of a linked list is not fixed.
    + The last node of the linked list points to null.
    + Memory is not wasted but extra memory is consumed as it also uses pointers to keep track of the next successive node.
    + The entry point of a linked list is known as the head. 
    *** Advantage:
        + The elements are not adjacent to each other
        + Inserting, editing, deleting a node only needs to affect the previous node and the following node
        + Insert continously at the begining of the table(applied to the priority queue problem)
        Disadvantage:
        + Cannot use random access
    ***
### How to declare and use linked_list
----------------
    ```
    #intclude <stdio.h>
    #include  <stdlib.h>
    struct Node{ //2 thanh phan value vs địa chỉ 
        int val;
        Node* ptr;
    };

    int main(){
        struct Node* head;
        head = (Node*) malloc(1*sizeof(Node)); //head đang trỏ tới node đâù tiền 
        head->val = 15;
        head->ptr = (Node*) malloc(1*sizeof(Node));
        head->ptr->val = 35;
        head->ptr->ptr = (Node*) malloc(1*sizeof(Node));
        head->ptr->ptr->val = 45;
        head->ptr->ptr->ptr = NULL; //mất thằng đầu mất luôn danh sách 
        struct Node* tmp = head;
        for(;tmp != NULL; tmp = tmp->ptr){
            printf("%d ", tmp->val); 
        }
        return 0; 
    }
    ```
### struct is user-define data types that can be used to group items of possibly different types into a single type. 
    struct <struct name>{
        <data type> <name val>;
        <data type> <name val>;
        .....
    };

