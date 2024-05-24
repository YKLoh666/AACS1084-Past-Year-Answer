<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

# AACS1084 September 2020 Answers

[Link to the paper](https://eprints.tarc.edu.my/16223/1/AACS1084.pdf)

- [Question 1](#question-1)
- [Question 2](#question-2)
- [Question 3](#question-3)
- [Question 4](#question-4)

## Answers

### Question 1

a) 

- A structure can store a group of variables with different data type, meanwhile, an array can only store a group of variables with one single data type.
- A structure can be returned by a function, meanwhile, an array cannot be returned by a function.

> Although we can't return an array, we can return the pointer to the array instead.  

b) (i)

```c
typedef struct {
	char cabinName[35];
	int noOfPax;
	double rate;
} Cabin;
```

b) (ii)

```c
Cabin cabinFA = {"Family A-Cabin", 4, 140.0};
```

c) (i)

```c
typedef struct {
	int guestId;
	char guestName[35];
	Cabin cab;
} Guest;
```

c) (ii)

```c
Guest guestA = {2166, "Chadwick", {"Mountain House", 8, 320.0}};
```

c) (iii)

```c
if (guestA.guestId == 2166) 
	guestA.cab.rate = 288.0;
```

### Question 2

a)

- The file is not exist when opened in read mode.
- The file has no enough space to be created when opened in write mode or append mode
- The file is being protected from reading and writing to
- The location specified is a directory or register.

b) (i)

```c
FILE *fPtr1, *fPtr2;
```

b) (ii)

```c
fPtr1 = fopen("guest.txt", "r");
fPtr2 = fopen("averageWeeklyGuest.txt", "w");
```

b) (iii)

```c
if (fPtr1 == NULL || fPtr2 == NULL) {
	printf("File(s) cannot be opened");
	exit(-1);	
}
```

b) (iv)

```c
int week;

while (fscanf(fPtr1, "%d\t", &week) != EOF) {
	double total = 0;
	int guest;
	for (int i = 0; i < 5; i++) {
		if (i != 5) fscanf(fPtr1, "%d\t", &guest);
		else fscanf(fPtr1, "%d\n", &guest);
		
		total += guest;
	}

	fprintf(fPtr2, "%d\t%.2f\n", week, total / 5);
}
```

### Question 3

a) (i)

```c
FILE* fPtr3;
```

a) (ii)

```c
fPtr3 = fopen("cabin.bin", "wb");
```

a) (iii)

```c
fprintf(&cabinCode, sizeof(int), 1, fPtr3);
fprintf(&bathroom, sizeof(char), 1, fPtr3);
fprintf(&rate, sizeof(double), 1, fPtr3);
```

a) (iv)

```c
fclose(fPtr3);
```

b)

```c
int readCode;
char readBathroom;

fread(&readCode, sizeof(int), 1, fPtr4);
fread(&readBathroom, sizeof(char), 1, fPtr4);

printf("Cabin Code: %d\n", readCode);
printf("Bathroom available? %c\n", readBathroom);
system("pause");
```

c)

Coupling is a measure of the strength of relation between two different modules. 

d)

- A module that changes one variable's value will affect the other module given that the module is shared by these modules
- The program is more error prone because higher chance of bad data to pass from one module to another.
- The module is hardly able to be reuse because it's heavy reliance to specific functionality that only existed in the other modules.

e) 

(i) Pathological Coupling

(ii) Data Coupling

(iii) Control Coupling

### Question 4

a)

- Much simpler to navigate between modules by categorising modules with folder structure.
- Separate modules with file and folders can isolate responsibility among the developers, ensure that each developer only able to access to the module in charged of, which enhance team's organisation.
- New modules can be developed in separate files to avoid affecting existing codebase.


b) (i)

```c
double computeBeforeDisc(int days) {
	return days * 70.0;
}
```

b) (ii)

```c
void computeAfterDisc(int days, double* afterDisc) {
	*afterDisc = 0.9 * (days * 70.0);
}
```
> Not sure if `*afterDisc = 0.9 * computeBeforeDisc(days);` is usable, because this introduces better modularity.

b) (iii)

```c
int main() {
	int days;
	double beforeDisc, afterDisc;

	printf("Enter days: ");
	scanf("%d", &days);

	beforeDisc = computeBeforeDisc(days);
	computeAfterDisc(days, &afterDisc);
	
	printf("Value before discount: %f\n", beforeDisc);
	printf("Value after discount: %f\n", afterDisc);
	system("pause");

	return 0;
}
```

c) 

```c
double computeBookingAverage(double b1[5]) {
	int total = 0;
	for (int i = 0; i < 5; i++) total += b1[i]
	return total / 5;
}
```
