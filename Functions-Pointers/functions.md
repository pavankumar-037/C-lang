## C Functions
- A function is a block of code which only runs when it is called.
- It's grouping set of instruction lines placing in a block for performing specific operation/task
- Functions are mainly used for solving complex problems by diving program into many functions.
	- each function will perform specific job/task
- Functions are used to perform certain actions, Define the code once, and use it many times.
- We can pass data, known as parameters, into a function.
- We can return operational result from function blocks/body.
- **Advantages**
	- Organizes the code, increases readability
	- High degree of code re-using,
	- Increases Modularity.


### Types
**1. Pre-Defined Functions**
	- Defined by language developers.
	- With the help of predefined functions, we can decrease lot of redundant code.
	- main(), scanf(), printf(), getch(), putc(), putchar(), fgets() , strlen() , srqt()
	- These functions will come in the form of headerfiles.

 ```c
 int main() {  
printf("Hello World!");  
return 0;  
}
```
-----------------------------
2. **User Defined Functions**
	- Defined by us/we/programmers
	- In order to write user defined functions we have to follow special syntax
	- There will be two phases in functions.
		- declaration phase
		- calling phase.


syntax:
```c
datatype functionName(param1, param2, .... paramn) {
	//body of funtion.
}
```

Example: 

**declaration**
```c
void myFunction() {  
// code to be executed  
}
```

**calling**
```c
myFunction()
```
-   `myFunction()` is the name of the function
-   `void` means that the function does not have a return value. 
-   Inside the function (the body), add code that defines what the function should do

```c
void myFunction() { //declaration
  printf("I just got executed!");
}

int main() {
  myFunction(); //calling.
  return 0;
}
```



## Function Parameters

- Information can be passed to functions as a parameter. 
- Parameters are specified after the function name, inside the parentheses.
- Parameters act as variables inside the function.
- These are called local variables, will be created in **stack memory location**.
- Scope will be only within function body.

```c
returnType functionName(parameter1, parameter2, parameter3) {  
// code to be executed  
}
```

```c
void printName(char name[]) {
  printf("Hello %s\n", name);
}

int main() {
  printName("Avan");
  printName("Ram");
  printName("Christopher");
  return 0;
}
```

---------------------
**## Multiple Parameters**

- Inside the function, we can add as many parameters as we want.

```c
void printInfo(char name[], int rank) {
  printf("Hi am %s. i got %d rank\n", name, rank);
}

int main() {
  printInfo("Anusha", 3);
  printInfo("Anjali", 14);
  printInfo("Bhavya", 30);
  return 0;
}
```

**Note**
- Note that when you are working with multiple parameters, 
- the function call must have the same number of arguments as there are parameters, and the arguments must be passed in the same order.

----------------------------
**## Pass Arrays as Function Parameters**

```c
#include<stdio.h>

int sumOfArray(int nums[]) {
  int sum = 0;
  for (int i = 0; i < 5; i++) {
	sum = sum + nums[i];
  }
  return sum; //returns result to outside of fun body.
}

int main() {
  int myNumbers[5] = {10, 20, 30, 40, 50};
  int result = sumOfArray(myNumbers); //calling & storing result
  printf("sum of array elemets = %d", result);
  return 0;
}

```

**Predict the Output**

```c
void arrayOperation(int* nums, int n) {
    int temp = nums[0];
    nums[0] = nums[n-1];
    nums[n-1] = temp;
}

int main() {
  int myNumbers[5] = {10, 20, 30, 40, 50};
  int size = sizeof(myNumbers)/sizeof(myNumbers[0]);
  
  arrayOperation(myNumbers, size);

  printf("Array 1st element: %d", myNumbers[0]);

  return 0;
}
```

-----------------------------------

## Return Values
- To return values from function we use **return** keyword at last line in function body.
- If function doesn't any values, the return type/datatype of function must be int.
- For correct values, always 
	- return_type of function should be same as data type of returning value.
	
**Example-1**
```c
int someOperation(int x) {
  return 5 + x;
}

int main() {
  printf("Result is: %d", someOperation(3));
  return 0;
}
```

**Example-2**
```c
int add(int n1, int n2) {
    return n1+n2;
}

long long multiply(long long n1, long long n2) {
    return n1*n2;
}

double subtraction(double n1, double n2) {
    return n1-n2;
}

int modulus(int n1, int n2) {
    return n1%n2;
}


int main() {

  printf("addition : %d\n", add(5,8));
  printf("subraction: %lf\n", subtraction(6.8,2.1));
  printf("multiplication: %ld\n", multiply(939,289));
  printf("modulus: %d\n", modulus(7,2));

  return 0;
}
```

**Predict the output**

```c
int fun(n1,n2) {
    printf("%d", (n1+n2));
}
int main() {

  int res = fun(10,2);
  printf("%d", res);  
  return 0;
}
```


```c
#include<stdio.h>

void fun(n1,n2) {
    printf("%d", (n1+n2));
}
int main() {
  int res = fun(10,20);
  printf("%d", res);  
  return 0;
}
```


```c
#include<stdio.h>

int fun(n1,n2) {
    return n1 + (n2-n1)/2;
}
int main() {

  int res = fun(10,20) + fun(2,7);
  printf("%d", res);  
  return 0;
}
```



## FUNCTION PROTOTYPE
----------------------------------------------------------------------------------------------------------------------------

- A **_function prototype_** is used to declare the **_signature_** of a function, which includes its 
	- name
	- return type
	- parameters
- Function prototypes are important because they inform the compiler of the function's interface before it is called, allowing for proper type checking and error handling.
When a **_function prototype_** is included in a C program, the compiler checks that the function is used correctly before running the program. It helps to catch errors early on before the program is executed.
	- If a function is called with the wrong number or type of arguments, the compiler will generate an **_error message_**, preventing the program from crashing or behaving unexpectedly at runtime.



- **_Function prototypes_** also make it easier to read and understand the code


**Syntax**
```c
	return_type function_name(parameter_list);

```

**Example**
```c
	int add(int num1, int num2);
```

**Finding average of array elements**

```c
    #include <stdio.h>  
    float calculate_average(int arr[], int size);   // function prototype.
      
    int main() {  
        int arr[] = {1, 2, 3, 4, 5};  
        int size = sizeof(arr)/sizeof(arr[0]);
      
        float average = calculate_average(arr, size);   // function calling
		    printf("The average is: %.2f", average);  
    
        return 0;  
    }  
      
    float calculate_average(int arr[], int size) {  //function implementation
        float sum = 0.0;  
        for (int i = 0; i< size; i++) {  
            sum += arr[i];  
        }  
        return sum / size;  
    } 
```



### Default function prototypes:

If a function is called before it is **_defined_** or **_declared_**, the compiler will assume a default function prototype. 
The **_default function prototype_** assumes that the function returns an **_int_** and takes any number of arguments of any type.

```c
#include<stdio.h>
#include "calculator.h"
void printInfo() {
    printf("Hi.. am printInfo function :) , not taking any i/p.\n");
}
void main() {

    printInfo();
    printInfo("SaiMedha", 2023);
}

```


**Common case uses**

- Function prototypes are essential in large programs:
- Function prototypes can be declared in header files
- Function prototypes can be overloaded?
	- C does not support function overloading like some other programming languages as it is not OOPs language.
	- C supports indirectly with the help of _Generic keyword.





**Guess the output**

```c
#include<stdio.h>

float average(float,float);

void main() {
    average(22.6,23.7);
}

int average(float mathMark, float scienceMark) {
    float avg = (mathMark + scienceMark) / 2;
    printf("average: %f", avg);

} 
```

```c
#include <stdio.h>  
  
int factorial(int n);  
  
int main() {  
    int n = 5;  
    int result = factorial(n);  
	printf("%d! = %d\n", n, result);  
    return 0;  
}  
  
int factorial(int n) {  
    if (n == 0) {  
        return 1;  
    } else {  
        return n * factorial(n-1);  
    } 
}	
```
