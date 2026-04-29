# A64: Function Overloading

**Code your program here:** [https://classroom.github.com/a/M7jLFZzm](https://classroom.github.com/a/M7jLFZzm)

---

## 3. Elaborate on Errors and Troubleshooting

- Programming algorithms used
- Errors encountered and troubleshooting steps taken
- Error experiences and lessons learned (how you identified and fixed each error)

---

## [Programming Assignment Guide]

**Read the Assignment Directions below, then complete the following `main.cpp` in your cloned Repository.**

**Assignment Directions:**

What is Function Overloading?
Function overloading means you can define **multiple functions with the same name**, as long as each version has a different number (or type) of parameters. The compiler automatically picks the right version based on how you call it.

For example, all three lines below call a function named `swapValues`, but each calls a different version:

```cpp
swapValues(a, b);           // 2-parameter version
swapValues(a, b, c);        // 3-parameter version
swapValues(a, b, c, d);     // 4-parameter version
```

This is useful because it keeps your code readable — you don't need different names like `swap2`, `swap3`, `swap4`.

What is a Reference Parameter (&)?
When you pass a variable to a function normally, the function gets a *copy* — changes inside the function do not affect the original. A **reference parameter** (written with `&`) passes the original variable directly, so the function *can* change it.

```cpp
void swapValues(int &n1, int &n2)  // & means "work with the original"
```

Your Task: Write Three Overloaded swapValues() Functions
You will write all three functions inside **main.hpp**. The file **main.cpp** already calls them for you — do not edit main.cpp.

**Function 1: swapValues(int &n1, int &n2)** — Swap two values

- After the call, n1 holds the old value of n2, and n2 holds the old value of n1.
- Example: n1=10, n2=20 → after swap: n1=20, n2=10
- Hint: You need a temporary variable to hold one value while you move the other.

```cpp
int tmp = n1;
n1 = n2;
n2 = tmp;
```

**Function 2: swapValues(int &n1, int &n2, int &n3)** — Circular (rotate) three values

- Each value shifts one position: n1 gets n2's value, n2 gets n3's value, n3 gets n1's original value.
- Example: n1=10, n2=20, n3=30 → after: n1=20, n2=30, n3=10
- Think of it as rotating left: 10, 20, 30 becomes 20, 30, 10.

```cpp
int tmp = n1;
n1 = n2;
n2 = n3;
n3 = tmp;
```

**Function 3: swapValues(int &n1, int &n2, int &n3, int &n4)** — Reverse four values

- The first and last swap, and the middle two swap: n1↔n4, n2↔n3.
- Example: n1=10, n2=20, n3=30, n4=40 → after: n1=40, n2=30, n3=20, n4=10
- You can call the 2-parameter swapValues twice, or use a temporary variable for each pair.

```cpp
swap(n1, n4);
swap(n2, n3);
```

Files You Need to Know

- main.hpp — This is the file you edit. Write all three swapValues() functions here.
- main.cpp — Do not edit. It calls your functions and prints results.
- tests.cpp — Do not edit. Automated Catch2 tests that verify your functions work correctly.

Step-by-Step Instructions

**Starter Code (`main.cpp`):**

```cpp
#include <iostream>
using namespace std;

void swapValues(int &, int &);
void swapValues(int &, int &, int &);
void swapValues(int &, int &, int &, int &);

void swapValues(int &n1, int &n2)
{
    // TODO: Swap the two values
    //       After this function, n1 holds the original n2, and n2 holds the original n1.

}

void swapValues(int &n1, int &n2, int &n3)
{
    // TODO: Circularly rotate the three values
    //       n1 = old n2, n2 = old n3, n3 = old n1

}

void swapValues(int &n1, int &n2, int &n3, int &n4)
{
    // TODO: Reverse the four values
    //       n1 <-> n4, n2 <-> n3

}
```

**How to compile and run your program:**

- To compile your program in VS Code, open the new terminal (ctrl-`) and type: `g++ main.cpp -o main`
- To run your program: `./main`

**How to test your program:**

- To run all tests: `make test`
- To run a specific test (e.g., T1): `make test ARGS="[T1]"`

**[Expected Output]**

*Your output should contain the correct values. The exact wording or formatting may differ — tests check values only, not the entire output.*

Example run (main.cpp with n1=10, n2=20, n3=30, n4=40):

```cpp
Original Values are 10	20	30	40
After changing two value n1 and n2 20	10
After changing three value n1, n2 and n3 10	30	20
After changing four value n1, n2, n3 and n4 40	20	30	10
```

**How to pass the test:**

Test items: **compile, run, T1, T2, T3, T4**

| Test | Input | Expected Values (checked by test) | Points |
|---|---|---|---|
| T1 | n1=10, n2=20 | n1=20, n2=10 | 20 |
| T2 | n1=10, n2=20, n3=30 | n1=20, n2=30, n3=10 | 20 |
| T3 | n1=10, n2=20, n3=30, n4=40 | n1=40, n2=30, n3=20, n4=10 | 20 |
| T4 | n1=-5, n2=7 | n1=7, n2=-5 | 20 |

To test your program, type the command in your terminal: `make test`

**Make sure that your program passes the test and there is ✓ in your GitHub Classroom Repository.**

