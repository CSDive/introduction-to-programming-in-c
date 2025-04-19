# **Operators**
✅ **scanf**
✅ **Loops**  

---
# `scanf()` in C

The `scanf()` function is used to **read input from the user** — such as integers, floats, characters, and strings — from the standard input (usually the keyboard).

---
## 1. **Basic Syntax**

```c
scanf("format_specifier", &variable);
```

### Example:

```c
int x;
scanf("%d", &x); // reads an integer
```

---

## 2. **Why the `&` (Address-of) Operator?**

C passes the **memory address** of the variable to `scanf()` so that it can store the input in the right place.

```c
int age;
scanf("%d", &age); // without &age, it won't know where to store the number
```

---

## 3. **Common Format Specifiers**

| Type     | Format | Example Input |
| -------- | ------ | ------------- |
| `int`    | `%d`   | `42`          |
| `float`  | `%f`   | `3.14`        |
| `char`   | `%c`   | `A`           |
| `string` | `%s`   | `hello`       |

---

## 4. **Reading Multiple Values**

You can read several inputs in a single line:

```c
int a, b;
scanf("%d %d", &a, &b);
```

**Note**: Inputs should be space-separated when entered.

---

## 5. **Reading Characters**

```c
char ch;
scanf(" %c", &ch); // Notice the space before %c
```

**Why the space?** It tells `scanf()` to ignore any leftover whitespace (like newline or space) before reading the character.
### Note: `%c` vs `%s` vs `%d` behavior with whitespace
- `%d`, `%f`, `%s` **automatically skip** leading whitespace (spaces, newlines, tabs). 
- `%c` **does NOT** skip whitespace — it reads **the very next character**, even if it's a space or newline.
- That’s why `%c` is a special case where a leading space is helpful.

---

## 6. **Reading Strings**
- skip it for now
```c
char name[20];
scanf("%s", name);
```

No `&` needed with strings because the array name is already an address.

⚠️ `scanf("%s", ...)` stops reading at the first space. To read full lines, use `fgets()`.

---

## 7. **Example 1: Read and Print Two Numbers**

```c
#include <stdio.h>
int main() {
    int a, b;
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);
    printf("Sum: %d\n", a + b);
    return 0;
}
```

---

## 8. **Example 2: Read a Character**

```c
#include <stdio.h>
int main() {
    char grade;
    printf("Enter your grade: ");
    scanf(" %c", &grade); // space before %c is important
    printf("You entered: %c\n", grade);
    return 0;
}
```

---

## 9. **Example 3: Read a Word**

```c
#include <stdio.h>
int main() {
    char name[20];
    printf("Enter your name: ");
    scanf("%s", name);
    printf("Hello, %s!\n", name);
    return 0;
}
```

---

## 10. **Example 4: Read Full Name (using fgets)**
- skip for now
```c
#include <stdio.h>
int main() {
    char fullName[50];
    printf("Enter your full name: ");
    fgets(fullName, sizeof(fullName), stdin);
    printf("Welcome, %s", fullName);
    return 0;
}
```

---
### **More Format Specifiers in C that you might need**

| Format Specifier | Data Type            | Description                                        | Example Input          |
| ---------------- | -------------------- | -------------------------------------------------- | ---------------------- |
| `%u`             | `unsigned int`       | Reads an unsigned decimal integer                  | `4294967295`           |
| `%ld`            | `long int`           | Reads a long integer                               | `2147483647`           |
| `%lu`            | `unsigned long int`  | Reads an unsigned long integer                     | `4294967295`           |
| `%lld`           | `long long int`      | Reads a long long integer                          | `9223372036854775807`  |
| `%llu`           | `unsigned long long` | Reads unsigned long long                           | `18446744073709551615` |
| `%x` / `%X`      | `unsigned int`       | Reads a hexadecimal number                         | `1A3F`                 |
| `%o`             | `unsigned int`       | Reads an octal number                              | `0754`                 |
| `%lf`            | `double`             | Reads a double (note: `%f` works too)              | `3.14159`              |
| `%Lf`            | `long double`        | Reads a long double                                | `3.1415926535`         |
| `%p`             | `void *`             | Reads a pointer address (less common in `scanf()`) | N/A                    |
| `%n`             | `int *`              | Stores the number of characters printed so far     | N/A                    |

---
### Notes
- `%f` and `%lf` behave the **same** in `scanf()` (but different in `printf()`).
- `%x` expects input in **hexadecimal** format (e.g., `0x1A` or just `1A`).
- `%o` expects **octal** numbers (e.g., `0755`).
- `%n` is rarely used — it's advanced and used to count characters printed so far.

---

### Example: Multiple Specifiers

```c
#include <stdio.h>
int main() {
    unsigned int a;
    long long int b;
    float c;
    printf("Enter unsigned int, long long int, and float: ");
    scanf("%u %lld %f", &a, &b, &c);
    printf("You entered: %u, %lld, %.2f\n", a, b, c);
    return 0;
}
```

---

Would you like to explore edge cases or formatting tricks next (like skipping input, width specifiers, etc.)?

### Summary:

- Always use `&` except for arrays.
- `%c` requires care with whitespace.
- Use `fgets()` instead of `scanf("%s", ...)` for multi-word input.


# Loops
## What is a Loop?

A **loop** is a control structure that repeats a block of code **as long as a certain condition is true**. It's a powerful way to avoid code repetition and automate tasks such as iteration, computation, and data input/output.

---

## Why Loops?

Imagine printing "Hello" 100 times — without a loop, you'd copy-paste that line 100 times. With loops, you can do it with just a few lines. Loops are essential in:
- Iterating over data structures (arrays, strings)
- Repeated input/output
- Mathematical computations (e.g. factorial, sum)
- Simulations and automation

---

## 🔹 Types of Loops in C

| Type       | Condition Checked | Use Case                                         |
| ---------- | ----------------- | ------------------------------------------------ |
| `for`      | Before execution  | Known number of iterations (e.g., from 1 to 100) |
| `while`    | Before execution  | Repeat until condition becomes false             |
| `do-while` | After execution   | Run at least once, then repeat if condition true |


---

## 1. `for` Loop — Count-controlled

### Syntax:

```c
for (initialization; condition; increment) {
    // body
}
```

### Example: Print even numbers from 2 to 10

```c
for (int i = 2; i <= 10; i += 2) {
    printf("%d ", i);
}
```

### How it works:

- **Initialization**: `int i = 2` → executed once.
- **Condition**: `i <= 10` → checked each time before loop body.
- **Increment**: `i += 2` → executed after each iteration.

---

## 2. `while` Loop — Condition-controlled

### Syntax:

```c
while (condition) {
    // body
}
```

### Example: Read numbers until 0 is entered

```c
int num;
scanf("%d", &num);
while (num != 0) {
    printf("You entered: %d\n", num);
    scanf("%d", &num);
}
```

### Key idea:

Use when you **don’t know in advance how many times** the loop should run.

---

## 3. `do-while` Loop — Guaranteed Execution

### Syntax:

```c
do {
    // body
} while (condition);
```

### Example: Menu that shows at least once

```c
int choice;
do {
    printf("Enter 1 to continue, 0 to exit: ");
    scanf("%d", &choice);
} while (choice != 0);
```

### Use case:

Menus, confirmation prompts — where the loop body must run **at least once**.

---

## Continue Loops

### 1. **Nested Loops**

A loop inside another loop.

Example: Multiplication table from 1 to 3

```c
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 12; j++) {
        printf("%d x %d = %d\n", i, j, i*j);
    }
}
```

### ✅ 2. **Infinite Loops**

Loops that run forever (or until interrupted).

```c
while (1) {
    // forever until break
}
```

Use carefully — for servers, embedded systems, or until `break` is called.

---

## Flowchart Understanding (Simple)

Every loop follows this:
1. Check condition
2. If true → execute body
3. Update variables (if any)
4. Repeat from step 1

> In `do-while`, step 1 happens after the first body execution.

---
## Examples

### 1. **Count the Number of Digits**

```c
#include <stdio.h>
int main() {
    int n, count = 0;
    printf("Enter a number: ");
    scanf("%d", &n);

    if (n == 0) count = 1;
    while (n != 0) {
        n /= 10;
        count++;
    }

    printf("Number of digits: %d\n", count);
    return 0;
}
```

---

### 2. **Reverse a Number**

```c
#include <stdio.h>
int main() {
    int n, reversed = 0;
    printf("Enter a number: ");
    scanf("%d", &n);

    while (n != 0) {
        reversed = reversed * 10 + (n % 10);
        n /= 10;
    }

    printf("Reversed number: %d\n", reversed);
    return 0;
}
```

---

### 3. **Sum of Digits**

```c
#include <stdio.h>
int main() {
    int n, sum = 0;
    printf("Enter a number: ");
    scanf("%d", &n);

    while (n != 0) {
        sum += n % 10;
        n /= 10;
    }

    printf("Sum of digits: %d\n", sum);
    return 0;
}
```

---

### 4. **Multiplication Table**

```c
#include <stdio.h>
int main() {
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);

    for (int i = 1; i <= 12; i++) {
        printf("%d x %d = %d\n", n, i, n * i);
    }

    return 0;
}
```

---

### 5. **First Power of 2 Greater Than N**

```c
#include <stdio.h>
int main() {
    int n, power = 1;
    printf("Enter a number: ");
    scanf("%d", &n);

    while (power <= n) {
        power *= 2;
    }

    printf("First power of 2 greater than %d is %d\n", n, power);
    return 0;
}
```

---

### 6. **Check if a Number is Prime**

```c
#include <stdio.h>
int main() {
    int n, isPrime = 1;
    printf("Enter a number: ");
    scanf("%d", &n);

    if (n <= 1) isPrime = 0;
    for (int i = 2; i*i <= n; i++) {
        if (n % i == 0) {
            isPrime = 0;
            break;
        }
    }

    if (isPrime)
        printf("Prime\n");
    else
        printf("Not Prime\n");

    return 0;
}
```

---

### 7. **All Divisors of a Number**

```c
#include <stdio.h>
int main() {
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);

    printf("Divisors of %d are: ", n);
    for (int i = 1; i <= n; i++) {
        if (n % i == 0)
            printf("%d ", i);
    }
    printf("\n");

    return 0;
}
```

---

### 8. **Factorial**

```c
#include <stdio.h>
int main() {
    int n;
    unsigned long long fact = 1;
    printf("Enter a number: ");
    scanf("%d", &n);

    for (int i = 1; i <= n; i++) {
        fact *= i;
    }

    printf("Factorial: %llu\n", fact);
    return 0;
}
```

---

### 9. **Power Calculation Without `pow()`**

```c
#include <stdio.h>
int main() {
    int base, exp;
    long long result = 1;
    printf("Enter base and exponent: ");
    scanf("%d %d", &base, &exp);

    for (int i = 0; i < exp; i++) {
        result *= base;
    }

    printf("%d^%d = %lld\n", base, exp, result);
    return 0;
}
```

---

### 10. **Count 1s in Binary Representation**

```c
#include <stdio.h>
int main() {
    int n, count = 0;
    printf("Enter a number: ");
    scanf("%d", &n);

    while (n != 0) {
        if (n & 1)
            count++;
        n >>= 1;
    }

    printf("Number of 1s in binary: %d\n", count);
    return 0;
}
```
