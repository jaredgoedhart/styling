# Styling
Jared Goedhart's coding style designed for clarity, consistency, and efficiency

---


## Type Hints 🔍
#### Use type hints wherever possible for function signatures and variables to enhance code readability and maintainability.

```python
def print_album_details(album_name: str, release_year: int) -> None:
    """
    Print the details of a music album.
    """
    
    print(f"Album: {album_name} ({release_year})")
```


---


## Docstrings 🗒️
### Every function, class, and module must have clear and concise docstrings.

```cpp
/**
 * @brief Adds two numbers.
 * 
 * @param number1 The first number.
 * @param number2 The second number.
 * @return The sum of the two numbers.
 */
int add_numbers(int number1, int number2)
{
    return (number1 + number2);
}
```


---


## Spacing 📏

1. Use tabs the size of 4 spaces for indentation.
2. Use **two white lines** between distinct code components such as functions, classes, and imports.
3. Use **one white line** between separate themed lines of code within a function or script.


---


## Naming Convention: Variable Names ✍️

1. Always use **clear and descriptive variable names** that precisely describe the data they hold or their purpose.
2. Avoid abbreviations or cryptic names.
    - Example: Use `average_grade_male_student` instead of `avgNumMaleStud`.
3. Variable names must use **snake_case**, even if this is uncommon for the language, to ensure consistency and readability.


---


## Naming Convention: Case Style 🐍

### Variables and Functions
- Use **snake_case** for naming.
    - **Why?** This style clearly distinguishes your code from external modules and standard libraries.
    - **Example:** 
      - ✅ `calculate_average_grade()`
      - ❌ `CalculateAvgGrade()`

### Classes and Files
- Use **PascalCase** for naming classes.
    - **Example:**
      - ✅ `StudentRecord`
      - ❌ `student_record`

- Use **PascalCase** for file names.
    - **Example:**
      - ✅ `DataProcessor.py`
      - ❌ `data_processor.py`


---


## Curly Braces `{}` on New Lines 🛠️

1. Always place opening and closing curly braces `{}` on **new lines** for better clarity and readability.
2. If a line contains an opening or closing curly brace for a scope (e.g., a class, function, or control structure), it must be the **only character on that line**. This ensures the braces are visually distinct and easy to locate.

#### Examples:
- Correct:
    ```c
    void example_function()
    {
        if (condition)
        {
            // Code block
        }
    }
    ```

- Incorrect:
    ```c
    void example_function(){
        if (condition){
            // Code block
        }
    }
    ```


---


## Integer Types 🎯

1. Always use **explicit integer types** such as `uint16_t`, `uint32_t`, `int8_t`, etc., for clarity and to avoid ambiguity.
2. Choose the integer type that best fits the range of the data it needs to hold, to ensure efficient memory use and prevent overflow or data loss.

### Common Integer Types and Their Ranges:

| Type        | Also Known As          | Size (bits) | Range                                |
|-------------|-----------------------|-------------|-------------------------------------|
| `int8_t`    | `char`, `signed char` | 8           | -128 to 127                         |
| `uint8_t`   | `unsigned char`       | 8           | 0 to 255                            |
| `int16_t`   | `short`, `short int`  | 16          | -32,768 to 32,767                   |
| `uint16_t`  | `unsigned short`      | 16          | 0 to 65,535                        |
| `int32_t`   | `int`, `signed int`   | 32          | -2,147,483,648 to 2,147,483,647     |
| `uint32_t`  | `unsigned int`        | 32          | 0 to 4,294,967,295                  |
| `int64_t`   | `long long`, `signed long long` | 64 | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
| `uint64_t`  | `unsigned long long`  | 64          | 0 to 18,446,744,073,709,551,615     |


---


## String and Character Formatting 🧵

1. Use double quotes `""` for **strings**.
2. Use single quotes `''` for **characters**.

#### Examples:
```c
const char letter = 'A';         // Character
const char* greeting = "Hi";    // String
```


---


## Import and Include Order 📂
1. First, include **standard library** imports.
2. Then, include **third-party library** imports.
3. Lastly, include **your own custom/project-specific** imports.
4. Separate the import groups with a single blank line.
5. Within each group, arrange imports from shortest to longest line for better readability.

#### Example:
```python
# Standard library imports
import os
import sys
import google

# Third-party library imports with aliases
import numpy as np
import polars as pl
import networkx as nx

# Third-party relative imports
from pandas import DataFrame
from open_cv.vision import U32Vector

# Project-specific direct imports
import utility

# Project-specific imports with aliases
import write as w

# Project-specific relative imports
from read import read_csv, read_pdf


---


## Constants ⚓

1. Use `const` to declare constant variables that should not be modified after initialization.
2. Use `constexpr` for compile-time constants to enable better compiler optimizations.
3. Prefer `constexpr` when the value is known at compile time; otherwise, use `const`.

#### Example:

```cpp
constexpr int max_connections = 100;

const std::string file_path;
```


---


## Memory Optimization ⚡

### Key Guidelines:

- Use **references** to avoid unnecessary copying of large objects or data structures.


- Prefer **integer keys** over string keys for maps and dictionaries to improve performance by:
    - Avoiding expensive string comparisons.
    - Reducing memory usage for keys.
    - **Example:**  
      An `uint8_t` key uses **1 byte**, whereas a string key uses `n * string.length() * 8 bits` (where *n* is the number of entries), which is significantly larger depending on string length.


---


## Suffixes for Types 🏷️

- Use **`f`** suffix for `float` literals to clearly indicate single precision.
- Use **`u`** suffix for **unsigned** integer literals.
- Use other appropriate suffixes as needed (e.g., `L` for long, `UL` for unsigned long).

#### Examples:

```cpp
float pi = 3.14f;                    // 'f' suffix for float literal

unsigned int max_users = 100u;       // 'u' suffix for unsigned integer literal

long long big_number = 123456789LL;  // 'LL' suffix for long long literal, but explicit integer type recommended
```


---


## Reduce System Calls Usage ⏳


- Minimize the use of system-level calls like `read`, `print`, `copy`, `malloc`, and similar functions.
- These calls are often costly in terms of performance and can introduce unnecessary overhead.



---


## Information Loss Awareness ⚠️

- Be mindful of potential **data loss** when casting between types, especially from higher-precision to lower-precision types.
- For example, casting a `double` (64-bit) to a `float` (32-bit) can cause loss of precision.
- Always verify if the cast is safe or if an alternative approach is needed to preserve data integrity.


---


## Conditional Statements 📐

- Always **surround if statement conditions with parentheses** for clarity and consistency.
- Use **proper indentation** to improve readability.
- For example, use:

```cpp
if ((statement_1) || (statement_2))
{
    // Code block
}
