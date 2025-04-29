# Ex2 Conversion of the infix expression into postfix expression
## DATE: 29/04/2025
## AIM:
To write a C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule.

## Algorithm
1. Start the program. 
2. Initialize a stack and set the top index to -1. 
3. Define the push() and pop() functions to add and remove elements from the stack. 
4. Define the priority() function to assign priorities to operators. 
5. Traverse the expression in the IntoPost() function, handling operands, parentheses, and 
operators. 
6. After processing the expression, pop and print any remaining operators from the stack. 
7. End.

## Program:
```
/*
Program to convert the infix expression into postfix expression
Developed by: SARANYA S.
RegisterNumber:  212223220101
*/
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
    char exp[] = "2*3%(2-1)+5|3";
    IntoPost(exp);
    printf("\n");
    return 0;
}

```

## Output:

## SAMPLE OUTPUT:
![image](https://github.com/user-attachments/assets/8f95471e-9a92-4e6f-b747-1e1e30495064)

## OUTPUT:

![image](https://github.com/user-attachments/assets/f6ffd100-9cf3-4a81-8b16-b55ea68d7c46)

## Result:
Thus, the C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule is implemented successfully.
