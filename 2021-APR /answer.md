<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

# AACS1084 April 2021 Answers

[Link to the paper](https://eprints.tarc.edu.my/17763/1/AACS1084.pdf)

- [Question 1](#question-1)
- [Question 2](#question-2)
- [Question 3](#question-3)
- [Question 4](#question-4)

## Answers

### Question 1

a) (i)

```c
struct Singer {
  char name[30];
  char gender;
  char nationality[30];
};
```

b)

```c
typedef struct {
  int id;
  char title[30];
  struct Singer singer;
  double price;
} Album;
```

c)

```c
Album cd[2] = {
  {1001, "Happy Moments", "Jane Berry", 'F', "American", 67.90},
  {1002, "Dreams", "Joseph Chan", 'M', "Taiwanese", 59.90}
};
```

d)

```c
strcpy(cd[1].singer.nationality, "Singaporean");
```

e)

```c
for (int i = 0; i < 2; i++) {
  printf("ID: %d\n", cd[i].id);
  printf("Title : %s\n", cd[i].title);
  printf("Singer : %s\n", cd[i].singer.name);
  printf("Price : %RM.2f\n\n", cd[i].price);
}
system("pause");
```

### Question 2

a)

```c
FILE *fptr1, *fptr2;
fptr1 = fopen("inventory.txt", "r");
fptr2 = fopen("replenishment.txt", "w");
```

b)

```c
if (fptr1 == NULL || fptr2 == NULL) {
    printf("Error : unable to open the file!");
    exit(-1);
}
```

c)

```c
char prodID[5];
char prodName[30];
int prodQty, minStockLvl;

while (fscanf(fptr1, "%[^|]|%[^|]|%[^|]|%[^\n]\n", prodID, prodName, &prodQty, &minStockLvl) != EOF) {
  if (prodQty < minStockLvl)
    fprintf(fptr2, "%s|%s|%d|%d\n", prodID, prodName, prodQty, minStockLvl);
}
```

d)

```c
fclose(fptr1);
fclose(fptr2);
```

### Question 3

a)
```c
FILE *fp;

fp = fopen("employeeInfo.bin", "ab");
fwrite(&emp, sizeof(Employee), 1, fp);

fp = fopen("employeeInfo.bin", "rb");
printf("Employee ID\t\tName\t\tSalary\n");
printf("================================================\n");
while (fread(&emp, sizeof(Employee), 1, fp) == 1) {
  printf("%d\t\t%s\t\t%f\n", &emp.empId, emp.name, &emp.salary);
}

fclose(fp);
```

b)
- Text files stores human readable characters whereas binary files stores binary values which are not human readable.
- Each lines in text files ends with a newline(\n) character whereas binary files does not separate the contents in lines.
- Text files are written using text stream whereas binary files are written using binary stream.

### Question 4

a) (i)
Sequential cohesion. The function performs 2 tasks on the same piece of data in order, which firstly converts the data from cm to inches, and secondly, prints the result in the console.

a) (ii)
External coupling. Both modules share global variable (cm).

b) (i)

```c
void countOccurrence(char str[], char ch, int *num) {
  *num = 0;
  for (int i = 0; i < strlen(str); i++) {
    if (toupper(str[i]) == toupper(ch)) 
      (*num)++;
  }
}
```

b) (ii)
```c
void main() {
  char string[20];
  char ch;
  int num;

  printf("Enter a string : ");
  scanf("%s", string);

  rewind(stdin);

  printf("Enter a character : );
  scanf(" %c", &ch);

  countOccurrence(string, ch, &num);
  printf("The character '%c' occurs %d times in the string '%s'.", ch, num, string);
}
```
