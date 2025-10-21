# NAME : LINGAESHWAR K

# MODULE-5
Module 5 respository for lab

---

## 1. Check Even or Odd Using Pointer

**Aim:**

To determine whether a number entered by the user is even or odd using a pointer.

**Algorithm:**  

1. Start the program.  
2. Declare an integer variable n and a pointer p.  
3. Read the number from the user and store it in n.  
4. Assign the address of n to the pointer p.  
5. Check the value pointed by p:  
   - If divisible by 2 → the number is even.  
   - Otherwise → the number is odd.  
6. Print the result.  
7. End the program.  

**Source Code:** 

```c
#include <stdio.h>
int main()
{
    int n;
    scanf("%d", &n);
    int *p;
    p = &n;

    if (*p % 2 == 0) {
        printf("%d is even.", *p);
    } else {
        printf("%d is odd.", *p);
    }

    return 0;
}
```

**output**

<img width="459" height="164" alt="image" src="https://github.com/user-attachments/assets/4d2aa4b3-a0ad-4dc2-8e83-17865061ce43" />


**Result:**

The program uses a pointer to determine and display whether the entered number is even or odd.
---

# 2.Program: Sum of Digits Using Recursion

**Aim:**  

To write a C program that calculates the sum of digits of a given number using recursion.

---

**Algorithm:**

1. Start the program.  
2. Define a recursive function sumOfDigits(int n) that:  
   - Returns 0 if n is 0 (base case).  
   - Otherwise, returns (n % 10) + sumOfDigits(n / 10) to sum the last digit with the recursive call for the remaining digits.  
3. In the main() function:  
   - Read an integer n from the user.  
   - Call the recursive function sumOfDigits(n) and store the result.  
   - Print the sum of digits.  
4. End the program.

---

**Source Code:**  

```c
#include <stdio.h>

// Recursive function
int sumOfDigits(int n) {
    if (n == 0)       // base case
        return 0;
    return (n % 10) + sumOfDigits(n / 10);  // last digit + sum of remaining
}

int main() {
    int n;
    scanf("%d", &n);

    int result = sumOfDigits(n);
    printf("Sum of digits of %d = %d\n", n, result);

    return 0;
}
```

**output**

<img width="705" height="205" alt="image" src="https://github.com/user-attachments/assets/396cd845-fc1a-4fc9-a025-0ae692c00504" />

**Result:**

The program successfully computes and displays the sum of digits of a given number using a recursive function.
---

# 3.Program: Maximum Element in Each Row of a Matrix

**Aim:**  

To write a C program that finds and prints the maximum element of each row in a given matrix.



**Algorithm:**  

1. Start the program.  
2. Declare a 2D array ma[m][n] to store the matrix elements.  
3. Read the number of rows m and columns n from the user.  
4. Input all elements of the matrix using nested for loops.  
5. For each row:  
   - Initialize max as the first element of that row.  
   - Compare each element in the row with max.  
   - If any element is greater than max, update max.  
6. After scanning each row, print the maximum element of that row.  
7. End the program.



**Source Code:** 

```c
#include<stdio.h>
int main()
{
    int m, n, row, col;
    scanf("%d%d", &m, &n);
    int ma[m][n];
    
    for(row = 0; row < m; row++) {
        for(col = 0; col < n; col++) {
            scanf("%d", &ma[row][col]);
        }
    }

    for(row = 0; row < m; row++) {
        int max = ma[row][0];
        for(col = 0; col < n; col++) {
            max = (ma[row][col] > max) ? ma[row][col] : max;
        }
        printf("Maximum element of the row %d is: %d\n", row + 1, max);
    }
    return 0;
}
```

**output**

<img width="924" height="306" alt="image" src="https://github.com/user-attachments/assets/b95cc447-664c-4e38-9513-b5b81dad9fe4" />

**Result**

The program successfully reads a matrix and displays the maximum element of each row.
---

# 4.Program: Reverse a String Using Pointer

**Aim:**  

To write a C program that reverses a given string using a pointer.



**Algorithm:**  

1. Start the program.  
2. Declare a character array str to store the input string and a pointer ptr.  
3. Read a string using fgets() from the user.  
4. Use strlen() to calculate the length of the string.  
5. Remove the newline character (\n) added by fgets(), if present.  
6. Initialize the pointer ptr to point to the last character of the string.  
7. Using a for loop, print characters in reverse order by:  
   - Printing the character pointed to by ptr.  
   - Decrementing the pointer in each iteration.  
8. Print the reversed string and end the program.



**Source Code:**  

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    char *ptr;
    int length, i;
    fgets(str, sizeof(str), stdin);

    // Remove newline character if present
    length = strlen(str);
    if (str[length - 1] == '\n') {
        str[length - 1] = '\0';
        length--;
    }

    // Set pointer to the last character of the string
    ptr = &str[length - 1];

    // Print characters in reverse using the pointer
    for (i = length - 1; i >= 0; i--) {
        printf("%c", *ptr);
        ptr--;  // Move pointer backward
    }
    printf("\n");

    return 0;
}
```

**output**

<img width="601" height="145" alt="image" src="https://github.com/user-attachments/assets/fa99c992-7d95-460e-9977-2e4f3c1a3a2d" />

**Result:**

The program successfully reverses the input string using a pointer and displays it in reverse order.
---

# 5.Program: Remove Duplicate Characters from a String

**Aim:**  

To write a C program that removes duplicate characters from a given string.

---

**Algorithm:**  

1. Start the program.  
2. Declare a character array str to store the input string.  
3. Read the string from the user using fgets().  
4. Calculate the length of the string using strlen().  
5. Use nested for loops to compare each character with the rest of the string:  
   - Outer loop iterates through each character (i).  
   - Inner loop checks for duplicate characters (j).  
6. If a duplicate character is found:  
   - Shift all characters after the duplicate one position to the left.  
   - Decrease the length of the string by 1.  
   - Decrement j to recheck from the shifted position.  
7. Print the final string after removing duplicates.  
8. End the program.

---

**Source Code:**  

```c
#include <stdio.h>
#include <string.h>

int main()
{
    char str[100];
    int i, j, k;
    
    fgets(str, sizeof(str), stdin);
    int len = strlen(str);
    
    for (i = 0; i < len; i++) {
        for (j = i + 1; j < len; j++) {
            if (str[i] == str[j]) {
                for (k = j; k < len; k++) {
                    str[k] = str[k + 1];
                }
                len--;
                j--;
            }
        }
    }
    printf("String after removing characters: %s", str);
    return 0;
}
```

**output**

<img width="937" height="118" alt="image" src="https://github.com/user-attachments/assets/f6658bde-4831-4dad-a19d-4bfafecbf1ea" />

**Result**

The program successfully removes all duplicate characters from the given input string and displays the unique-character string.
---
