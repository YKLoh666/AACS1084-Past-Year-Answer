<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

# AACS1084 October 2021 Answers

[Link to the paper](https://eprints.tarc.edu.my/20030/1/AACS1084.pdf)

- [Question 1](#question-1)
- [Question 2](#question-2)
- [Question 3](#question-3)
- [Question 4](#question-4)

## Answers

### Question 1

a) (i)

```c
struct Date {
	int month;
	int day;
	int year;
};
```

a) (ii)

```c
struct Date regDate, payDueDate;
```

b) (i)

```c
typedef struct {
    char programmeTitle[50];
    int mqfLevel;
    double fees;
} Programme;
```

b) (ii)

```c
Programme dft;
strcpy(dft.programmeTitle, "Diploma in Information Technology");
dft.mqfLevel = 4;
scanf("%lf", &dft.fees);
```

b) (iii)

```c
typedef struct {
    char studentID[8];
    char studentName[40];
    Programme prog;
} Student;
```

### Question 2

a)

```c
FILE *fp1, *fp2;
```

b)

```c
fp1 = fopen("attendance.txt", "r");
if (fp1 == NULL) {
	printf("File opening errors");
	exit(-1);
}
```

c)

```c
fp2 = fopen("attnAverage.txt", "w");
```

d)

```c
int day, classA, classB;
double totalA = 0, totalB = 0;

while (fscanf(fp1, "%d\t%d\t%d\n", &day, &classA, &classB) != EOF) {
	totalA += classA;
	totalB += classB;
}

double avgA = totalA / day;
double avgB = totalB / day;

fprintf(fp2, "%.1f\t%.1f\n", avgA, avgB);
```

e)

```c
fclose(fp1);
fclose(fp2);
```

### Question 3

a)
- Binary files stores binary values which are not human readable.
- Binary files does not separate the contents in lines.
- Binary files are written using binary stream.

b) i)

```c
FILE* ptrMember;
```

b) ii)

```c
ptrMember = fopen("member.bin", "wb");
```

b) iii)

```c
fwrite(&status, sizeof(char), 1, ptrMember);
fwrite(customerName, sizeof(char), strlen(customerName), ptrMember);
fwrite(&memberID, sizeof(int), 1, ptrMember);
```

c)

| Pass by Value | Pass by Address |
| ------------- | --------------- |
| When a parameter is passed during a function call, a new variable will be allocated and initialized with the value copied from the parameter passed | The parameter's memory address is being passed during a function call, allowing the function to access to the memory of the same variable |
| Modifying the parameter within the function will not modify the variable that is being passed as a parameter during function call | Modifying the parameter within the function will also modify the variable that is passed as a parameter during function call due to the variables shares a single memory address |

d)

```c
void myFormula(int B, int C, int* A) {
	*A = B * C;
}
```

### Question 4

a)
| static | auto |
| ------ | ---- |
| Variable allocated and initialised once at compile time | Variable stored on runtime stack |
| Persistent until program terminated instead of function terminated | Destroyed upon function terminated|

b)

```c
float donation(float funds[20], float target) {
	float totalFunds = 0;
	for (int i = 0; i < 20; i++) {
		totalFunds += funds[i];
	}
	if (totalFunds > target) return totalFunds;
	return 0;

	// OR return totalFunds > target ? totalFunds : 0;
}
```

c)
| coupling | cohesion |
| :------- | :------- |
| The measure of the strength of the relation between 2 modules | The measure of independence of the module |
| Data Coupling: Modules share data by passing parameters | Functional Cohesion: The function only perform one task |
| Common Coupling: Modules share a global structure | Coincidental Cohesion: Statements within the function have no meaningful relationship with each other |
