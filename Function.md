# Simple function:
## Definition:
    + A function group a number of program statements into a unit and give it name. This unit can then be invoked from other parts of the program.
    + why:   -define the code one 
             - use it many times
    
## Create a function and call functions:
   + To create (often referred to as declare) your own function, specify the name of the function, followed by parentheses () and curly brackets {}.
   ```
   void create_New_function(//parameters){
    // code to be executed
   }
   ```
   + Declared functions are not executed immediately. They are saved for later used. And just call it when use.
### A function can be called many timnes
    To call a function, write the function's name followed by two parentheses () and a semicolon ; 
   int main(){
    ....
    ....
    create_New_function(//parameter);
   }
***
DECLARETION :  Specifies function name, argument types, and return valuse.
CALL:          Cause the function to be executed 
Definition:    The function itself.Contains the lines of code that constisute the function.
Declarator:    The firts line of definition
***
## Passing Arguments to funtions:
### Pass by Value:
   The function creates new variables to hold the values of these variable argument. The functions get these new variables name and data types of the parameters specified in the declarator.
   ```
   #include <stdio.h>
   int return_val(int val4, int val5){
      val 3 = val4 - val5;
      return val3;
   }
   int main(){
      int val1 = 145;
      int val2 = 564;
      int val4 = return_val(val1, val2);
      int val5 = return_val(va2, val1);
      printf("%d %d", val4 val5);
      return 0;
      }
   ```
### Passing pointer:
   Using pointer to stores address of arguments 
   

    
