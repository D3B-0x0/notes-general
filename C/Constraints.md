---

## C Constraints

In C programming, **constraints** are the rules you must follow to write correct code. These rules apply to how you name variables, use data types, write functions, and more.

### 1. **Variable Constraints**

- **Naming**: Variable names must start with a letter or underscore (`_`). They can’t use C keywords like `int`, `if`, or `return`.
- **Scope**: Where you declare a variable affects where you can use it. For example, variables declared inside a function can’t be used outside it.

### 2. **Type Constraints**

- **Type Matching**: When you do operations (like adding or multiplying), the data types must be compatible (e.g., adding two integers).
- **Size**: Each data type (like `int`, `char`, etc.) has a specific size, which limits how much data it can hold.

### 3. **Function Constraints**

- **Declaration**: You must declare a function before using it. The function's name, return type, and parameters should match its declaration.
- **Parameters**: The number and type of parameters you pass to a function must match what the function expects.

### 4. **Pointer Constraints**

- **Valid Type**: Pointers must point to a specific data type (like `int *`, `char *`).
- **NULL**: Pointers should be checked to ensure they aren’t NULL (i.e., don’t point to anything) before you use them.

### 5. **Array Constraints**

- **Size**: You must specify the size of an array when you create it. The size can’t change later.
- **Bounds**: Don’t access elements outside the array’s defined size (e.g., if an array has 5 elements, don’t try to access the 10th element).

### 6. **Control Flow Constraints**

- **Loops**: Loops (`for`, `while`) must eventually stop, or they’ll run forever.
- **Conditions**: `if`, `else`, and `switch` statements must check conditions that result in true (`1`) or false (`0`).

### 7. **Memory Constraints**

- **Allocation**: If you allocate memory dynamically (e.g., with `malloc()`), remember to free it when done to avoid memory leaks.

---

#### Lets move to \[\[Keywords and Comments\]\]

#### Also check \[\[Variables\]\]