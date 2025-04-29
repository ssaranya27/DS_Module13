# EX 1 Display operator precedence in the infix expression.
## DATE:
## AIM:
To write a C program to find and display the priority of the operator in the given Postfix expression "(P%Q)/A*B^C+(R-S/U)+W^V".
## Algorithm
1.Start the program.
2.Define the priority() function to return the priority of operators.
3.Initialize the string containing operators and operands.
4.Loop through each character in the string.
5.For each operator, call the priority() function to determine its priority.
6.Print the operator and its corresponding priority level.
7.End.

## Program:
```
#include <stdio.h>
#include <ctype.h>

char stack[100];
int top = -1;

void push(char x) {
    stack[++top] = x;
}

char pop() {
    if (top == -1)
        return '\0'; 
    return stack[top--];
}

int priority(char x) {
    if (x == '^') return 3;  
    if (x == '*' || x == '/' || x == '%') return 2; 
    if (x == '+' || x == '-') return 1;
    return 0;
}

void IntoPost(char *exp) {
    char *e, x;
    e = exp;

    while (*e != '\0') {
        if (isalnum(*e)) {
            printf("%c ", *e);
        } 
        else if (*e == '(') {
            push(*e);
        } 
        else if (*e == ')') {
            while ((x = pop()) != '(') {
                printf("%c ", x);
            }
        } 
        else { 
            while (top != -1 && priority(stack[top]) >= priority(*e)) {
                if (*e == '^' && stack[top] == '^') 
                    break;
                printf("%c ", pop());
            }
            push(*e);
        }
        e++;
    }

    while (top != -1) {
        printf("%c ", pop());
    }
}

int main() {
    char exp[] = "(P%Q)/A*B^C+(R-S/U)+W^V";
    IntoPost(exp);
    printf("\n");
    return 0;
}

```

## Output:
## SAMPLE OUTPUT:
![image](https://github.com/user-attachments/assets/e82e4557-be7b-4f8f-9a20-7c9170f10a40)

## EXPECTED OUTPUT:

![image](https://github.com/user-attachments/assets/9fa4c8ab-8955-49fe-9536-2316d2630bbd)

## Result:
Thus the C program to find and display the priority of the operator in the given Postfix expression is implemented successfully
