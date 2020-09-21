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
