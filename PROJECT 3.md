
# CODSOFT Project 3
This is code for simple calculator using C++ language.
---
# Specifications-
calculator program that performs basic arithmetic
operations such as addition, subtraction, multiplication, and
division. Allow the user to input two numbers and choose an
operation to perform.
```C++
#include <iostream>
using namespace std;
int calculator(){
char op;
float num1, num2;
cout << "Enter an operator (+, -, *, /): ";
cin >> op;
cout << "Enter two numbers: " << endl;
cin >> num1 >> num2;
switch (op) {
case '+':
cout << num1 << " + " << num2 << " = " << num1 + num2;
break;
case '-':
cout << num1 << " - " << num2 << " = " << num1 - num2;
break;
case '*':
cout << num1 << " * " << num2 << " = " << num1 * num2;
break;
case '/':
cout << num1 << " / " << num2 << " = " << num1 / num2;
break;
default:
cout << "Error! The operator is not correct";
// operator doesn't match with any case constant (+, -, *, /)
break;
}
    
}



int main() {
    calculator();



return 0;
}
```



## Authors

- [@chitrangv27](https://github.com/chitrangv27)

