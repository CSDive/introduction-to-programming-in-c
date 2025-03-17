
# **Operators**
✅ **Assignment Operators**  
✅ **Comparison Operators**  
✅ **Logical Operators**  
✅ **Ternary Operator (`? :`)**


---

## **1️.Assignment Operators (`=, +=, -=, *=, /=, %=, &=, |=, ^=, <<=, >>=`)**

### **What are they?**

Assignment operators **assign values** to variables. Some modify the variable in place.

| Operator | Meaning                 | Example                | Equivalent To | Result                    |
| -------- | ----------------------- | ---------------------- | ------------- | ------------------------- |
| `=`      | Assigns value           | `a = 5;`               | N/A           | `a` becomes `5`           |
| `+=`     | Adds and assigns        | `a += 3;`              | `a = a + 3;`  | If `a = 5`, now `a = 8`   |
| `-=`     | Subtracts and assigns   | `a -= 2;`              | `a = a - 2;`  | If `a = 8`, now `a = 6`   |
| `*=`     | Multiplies and assigns  | `a *= 4;`              | `a = a * 4;`  | If `a = 6`, now `a = 24`  |
| `/=`     | Divides and assigns     | `a /= 2;`              | `a = a / 2;`  | If `a = 24`, now `a = 12` |
| `%=`     | Modulus and assigns     | `a %= 5;`              | `a = a % 5;`  | If `a = 12`, now `a = 2`  |
| `&=`     | Bitwise AND and assigns | `a &= 3;`              | `a = a & 3;`  | Performs bitwise AND      |
| \|=      | Bitwise OR and assigns  | Bitwise OR and assigns | a = a \| 3;   | Performs bitwise OR       |
| `^=`     | Bitwise XOR and assigns | `a ^= 2;`              | `a = a ^ 2;`  | Performs bitwise XOR      |
| `<<=`    | Left shift and assigns  | `a <<= 1;`             | `a = a << 1;` | Shifts bits left          |
| `>>=`    | Right shift and assigns | `a >>= 1;`             | `a = a >> 1;` | Shifts bits right         |

### **Example**

```c
#include <stdio.h>

int main() {
    int a = 5;
    a += 3;   // Now a = 8
    a *= 2;   // Now a = 16
    a %= 5;   // Now a = 1
    printf("Final value of a: %d\n", a);  // Output: 1
    return 0;
}
```

---

## **2️.Comparison Operators (`==, !=, >, <, >=, <=`)**

### **What are they?**

Comparison operators **compare** two values and return **1 (true)** or **0 (false)**.

| Operator | Meaning                  | Example  | Result                               |
| -------- | ------------------------ | -------- | ------------------------------------ |
| `==`     | Equal to                 | `a == b` | `1` if equal, otherwise `0`          |
| `!=`     | Not equal to             | `a != b` | `1` if not equal, otherwise `0`      |
| `>`      | Greater than             | `a > b`  | `1` if `a` is greater, otherwise `0` |
| `<`      | Less than                | `a < b`  | `1` if `a` is smaller, otherwise `0` |
| `>=`     | Greater than or equal to | `a >= b` | `1` if `a` is greater or equal       |
| `<=`     | Less than or equal to    | `a <= b` | `1` if `a` is smaller or equal       |

### **Example**

```c
#include <stdio.h>

int main() {
    int a = 10, b = 5;

    printf("a == b: %d\n", a == b);  // 0 (false)
    printf("a != b: %d\n", a != b);  // 1 (true)
    printf("a > b: %d\n", a > b);    // 1 (true)
    printf("a < b: %d\n", a < b);    // 0 (false)
    printf("a >= b: %d\n", a >= b);  // 1 (true)
    printf("a <= b: %d\n", a <= b);  // 0 (false)

    return 0;
}
```

---

## **3️.Logical Connectors (`&&, ||, !`)**

### **What are they?**

Logical operators **combine multiple conditions** to return **true (1)** or **false (0)**.

| Operator   | Meaning                   | Example             | Result                          |
| ---------- | ------------------------- | ------------------- | ------------------------------- |
| `&&` (AND) | True if both are true     | `(a > 5 && b < 10)` | `1` if both conditions are true |
| \|\|       | True at least one is true | (a > 5 \|\| b < 10) | 1 if at least one is true       |
| `!` (NOT)  | Inverts the condition     | `!(a == 5)`         | `1` if `a` is not `5`           |

### **Example**

```c
#include <stdio.h>

int main() {
    int x = 10, y = 20;

    printf("x > 5 && y < 30: %d\n", x > 5 && y < 30);  // 1 (true)
    printf("x < 5 || y > 10: %d\n", x < 5 || y > 10);  // 1 (true)
    printf("!(x == 10): %d\n", !(x == 10));           // 0 (false)

    return 0;
}
```

🔹 **Note:**

- `&&` **requires** both conditions to be true.
- `||` **requires at least one** condition to be true.
- `!` **flips** the condition.

---

## **4️.Ternary Operator (`? :`)**

### **What is it?**

The **ternary operator** is a shortcut for `if-else`.

### **Syntax**

```c
condition ? value_if_true : value_if_false;
```

### **Example**

```c
#include <stdio.h>

int main() {
    int num = 10;
    char *result = (num % 2 == 0) ? "Even" : "Odd";

    printf("%d is %s\n", num, result);  // Output: 10 is Even

    return 0;
}
```

### **Breaking it Down:**

- If `num % 2 == 0` is **true**, it returns `"Even"`.
- If **false**, it returns `"Odd"`.

### **Challenge Question**

- **What will this print?**

```c
#include <stdio.h>

int main() {
    int x = 5, y = 10;
    int result = x > y ? (x < y ? x : y) : x;
    printf("%d\n", result);
    return 0;
}
```

---

## **5.Postfix & Prefix Increment (`++i` vs `i++`)**

### **What’s the difference?**

- `i++` (**Post-increment**): Uses `i`, then increases it.
- `++i` (**Pre-increment**): Increases `i`, then uses it.

### **Example**

```c
#include <stdio.h>

int main() {
    int a = 5, b = 5;
    printf("a++: %d\n", a++);  // Prints 5, then a becomes 6
    printf("++b: %d\n", ++b);  // b becomes 6, then prints 6
    return 0;
}
```


# **if Statement**

The `if` statement in C is used to **make decisions** based on conditions. If the condition is **true**, the code inside the `if` block executes; otherwise, it is skipped.

---

## **1️.Basic if Statement**

### **✅ When to Use?**

- When you need to **execute a block of code only if a condition is met**.

### **📝 Syntax**

```c
if (condition) {
    // Code to execute if condition is true
}
```

**Key Points:**

- The **condition** inside `if` must evaluate to **true (nonzero) or false (zero)**.
- If the condition is **true**, the block executes.
- If the condition is **false**, the block is **skipped**.

---

### ** Example 1 – Check if a Number is Positive**

```c
#include <stdio.h>

int main() {
    int num = 10;

    if (num > 0) {
        printf("The number is positive.\n");
    }

    return 0;
}
```

**Output:**

```
The number is positive.
```

**Explanation:** Since `num > 0` is **true**, the message prints.

---

## **2️.if-else Statement**

### **✅ When to Use?**

- When you need **two different actions** based on a condition.

### **📝 Syntax**

```c
if (condition) {
    // Executes if condition is true
} else {
    // Executes if condition is false
}
```

---

### **Example 2 – Check Even or Odd Number**

```c
#include <stdio.h>

int main() {
    int num = 7;

    if (num % 2 == 0) {
        printf("Even number.\n");
    } else {
        printf("Odd number.\n");
    }

    return 0;
}
```

 **Output:**

```
Odd number.
```

**Explanation:**

- `7 % 2 == 0` is **false**, so the `else` block executes.

---

## **3️.if-else if-else Statement**

### **✅ When to Use?**

- When there are **multiple conditions** to check.

### **📝 Syntax**

```c
if (condition1) {
    // Executes if condition1 is true
} else if (condition2) {
    // Executes if condition2 is true
} else {
    // Executes if none of the above conditions are true
}
```

---

### **Example 3 – Check if Number is Positive, Negative, or Zero**

```c
#include <stdio.h>

int main() {
    int num = -5;

    if (num > 0) {
        printf("Positive number.\n");
    } else if (num < 0) {
        printf("Negative number.\n");
    } else {
        printf("Number is zero.\n");
    }

    return 0;
}
```

**Output:**

```
Negative number.
```

**Explanation:**

- Since `num > 0` is **false**, it checks `num < 0`, which is **true**.

---

## **4️.Nested if Statements**

### **✅ When to Use?**

- When **one condition depends on another**.

### **📝 Syntax**

```c
if (condition1) {
    if (condition2) {
        // Executes if both conditions are true
    }
}
```

---

### **Example 4 – Check If a Number is Even and Positive**

```c
#include <stdio.h>

int main() {
    int num = 8;

    if (num > 0) {
        if (num % 2 == 0) {
            printf("Positive even number.\n");
        }
        
    }

    return 0;
}
```

**Output:**

```
Positive even number.
```

**Explanation:**

- The **first if** checks if `num > 0` (true).
- The **nested if** checks if `num % 2 == 0` (true), so it prints.

---

# **Logical Operator Shortcuts (Short-Circuiting) in C**

Logical operations (`&&`, `||`, `!`) in C follow **short-circuit evaluation**, meaning the compiler **skips** unnecessary operations. This can be used as a **shortcut** to write cleaner and more efficient code.

---

## **1️.Short-Circuit AND (`&&`)**

### **What Happens?**

- If the **first condition is `false`**, the **rest is skipped**.
- This is useful for **avoiding unnecessary checks**.

### **Example (Avoiding Division by Zero)**

```c
#include <stdio.h>

int main() {
    int a = 0, b = 10;

    if (a != 0 && b / a > 2) {  // The second condition is NEVER checked
        printf("Safe division\n");
    } else {
        printf("Skipped division to prevent error\n");
    }
    return 0;
}
```

**Why?**
- Since `a != 0` is **false**, the compiler **never** checks `b / a > 2`.
- This **prevents division by zero**.

---

## **2.Using `&&` for Compact If-Statements**

If the **right-hand side** has **no side effects**, use `&&` for **simpler conditions**.

### **Example (One-Line If Statement)**

```c
#include <stdio.h>

int main() {
    int a = 5;
    (a > 0) && printf("a is positive\n");  // Runs only if a > 0
    return 0;
}
```

📌 **Why?**

- If `a > 0` is **true**, it prints `"a is positive"`.
- If `a > 0` is **false**, `printf` is **never executed**.

---
## **Challenge Questions**

### **Q1:** What will be the output?

```c
#include <stdio.h>

int main() {
    int x = 5;
    if (x = 1) {
        printf("True\n");
    } else {
        printf("False\n");
    }
    return 0;
}
```


---

### **Q2:** Predict the output of this program:

```c
#include <stdio.h>

int main() {
    int a = 10;
    if (a > 5 || a / 0) {
        printf("Success\n");
    }
    return 0;
}
```

--- 
### **Q3:** Predict the output of this program:
```c
#include <stdio.h>

int main() {
    int x = 0, y = 1;
    (x || y) && printf("Hello\n");
    return 0;
}
```

# **Switch Statement**

The `switch` statement in C is a **multi-way branching** statement that allows a variable to be tested against multiple constant values efficiently. It is often used as an alternative to long `if-else if` chains.

---

## **1️.Basic Syntax of `switch`**

```c
switch (expression) {
    case constant1:
        // Code block
        break;
    case constant2:
        // Code block
        break;
    default:
        // Default block (optional)
}
```

**How it Works:**

1. **`expression` is evaluated.**
2. **Control jumps** to the matching `case` label.
3. If no match is found, the `default` block (if present) executes.
4. **`break` prevents fall-through** (execution of subsequent cases).

---

## **2️. Example – Simple `switch` Case**

```c
#include <stdio.h>

int main() {
    int choice = 2;

    switch (choice) {
        case 1:
            printf("You selected option 1\n");
            break;
        case 2:
            printf("You selected option 2\n");
            break;
        case 3:
            printf("You selected option 3\n");
            break;
        default:
            printf("Invalid option\n");
    }

    return 0;
}
```

**Output:**

```
You selected option 2
```

**Explanation:**

- Since `choice = 2`, execution jumps to `case 2` and prints the message.
- The `break` ensures that execution does not continue to `case 3`.

---

## **3️.`break` vs. Fall-through**

Without `break`, execution **falls through** to the next case.

### **Example – Fall-through Behavior**

```c
#include <stdio.h>

int main() {
    int num = 2;

    switch (num) {
        case 1:
            printf("One\n");
        case 2:
            printf("Two\n"); // No break here
        case 3:
            printf("Three\n");
            break;
        default:
            printf("Invalid\n");
    }

    return 0;
}
```

**Output:**

```
Two
Three
```

**Explanation:**

- `case 2` **executes** and falls through to `case 3` because there is **no `break`**.
- To prevent fall-through, always use **`break`**, unless intended.

---

## **4️.Using `default` Case**

The `default` case **handles unexpected values**.

### **Example – Handling Invalid Input**

```c
#include <stdio.h>

int main() {
    int option = 5;

    switch (option) {
        case 1:
        case 2:
        case 3:
            printf("Valid option selected\n");
            break;
        default:
            printf("Invalid option\n"); // Runs if no case matches
    }

    return 0;
}
```

**Output:**

```
Invalid option
```

**Best Practice:**  
Always include a **`default` case** to handle unexpected inputs.

---

## **5️.Multiple Cases with Same Code**

Instead of repeating code, **group multiple cases**.

### **Example – Grouping Cases**

```c
#include <stdio.h>

int main() {
    char grade = 'B';

    switch (grade) {
        case 'A':
        case 'B':
            printf("Good job!\n");
            break;
        case 'C':
        case 'D':
            printf("Needs improvement\n");
            break;
        default:
            printf("Invalid grade\n");
    }

    return 0;
}
```

📌 **Output:**

```
Good job!
```

📌 **Explanation:**

- Both `case 'A'` and `case 'B'` share the same code block.

---

## **6️.Switch with `enum` Values**

C allows using `enum` values in `switch`.

### **Example – Using `enum` with `switch`**

```c
#include <stdio.h>

enum Day { MON, TUE, WED, THU, FRI, SAT, SUN };

int main() {
    enum Day today = WED;

    switch (today) {
        case MON:
        case TUE:
            printf("It's a weekday.\n");
            break;
        case WED:
        case THU:
        case FRI:
            printf("Midweek!\n");
            break;
        case SAT:
        case SUN:
            printf("Weekend!\n");
            break;
        default:
            printf("Invalid day\n");
    }

    return 0;
}
```

**Output:**

```
Midweek!
```

**Why use `enum`?**

- Increases **readability** and avoids **magic numbers**.

---

## **7️.Switch vs If-Else: When to Use?**

| Criteria            | `switch`                 | `if-else`                      |
| ------------------- | ------------------------ | ------------------------------ |
| **Use case**        | Multiple fixed values    | Complex conditions             |
| **Execution speed** | Faster (jump table)      | Slower (checks all conditions) |
| **Readability**     | Better for many cases    | Better for range checks        |
| **Works with**      | Integers, `char`, `enum` | Any condition                  |

**Use `switch` for:**  
✅ Checking **fixed values** (e.g., menu selection, days of the week).  
✅ Better **performance** when dealing with many cases.

**Use `if-else` for:**  
✅ Checking **ranges** (`x > 10`, `y < 50`).  
✅ Conditions involving **logical operators** (`&&`, `||`).

---
## **Simple Calculator**

```c
#include <stdio.h>

int main() {
    char op;
    double num1, num2, result;

    printf("Enter an operator (+, -, *, /): ");
    scanf(" %c", &op);
    printf("Enter two numbers: ");
    scanf("%lf %lf", &num1, &num2);

    switch (op) {
        case '+':
            result = num1 + num2;
            break;
        case '-':
            result = num1 - num2;
            break;
        case '*':
            result = num1 * num2;
            break;
        case '/':
            if (num2 != 0)
                result = num1 / num2;
            else {
                printf("Cannot divide by zero!\n");
                return 1;
            }
            break;
        default:
            printf("Invalid operator\n");
            return 1;
    }

    printf("Result: %.2lf\n", result);
    return 0;
}
```

**Try It Out:**

```
Enter an operator (+, -, *, /): *
Enter two numbers: 5 3
Result: 15.00
```

---

## **Summary**

✅ `switch` is used for **fixed-value conditions**.  
✅ `break` **prevents fall-through**.  
✅ `default` handles **unexpected cases**.  
✅ Works only with **integers, characters, and enums**.  
✅ **Faster** than `if-else` for multiple cases.
