<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

# AACS1084 October 2023 Answers

[Link to the paper](https://eprints.tarc.edu.my/26826/1/AACS1084.pdf)

- [Question 1](#Question-1)
- [Question 2](#Question-2)
- [Question 3](#Question-3)
- [Question 4](#Question-4)

## Answers

### Question 1

a)

```c
struct Student {
    int id;
    char name[20];
    char gender;
    float cgpa;
};
```

b)

```c
struct Student = {1003, "Tan Lily", 'F', 3.75f};
```

c)

```c
typedef struct {
    char title[35];
    int groupNo;
    struct Student teamMember[250];
} Project;

Project myProject;
```

d)

```c
printf("Project Title > ");
scanf("%[^\n]", myProject.title);
printf("Group No. > ");
scanf("%d", &myProject.groupNo);
```

e)

```c
for (int i = 0; i < 250; i++) {
	printf("Student ID > ");
	scanf("%d", &myProject.teamMember[i].id);
	printf("Student Name > ");
	scanf("%[^\n]", myProject.teamMember[i].name);
	printf("Student Gender > ");
	scanf("%c", &myProject.teamMember[i].gender);
	printf("Student CGPA > ");
	scanf("%f", &myProject.teamMember[i].cgpa);
}
```

f)

```c
myProject.teamMember[4].cgpa = 3.80f;
```

### Question 2

a)

```c
FILE *fp1, *fp2;
```

b)

```c
fp1 = fopen("sales.txt", "r");

if (fp1 == NULL) {
	printf("File opening errors\n");
	exit(-1);
}
```

c)

```c
fp2 = fopen("saleaverages.txt", "w");
```

d)

```c
int week = 0;
double prod1, prod2, sumProd1 = 0.0, sumProd2 = 0.0;
while (fscanf(fp1, "%d\t%lf\t%lf\n", &week, &prod1, &prod2) != EOF) {
	sumProd1 += prod1;
	sumProd2 += prod2;
}

fprintf(fp2, "%f\t%f\n", sumProd1 / week, sumProd2 / week);
```

e)

```c
fclose(fp1);
fclose(fp2);
```

### Question 3

a)

- Text file stores human-readable characters, meanwhile binary file stores binary values which are not human-readable.
- Each line in text file end with newline (\n) character, meanwhile there is no lines in binary file.
- Text file written using a text stream, binary file written using a binary stream.

b)

i)

```c
FILE *ptrStudent;
```

ii)

```c
ptrStudent = fopen("student.bin", "wb");
```

iii)

```c
fwrite(name, sizeof(char), strlen(name), ptrStudent);
fwrite(&gender, sizeof(char), 1, ptrStudent);
fwrite(&age, sizeof(int), 1, ptrStudent);
```

iv)

```c
fclose(ptrStudent);
```

c)

```c
void computePerimeter(int length, int *perimeter) {
	*perimeter = length * 4;
}
```

### Question 4

a)
| static | auto |
| :----- | :--- |
| Variable allocated and initialised once at compile time | Variable stored on runtime stack |
| Persistent until program terminated instead of function terminated | Destroyed upon function terminated|

b)

```c
float findTotal(float payment[20], int limit) {
	float total = 0;
	for (int i = 0; i < 20; i++) {
		if (payment[i] > limit) total += payment[i];
	}
	return total;
}
```

c)
| coupling | cohesion |
| :------- | :------- |
| The measure of the strength of the relation between 2 modules | The measure of independence of the module |
| Data Coupling: Modules share data by passing parameters | Functional Cohesion: The function only perform one task |
| Common Coupling: Modules share a global structure | Coincidental Cohesion: Statements within the function have no meaningful relationship with each other |
