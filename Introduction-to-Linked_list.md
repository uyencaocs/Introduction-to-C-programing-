# Introduction Liked_list 
    when using Array, you will encounter problems:
        + Fixed array length
        + Consecutive elements(both an advantage and a disavantage) in case the is enough menory needed for an Array and they are not consecutive, the array cannot be used.
        + Inserting, editing, or deleting an element in array will affect all remaining elements(except when that element is at the end of the array)
        -----> To solve the problem of fixing array length, they create dynamic array. But if the number of elements in the array is too large , copying data to the dynamic array takes a lot of time 
        ***Linked_list was born to solve these problems.  
## what is Linked_list?
    Linked_list is an array not consecutive, a linked list consists of nodes where each node contains a data field and a reference(link) to the next node in the list.
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
    - A `struct Node` is defined to represent each node of the linked list. It consists of an integer value (`val`) and a pointer to the next node (`ptr`).
### struct is user-define data types that can be used to group items of possibly different types into a single type. 
    struct <struct name>{
        <data type> <name val>;
        <data type> <name val>;
        .....
    };

## Application to Linked_list:
   + Inserting 
   + Editing 
   + Deleting
   + Assesing 
### Inserting:
   + Push:
    ```
            #include <stdio.h>
            #include <stdlib.h>

            void push(struct Node** head, int data){
                struct Node* newnode = (struct Node*) malloc(1 * sizeof(struct Node)); 
                newnode->ptr = *head;  // Assigning the next pointer of the new node to the current head 
                *head = newnode;// updating the head pointer to poin to newnode (head is pointer to pointer and newnode is a pointer so change address of head need use operator (*))
                newnode->val = data; // assing the value of newnode
            } 
                int main(){
                struct Node* head;
                head = (struct Node*) malloc(1* sizeof( struct Node)); // allocating menory for head node  
                head->val = 15;
                head->ptr = (struct Node*) malloc(1* sizeof( struct Node));
                head->ptr->val = 35;
                head->ptr->prt = NULL;
                struct Node* tmp = head;// Creating a temporary pointer to traverse the linked list
                push(&head, 100); 
                for(;tmp != NULL; tmp = tmp->ptr){
                    printf("%d ", tmp->val); // tmp-> val la con tro tmp mang gia tri tai node val 
                }
                return 0;
            }
    ```
        Explanation:

        - A `struct Node` is defined to represent each node of the linked list. It consists of an integer value (`val`) and a pointer to the next node (`ptr`).
        - The `push` function takes a pointer to a pointer to a `struct Node` (`struct Node** head`) and an integer `data`. It allocates memory for a new node, assigns its value to `data`, sets its next pointer to the current head, and updates the head pointer to point to the new node.
        - In the `main` function:
        - Memory is allocated for the head node.
        - A value of 15 is assigned to the `val` member of the head node.
        - Memory is allocated for the next node.
        - A value of 35 is assigned to the `val` member of the next node.
        - The next pointer of the next node is set to `NULL`.
        - A temporary pointer `tmp` is created to traverse the linked list.
        - The `push` function is called to add a new node with a value of 100 to the linked list.
        - A loop is used to traverse the linked list, printing the value of each node.
            Question:
                * What is the operating principle of the push function in the above programming?
                * why to need use pointer-to-pointer(at head)?
            
    + Push_back:
            ```
                void push_back(struct Node* head, int data){
                    struct Node* node_back = (struct Node*) malloc(1 * sizeof(struct Node));
                    node_back->val = data;
                    struct Node* tmp = head;
                    while(tmp->ptr != NULL){
                        tmp = tmp->ptr;
                    }
                    tmp->ptr = node_back;
                    node_back->ptr = NULL;
                }
                        ```
            Allocate memory for a new node:

                struct Node* node_back = (struct Node*) malloc(sizeof(struct Node));
                This line allocates memory for a new node (node_back) using malloc. The size allocated is the size of struct Node.
                Assign the value to the new node:

                node_back->val = data;
                This line sets the value of the new node to the data parameter passed to the function.
                Create a temporary pointer to traverse the linked list:

                struct Node* tmp = head;
                This line initializes a temporary pointer tmp to the head of the linked list. This pointer will be used to traverse the list.
                Traverse the linked list until reaching the last node:

                while(tmp->ptr != NULL){ tmp = tmp->ptr; }
                This loop iterates through the linked list until tmp points to the last node, i.e., the node whose ptr member is NULL.
                Set the next pointer of the last node to point to the new node:

                tmp->ptr = node_back;
                Once the loop exits, tmp points to the last node of the linked list. This line sets the ptr member of the last node to point to the new node (node_back), effectively appending the new node to the end of the list.
                Set the next pointer of the new node to NULL:

                node_back->ptr = NULL;
                Finally, this line sets the ptr member of the new node to NULL, indicating that it is the last node in the list.
    
    + Push_at_index:
        ```
            void push_at_index(struct Node** head, int data, int index){
                struct Node* Node_ith = (struct Node*) malloc(1* sizeof(struct Node)); 
                Node_ith->val = data;
                Node_ith->ptr = NULL; //Node_ith is Null
                if(index == 0){ // if index = 0, push to head
                    Node_ith->ptr = *head; 
                    *head = Node_ith;
                    return;
                }
                struct Node* tmp = *head; //declares a temporary pointer point to head to nextnode
                for(int i = 0; i < index - 1; i++){ // assesing tmp to the node before the index 
                    tmp = tmp->ptr;// tmp point to next node
                }
                Node_ith->ptr = tmp->ptr;//pointe Node_ith point to ptr at tmp->ptr
                tmp->ptr = Node_ith; // assessing address of tmp
            }
        ```
### Deleting node:
+ Pop:
    ```
  int pop(struct Node** head){
    struct Node *tmp = *head;
    *head = tmp->ptr; //head points to next node
    int val_return = tmp->val;
    free(tmp);
    return val_return;
   }  
    ```
+ Pop_back:
   int pop_back(struct Node* head){
    struct Node* tmp = head;
    while(tmp->ptr->ptr != NULL){//tmp points to the node before the last node
        tmp = tmp->ptr; //tmp points to last node
    }
    int val_return = tmp->ptr->val;
    free(tmp->ptr);
    tmp->ptr = NULL;
    return val_return;
  }

### Editing:
   Just bring the ptr to the position that needs to changed and change the value

### Finding:
    Finding the node should use the algorithm linear search  