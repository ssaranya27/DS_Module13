# EX3 Implementation of Tower of Hanoi
## DATE:
## AIM:
To write a C program to implement Tower of Hanoi

## Algorithm

1. If n > 0, proceed; otherwise, stop (base condition for recursion).

2. Recursively move n-1 disks from source peg x to auxiliary peg z, using destination peg y as a helper.

3. Print the move: move the largest (current) disk from source peg x to destination peg y.

4. Recursively move the n-1 disks from auxiliary peg z to destination peg y, using source peg x as a helper.

5. In main(), read the number of disks n, and call TOH(n, 'A', 'B', 'C') to start the process.

## Program:
```
#include<stdio.h>
void TOH(int n,char x,char y,char z)
{
  // Write your code here 
  if(n>0){
      TOH(n-1,x,z,y);
      printf("%c to %c\n",x,y);
      TOH(n-1,z,y,x);
  }
}
int main()
{
   // Write your code here 
   int n;
   scanf("%d",&n);
   TOH(n,'A','B','C');
}
```

## Output:

SAMPLE OUTPUT:
![image](https://github.com/user-attachments/assets/3c4f04c1-7a9f-49ee-8e28-78079f05a4f4)

EXPECTED OUTPUT:
![image](https://github.com/user-attachments/assets/130aaf26-2173-4b83-9974-7df709ecf49c)

## Result:
Thus, the C program to implement Tower of Hanoi using recursion is implemented successfully.
