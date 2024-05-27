<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

# AACS1084 May 2023 Answers

[Link to the paper](https://eprints.tarc.edu.my/25082/1/AACS1084.pdf)

- [Question 1](#question-1)
- [Question 2](#question-2)
- [Question 3](#question-3)
- [Question 4](#question-4)

## Answers

### Question 1

a)

```c
struct Employee {
	int id;
	char name[20];
	char gender;
	float salary;
};
```

b)

```c
struct Employee john = {1001, "John Lee", 'M', 5000.0f};
```

c)

```c
typedef struct {
	char projName[35];
	int projId;
	struct Employee projMember[250];
	
} Project;

Project companyProj;
```

d)

```c
printf("Project Name> ");
scanf("%[^\n]", companyProj.projName);
printf("Project ID > ");
scanf("%d", &companyProj.projId);
```

e)

```c
for (int i = 0; i < 250; i++) {
	printf("Employee ID > ");
	scanf("%d", &companyProj.projMember[i].id);
	printf("Employee Name > ");
	scanf("%[^\n]", companyProj.projMember[i].name);
	printf("Employee Gender > ");
	scanf("%c", &companyProj.projMember[i].gender);
	printf("Employee Salary > ");
	scanf("%f", &companyProj.projMember[i].salary);
}
```

f)

```c
companyProj.projMember[4].salary = 2800.0f;
```

### Question 2

a)
- Text file stores human-readable character
- Each line in text file end with newline (\n) character
- Text file written using a text stream

b) i)

```c
FILE *fPtr1, *fPtr2;
```

b) ii)

```c
fPtr1 = fopen("temperature.txt", "r");
fPtr2 = fopen("averageTemp.txt", "w");
```

b) iii)

```c
if (fPtr1 == NULL || fPtr2 == NULL) {
	printf("Unable to open the file(s)");
	exit(-1);
}
```

b) iv)

```c
int week;

while (fscanf(fPtr1, "%d\t", &week) != EOF) {
	int sum = 0;
	int temperature = 0;
	for (int i = 1; i <= 7; i++) {
		if (i != 7) fscanf(fPtr1, "%d\t", &temperature);
		else fscanf(fPtr1, "%d\n", &temperature);

		sum += temperature;
	}

	fprintf(fPtr2, "%d\t%f\n", week, sum / 7.0); // use 7.0 to cast the result to double
}
```

### Question 3

a) i)

```c
FILE *fPtr3;
```

a) ii)

```c
fPtr3 = fopen("ticket.bin", "wb");
```

a) iii)

```c
fwrite(&category, sizeof(char), 1, fPtr3);
fwrite(&quantity, sizeof(int), 1, fPtr3);
fwrite(&price, sizeof(double), 1, fPtr3);
```

a) iv)

```c
fclose(fPtr3);
```

b)

- Variable and module identifier need to be pronounceable
- Variable and module identifier need to be short and meaningful
- Use suitable abbreviation to avoid confusion

c)

Coupling is a measure of a strength of relation between two modules. A system should have loose coupling to increase its maintainability.

d)   i) Control Coupling
    ii) Pathological Coupling
   iii) Data Coupling
    iv) External and Common Coupling

### Question 4

a)

```
30
31
40
45
31 45
```

b)

```c
void profitEarn(double sellingPrice, double costPrice, double* profit, double* markup) {
	*profit = sellingPrice - costPrice;
	*markup = *profit / costPrice x 100;
}
```

c)

| Variable | Storage Class | Scope |
|----------|---------------|-------|
| a | extern | 3-26 |
| b | extern | 7-10 |
| c | static | 12-26 |
| d | auto | 16-18 |
| e | extern | 20-26 |
| f | auto | 22-26 |
| g | static | 24-26 |

d) i)

```c
void square(int arrX[5]) {
	for (int i = 0; i < 5; i++) {
		arrX[i] *= arrX[i];
	}
}
```

d) ii)

```c
void main() {
	int arrX[5] = {1, 2, 3, 4, 5};
	square(arrX);
}
```
