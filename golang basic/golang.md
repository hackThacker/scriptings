# Getting Started with Go security learners

## What is Go?

**Go**, sometimes known as **Golang**, is a statically typed, compiled programming language developed by Google. Go is noted for its simplicity, efficiency, and performance, making it ideal for constructing high-performance and scalable applications. It was designed to remedy flaws in existing languages, such as C/C++, and to make systems development easier and more efficient. Go is known for its simplicity, readability, and speed, making it a popular choice for developing scalable, high-performance software. Some major elements of Go are:

## Topics Covered:

- [first program](#hello-world-example)
    1. [Execute & Build ](#execute-and-build)
- [variables](#variables-in-go)
- [Function](#functions-in-go)
- [Array](#arrays-and-slices-in-go)
- [Condtions](#conditionals-in-go)
- [Loop](#for-loop-in-go)
- [Pointer](#pointers-in-go)
- [Map & Struct](#map--struct-in-go)
- [Go in Cybersecurity and Pen Testing](#why-do-cybersecurity-professionals-and-penetration-testers-use-go)

Some major elements of Go are:
- **Simplicity**: The syntax is simple and straightforward, making it easier for developers to read and create code.
- **Concurrency**: Go has built-in support for concurrent programming via goroutines and channels, allowing developers to construct concurrent code without dealing with difficult synchronization issues.
- **Memory management**: Go supports automatic garbage collection, allowing developers to manage memory without the need for manual memory allocation and deallocation.
- **Cross-platform**: Go can compile code into executables for several operating systems, such as Linux, Windows, and macOS.
- **Performance**: As a compiled language, Go provides performance comparable to C/C++ while keeping the ease of use and productivity found in higher-level languages.
Go`s popularity stems from its **fast execution speed**, **simplicity**, and **excellent support for concurrency**, making it an excellent solution for a wide range of applications, including **network services, cloud computing, and security tools**.

---




## Hello World Example

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello World!")
}
```

## Explanation:
- **package main**: This line specifies which package this application belongs to. Every Go program must have a`main` package if it is to be executed.
- **import "fmt"**: This imports the **fmt** (format) package, which includes functions for formatted I/O operations (such as printing).
- **func main()**: This defines the main function, which is the starting point of a Go program. This function is called whenever the program is run.
- **fmt.Println("Hello World!")**: This function outputs "Hello World!" to the console.

The **main** function is essential in Go as it serves as the program`s starting point.

## Execute and Build

Go offers easy commands for running and building your programs.


### Running the Code:
To run the Go code directly in development mode (without creating a build), use:

```bash
go run app.go
```

This command compiles the code and executes it in one step. It`s useful for quick testing.

### Building the Executable:
To **compile** the Go code into an executable file, use:

```bash
go build app.go
```

This will generate an executable file named `app` (or `app.exe` on Windows) in the same directory as the Go file.

### Running the Executable:
To run the compiled program, use:

```bash
./app   # On Unix-based systems (Linux, macOS)
app.exe # On Windows
```

This executes the compiled file, which does not require Go to be installed on the machine. The compiled binary is platform-specific, meaning it will differ depending on the operating system:

- **Linux/macOS**: `app` (no extension).
- **Windows**: `app.exe` (executable file).

This allows you to distribute Go programs as standalone executables.

## Summary of Commands:
- `go run app.go` — Runs the Go code directly, without creating a binary.
- `go build app.go` — Compiles the Go code into an executable.
- `./app or app.exe`: Runs the compiled executable file. 

Following these instructions will allow you to easily write, run, and compile Go code.


---


# Variables in Go

## Key Properties of Variables in Go

- **No Undefined or Null Values**: When defining variables in Go, no undefined or `null` values are permitted.
- **Type Declaration**: In some circumstances, Go permits variables to be declared without explicitly defining their data type.
- **several Variables Declaration**: You can define several variables simultaneously.
**Two Methods to Declare Variables**:
  - **Long Form**: Declare using the data type supplied.
  - **Short Form**: Use type inference, which allows Go to automatically detect the type.
- **`var` and `const`**: - `var` declares regular variables.
  - To declare constants, use the keyword `const`. Constants cannot be altered once assigned, and each constant must have an initial value.


## Declaring Variables

### Providing the Value Later

```go
var name string
name = "Max"
```

### Providing the Value First

```go
var name string = "Max"
```

### Using Type Inference

```go
name := "Max"
```

### Declaring Multiple Variables at Once

```go
var width, height float32 = 2.5, 6.1
```

Or, using type inference:

```go
width, height := 2.5, 6.1
```

### Example Output:

```go
fmt.Println(width)   // 2.5
fmt.Println(height)  // 6.1
```

## Default Values for Variables

When you declare a variable without an explicit value, Go assigns default values based on the type:

```go
var firstVar bool
fmt.Println(firstVar) // false

var firstVar string
fmt.Println(firstVar) // ""

var firstVar float64
fmt.Println(firstVar) // 0

var firstVar int
fmt.Println(firstVar) // 0
```
---
# Functions in Go

In Go`s **functions** are a key building element that allows you to arrange related code together, making your applications more modular, legible, and reusable. A Go function consists of the following parts:

- **Function Declaration**: This defines the function`s name, parameters, and return type.
- **Function Body**: Contains the code that runs when the function is invoked.
- **Return Statement**: The function can return values to the caller. The return type is specified at the function declaration.

## Function and Return

In Go, the function signature contains both the parameters and the return type. Here is a simple example in which we define a function that adds two integers:


```go
package main

import "fmt"

// Function declaration
func add(x int, y int) int {
    return x + y  // Returning the sum of x and y
}

func main() {
    fmt.Println(add(5, 5))  // 10
}
```

### Explanation:

- **Function Declaration**: `func add(x int, y int) int` creates the `add` function, which accepts two `int` parameters and returns a `int`.
- **return type**: The `int` after the parameter list specifies the kind of value that the function will return. In this situation, the method returns `x` + `y`.
- **Call the Function**: Within`main()`, we invoke the `add` function with the inputs `5` and `5`. The outcome is printed as `10`.

### Shortening the data types

If both parameters of a function have the same data type, Go allows you to use the following shortcut to avoid repeating the type for each parameter:


```go
package main

import "fmt"

// Shortened function declaration
func add(x, y int) int {
    return x + y
}

func main() {
    fmt.Println(add(5, 5))  // 10
}
```

### Explanation:

- **Shortcut**: Instead of writing `x int, y int`, we can simply write `x, y int`. This is possible because both `x` and `y` have the same data type (`int`).
- The function still works the same way and returns the sum of `x` and `y`.

---

### Multiple Returns

Go functions can return multiple values. This functionality is frequently used to deliver numerous outcomes or values, together with errors, which is a common Go programming pattern.

Here`s an example of a function returning two values:


```go
package main

import "fmt"

// Function with multiple return values
func person(name string, age int) (string, int) {
    return name, age + 1  // Returning both name and age incremented by 1
}

func main() {
    name, age := person("Max", 22)  // Receiving both values
    fmt.Println(name, age)  // max 23
}
```

### Explanation:
- **Multiple Return Values**: The `person` function accepts two parameters: a`string` for `name` and a `int` for `age`. It returns two values:`string` and `int`.
- **Return statement**: The`return` statement returns both `name` and `age + 1` to the caller.
- Unpacking Return Values: In`main()`, we capture the returned values with `name, age:= person("Max", 22)`. Go lets you unpack multiple return values into distinct variables.
- The outcome is`max 23` since `age` was increased by one within the function.

## Summary:

1. **Function Declaration**: Functions are defined with the `func` keyword, followed by the name, parameters (with data types), and return type.
2. **Shortened Parameter Syntax**: If many parameters share the same data type, you can abbreviate the declaration by  listing the types once.
3. **Multiple Return Values**: Go functions can return more than one value, making it easy to handle multiple results or error handling in a single function call.

---

# Arrays and Slices in Go

In Go, **arrays** and **slices** are two important data structures that allow you to work with collections of elements. While arrays are fixed in size, slices provide more flexibility and are commonly used when the size of the collection can change dynamically.

## Arrays in Go

### Basic Array
In Go, a **array** is a collection of elements with the same data type and a fixed size. Once the size is set, it cannot be modified. All array entries are set to the default zero value of their respective types (e.g., `0` for `int`, `""` for`string`, and so on).

Here is an example of creating and printing an array:


```go
package main

import "fmt"

func main() {
    var ages [5]int
    fmt.Println(ages)  // Output: [0 0 0 0 0]
}
```

### Explanation:
- `var ages [5]int`: This declares an array of integers with a fixed size of `5`. The array is automatically initialized to the zero value (`0`) for each element.
- `fmt.Println(ages)`: This prints the array, showing the default values `[0 0 0 0 0]`.

### Adding Values to the Array
You can assign values to specific elements of an array by referencing their index:

```go
package main

import "fmt"

func main() {
    var ages [5]int
    ages[0] = 21
    ages[1] = 23
    fmt.Println(ages)  // Output: [21 23 0 0 0]
}
```

### Explanation:
- `ages[0] = 21`: Sets the value of the first element (index 0) to `21`.
- `ages[1] = 23`: Sets the value of the second element (index 1) to `23`.
- `fmt.Println(ages)`: Prints the updated array: `[21 23 0 0 0]`.

### Better Way to Initialize Arrays
You can initialize an array with values directly using the following syntax:

```go
package main

import "fmt"

func main() {
    ages := [5]int{23, 21, 19, 23, 24}
    fmt.Println(ages)  // Output: [23 21 19 23 24]
}
```

### Explanation:
- `ages := [5]int{23, 21, 19, 23, 24}`: This initializes the array with specific values, bypassing the need to assign them individually.
- `fmt.Println(ages)`: Prints the array with the values `[23 21 19 23 24]`.

## Slices in Go
A **slice** is a more adaptable and effective data structure than an array. Slices, unlike arrays, have a variable size, allowing them to grow and decrease dynamically. Slices are built on top of arrays and enable additional functionality, such as adding elements.


### Declaring and Initializing a Slice
Here`s how you can declare and initialize a slice:

```go
package main

import "fmt"

func main() {
    ages := []int{23, 21, 19, 23, 24}
    fmt.Println(ages)  // Output: [23 21 19 23 24]
}
```

### Explanation:
- `ages := []int{23, 21, 19, 23, 24}`: This creates a slice with the given values. Unlike arrays, the size of the slice is inferred based on the number of elements.

### Appending to a Slice
You can append elements to a slice using the `append()` function. This does not modify the original slice but instead returns a new slice with the additional elements.

```go
package main

import "fmt"

func main() {
    ages := []int{23, 21, 19, 23, 24}
    ages = append(ages, 27)  // Append 27 to the slice
    fmt.Println(ages)  // Output: [23 21 19 23 24 27]
}
```

### Explanation:
- `ages = append(ages, 27)`: The `append()` function adds the value `27` to the end of the `ages` slice. Note that `append()` does not modify the original slice but returns a new slice with the added value.
- `fmt.Println(ages)`: Prints the updated slice: `[23 21 19 23 24 27]`.

## Slices vs Arrays 
- **Arrays** have a fixed size and cannot be added or removed once defined.
- **Slices** are dynamic, meaning they can expand and contract. When the slice is amended with `append()`, it may internally allocate a new array to fit the new elements, making slices far more adaptable than arrays.
Here`s a Markdown-formatted explanation of how to loop through an array in Go, using your provided example:

# Looping Through an Array in Go

In Go, you can loop through arrays using the `for` loop combined with the `range` keyword. This is useful when you want to access both the index and the value of elements in the array.

## Example

```go
ages := [3]int{23, 21, 19}

for index, value := range ages {
    fmt.Println(index, value)
    // Output:
    // 0 23
    // 1 21
    // 2 19
}
```

### Explanation:
- `ages := [3]int{23, 21, 19}`: This creates an array named `ages` with 3 integers: `23`, `21`, and `19`.
- `for index, value := range ages`: The `range` keyword returns two values on each iteration:
  - `index`: The index of the current element in the array.
  - `value`: The value of the current element.
- `fmt.Println(index, value)`: This prints the index and value of each element in the array.

### Output:
```
0 23
1 21
2 19
```

## Important Notes:
- The `range` keyword is commonly used for iterating over arrays, slices, and maps in Go.
- You can omit the `index` or `value` if you don`t need them. For example:
  
- If you only need the values, you can write:
    ```go
    for _, value := range ages {
        fmt.Println(value)
    }
    ```

- If you only need the indexes, you can write:
    ```go
    for index := range ages {
        fmt.Println(index)
    }
    ```

---
### Conditionals in Go

#### If-Else
```go
if 5 > 3 {
    fmt.Println("5 > 3")
} else {
    fmt.Println("3 > 5")
}
```

#### Else-if
```go
if 5 > 5 {
    fmt.Println("5 > 3")
} else if 5 >= 5 {
    fmt.Println("Greater / equal")
} else {
    fmt.Println("3 > 5")
}
```

#### Variables in If-Else
```go
if age := 9; age < 18 {
    fmt.Print("Not grown up")
}
```
---

### For Loop in Go

#### For-Loop
In Go, there is only the `for` loop available, but it can be used in various ways, including as a traditional for-loop or a while-like loop.

```go
func main() {
    for i := 0; i < 5; i++ {
        fmt.Println(i)
    }
}
```
- This is a standard `for` loop where `i` starts at 0 and increases by 1 until it is no longer less than 5.

#### While -Loop in Go
Go doesn`t have a specific `while` loop, but you can replicate it using a `for` loop without the increment section.

```go
for i := 0; i < 5; {
    fmt.Println(i)
    // Endless prints if condition is true
}
```
- This loop behaves like a `while` loop, continuously executing the block while the condition is true. Be careful, as this can lead to an infinite loop if not controlled properly.

---

### Pointers in Go

#### Using a Pointer
In Go, a pointer holds the memory address of a variable.

```go
func main() {
    var age = 24
    var agePointer = &age
    fmt.Println(agePointer)
    // Output: for example `0xc000016078` (memory address)
}
```
- The `&` symbol returns the memory address of the variable `age`. The pointer `agePointer` holds this memory address.

#### Getting the Value Behind the Pointer
To get the value stored at the memory address the pointer is holding, use the `*` symbol.

```go
var age = 24
var agePointer = &age
fmt.Println(*agePointer) // 24
```
- The `*` dereferences the pointer and gives the value stored at the memory address, in this case `24`.

#### Changing Values with Pointers
You can also modify the value stored at the memory address the pointer is holding.

```go
var age = 24
var agePointer = &age
*agePointer++ // Increment the value at the memory address
fmt.Println(*agePointer) // 25
```
- The `*` operator is used to modify the value stored at the pointer`s address, changing `age` from `24` to `25`.
---


### Map & Struct in Go

#### Basic Struct
A **struct** is a composite data type in Go that groups together variables (fields) under a single name.

```go
type person struct {
    name string
    age  int
}

func main() {
    personMax := person{name: "Max", age: 21}
    fmt.Println(personMax)      // Output: {Max 21}
    fmt.Println(personMax.name) // Output: Max
}
```
- **Struct Declaration**: The `person` struct has two fields: `name` (string) and `age` (int).
- **Struct Initialization**: You create an instance of the `person` struct and initialize its fields.

#### Basic Map
A **map** is an unordered collection of key-value pairs. In Go, you declare maps using the `make()` function.

```go
people := make(map[string]int)
people["Max"] = 23
people["Tom"] = 19

fmt.Println(people["Max"]) // Output: 23
```
- **Map Declaration**: `make(map[string]int)` creates a map where keys are of type `string` and values are of type `int`.
- **Assigning Values**: You can assign values to keys in the map.

#### Looping through a Map
You can iterate over a map using the `range` keyword.

```go
people := make(map[string]int)
people["Max"] = 23
people["Tom"] = 19

for key, value := range people {
    fmt.Println(key, value)
    // Output:
    // Max 23
    // Tom 19
}
```
- **Looping**: The `for key, value := range people` syntax loops through the map, where `key` is the map key and `value` is the map`s corresponding value.
---

# Why Do Cybersecurity Professionals and Penetration Testers Use Go?

Cybersecurity professionals and **penetration testers** frequently utilize Go for a variety of reasons, including the language`s characteristics and benefits, which make it especially beneficial for security-related tasks. The following are some of the reasons why Go is a preferred choice in cybersecurity and penetration testing.

### 1. **Fast Development and Execution** 
- **Efficiency**: Go`s concise syntax allows for speedier development cycles. Security professionals can quickly create tools and scripts, which is critical when working on tight deadlines or conducting active penetration tests.
- **Speed**: Go, as a compiled language, generates highly efficient binaries that outperform interpreted languages (such as Python or Ruby). This makes Go ideal for developing high-performance tools like **network scanners**, **exploitation tools**, and **exfiltration tools**.


### 2. **Cross-Platform Compatibility** 
- **Building Cross-Platform Tools**: Go`s ability to generate programs for many platforms (Windows, Linux, macOS) allows for the creation of tools that work across multiple environments without requiring code modifications.
- **Penetration Testing**: Tools built in Go can operate on a variety of operating systems used in penetration testing (e.g., Kali Linux, Windows), giving penetration testers more choice in their toolkits.

### 3. **Concurrency and Networking** 
- **Concurrency Support**: Go`s goroutines and channels enable simultaneous execution of several tasks, making it ideal for penetration testing.
  - **Brute-forcing passwords**: Go can handle many tries at once, resulting in faster procedures.
  - **Network scanning**: Penetration testers frequently need to scan numerous ports or execute other network-related operations simultaneously, which is simple to implement in Go using goroutines.

- **Networking Libraries**: Go offers a rich collection of libraries for creating and manipulating network protocols, making it perfect for developing tools for **network reconnaissance**, **exploitation**, or **data exfiltration**.


### 4. **Strong Standard Library** 
- **Security and Networking Tools** Go`s standard library is excellent, with packages for cryptography, networking, HTTP servers, and more. This allows penetration testers to easily create unique security tools. For example, Go includes support for **TLS** (Transport Layer Security) and **SSH** (Secure Shell), both of which are often used in security jobs.


### 5. **Compiled Binaries and Stealth** 
- **No Dependencies**: Go builds programs into standalone executable binaries that include all required dependencies. This allows you to easily deploy tools on machines without having to install Go or any other libraries. This is especially handy for penetration testers who need to execute tools on systems where the installation of external software is limited.
- **Minimum Footprint**: Go executables are often small, making them less apparent and easier to launch covertly during penetration tests.

### 6. **Security Research and Exploitation** 
- **Creating Custom Exploits**: Go is commonly used by security researchers to create bespoke exploits, **malware analysis tools**, and **fuzzing**. Its simplicity and capability enable rapid design and deployment of security vulnerabilities and exploits.

- **Memory Safety**: Go, while not as low-level as C or C++, provides improved memory safety with features such as garbage collection. This helps to avoid typical security problems such as buffer overflows and memory corruption.



### 7. **Community and Open-Source Tools**

Go has gained popularity in the **cybersecurity community**, and numerous well-known **penetration testing frameworks** and tools have been created in Go.

Here are some popular GoLang tools that **(hackthacker)** uses for security testing. 


  - **Nuclei**: A quick and adaptable vulnerability scanner that automates security audits with pre-defined templates.
  - **Subfinder**: A tool for detecting subdomains from passive sources, which aids in enumeration during a penetration test.
  - **Naabu**: A high-speed port scanner that scans vast swaths of IP addresses for open ports.
  - **Katana**: An advanced tool for automated penetration testing that includes modules for several attack vectors.
  - **Httpx**: A fast and versatile HTTP probing tool that detects live web servers and scans for HTTP-related faults.
  - **Dnsx**: A powerful DNS toolkit for DNS resolution and enumeration, which aids in domain discovery and security. assessments.
 - **CveMap**: A tool for tracking and visualizing CVEs (Common Vulnerabilities and Exposures) across several systems, which aids in vulnerability management.


These open-source Go tools are easily extended or changed by penetration testers to meet their individual requirements, making Go a versatile and important addition in their toolbox.


---