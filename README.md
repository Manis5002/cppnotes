# Introduction to C++

## What is C++?
C++ is a highly versatile, general-purpose programming language. It is widely used across various domains including game development, web servers, desktop applications, console game development, and embedded systems. 

### Key Characteristics
* **High Performance:** C++ allows direct access to hardware.
* **Low Abstraction Overhead:** It enables programmers to write code without unnecessary layers of abstraction getting in the way.
* **Multi-Paradigm:** C++ does not force a single style of programming. You can write code in several paradigms to best solve your specific problem:
  * Procedural
  * Object-Oriented
  * Functional
* **Cross-Platform:** Available on Windows, Linux, Mac, and many other operating systems.

### Advanced Concepts Preview
*(Note: These are advanced Modern C++ concepts mentioned as future topics in the series)*
* **Rule of Three / Rule of Five**
* **Move Semantics**
* **Memory Allocators**
* **Smart Pointers** (and knowing when/where to use different types)
* **Design Patterns**

---

# The C++ Compilation Process

## Compiled vs. Interpreted Languages
Unlike languages like Python (which are interpreted), C++ is a **fully compiled language**. This compilation step is a primary reason for C++'s speed and high performance. 

### The Core Components
1. **Source Code (`.cpp` file):** A plain text file containing your C++ code. You can write this in any text editor (e.g., Vim, Visual Studio Code, Kate on Linux).
2. **Compiler:** A tool that reads your source code and translates it into machine code. 
   * Common compilers: `g++` (GNU), `clang++` (LLVM), `MSVC` (Microsoft Visual Studio Compiler), Intel Compiler.
3. **Executable / Binary File:** The resulting machine code file produced by the compiler. 
   * Windows extension: `.exe`
   * Linux/Mac: Typically has no extension (executed directly).

## The C++ Development Workflow

**Crucial Rule:** In C++, you cannot simply run your code immediately after typing it. 

Every time you make a change to your code, you **must** follow this exact loop:
1. **Write/Modify** the code in your text editor.
2. **Save** the file (`Ctrl + S` or `:w` in Vim). *If you don't save, the compiler will compile the old version of the file.*
3. **Recompile** the file using your compiler.
4. **Run** the newly generated executable.

### Compilation Example (Terminal)

Assume you have a source file named `hello.cpp`.

```bash
# 1. Compile the source code using the g++ compiler
# Syntax: g++ <source_file> -o <output_executable_name>
g++ hello.cpp -o prog

# 2. Execute the compiled program (Linux/Mac)
./prog
```
* **Note:** If you are using Linux or Mac, you execute the program by prepending `./` (dot-slash) to the executable name (e.g., `./prog`), which tells the system to run the file located in the current directory.

---

# Setting Up the C++ Environment (Linux)

## Verifying the Compiler
To check if a C++ compiler is already installed, open your terminal and type:
```bash
g++
```
* If it returns a message like `g++: fatal error: no input files`, the compiler **is installed** and ready to use. 
* If the command is not found, you need to install it.

## Installing `g++`
Use your Linux distribution's package manager to install the compiler.

| Package Manager | Operating System | Installation Command |
| :--- | :--- | :--- |
| **APT** | Debian / Ubuntu | `sudo apt-get install g++` |
| **YUM** | CentOS / RHEL | `sudo yum install gcc-c++` *(implied by transcript as yum install g++)* |
| **Pacman** | Arch Linux | `sudo pacman -S gcc` *(implied by transcript as pacman install g++)* |

**Additional Tools:**
It is highly recommended to install the standard build tools package, which includes `g++` and other essential compilation tools:
```bash
sudo apt-get install build-essential
```

## Alternative Compilers: Clang
You can also use the Clang compiler, which functions very similarly to `g++`:
```bash
sudo apt-get install clang
```

## Compiler Versions and Modern C++ Standards
C++ is heavily versioned (e.g., C++11, C++14, C++17, C++20, C++23, C++26). When writing Modern C++, you need a compiler recent enough to support the standard you want to use (usually at least C++11 or C++17).

### How to check your compiler version:
```bash
g++ --version
```
*(Example output: `g++ (Ubuntu 10.x.x) 10...` indicates version 10).*

### How to check the default C++ Standard:
You can look through the compiler manual to see what version of C++ it defaults to if you don't specify one.
```bash
man g++
```
*(For example, an older version of `g++` might default to C++14).*

### Installing a Specific Version of `g++`
If your default package manager installs an outdated version, you can search for newer versions and install them explicitly.

**Trick to see available versions:**
Type `g++-` and hit the `<TAB>` key twice to trigger autocomplete. This will list all the specific versions available in your package manager repositories (e.g., `g++-8`, `g++-9`, `g++-10`).

Install the specific version:
```bash
sudo apt-get install g++-10
```
*Note: Installing this way usually creates an alias, so typing `g++` will automatically use the newly installed modern version instead of forcing you to type `g++-10` every time.*
# Setting Up the C++ Environment

## macOS Setup

### The Clang Compiler
macOS typically defaults to using the **Clang** compiler. 
* **Check Installation:** Open the terminal and type `clang++`. If installed, it will return a message indicating no input files.
* **Check Version:** `clang++ --version`. Any version past 5 is sufficient, though 12+ is standard for Modern C++.
* **Install via Xcode Command Line Tools:** If Clang is not installed, install it alongside Apple's Xcode IDE environment by running:
  ```bash
  xcode-select --install
  ```

### The GCC Compiler (Optional)
If you specifically want to use `g++` on a Mac, you can install it using the **Homebrew** package manager.
* **Search for GCC versions:** `brew search gcc`
* **Install a specific modern version:** `brew install gcc@10` (Version 10 or beyond is recommended for modern C++).

### Using the Xcode IDE
For professional development on macOS, you can use the complete Xcode IDE.
1. Create a New Project -> Select **macOS Command Line Tool**.
2. Select **C++** as the language.
3. The IDE provides a `main.cpp` file automatically.
4. Use the built-in "Run" button to compile, link, and execute the program in one step. Build output and errors appear directly inside the IDE.

---

## Windows Setup (Microsoft Visual Studio)

### Visual Studio vs. Visual Studio Code
* **Visual Studio (Community Edition):** A full Integrated Development Environment (IDE). Recommended for C++ development on Windows.
* **Visual Studio Code:** A lightweight text editor. (Not used in this specific setup).

### Creating a Project
1. Open Visual Studio and click **Create a new project**.
2. Choose **Empty Project** (this gives you full control over your files).
3. A **Solution** is created, which can contain multiple projects.
4. Right-click the project -> **Add** -> **New Item** -> **C++ File (.cpp)**. By convention, name the entry point file `main.cpp`.

### Configuring Project Properties (Modern C++)
To use Modern C++ standards or link external libraries, configure the project properties:
* Right-click the specific project (not the solution) -> **Properties**.
* **Change Language Standard:** Go to `Configuration Properties` -> `C/C++` -> `Language` -> `C++ Language Standard` (Set this to **C++17**, **C++20**, etc.).
* **Include Directories (Header files):** Configured in `C/C++` -> `General` -> `Additional Include Directories`.
* **Libraries (Linking):** Configured in `Linker` -> `General` / `Input`.

### Debugging Basics in Visual Studio
Visual Studio provides powerful built-in debugging tools:
* **Breakpoints:** Press `F9` (or click the margin) to toggle a breakpoint. Execution will pause on this line.
* **Inspecting Variables:** When paused, use the "Autos" or "Locals" window to see the current values of variables in memory.
* **Step Over:** Executes the current line and moves to the next line without jumping into function calls.
* **Continue:** Resumes execution until the next breakpoint.

---

# Anatomy of a C++ Program (Hello World)

## The `main` Function
Every C++ program must have a single **entry point**, which is the `main` function.

### Syntax
```cpp
int main() {
    // Code goes here
    return 0;
}
```
### Explanation
* `int`: The `main` function returns an integer value to the operating system.
* `return 0;`: By convention, returning `0` (or macros like `EXIT_SUCCESS`) indicates that the program executed successfully without errors.

## The Standard Library and `#include`
C++ does not have built-in primitive string output capabilities. To interact with the screen, you must include code from the **C++ Standard Library**.

### `#include <iostream>`
* **Definition:** A preprocessor directive that imports the Input/Output Stream library.
* **Explanation:** Similar to `import` in Python or Java. It brings in external library code into your current file so you can use its functions (like outputting text).

## Outputting Text (`std::cout`)
* **`std::cout`**: Stands for "Standard Character Output". It represents the standard output stream (usually the terminal).
* **`<<`**: The insertion operator. It "streams" the data on the right into the output stream on the left.

## Formatting Output: Newlines
There are two ways to emit a newline character in C++:
1. `\n` : The standard newline escape character embedded within a string (e.g., `"Hello World\n"`).
2. `std::endl`: A function from the standard library that not only emits a newline but also flushes the output stream.

## Namespaces
A **namespace** is a declarative region that provides a scope to the identifiers (names of types, functions, variables) inside it. It prevents naming conflicts.

### The `std` Namespace
All components of the C++ standard library fall under the `std` namespace. This is why you must prepend standard library features with `std::`.

### `using namespace std;`
```cpp
#include <iostream>
using namespace std; // Brings all std names into global scope

int main() {
    cout << "Hello World!" << endl; // std:: is no longer needed
    return 0;
}
```
### Important Caveat
While `using namespace std;` saves typing, it is **highly discouraged** in professional code. 
* **Reason:** It pollutes the global namespace, making it unclear where specific functions or objects are coming from, increasing the risk of naming collisions.
* **Best Practice:** Always explicitly use the `std::` prefix (e.g., `std::cout`, `std::endl`).

## Complete Hello World Example
```cpp
#include <iostream>

int main() {
    std::cout << "Hello World!\n";
    return 0;
}
```

---

# Compilation and Error Handling

## Command Line Compilation
To compile a modern C++ program from the terminal, explicitly provide the standard flag:
```bash
clang++ -std=c++17 hello.cpp -o prog
# or
g++ -std=c++17 hello.cpp -o prog
```

## Debugging Compiler Errors

### 1. Cascading Errors
A single syntax mistake (such as a missing closing quotation mark or semicolon) can confuse the compiler, causing it to generate multiple cascading errors and warnings downstream. 

**Rule:** Always fix compilation errors starting from the **very top** of the error output list. Fixing the first error often resolves the subsequent ones automatically.

### 2. Make Small Iterations
Because C++ is a compiled language, debugging large blocks of untested code is difficult. 
**Rule:** Make small changes to your code, save, and recompile frequently. This allows you to pinpoint exactly which new line caused the build to fail.

### 3. Treat Warnings as Errors
Warnings indicate suspicious code that might compile but could lead to unintended behavior.
* **Best Practice:** Treat warnings as strictly as errors. 
* **Compiler Flag (`-Werror`):** Passing `-Werror` to the compiler instructs it to halt compilation entirely if *any* warning is detected, enforcing safer programming habits.
  ```bash
  g++ -Werror -std=c++17 hello.cpp -o prog
  ```
  # Modern C++ Standards & Evolution

## What is Modern C++?
C++ is a rapidly evolving language. The term **Modern C++** typically refers to the versions of the language starting from C++11 and onward. 

### The Release Cycle
The C++ standard is updated on a strict **three-year release cycle**.
* Major recent and upcoming versions include: **C++11, C++14, C++17, C++20, C++23, C++26**.
* By specifying a flag during compilation (e.g., `-std=c++17` or `-std=c++20`), you instruct the compiler to allow features specific to that standard.
* Compilers (like GCC, Clang, MSVC) implement new features over time, so you must ensure your compiler version supports the standard you wish to use.

## Recommended Resources
When learning or referencing C++, the instructor recommends:
1. **cppreference.com**: The definitive, highly technical standard reference for C++. It includes exact implementation details, standard versions, and interactive code snippets you can run in the browser. Best for intermediate/advanced use.
2. **cplusplus.com**: Offers comprehensive, beginner-friendly tutorials to build a foundation.
3. **isocpp.org**: The official site for C++ news, core guidelines (best practices), conferences, and major updates.

---

# Fundamental Data Types

## Statically Typed Language
C++ is a **statically typed** language. 
* **Definition:** You must specify the data type of a variable when you declare it, and this is determined at **compile time**.
* **Explanation:** The compiler needs to know exactly how much memory (how many bytes) to allocate for the variable before the program even runs.

## Memory and the `sizeof` Operator
To figure out how much memory a specific data type or variable uses on your system, C++ provides the `sizeof` operator.

* **Syntax:** `sizeof(type)` or `sizeof(variable)`
* **Output:** Returns the size in **bytes**. (Remember: 1 byte = 8 bits).

```cpp
#include <iostream>

int main() {
    int x = 42;
    std::cout << sizeof(x) << '\n';   // Output: 4 (typically)
    std::cout << sizeof(int) << '\n'; // Output: 4 
    return 0;
}
```

## Primitive Types Overview

Here is a summary of the common fundamental (built-in) data types in C++:

| Type | Description | Typical Size | Example |
| :--- | :--- | :--- | :--- |
| **`int`** | Integer values. | 4 bytes (32 bits) | `int x = 42;` |
| **`long long`** | Very large integer values. | 8 bytes (64 bits) | `long long bigNum = 99999999999;` |
| **`float`** | Single-precision floating point (decimal). Requires `f` suffix. | 4 bytes | `float pi = 3.14f;` |
| **`double`** | Double-precision floating point. Defaults for decimals without `f`. | 8 bytes | `double precisePi = 3.14159265;` |
| **`bool`** | Boolean value (`true` or `false`). Evaluates to `1` or `0`. | 1 byte | `bool isReady = true;` |
| **`char`** | Single text character. Enclosed in **single quotes**. | 1 byte | `char letter = 'A';` |

### Important Behaviors and Caveats
* **Integer Overflow:** If you try to store a number larger than the allocated memory can hold (e.g., storing a 64-bit number inside a 32-bit `int`), the compiler will throw an overflow warning, and the data will be corrupted. Use `long long` for larger numbers.
* **Booleans Print as Integers:** By default, printing a `bool` outputs `1` for `true` and `0` for `false`, not the literal words "true" or "false".
* **Floats vs. Doubles:** Decimals in C++ default to `double`. If you specifically want a `float`, you **must** append the `f` suffix (e.g., `3.14f`). If you exceed the precision of a `float`, it will truncate/round the value.

## Fixed-Width Integers (Modern C++)
Because standard sizes (like `int`) can technically vary depending on the system architecture (32-bit vs. 64-bit systems), Modern C++ introduces **fixed-width integer types**.
* **Usage:** Guarantees exact bit sizes across all platforms.
* **Convention:** The `_t` suffix stands for "type".

```cpp
#include <iostream>
#include <cstdint> // Required for fixed-width integers

int main() {
    // Guarantees exactly 64 bits (8 bytes) of storage
    int64_t fixedInt = 99999999999999; 
    return 0;
}
```

## Strings in C++ (Non-Primitive)
**Strings are NOT a primitive data type in C++.**

### The Character Array/Literal Problem
* A `char` only holds a *single* character in single quotes: `'a'`.
* If you attempt to put multiple characters in single quotes (`'abc'`), you will get a multi-character warning, and it will produce unpredictable behavior (usually keeping only the last character).
* Text in double quotes (`"abc"`) is treated as a `const char*` (a pointer to a character array), which is a C-style string.

### The Modern C++ Solution: `std::string`
To use strings properly and safely, you must include the standard library `<string>`.

```cpp
#include <iostream>
#include <string> // Must include the string library

int main() {
    std::string name = "abc";
    std::cout << name << '\n';
    return 0;
}
```

---

# Immutability and the `const` Keyword

## Mutable vs. Immutable Variables
* **Mutable (Default):** Variables in C++ can be modified or reassigned after they are declared.
* **Immutable:** The state or value of the variable cannot change once initialized.

## The `const` Keyword
Adding `const` before a data type makes the variable **read-only** (immutable).

### Use Case
Use `const` when you want to protect a variable from being changed accidentally, which prevents programmer errors. (e.g., defining mathematical constants, configurations).

```cpp
#include <iostream>

int main() {
    const float pi = 3.1415f;
    
    // pi = 3.0f; // COMPILE ERROR: assignment of read-only variable 'pi'
    
    std::cout << pi << '\n';
    return 0;
}
```

### Important Details
* **Compiler Enforcement:** If you attempt to reassign a `const` variable, the compiler will immediately throw a compilation error.
* **Casting away const:** While C++ technically allows you to force the removal of `const` using specific casting techniques, this is considered extremely dangerous and is almost never recommended.

## Teaser: `constexpr` (Compile-Time Evaluation)
While `const` means a variable is read-only at runtime, Modern C++ introduces **`constexpr`**.
* **Explanation:** `constexpr` indicates that the value is a constant *and* can be fully evaluated before the program even runs (at compile time).

```cpp
// The compiler calculates 3 + 6 + 8 and just stores 17 in the final binary
constexpr int x = 3 + 6 + 8; 
```

# Scope and Variable Lifetime

## Block Scope
C++ is a curly-brace language. The region enclosed by a pair of curly braces `{}` is known as a **block scope**. 
* **Visibility:** A variable declared inside a block is strictly local to that block. It cannot be accessed from outside.
* **Shadowing/Reuse:** You can reuse common variable names (like `x` or `i`) throughout your program as long as they are declared in separate local scopes.
* **Memory Efficiency:** When a variable goes out of scope (i.e., execution reaches the closing brace `}`), it is automatically destroyed, and its memory is reclaimed. This is a fundamental concept for memory efficiency in C++.

```cpp
int main() {
    {
        int x = 7; 
        // 'x' is valid here
    }
    // x = 10; // COMPILE ERROR: 'x' is not declared in this scope
    
    {
        int x = 42; // Perfectly valid, this is a new 'x' in a different scope
    }
    return 0;
}
```

## Global Variables
Variables declared completely outside of any function or block are **global variables**.
* **Visibility:** They can be accessed and modified from anywhere in the file (and potentially across multiple files).
* **Best Practice:** **Avoid global variables.** Because they lack strict scope limits, they can be modified unpredictably from anywhere in the program, making state difficult to track and bugs hard to isolate.

---

# Data Structures: Arrays

## What is an Array?
An array is a fundamental data structure built into C++ that stores a collection of items.
* **Homogeneous:** All elements in the array must be of the exact same data type.
* **Contiguous Memory:** Elements are stored in memory directly next to one another. This sequential layout is highly optimized for the CPU.
* **Zero-indexed:** The first element is always at index `0`.

## 1. Raw Arrays (C-Style)
* **Compile-Time Sizing:** The size of a raw array must be known and fixed when the program compiles. You cannot change its size while the program is running.
* **Uninitialized Memory:** By default, raw array elements are not initialized. They will contain whatever garbage data was previously left in that memory location. You must initialize them before use.

```cpp
int main() {
    // Declares an array of 100 integers
    int ids[100]; 
    
    // Accessing elements
    ids[0] = 12345; // First element
    ids[99] = 9;    // Last element
    
    // Out-of-bounds access (Undefined Behavior)
    // ids[100000] = 5; // DANGER: May cause a "Segmentation Fault" and crash.
    return 0;
}
```

## 2. Modern C++: `std::array`
Modern C++ programmers heavily prefer `std::array` over raw arrays. It is part of the Standard Template Library (STL).
* **Include Header:** Requires `#include <array>`
* **Syntax:** `std::array<Type, Size> variableName;`
* **Safety:** Provides `.at()`, a bounds-checking member function. 

### `.at()` vs Raw Indexing `[]`
If you access an index that does not exist:
* `ids[100000]`: Causes an unpredictable **Segmentation Fault** (program crashes silently or corrupts memory).
* `ids.at(100000)`: Throws an explicit **out_of_range Exception**, identifying exactly what went wrong and allowing you to handle the error gracefully.

```cpp
#include <iostream>
#include <array>

int main() {
    // Template syntax: <type, size>
    std::array<int, 100> ids;
    
    // ids.at(100000) = 42; // Throws a clean std::out_of_range exception
    ids.at(99) = 9;         // Safe, bounded access
    
    return 0;
}
```

## Algorithms on Arrays: `std::iota`
You can run standard algorithms on contiguous data structures. 
* **Header:** `#include <numeric>`
* **Purpose:** Fills a data structure with sequentially increasing values.

```cpp
#include <numeric>
#include <array>

int main() {
    std::array<int, 100> ids;
    // Fills array from start to end with 0, 1, 2, 3... 99
    std::iota(std::begin(ids), std::end(ids), 0);
    return 0;
}
```

---

# Loops and Iteration

Loops are fundamental constructs used to build algorithms and repeat execution.

## 1. The `for` Loop
Used when you know exactly how many times you want to iterate.
* **Syntax:** `for (Initialization; Condition; Update Expression) { ... }`

```cpp
int arr[] = {1, 3, 5};

for (int i = 0; i < 3; i++) {
    std::cout << arr[i] << '\n';
}
```
* **Optional Arguments:** All parameters in a `for` loop are technically optional. 
  * `for(;;)` will create an **infinite loop**.

## 2. Range-Based `for` Loop (Modern C++)
Introduced in Modern C++, this loop is specifically designed to iterate through an entire collection (like an array or `std::array`) cleanly, without managing an index manually.

```cpp
#include <iostream>
#include <array>

int main() {
    std::array<int, 3> arr2 = {1, 3, 5};
    
    // Automatically loops from the first element to the last
    for (int element : arr2) {
        std::cout << element << '\n';
    }
    return 0;
}
```

### The `auto` Keyword in Loops
Instead of explicitly typing the data type (`int`), you can use `auto`. The compiler will automatically deduce the underlying type of the collection.
```cpp
for (auto element : arr2) { ... }
```
* **Performance Note (Teaser):** You will often see `auto& element` used. The `&` (reference) avoids copying the elements in memory, which is crucial for performance when dealing with large objects.

## 3. `while` and `do-while` Loops

| Loop Type | Behavior | Syntax Example |
| :--- | :--- | :--- |
| **`while`** | Tests the condition at the **top**. The loop body might never run if the condition is initially false. | `while (count > 0) { count--; }` |
| **`do-while`**| Tests the condition at the **bottom**. Guarantees the loop body will execute **at least once**. | `do { count--; } while (count > 0);` |

* **Infinite Loop Example:** `while (true) { ... }`

## Algorithms on Arrays: `std::fill`
Instead of writing manual loops to initialize data, Modern C++ provides standard algorithms.
* **Header:** `#include <algorithm>`
* **Purpose:** Populates all elements in a range with a specific, identical value.

```cpp
#include <algorithm>
#include <array>

int main() {
    std::array<int, 3> myArray;
    // Fills the entire array with the value 1024
    std::fill(std::begin(myArray), std::end(myArray), 1024);
    return 0;
}
```

---

# Control Flow Modifiers: `break` and `continue`

These keywords are used to alter the normal control flow inside any loop (`for`, `while`, `do-while`).

## The `continue` Keyword
* **Behavior:** Immediately stops executing the current iteration's code block. 
* **Result:** It jumps directly back to the top of the loop to test the condition again (in a `for` loop, it executes the increment statement first, then tests the condition).

```cpp
for (int i = 0; i < 10; i++) {
    continue; // Skips everything below this line for the current iteration
    std::cout << "This will never print\n";
}
```

## The `break` Keyword
* **Behavior:** Completely terminates the loop.
* **Result:** Execution jumps out of the curly braces and resumes at the first line of code immediately following the loop.

```cpp
for (int i = 0; i < 10; i++) {
    std::cout << "Start of loop\n";
    break; // Loop dies here immediately
}
// Code resumes here after the very first iteration
```

# Functions in C++

## What is a Function?
A function is a self-contained block of code designed to perform a specific task. It allows you to reuse code, break complex problems down into smaller chunks, and map specific inputs to specific outputs.

## Anatomy of a Function
1. **Return Type:** Specifies what type of data the function will send back (e.g., `int`, `float`, `void`). If it does not return anything, the type is `void`.
2. **Function Name:** The identifier used to call the function.
3. **Parameters:** Variables declared in the function declaration that accept data (inputs) from the caller. 
4. **Function Body:** The code inside the curly braces `{}` that executes when the function is called.

### Arguments vs. Parameters
* **Parameters:** The variables defined in the function signature (e.g., `int a, int b`).
* **Arguments:** The actual values passed into the function when it is called (e.g., `add(1, 2)`).

```cpp
// Return Type | Name | Parameters
int             add   (int a, int b) {
    return a + b; // Function Body
}
```

## Function Declaration vs. Definition
Because C++ compiles code sequentially from top to bottom, the compiler must know about a function before you try to call it in `main()`.

* **Function Definition:** The full implementation of the function (signature + body).
* **Function Declaration (Forward Declaration):** A promise to the compiler that the function exists and will be defined later. It consists *only* of the function signature followed by a semicolon.

```cpp
#include <iostream>

// Forward Declaration (Compiler now knows 'add' exists)
int add(int a, int b); 

int main() {
    std::cout << add(5, 10) << '\n'; // Valid call
    return 0;
}

// Function Definition
int add(int a, int b) {
    return a + b;
}
```

## Function Overloading
C++ allows you to have multiple functions with the **exact same name**, as long as their **parameters differ** (different types or a different number of parameters). The compiler determines which one to call based on the arguments provided.

```cpp
int add(int a, int b) { return a + b; }
float add(float a, float b) { return a + b; }

// add(5, 5) calls the int version
// add(5.0f, 5.0f) calls the float version
```
* **Ambiguity Error:** If you try to call `add(5, 5.0f)` (one `int`, one `float`), the compiler will throw an ambiguous overload error. You must explicitly cast the arguments so they match one of the signatures exactly.

## Trailing Return Type (Modern C++ Syntax)
Modern C++ provides an alternative, functional-style syntax using the `auto` keyword and a trailing return type `->`.
```cpp
// Standard syntax
float add(float a, float b) { ... }

// Modern syntax (Trailing return type)
auto add(float a, float b) -> float { ... }
```

---

# Recursion and the Call Stack

## Recursion
A recursive function is a function that calls itself. Every recursive function must have two parts:
1. **Base Case:** The condition under which the function stops calling itself and returns.
2. **Recursive Case:** The part where the function calls itself with a slightly modified (smaller) problem space.

```cpp
void countdown(int n) {
    if (n == 0) { // Base Case
        std::cout << "Blast off!\n";
        return;
    }
    std::cout << n << '\n';
    countdown(n - 1); // Recursive Case
}
```

## The Call Stack and Stack Overflow
When a function is called, a **stack frame** is created in the working memory (the Call Stack). This frame stores:
* The local variables (like `n`).
* The return address (where to go when the function finishes).

If you call a recursive function too many times (e.g., `countdown(5000000)`), the program will run out of stack memory. This causes a **Stack Overflow**, resulting in a **Segmentation Fault** (program crash).

---

# Memory and The Address-Of Operator (`&`)

Every variable and function in a C++ program lives at a specific physical location in the computer's memory (RAM). 

## The Address-Of Operator (`&`)
Placing an ampersand (`&`) directly in front of a variable returns its **memory address** (typically displayed as a hexadecimal number).

```cpp
#include <iostream>

int main() {
    int x = 42;
    // Prints the memory address of x (e.g., 0x7ffd5e2a1b4)
    std::cout << &x << '\n'; 
    return 0;
}
```

## Important Caveats with Printing Addresses
* **Contiguous Variables:** If you print the addresses of variables declared one after another, you will often see their addresses offset by their data size (e.g., two `int` variables might be offset by 4 bytes).
* **Characters (`char`):** If you try to print `&c` where `c` is a `char`, `std::cout` assumes it is a C-style string and will print text instead of the memory address. To force it to print the address, you must cast it to a raw pointer (`void*`).
  ```cpp
  char letter = 'A';
  std::cout << (void*)&letter << '\n'; // Safely prints the memory address
  ```
* **Functions:** Functions also have memory addresses. You can find where a function begins in memory by using `(void*)&functionName`.

---

# Pass by Value Semantics

By default, C++ passes arguments to functions **by value**.

## What is Pass by Value?
When you pass a variable into a function, C++ **makes a complete, independent copy** of that variable and places it inside the new function's stack frame. 

Because it is a copy:
1. The new function can modify the argument internally.
2. **The original variable in the calling function (`main`) remains completely unchanged.**

### Proof of Pass by Value (Using Addresses)
You can prove that a function receives a copy by printing the memory addresses. The original variable in `main` and the parameter inside the function will have completely different memory addresses.

```cpp
#include <iostream>

void setValue(int arg) {
    std::cout << "Address of arg inside function: " << &arg << '\n';
    arg = 9999; // Modifies the COPY
}

int main() {
    int x = 42;
    std::cout << "Address of x inside main: " << &x << '\n';
    
    setValue(x); 
    
    // x is still 42, because setValue only changed its own copy
    std::cout << "Value of x is still: " << x << '\n'; 
    return 0;
}
```

## The Cost of Copies
Pass by value is great for primitives (like `int`, `float`) because copying a few bytes is fast and ensures the original data is safe from accidental modification. 

**However:** If you pass a massive data structure (e.g., a vector with millions of elements or a large custom object) by value, C++ will copy the *entire* data structure, which consumes significant memory and CPU time. Modern C++ provides tools (like pointers and references, to be covered later) to avoid these expensive copies.


# References in C++

## What is a Reference?
A reference is an **alias** (another name) for an already existing variable in memory. Once a reference is initialized to a variable, using the reference is exactly identical to using the original variable.

## Syntax and Initialization
You create a reference by appending an ampersand (`&`) to the data type.

```cpp
#include <iostream>

int main() {
    int x = 42;
    int& ref = x; // 'ref' is now an alias for 'x'
    
    ref = 43; // Modifies 'x' directly
    
    std::cout << x << '\n'; // Outputs 43
    return 0;
}
```

### Key Rules of References
1. **Must be initialized upon creation:** You cannot create an empty reference. `int& ref;` will cause a compiler error. It must immediately alias something (e.g., `int& ref = x;`).
2. **Cannot be null:** A reference is guaranteed to point to valid data. (While it is technically possible to trick the compiler into binding a reference to a null pointer, doing so is **strictly illegal** and results in Undefined Behavior).
3. **Cannot be reseated:** Once `ref` is initialized to `x`, it can never be changed to alias `y`.
4. **Same Memory Address:** `&ref` will output the exact same memory address as `&x`.

*(Note: In Modern C++, you can inspect the exact underlying type of a variable using `#include <typeinfo>` and `typeid(var).name()`).*

---

# Pass by Reference vs. Pass by Value

## The Problem with Pass by Value
When passing a large data structure (like a `std::vector` with a billion elements) by value, C++ makes a complete copy of the data. This requires significant time (e.g., several seconds for a massive array) and doubles the memory usage. Furthermore, any modifications made inside the function are lost when the function returns.

## The Solution: Pass by Reference
By modifying the function parameter to be a reference type (e.g., `std::vector<int>&`), C++ passes the *alias* of the original variable rather than copying it.

### Benefits:
1. **Efficiency:** Passing by reference is nearly instantaneous, regardless of how large the data structure is, because no data is copied.
2. **Mutation:** Because the function operates on an alias of the original data, any changes made inside the function directly affect the original variable in the calling scope.

```cpp
#include <iostream>
#include <vector>

// Pass by Reference (Notice the '&')
void modifyVector(std::vector<int>& vec) {
    vec.at(0) = 999; // Modifies the original vector in main
}

int main() {
    std::vector<int> myData(1000, 1); // 1000 elements, all initialized to 1
    modifyVector(myData);
    
    std::cout << myData.at(0) << '\n'; // Outputs 999
    return 0;
}
```

---

# `const` References (Safe and Efficient)

## The Use Case
What if you want the **efficiency** of Pass by Reference (avoiding expensive copies) but you want the **safety** of Pass by Value (preventing the function from accidentally modifying your original data)?

## The Solution: `const` Reference
By passing parameters as a `const` reference (e.g., `const std::vector<int>& vec`), you achieve both.
* The `&` avoids the copy.
* The `const` makes the data read-only inside the function.

```cpp
#include <iostream>
#include <vector>

// Safe AND Efficient
void printVector(const std::vector<int>& vec) {
    // vec.at(0) = 5; // COMPILE ERROR: read-only reference
    std::cout << vec.at(0) << '\n';
}
```

*(Note: Modern C++ offers `<type_traits>` and `std::is_const_v<decltype(x)>` to programmatically verify at compile-time if a variable `x` is explicitly marked as `const`).*

---

# Introduction to Pointers

## What is a Pointer?
A pointer is a distinct data type whose sole purpose is to **store a memory address**. 
* While a reference acts as a permanent, hidden alias to a variable, a pointer is an actual variable itself that explicitly holds the hexadecimal memory address of another variable.

## Syntax and Initialization
To declare a pointer, you place an asterisk (`*`) between the data type and the variable name.
* **Prefix Convention:** It is a common convention to prefix pointer variables with a `p` (e.g., `px` or `p_x`).

```cpp
#include <iostream>

int main() {
    int x = 7;
    
    // Pointer declaration
    int* p_x = &x; // p_x stores the memory address of x
    
    std::cout << &x << '\n';  // Outputs address (e.g., 0x1000)
    std::cout << p_x << '\n'; // Outputs exact same address (0x1000)
    return 0;
}
```

## Dereferencing a Pointer
If you print the pointer `p_x`, you just get a memory address. To retrieve or modify the actual data living at that memory address, you must **dereference** the pointer using the asterisk (`*`) operator.

* Think of the `*` operator as saying: "Follow the arrow to the address, and give me the actual value stored there."

```cpp
#include <iostream>

int main() {
    int x = 7;
    int* p_x = &x;
    
    // Dereferencing to read the value
    std::cout << *p_x << '\n'; // Outputs 7
    
    // Dereferencing to write a new value
    *p_x = 9; 
    
    std::cout << x << '\n';    // Outputs 9
    return 0;
}
```

## Why Use Pointers?
If we have references, why do we need pointers?
1. **Sharing Data:** Multiple pointers can point to the exact same piece of data. If the underlying data changes, all pointers reflect that change when dereferenced.
2. **Reassignment:** Unlike references, pointers can be reassigned to point to different variables during their lifetime.
3. **Nullability:** Pointers can point to "nothing" (`nullptr`), whereas references must always bind to valid data.
4. **Dynamic Data Structures:** Pointers are strictly required for building linked lists, trees, and graphs, where nodes must point to one another dynamically.
5. **Object Lifetime / Memory Management:** Pointers are used to manage data that lives on the heap (dynamically allocated memory), controlling exactly when data is created and destroyed.


# Pointer Arithmetic and Memory Visualization

## Understanding Memory Layout
When you create a pointer and point it to a variable, the pointer stores the explicit memory address (usually represented in hexadecimal, like `0x1000`).

To mentally visualize pointers and memory:
1. Draw a box for the variable (e.g., `x`). Inside the box, put its value (e.g., `7`). Above the box, put its memory address (e.g., `0x1000`).
2. Draw a separate box for the pointer (e.g., `p_x`). Inside the box, write the memory address it is storing (`0x1000`). Draw an arrow from the pointer box pointing to the variable box.
3. When you **dereference** (`*p_x`), follow the arrow from the pointer to the box it points to, and retrieve or modify the value inside.

---

# Dynamic Memory Allocation: The Heap

## Stack vs. Heap Memory
1. **Stack Memory (Local Scope):** Variables declared normally (e.g., `int x = 5;`) are allocated on the Stack. Stack memory is fast, but it is strictly limited by block scope `{}`. When the block ends, the memory is automatically reclaimed (destroyed). Furthermore, the size of stack allocations (like raw arrays) must be fixed at compile time.
2. **Heap Memory (Dynamic Allocation):** The Heap is a vast pool of memory (your system's RAM). You can request memory from the Heap while the program is actually running (**runtime**). This memory stays alive indefinitely until you explicitly tell the program to release it.

## The `new` Operator
The `new` operator allocates memory on the Heap and returns a **pointer** to the starting address of that memory block.

```cpp
// Allocates a single integer on the heap. 'p' stores its address.
int* p = new int; 

// Allocates an array of 100 integers on the heap. 'arr' stores the starting address.
int* arr = new int[100]; 
```

### Dynamic Sizing at Runtime
Because `new` runs at runtime, you can use variables to determine how much memory you need based on user input or dynamic conditions.

```cpp
int numStudents = 1000;
// Perfectly valid. The array size is determined at runtime.
int* studentIds = new int[numStudents]; 
```

## The `delete` Operator
With great power comes great responsibility. C++ does not have a garbage collector. Every time you use `new`, you **must** pair it with a corresponding `delete` when you are done using the memory. If you fail to do this, the memory remains occupied forever, causing a **Memory Leak**.

```cpp
int* p = new int;
delete p; // Frees the single integer

int* arr = new int[100];
delete[] arr; // CRITICAL: Use brackets [] to delete an entire array
```
*(Note: Tools like **Valgrind** on Linux can be used to analyze your compiled program and detect memory leaks).*

---

# Arrays and Pointer Arithmetic

## The Truth About Arrays
A raw array is simply a contiguous block of memory. The name of a raw array (e.g., `array`) actually decays into a pointer pointing to the memory address of its very first element (`array[0]`).

## Pointer Arithmetic
You can add integers to a pointer to move it forward in memory. 
* **Crucial Rule:** When you increment a pointer (e.g., `p + 1`), the compiler does not literally add 1 to the memory address. It adds the **size of the underlying data type**.
* For example, if `p` points to an `int` (which is 4 bytes) at address `0x1000`, `p + 1` will result in address `0x1004`.

```cpp
#include <iostream>

int main() {
    int arr[3] = {10, 20, 30};
    int* p = arr; // p points to the start of the array
    
    std::cout << *p << '\n';       // Outputs 10 (offset 0)
    std::cout << *(p + 1) << '\n'; // Outputs 20 (offset 1, moved 4 bytes)
    std::cout << *(p + 2) << '\n'; // Outputs 30 (offset 2, moved 8 bytes)
    return 0;
}
```

## The Secret Behind Array Brackets `[]`
The bracket syntax `array[index]` is actually just syntactic sugar (shorthand) for pointer arithmetic and dereferencing!

`array[2]` is exactly identical to writing `*(array + 2)`.

---

# Warning: The `sizeof` Operator Pitfalls

The `sizeof` operator returns the size of a data type in bytes, as determined by the compiler at compile time. It is easily misunderstood when dealing with pointers, arrays, and standard data structures.

## 1. Primitives and Pointers
* `sizeof(int)`: Typically returns `4` bytes.
* `sizeof(int*)`: Returns the size of a memory address. On a 64-bit system, this is **always `8` bytes**, regardless of what data the pointer points to.

## 2. Stack-Allocated Arrays
If an array is allocated on the stack with a fixed, compile-time size, `sizeof` will return the total byte size of the entire array.
```cpp
int stackArr[5];
// Returns 20 (5 elements * 4 bytes). You CAN use this to find the array length.
std::cout << sizeof(stackArr) << '\n'; 
```

## 3. Dynamically Allocated Arrays (Heap)
If an array is allocated on the heap using `new`, the variable holding it is just a pointer.
```cpp
int* heapArr = new int[1000];
// DANGER! This returns 8 (the size of the pointer), NOT 4000. 
// You CANNOT use sizeof to find the length of a dynamic array.
std::cout << sizeof(heapArr) << '\n'; 
```

## 4. Standard Library Containers (e.g., `std::vector`)
If you use `sizeof(std::vector<int>)`, it returns the size of the vector's internal control structure (typically 24 bytes), **not** the size of the elements inside it. 
* Even if you push a million integers into the vector, `sizeof(vector)` remains 24.
* To get the number of elements in a vector, always use the member function: `vector.size()`.

---

# `const` Pointers and `const` Data (Teaser)
Just as we learned how to pass by `const` reference for safety, we can use `const` with pointers.
* This can ensure that the data a pointer points to becomes read-only and cannot be manipulated by dereferencing it. (Specific syntax and behavior to be covered in future lessons).


# Arrays and Functions in C++

## Array Decay to Pointers
When you pass a raw C-style array (e.g., `int arr[5]`) into a function, it does **not** get passed as a complete array object. Instead, the array **decays into a pointer** to its first element.

```cpp
// This parameter 'int arr[]' actually becomes 'int* arr'
void printArray(int arr[]) {
    // std::cout << sizeof(arr); // WARNING: Prints 8 (size of pointer), NOT the array size!
}

int main() {
    int myArray[5] = {1, 3, 5, 7, 9};
    printArray(myArray); 
}
```

### The Missing Size Problem
Because the array decays into a pointer, the function loses all information about the array's original length. You cannot use `sizeof(arr)` inside the function to determine the length. 

### Solutions
1. **Pass the Size Explicitly:** In C and older C++, the standard practice is to pass a second argument representing the size (usually using the `size_t` data type).
   ```cpp
   void printArray(int arr[], size_t size) {
       for (size_t i = 0; i < size; i++) {
           std::cout << arr[i] << '\n';
       }
   }
   ```
2. **Use `std::array`:** If the size is fixed and known at compile time, use `std::array<int, 5>`.
3. **Use `std::vector` (Recommended):** The Modern C++ best practice is to use `std::vector`, which inherently tracks its own size (`vec.size()`) and can be passed by reference efficiently.
   ```cpp
   void printVector(const std::vector<int>& vec) {
       for (size_t i = 0; i < vec.size(); i++) {
           std::cout << vec.at(i) << '\n';
       }
   }
   ```

---

# Pointer Pitfalls

Because you manually manage memory in C++, you must watch out for these four common pointer errors.

## 1. Null Pointer Dereference
A pointer that does not point to anything valid should be initialized to `nullptr` (introduced in C++11 to replace the older `NULL` macro). 
* **The Error:** Attempting to dereference (`*p`) a `nullptr` results in an immediate **Segmentation Fault** (crash).

## 2. Memory Leaks
* **The Error:** When you allocate memory using `new` on the heap but forget to call `delete` before the pointer goes out of scope or is reassigned.
* **The Impact:** The memory remains permanently occupied. If this happens in a loop or a long-running program (like a server), the system will eventually run out of RAM and crash.
* **Detection:** Tools like **Valgrind** or compiler sanitizers (`-fsanitize=address` using `g++` or `clang++`) can detect memory leaks.

## 3. Dangling Pointers
* **The Error:** Returning a pointer to a local variable (stack memory) from a function.
* **The Impact:** When the function finishes, its stack frame is destroyed. The returned pointer now points to invalid, reclaimed memory. Dereferencing it later will cause a crash or garbage data.

## 4. Double Free
* **The Error:** Calling `delete` twice on the exact same memory address (e.g., if two different pointers point to the same heap memory and both try to delete it).
* **The Impact:** Corrupts the memory manager, leading to a crash or undefined behavior.

---

# Function Pointers

## What is a Function Pointer?
Functions, just like variables, live at specific memory addresses. A **Function Pointer** is a pointer that points to the execution address of a function rather than data. 

### Why use them?
They allow you to choose which function to execute at **runtime** (e.g., dynamic callbacks, UI button click events, state machines).

## Syntax and Usage
The syntax for raw function pointers is notoriously tricky.

```cpp
int add(int x, int y) { return x + y; }
int multiply(int x, int y) { return x * y; }

int main() {
    // 1. Declare the function pointer
    // ReturnType (*PointerName)(Param1Type, Param2Type);
    int (*op)(int, int); 
    
    // 2. Point it to a function
    op = add; 
    std::cout << op(2, 2) << '\n'; // Calls add(2, 2) -> 4
    
    // 3. Change it at runtime
    op = multiply;
    std::cout << op(2, 2) << '\n'; // Calls multiply(2, 2) -> 4
}
```

## Modern C++ Alternatives
To avoid the confusing raw pointer syntax, C++ provides two cleaner alternatives:

### 1. `typedef` (or `using`)
You can alias the complex pointer syntax to a readable type name.
```cpp
// PFN stands for Pointer to FunctioN
typedef int (*PFN_IntegerOperation)(int, int); 

PFN_IntegerOperation op = add;
```

### 2. `std::function` (Modern C++)
Found in the `<functional>` header, this is the modern, preferred way to handle callable objects in C++.
```cpp
#include <functional>

// std::function<ReturnType(ParamTypes...)>
std::function<int(int, int)> op = add;
```

---

# Value Categories: lvalues and rvalues

Understanding lvalues and rvalues helps decode cryptic C++ compiler errors (e.g., *"lvalue required as left operand of assignment"*).

## 1. lvalue (Locator Value)
* **Definition:** An expression that points to a specific, identifiable memory location. You can safely take its memory address using `&`.
* **Example:** Variables (`x`, `y`, `myArray[0]`).
* **Rule:** lvalues can safely exist on the left or right side of an assignment (`x = 10;` or `y = x;`).

## 2. rvalue
* **Definition:** A temporary value that does not have a persistent memory address. You cannot use `&` on it.
* **Example:** Literals (`10`, `"hello"`), or the results of expressions (`a + b`).
* **Rule:** rvalues can **only** exist on the right side of an assignment. You cannot assign data to them (`10 = x;` is illegal).

## 3. lvalue References (`&`)
This is the standard reference we learned previously (`int& ref = x;`). 
* **Rule:** An lvalue reference can **only bind to an lvalue**. It cannot bind to an rvalue.
  * `int& ref = 10;` // COMPILE ERROR: Cannot bind lvalue ref to rvalue.
* **Exception:** A `const` lvalue reference **can** bind to an rvalue (`const int& ref = 10;` is valid because the compiler secretly creates temporary storage for it).

## 4. rvalue References (`&&`) (Modern C++ Teaser)
Introduced in C++11, an rvalue reference uses double ampersands (`&&`).
* **Rule:** It binds specifically to temporary rvalues. 
  * `int&& r_ref = 10;` // PERFECTLY VALID

### Why do we care about `&&`? (Move Semantics)
rvalue references are the foundation of **Move Semantics**. 
If you concatenate two massive strings (`s3 = s1 + s2;`), `s1 + s2` generates a temporary rvalue. In older C++, that temporary result had to be completely copied byte-by-byte into `s3`, and then the temporary was destroyed. 
With rvalue references, C++ knows the temporary is about to be destroyed anyway, so it simply **"moves"** (steals) the memory pointers from the temporary directly into `s3`, completely eliminating the expensive copy process.
## Nested Loop Caveat
When using `continue` or `break` inside nested loops (loops inside loops), **they only affect the innermost loop** in which they are placed. They will not break or continue the outer loops.
### Best Practice for Modern C++
Even if the compiler defaults to a specific version, it is best practice to explicitly specify the standard version you want to use (e.g., C++11, C++17, C++20) when compiling, ensuring you have access to the specific modern features you intend to use.
