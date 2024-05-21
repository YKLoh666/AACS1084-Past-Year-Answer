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
a)

```c
FILE *fpR, *fpW;
```

b)

```c
fpR = fopen("coursework.txt", "r");
fpW = fopen("repeat.txt", "w");
```

c)

```c
char id[6], name[35];
int assMark, testMark, cwMark, repeat = 0;
fprintf(fpW, "ID\tName\n--\t-----\n");
while(fscanf(fpR, "%[^|]|%[^|]|%d|%d\n", id, name, &assMark, &testMark) != EOF) {
	cwMark = assMark + testMark;
	if(cwMark < 50) {
		fprintf(fpW, "%s\t%s\n", id, name);
		repeat++;
	}
}
fprintf(fpW, "\nTotal Number of Repeat Students: %d\n", repeat);
```

d)

To keep a record of data permanently in auxiliary/secondary storage devices (e.g. hard disk, CD, DVD, tape)

e)

1. Data are human readable

2. Each line ends with a newline character

### Question 3

a)

```c
FILE *fptr = fopen("movies.bin", "ab");

if(fptr = NULL) {
 	printf("Can't open the file.\n");
	exit(-1);
}

fwrite(&name, sizeof(name), 1, fptr);
fwrite(&releaseYear, sizeof(int), 1, fptr);
fwrite(&rating, sizeof(double), 1, fptr);

fclose(fptr);
```

b)

i)

Modules share data by passing parameters

ii)

Main program controls module actions

iii)

Modules share global structures

c)

| Variable | Visibility | Storage Class |
| :----- | :--- | :--- |
| a at line 5 | 5 - 7 | auto |
| b at line 9 | 9 - 14 | extern |
| c at line 12 | 12 - 14 | static |

### Question 4

a)

1. Minimize program complexity

2. Increase program readability

3. Simplify program maintenance

b)

(i)

```c
double calCommission(double totalSale) {
	double commission;
	commission = totalSale * 0.2;

	return commission;
}
```

(ii)

```c
void getBonus(double totalSale, double *bonus) {
	if(totalSale < 5000)
		*bonus = 0.00;
	else if(totalSale < 7999)
		*bonus = 300.00;
	else
		*bonus = 500.00;
}
```

(iii)

```c
void main() {
	double totalSale, commission, bonus;

	printf("Please enter your total sale : ");
	scanf("%lf", &totalSale);
	commission = calCommission(totalSale);
	getBonus(totalSale, &bonus);

	printf("Your commission is %f and your bonus is %f.\n", commission, bonus);
}
```
