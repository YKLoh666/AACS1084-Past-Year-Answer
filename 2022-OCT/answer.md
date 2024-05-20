# AACS1084 October 2023 Answers

[Link to the paper](https://eprints.tarc.edu.my/23317/1/AACS1084.pdf)

- [Question 1](#Question-1)
- [Question 2](#Question-2)
- [Question 3](#Question-3)
- [Question 4](#Question-4)

## Answers

### Question 1

a)

```c
typedef struct {
    char name[35];
    int id;
    float salary; // double is also acceptable
}Staff;
```

b)

```c
Staff stf;

strcpy(stf.name, "Wong King Hong");
stf.id = 1234;
printf("Please enter the salary : ");
scanf("%f", stf.salary);
```

c)

```c
struct Company {
    char name[35];
    char regNum[35];
    char ranking;
    Staff employee;
};
```

d) 

(i)

```c
struct Company comList[15];
```

(ii)

```c
for(int i = 0;i < 15;i++) {
    printf("%s - %d\n", comList[i].name, comList.employee.id);
}
```

### Question 2

a)

```c
FILE *fptr1, *fptr2;
fptr2 = fopen("AverageSales.txt", "w");
```

b)

```c
fptr1 = fopen("Qsales.txt", "r");

if (fptr1 == NULL) {
	printf("File opening error\n");
	exit(-1);
}
```

c)

```c
int year;
float month[3], average = 0;

while(fscanf(fptr1, "%d\t", year) != EOF)
{
	for(int i = 0; i < 3;i++){
		fscanf(fptr1, "%f\t", month[i]);
		average += month[i];
	}
	fprintf(fptr2, "%d\t%f\n", year, average);
}
```

### Question 3

a)

(i)

```c
FILE *fCourse = fopen("expCourse.dat", "wb");
```

(ii)

```c
// not yet done
```

b)
// not yet done

### Question 4

a)
// not yet done

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

d)

