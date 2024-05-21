# AACS1084 October 2022 Answers

[Link to the paper](https://eprints.tarc.edu.my/23317/1/AACS1084.pdf)

- [Question 1](#question-1)
- [Question 2](#question-2)
- [Question 3](#question-3)
- [Question 4](#question-4)

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
scanf("%f", &stf.salary);
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

d) (i)

```c
struct Company comList[15];
```

(ii)

```c
for(int i = 0;i < 15;i++) {
    printf("%s - %d\n", comList[i].name, comList[i].employee.id);
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
float month[3], average;

while(fscanf(fptr1, "%d\t", &year) != EOF)
{
	average = 0;
	for(int i = 0; i < 3;i++){
		fscanf(fptr1, "%f\t", &month[i]);
		average += month[i];
	}
	average /= 3;
	fprintf(fptr2, "%d\t%f\n", year, average);
}
```

### Question 3

a) (i)

```c
FILE *fCourse = fopen("expCourse.dat", "wb");
```

(ii)

```c
int index = 0;
for (int i = 1; i < 5; i++) {
  // if current course's fees more than the recorded greatest fee
  if (aryCourse[i].fees > aryCourse[index].fees) index = i;
}

fwrite(&aryCourse[index], sizeof(Course), 1, fCourse);
```

b)

```c
FILE *fptr = fopen("expCourse.dat", "rb");
Course mostExpCourse;

while(fread(&mostExpCourse, sizeof(Course), 1, fptr) != 0) {
	printf("Course Code : %s\n", mostExpCourse.code);
	printf("Course Title : %s\n", mostExpCourse.title);
	printf("Course Fees : %.2f\n", mostExpCourse.fees);
}
```

### Question 4

a)
```c
double getLoanAmount() {
	double loanAmount;
 	printf("Enter your loan amount : ");
  	scanf("%lf", &loanAmount);

   	return loanAmount;
}
```

b)

```c
void getCalculateInput(double *rate, int *year) {
	printf("Enter your loan interest rate : ");
	scanf("%f", rate);
	printf("Enter your loan tenure(year) : ");
	scanf("%d", year);
}
```

c)

```c
float calIntAmount(double loanAmount, double rate, int year) {
	double intAmount;
	intAmount = loanAmount * rate * year;

	return intAmount;
}
```

d)
```c
void main() {
	double loanAmount, rate, intAmount;
	int year;

	loanAmount = getLoanAmount();
	getCalculateInput(&rate, &year);
	intAmount = calIntAmount(loanAmount, rate, year);

	printf("\nInterest amount is RM%.2f\n", intAmount);

	system("pause");
}
```
