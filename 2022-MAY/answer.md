# AACS1084 May 2022 Answers

[Link to the paper](https://eprints.tarc.edu.my/21158/1/AACS1084.pdf)

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
    char telNo[12];
}Customer;
```

b)

```c
struct DateTime {
    int day, month, year, hour, minutes;
};
```

c)

```c
struct Reservation {
    Customer customer;
    struct DateTime arrival;
    int totalPax;
};
```

d)

```c
struct Reservation reserve = { {"Lily Tan", "012-3456789"}, {27, 5, 2022, 18, 30}, 8 };
```

e)

```c
printf("***Reservation Details***\n");
printf("Customer Name: %s\n", reserve.customer.name);
printf("Tel No: %s\n", reserve.customer.telNo);
printf("Arrival Date: %d-%d-%d\n", reserve.arrival.day, reserve.arrival.month, reserve.arrival.year);
printf("Arrival Time: %d:%d\n", reserve.arrival.hour, reserve.arrival.minutes);
printf("Total Pax: %d, reserve.totalPax);
}
```

f) (i)

```c
reserve.arrival.month = 9;
```

(ii)

```c
reserve.customer.name[0] = 'B';
```

(iii)

```c
struct Reservation reserveArr[50];
reserveArr[49] = reserve;
```

### Question 2
// Not yet done
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
