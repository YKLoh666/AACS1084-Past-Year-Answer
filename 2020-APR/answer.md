<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

# AACS1084 April 2020 Answers

[Link to the paper](https://eprints.tarc.edu.my/14889/1/AACS1084.pdf)

- [Question 1](#question-1)
- [Question 2](#question-2)
- [Question 3](#question-3)
- [Question 4](#question-4)

## Answers

### Question 1

a) (i)

Structure is a data structure that allows user to store a group of variables with different data types.

b)
Structure are commonly used to define records to be stored in a file, where each element in a structure represents a field within a record.

c) (i)

```c
typedef struct {
  char treatmentName[30];
  char footSoak;
  double price;
} Treatment;
```

c) (ii)

```c
Treatment treatmentM = {"Original Urutan Malaysia", 'Y', 268.0};
```

c) (iii)

```c
typedef struct {
  int code;
  char name[20];
  Treatment treat;
} Customer;
```

c) (iv)

```c
Customer custA = {1277, "Mandy", {"Herbal Massage", 'N', 188.0}};
```

(c) (v)

```c
if (custA.code == 1277)
  custA.treat.price = 150.4;
```

### Question 2

a)
- Text files store human readable characters.
- Each line in the text file ends with newline(\n) character.
- Text files are easily readable and modifiable using text editor.

b) (i)

```c
FILE *fPtr1, *fPtr2;
```

b) (ii)

```c
fPtr1 = fopen("sales.txt", "r");
fPtr2 = fopen("averageWeeklySales.txt", "w");
```

b) (iii)

```c
if (fPtr1 == NULL || fPtr2 == NULL) {
  printf("Error opening the file(s).");
  exit(-1);
}
```

b) (iv)

```c
int week;
while (fscanf(fPtr1, "%d\t", &week) != EOF) {
  double total = 0;
  int prod;
  for (int i = 1; i <= 5; i++) {
    if (i != 5) fscanf(fPtr1, "%d\t", &prod);
    else fscanf(fPtr1, "%d\n", &prod);
    total += prod;
  }
  fprintf(fPtr2, "%d\t%.1f\n", week, total / 5);
}
```

### Question 3

a) (i)
```c
FILE *fPtr3;
```

a) (ii)
```c
fPtr3 = fopen("product.bin", "wb");
```

a) (iii)
```c
fwrite(&prodCode, sizeof(int), 1, fPtr3);
fwrite(&costPrice, sizeof(double), 1, fPtr3);
fwrite(&category, sizeof(char), 1, fPtr3);
```

a) (iv)
```c
fclose(fPtr3);
```

b)
```c
int readCode;
double readCost;
fread(&readCode, sizeof(int), 1, fPtr4);
fread(&readCost, sizeof(double), 1, fPtr4);
printf("Product Code : %d\n", readCode);
printf("Cost Price : RM%.2f\n", readCost);
system("pause");
```

c)

- Write comments for our code for understanding purpose and future use for reviewing.
- Declare meaningful and contextual variables and function names to avoid confusion in our code.
- Draw flowchart or write pseudocode before writing a program to visualize the program flow better.

d) Cohesion is a measure of the independence of a module.

e) 

(i) Funtional cohesion

(ii) Sequential cohesion

(iii) Communicational cohesion

### Question 4

a)
- Modular programming enables us to organize a program into small, independent modules that are separately named and individually invokeable program elements.

b) (i)

```c
void computePerimeter(int length) {
  *perimeter = 4 * length;
}
```

b) (ii)
```c
int computeArea(int length) {
  int area = length * length;
  return area;
}
```

b) (iii)
```c
void main() {
  int length;
  printf("Enter value of square's length : ");
  scanf("%d", &length);

  int perimeter;
  computePerimeter(length, &perimeter);

  int area = computeArea(length);

  printf("Perimeter : %d\n", perimeter);
  printf("Area : %d\n", area);
}
```

c)
```c
double computeSalesAverage(double s1[5]) {
  double total = 0;
  for (int i = 0; i < 5; i++) {
    total += s1[i];
  }
  return total / 5;
}
```
