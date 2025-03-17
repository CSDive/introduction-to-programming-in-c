# **Understanding Binary Number Representation**

Before working with bitwise operations, we must understand how numbers are represented in binary and how to convert between decimal and binary.

---

## **1. Decimal to Binary Conversion**

The **decimal system** (base 10) uses digits `0-9`, while the **binary system** (base 2) only uses `0` and `1`. Each digit in a binary number represents a power of 2.

### **Step-by-Step Conversion from Decimal to Binary**

To convert a decimal number to binary:

1. **Divide** the number by 2.
2. **Record the remainder** (0 or 1).
3. **Repeat** the division until the quotient is 0.
4. **Read the remainders from bottom to top** to get the binary equivalent.

#### **Example 1: Convert 19 to Binary**

``` 
19 ÷ 2 = 9  remainder 1  
 9 ÷ 2 = 4  remainder 1  
 4 ÷ 2 = 2  remainder 0  
 2 ÷ 2 = 1  remainder 0  
 1 ÷ 2 = 0  remainder 1  
```

**Binary Representation:** `10011`

#### **Example 2: Convert 45 to Binary**

```
45 ÷ 2 = 22 remainder 1  
22 ÷ 2 = 11 remainder 0  
11 ÷ 2 = 5  remainder 1  
 5 ÷ 2 = 2  remainder 1  
 2 ÷ 2 = 1  remainder 0  
 1 ÷ 2 = 0  remainder 1  
```

**Binary Representation:** `101101`

---

## **2. Binary to Decimal Conversion**

To convert binary back to decimal:

1. Multiply each binary digit by **2 raised to its position** (starting from right as position 0).
2. Sum all the values.

### **Example 1: Convert `10011` to Decimal**

```
10011
(1 × 2⁴) + (0 × 2³) + (0 × 2²) + (1 × 2¹) + (1 × 2⁰)
= 16 + 0 + 0 + 2 + 1
= 19
```

### **Example 2: Convert `101101` to Decimal**

```
(1 × 2⁵) + (0 × 2⁴) + (1 × 2³) + (1 × 2²) + (0 × 2¹) + (1 × 2⁰)
= 32 + 0 + 8 + 4 + 0 + 1
= 45
```

---

## **3. Binary Representation in C**

In C, binary literals can be represented using the `0b` or `0B` prefix.

### **Example: Storing Binary Values in Variables**

```c
#include <stdio.h>

int main(void) {
    char ch = 0b01111110; // Binary representation of 126
    printf("Letter representation is %c\n", ch);
    printf("Number value is %d\n", ch);
    return 0;
}
```

**Output:**

```
Letter representation is ~
Number value is 126
```

💡 `~` is the ASCII character for decimal `126` (`0b01111110`).

### **Handling Larger Binary Numbers in char**

A `char` is **8 bits** wide. If we assign a value larger than 8 bits, only the **least significant 8 bits** are used.

```c
#include <stdio.h>

int main(void) {
    char ch1 = 0b01111110;
    char ch2 = 0b11001101111110; // Only last 8 bits (01111110) are stored
    char ch3 = 126; // Decimal 126, same as 0b01111110

    printf("Letter representations: %c %c %c\n", ch1, ch2, ch3);
    printf("Number values: %d %d %d\n", ch1, ch2, ch3);
    return 0;
}
```

**Output:**

```
Letter representations: ~ ~ ~
Number values: 126 126 126
```

### **Why Use Binary Representation in C?**

- **Embedded systems:** Registers store configuration bits, so binary notation makes it easy to set flags.
- **Bitwise operations:** Working with specific bits for performance optimizations.
- **Low-level programming:** Operating systems, cryptography, and compression algorithms use binary directly.

---

### **4. Signed and Unsigned Binary Representation**

In C, numbers can be stored as **signed** or **unsigned**.

| Type            | Range (8-bit) | Example Binary Representation         |
| --------------- | ------------- | ------------------------------------- |
| `unsigned char` | `0 to 255`    | `00000000` (0) to `11111111` (255)    |
| `signed char`   | `-128 to 127` | `10000000` (-128) to `01111111` (127) |

#### **Two’s Complement Representation (Signed Numbers)**

- Positive numbers are stored normally.
- Negative numbers are stored using **two’s complement**:
    1. Write the positive binary equivalent.
    2. Flip all bits (`1` → `0`, `0` → `1`).
    3. Add `1` to the result.

👉 **Example: Represent -5 in 8-bit binary**

1. `5` in binary: `00000101`
2. Flip bits: `11111010`
3. Add `1`: `11111011`

Thus, `-5` in **two’s complement (8-bit)** is `11111011`.

---

## **Bitwise Operators in C**

Now that we understand how binary numbers are represented, let's explore **bitwise operators** in C. Bitwise operators allow us to manipulate individual bits directly, which is useful for low-level programming, embedded systems, and performance optimizations.

---

## **1. Types of Bitwise Operators in C**

C provides six bitwise operators:

| Operator | Name            | Description                                                                               |
| -------- | --------------- | ----------------------------------------------------------------------------------------- |
| `&`      | **Bitwise AND** | Sets a bit to `1` only if both corresponding bits are `1`.                                |
| \|       | \|              | **Bitwise OR**                                                                            |
| `^`      | **Bitwise XOR** | Sets a bit to `1` if the corresponding bits are different.                                |
| `~`      | **Bitwise NOT** | Inverts all bits (1 → 0, 0 → 1).                                                          |
| `<<`     | **Left Shift**  | Shifts bits to the left, filling with `0`s.                                               |
| `>>`     | **Right Shift** | Shifts bits to the right, discarding bits (for unsigned) or preserving sign (for signed). |

---

## **2. Bitwise AND (`&`)**

The `&` operator performs a **bitwise AND** operation. A bit is set to `1` only if both corresponding bits are `1`.

**Example:**

```c
#include <stdio.h>

int main() {
    int a = 5;  // 0101 (binary)
    int b = 3;  // 0011 (binary)

    int result = a & b; // 0101 & 0011 = 0001

    printf("Bitwise AND: %d\n", result);
    return 0;
}
```

**Output:**

```
Bitwise AND: 1
```

🛠 **Use case:** Masking bits to check specific flags in registers.

---

## **3. Bitwise OR (`|`)**

The `|` operator performs a **bitwise OR** operation. A bit is set to `1` if at least one of the corresponding bits is `1`.

**Example:**

```c
#include <stdio.h>

int main() {
    int a = 5;  // 0101
    int b = 3;  // 0011

    int result = a | b; // 0101 | 0011 = 0111

    printf("Bitwise OR: %d\n", result);
    return 0;
}
```

**Output:**

```
Bitwise OR: 7
```

🛠 **Use case:** Setting specific bits in bitfields.

---

## **4. Bitwise XOR (`^`)**

The `^` (XOR) operator sets a bit to `1` if the corresponding bits are different.

**Example:**

```c
#include <stdio.h>

int main() {
    int a = 5;  // 0101
    int b = 3;  // 0011

    int result = a ^ b; // 0101 ^ 0011 = 0110

    printf("Bitwise XOR: %d\n", result);
    return 0;
}
```

**Output:**

```
Bitwise XOR: 6
```

🛠 **Use case:** Toggling specific bits.

---

## **5. Bitwise NOT (`~`)**

The `~` operator **inverts** all bits.

**Example:**

```c
#include <stdio.h>

int main() {
    int a = 5;  // 00000101 (8-bit)

    int result = ~a; // 11111010 (in two's complement: -6)

    printf("Bitwise NOT: %d\n", result);
    return 0;
}
```

**Output:**

```
Bitwise NOT: -6
```

💡 **Note:** The output is negative because C uses **two’s complement** for signed numbers.

🛠 **Use case:** Flipping all bits or creating bitmasks.

---

## **6. Left Shift (`<<`)**

The `<<` operator shifts bits **to the left**, filling the right with `0`s.

**Example:**

```c
#include <stdio.h>

int main() {
    int a = 5;  // 00000101

    int result = a << 2; // 00010100

    printf("Left Shift: %d\n", result);
    return 0;
}
```

**Output:**

```
Left Shift: 20
```

💡 **Shifting left by `n` is equivalent to multiplying by `2^n`.**

🛠 **Use case:** Fast multiplication by powers of 2.

---

## **7. Right Shift (`>>`)**

The `>>` operator shifts bits **to the right**, discarding bits on the right.

**Example:**

```c
#include <stdio.h>

int main() {
    int a = 20;  // 00010100

    int result = a >> 2; // 00000101

    printf("Right Shift: %d\n", result);
    return 0;
}
```

**Output:**

```
Right Shift: 5
```

💡 **Shifting right by `n` is equivalent to dividing by `2^n`.**

🛠 **Use case:** Fast division by powers of 2.

---
### **Example 1**

**Task:** Given an integer `x`, perform the following bitwise operations:
1. **Set** the **5th** bit of `x` (0-based index).
2. **Clear** the **3rd** bit of `x`.
3. **Toggle** the **1st** bit of `x`.
4. **Print** the binary representation before and after modification.

- **test case:**
```
Input: x = 18  (Binary: 00010010)
Output:
Before: 00010010
After:  00111000
```

- **Code:**
```c
#include <stdio.h>

int main() {
    int x = 18; // Binary: 00010010
    printf("Before: ");
    print_binary(x);

    // Set the 5th bit (bit index 5)
    x |= (1 << 5);

    // Clear the 3rd bit (bit index 3)
    x &= ~(1 << 3);

    // Toggle the 1st bit (bit index 1)
    x ^= (1 << 1);

    printf("After:  ");
    print_binary(x);

    return 0;
}
```

## **Example 2: Checking if a number is even or odd**


```c
#include <stdio.h>

int main() {
    int num = 7;
    
    if (num & 1) {
        printf("%d is odd\n", num);
    } else {
        printf("%d is even\n", num);
    }
    
    return 0;
}
```

**Output:**

```
7 is odd
```

💡 **How?** The least significant bit of even numbers is `0`, and for odd numbers, it's `1`.
