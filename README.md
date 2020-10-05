# CS140_DS_LAB
#include<stdio.h>
struct Student {
    int id;
    int age;
    int marks;
};
int main()
{
    int i;
    int n;
    struct Student stud[100];
    printf("Enter number of students\n");
    scanf("%d",&n);
    printf("Enter records of students\n");
    for(i=0;i<n;i++)
    {
        printf("Enter id, age and marks of student %d\n", i+1);
        scanf("%d %d %d",&stud[i].id, &stud[i].age, &stud[i].marks);
        if (stud[i].age<20||stud[i].marks>100||stud[i].marks<0)
        {
          printf("Invalid data\n");
        }
        else if (stud[i].marks>=65)
        {
            printf("Student is qualified\n");
        }
        else
        {
         printf("Student is not qualified\n");
        }
        return 0;
    }
}

//c program to convert infix to postfix
#include <stdio.h>
#include <string.h>
int F(char symbol)
{
  switch(symbol)
  {
    case '+':
    case '-': return 2;
    case '*':
    case '/': return 4;
    case '$':
    case '^': return 5;
    case '(': return 0;
    case '#': return -1;
    default: return 8;
  }
}
int G(char symbol)
{
  switch(symbol)
  {
    case '+':
    case '-': return 1;
    case '*':
    case '/': return 3;
    case '$':
    case '^': return 6;
    case '(': return 9;
    case ')': return 0;
    default: return 7;
  }

}
void infix_postfix(char infix[],char postfix[])
{
  int i,j,top;
  char s[40],symbol;
  top = -1;
  s[++top] = '#';
  j = 0;
  for(i=0;i<strlen(infix);i++)
  {
    symbol = infix[i];
    while(F(s[top])>G(symbol))
    {
      postfix[j] = s[top--];
      j++;
    }
      if(F(s[top])!=G(symbol))
      s[++top] = symbol;
      else
      top--;
  }
    while(s[top]!='#')
    {
      postfix[j++] = s[top--];
    }
    postfix[j] = '\0';
}
  void main()
 {
    int c1,c2;
    char infix[20];
    char postfix[20];
    printf("Enter the infix:\n");
    scanf("%s",infix);
    for(int k=0;k<strlen(infix);k++)
    {
        if(infix[k]=='(')
            c1++;
        else if(infix[k]==')')
            c2++;
        else
        continue;
    }
    if(c1!=c2)
    {
        printf("Invalid expression!");
        exit(0);
    }
    infix_postfix(infix,postfix);
    printf("The postfix is:\n");
    printf("%s\n",postfix);
  }

