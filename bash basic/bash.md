# Welcome to the Introductory Bash Scripting learning!

Bash is an important programming language that runs in the terminal on most Linux versions and MacOS. It is extremely handy for automating a variety of operations and is a necessary ability for system administrators. In this room, you will be able to examine the following concepts:

## Topics Covered:
- [Bash scripting](#introduction-to-bash-scripting)
- [Basic of bash](#bash-scripting-techniques)
    1. [variables](#variables-in-bash)
    2. [Parameter Expansion](#parameter-expansion-in-bash)
    3. [loops](#loops-in-bash)
    4. [Function](#functions-in-bash)
    5. [Array](#arrays-in-bash)
    6. [Dictionary](#dictionaries-associative-arrays-in-bash)
    7. [Options](#bash-options-and-glob-options)
    8. [History](#history-expansion-in-bash)
    9. [Miscellaneous](#miscellaneous-bash-tips-and-techniques)

## Why Learn Bash?

Bash scripts enable you to combine numerous commands in a single file to complete more complex operations. They are especially handy for automating routine processes like backups, system monitoring, and so on. Bash scripting is an essential ability for system administrators, penetration testers, and developers alike.


## Recommended Resource
To help you on your Bash learning journey, here's a helpful site I discovered while learning: [Devhints - Bash](https://devhints.io/bash). This website provides quick references and is an excellent tool for continuing your education even after you have completed this learning.

Happy scripting! 🎉


# Introduction to Bash Scripting

When writing a Bash script, it's critical to provide the environment in which it will run. This is accomplished with the **shebang** ('#!/bin/bash'), which specifies the interpreter that will run the script. In this example, we are utilizing Bash.

### Structure of a Bash Script

A Bash script always starts with the following line of code at the top:

```bash
#!/bin/bash
```

This tells your terminal that the script should be executed with Bash, regardless of the shell you're using.

---

## Basic Examples

Let's start with a simple example. The `echo` command is used to print a string to the terminal, similar to Python's `print()` function. Here’s an example that prints "Hello World":

```bash
echo "Hello World"
```

Running this will output:

```
Hello World
```

### Running Linux Commands in a Script

You can also run standard Linux commands in your Bash script. For example, if you want to list the contents of a directory, you can use the `ls` command within your script:

```bash
ls
```

This will list all the files and directories in the current directory. You can try running this in your terminal as well!

---

## Running Your Bash Script

Before running your Bash script, you need to make sure that the script has executable permissions. You can do this using the `chmod` command:

```bash
chmod +x yourfile.sh
```

This command makes the script executable. After giving it executable permissions, you can run the script using:

```bash
./yourfile.sh
```

---

## Example: Who Am I?

Now let's create a script that uses the `whoami` and `id` commands to display information about the current user.

```bash
#!/bin/bash
whoami
id
```

This script will output the current user's name and their user ID information. When you run this script, it will return results similar to:

```
username
uid=1000(username) gid=1000(username) groups=1000(username),27(sudo)
```

---

### Note:
- **`#!/bin/bash`**: This is always the first line of your script to define that it should be run with Bash.
- **Permissions**: Use `chmod +x yourfile.sh` to make the script executable.
- **Execution**: Use `./yourfile.sh` to run your script.

---

#  Bash Scripting Techniques

#  Variables in Bash

In Bash, variables are essential for storing and manipulating data. Quoting variables correctly is crucial to avoid unexpected behaviors such as word splitting and globbing. This section highlights best practices for using variables, including examples with wildcards and command options.

## Declaring and Using Variables

Variables in Bash are assigned using the `=` operator and referenced with a dollar sign (`$`). It's best practice to quote variables to prevent issues such as word splitting.

### Example: Variable Assignment and Output

```bash
name="John"
echo $name        # Output: John
echo "$name"      # Output: John
echo "${name}!"   # Output: John!
```

In the examples above:
- `echo $name` outputs the value of the `name` variable.
- `echo "$name"` also outputs `John`, but quoting the variable ensures that if it contains spaces or special characters, they will be treated as a single value.
- `echo "${name}!"` demonstrates variable interpolation, appending `!` to the value of `name`.

## Quoting Variables

It is strongly recommended to quote variables unless you need to perform specific operations like wildcard expansion or use them as command fragments.

### Example: Using Wildcards in Variables

Wildcards (`*`, `?`, etc.) allow for pattern matching. When using a wildcard inside a variable, you can expand it to match files or directories in a command.

```bash
wildcard="*.txt"
options="iv"
cp -$options $wildcard /tmp
```

### Explanation:
- `$wildcard` holds the pattern `*.txt`, which matches all `.txt` files in the current directory.
- `$options` holds the string `iv`, which is passed as options to the `cp` command. The `-i` option makes the copy operation interactive (prompting before overwriting), and the `-v` option enables verbose output.
- The `cp` command copies all `.txt` files to the `/tmp` directory, applying the options.

## Best Practices
1. **Quoting variables:** Always quote your variables, especially when they contain spaces or special characters. For example, instead of `echo $name`, use `echo "$name"`.
2. **Wildcards and command fragments:** You may choose not to quote variables when you're intentionally expanding wildcards (e.g., `*.txt`) or when passing variables as command options.
3. **Minimize side effects:** Quoting variables ensures that spaces, newlines, and special characters are handled correctly, avoiding unexpected behavior when dealing with filenames or user input.


---
# Parameter Expansion in Bash

Parameter expansion in bash allows for advanced string manipulation, substitution, and handling of variables. Below are various use cases and examples of how to use parameter expansion effectively.

## Basics

Parameter expansion can be used to retrieve the value of variables or to modify them.

```bash
name="John"
echo "${name}"                # Output: John
echo "${name/J/j}"             # Output: john (substitution)
echo "${name:0:2}"             # Output: Jo (slicing)
echo "${name::2}"              # Output: Jo (slicing)
echo "${name::-1}"             # Output: Joh (slicing)
echo "${name:(-1)}"            # Output: n (slicing from the right)
echo "${name:(-2):1}"          # Output: h (slicing from the right)
```

### Default Values

You can provide default values for variables in case they are unset or null:

```bash
echo "${food:-Cake}"           # Output: $food or "Cake"
```

### Length and Substring Extraction

You can extract substrings from variables by specifying the starting index and length:

```bash
length=2
echo "${name:0:length}"       # Output: Jo
```

## String Manipulation

### Remove Suffix and Prefix

You can remove a suffix or prefix from a string using `${parameter#pattern}` and `${parameter%pattern}`.

```bash
str="/path/to/foo.cpp"
echo "${str%.cpp}"            # Output: /path/to/foo
echo "${str%.cpp}.o"          # Output: /path/to/foo.o
echo "${str%/*}"              # Output: /path/to
```

### Base Path and File Extension

To retrieve the file extension or base path:

```bash
echo "${str##*.}"              # Output: cpp (extension)
echo "${str##*/}"              # Output: foo.cpp (basepath)
```

### Pattern Matching

You can replace specific patterns in strings:

```bash
echo "${str/foo/bar}"          # Output: /path/to/bar.cpp
```

## Advanced Substring and Indirection

### Substring Extraction

Extract substrings based on position and length. Negative indices can be used to count from the right.

```bash
str="Hello world"
echo "${str:6:5}"              # Output: world
echo "${str: -5:5}"            # Output: world
```

### Indirection

Use indirection to dynamically refer to variable names:

```bash
name=joe
pointer=name
echo ${!pointer}              # Output: joe
```

## Prefix Name Expansion

You can expand variables that match a given prefix using indirect expansion.

```bash
prefix_a=one
prefix_b=two
echo ${!prefix_*}              # Output: prefix_a prefix_b
```

## Substitution

Bash supports various substitution operations:

- Remove prefix or suffix
- Replace first match or all matches

```bash
${foo%suffix}      # Remove suffix
${foo#prefix}      # Remove prefix
${foo%%suffix}     # Remove long suffix
${foo/%suffix}     # Remove long suffix
${foo##prefix}     # Remove long prefix
${foo/#prefix}     # Remove long prefix
${foo/from/to}     # Replace first match
${foo//from/to}    # Replace all
${foo/%from/to}    # Replace suffix
${foo/#from/to}    # Replace prefix
```

## Length and Comments

### Length of Variables

You can get the length of a string using `${#variable}`.

```bash
echo "${#foo}"          # Output: Length of foo
```

### Comments

Use `#` for single-line comments, and `: ' '` for multi-line comments.

```bash
# Single-line comment

: '
This is a
multi-line
comment
'
```

## String Manipulation: Case Conversion

You can manipulate the case of characters:

```bash
str="HELLO WORLD!"
echo "${str,}"           # Output: hELLO WORLD! (lowercase 1st letter)
echo "${str,,}"          # Output: hello world! (all lowercase)

str="hello world!"
echo "${str^}"           # Output: Hello world! (uppercase 1st letter)
echo "${str^^}"          # Output: HELLO WORLD! (all uppercase)
```

## Default Values and Error Handling

Bash allows you to handle unset or null values with conditional checks and default assignments:

```bash
${foo:-val}     # If $foo is unset or null, use "val"
${foo:=val}     # Set $foo to "val" if unset or null
${foo:+val}     # Use "val" if $foo is set (not null)
${foo:?message} # Show error message and exit if $foo is unset or null
```

# Loops in Bash

Loops are essential for automating repetitive tasks. Bash provides several types of loops, each suitable for different scenarios. This section covers the basic `for` loop, C-style loops, and other loop variations, along with examples.

## Basic `for` Loop

A basic `for` loop iterates over a list of items. In this case, it loops over files that match the pattern `/etc/rc.*`:

```bash
for i in /etc/rc.*; do
  echo "$i"
done
```

### Explanation:
- This loop iterates through each file in the `/etc` directory that starts with `rc.` and prints each file path to the screen.

## C-like `for` Loop

Bash also supports a C-style `for` loop, which is useful when you need to specify a counter, start and end conditions, and an increment expression.

```bash
for ((i = 0 ; i < 100 ; i++)); do
  echo "$i"
done
```

### Explanation:
- This loop initializes `i` to 0, runs while `i` is less than 100, and increments `i` by 1 after each iteration. The value of `i` is printed on each loop cycle.

## Using Ranges in a `for` Loop

You can use ranges in a `for` loop to easily iterate over a series of numbers.

```bash
for i in {1..5}; do
    echo "Welcome $i"
done
```

### Explanation:
- The loop iterates over the numbers 1 to 5, and prints `Welcome 1`, `Welcome 2`, etc., for each iteration.

## `for` Loop with Step Size

You can also specify a step size (increment value) when using a range in the loop. For example:

```bash
for i in {5..50..5}; do
    echo "Welcome $i"
done
```

### Explanation:
- This loop iterates over the numbers from 5 to 50 with a step size of 5. The output will include `Welcome 5`, `Welcome 10`, `Welcome 15`, etc.

## Reading Lines from a File

To read lines from a file, you can use a `while` loop in combination with the `read` command:

```bash
while read -r line; do
  echo "$line"
done < file.txt
```

### Explanation:
- The `while` loop reads each line from `file.txt` and prints it. The `-r` flag ensures that backslashes are not interpreted as escape characters.

## Infinite Loop

You can create an infinite loop with `while true` to keep running a block of code indefinitely. For example:

```bash
while true; do
  # Code goes here
done
```

### Explanation:
- The loop will run forever unless explicitly broken using a `break` statement or an exit condition.

---

# Functions in Bash

Functions allow you to group commands together and call them with different arguments, improving the reusability and modularity of your scripts. This section explains how to define functions, return values, handle errors, and work with function arguments.

## Defining Functions

Functions in Bash can be defined in two common ways.

### Syntax 1: Traditional Function Definition

```bash
myfunc() {
    echo "hello $1"
}
```

### Syntax 2: Alternative Function Definition

```bash
function myfunc {
    echo "hello $1"
}
```

In both cases, the function `myfunc` takes one argument (`$1`), which is printed along with the string "hello".

### Calling a Function

To call the function with an argument:

```bash
myfunc "John"
```

Output:

```bash
hello John
```

## Returning Values

To return values from a function, you can use `echo` or assign values to a variable. Here's an example:

```bash
myfunc() {
    local myresult='some value'
    echo "$myresult"
}

result=$(myfunc)
```

### Explanation:
- The function `myfunc` sets a local variable `myresult`, and uses `echo` to output it.
- The returned value is captured by the `result` variable when calling the function.

## Raising Errors

You can raise errors from a function using the `return` command. If a function returns a non-zero value, it indicates an error or failure. Here's an example:

```bash
myfunc() {
  return 1
}

if myfunc; then
  echo "success"
else
  echo "failure"
fi
```

### Explanation:
- The function `myfunc` returns `1`, which is treated as an error.
- The `if` condition checks the return value of the function, and since it is non-zero, the output will be `failure`.

## Function Arguments

Functions in Bash can accept arguments, which can be accessed using special variables:

- `$#` – Number of arguments passed to the function
- `$*` – All positional arguments as a single word
- `$@` – All positional arguments as separate strings
- `$1` – First argument passed to the function
- `$_` – Last argument of the previous command

### Important Note:
- Both `$*` and `$@` must be quoted to behave as described. Without quotes, they treat the arguments as separate words.

```bash
myfunc() {
    echo "Number of arguments: $#"
    echo "All arguments: $*"
    echo "First argument: $1"
}

myfunc "apple" "banana" "cherry"
```

### Output:
```bash
Number of arguments: 3
All arguments: apple banana cherry
First argument: apple
```

### Difference between `$*` and `$@`:
- When quoted (`"$@"`), each argument is treated as a separate string, which is useful when passing arguments to other commands or loops.
- `$*` without quotes combines the arguments into a single string.

---
# Arrays in Bash

Arrays in Bash allow you to store multiple values in a single variable. Unlike other programming languages, arrays in Bash are indexed by integers and can store both strings and numbers.

## Defining Arrays

You can define an array in two ways: by explicitly specifying the elements or by assigning values to specific indices.

### Example 1: Defining an array with specific values

```bash
Fruits=('Apple' 'Banana' 'Orange')
```

### Example 2: Defining an array element by element

```bash
Fruits[0]="Apple"
Fruits[1]="Banana"
Fruits[2]="Orange"
```

In this case, each element is manually assigned a specific index.

## Working with Arrays

Once you have defined an array, you can work with it using various syntax patterns.

### Accessing elements

- To access an element at a specific index:
  
  ```bash
  echo "${Fruits[0]}"   # Output: Apple
  ```

- To access the last element of the array:

  ```bash
  echo "${Fruits[-1]}"  # Output: Orange
  ```

- To access all elements of the array:

  ```bash
  echo "${Fruits[@]}"   # Output: Apple Banana Orange
  ```

- To find the number of elements in the array:

  ```bash
  echo "${#Fruits[@]}"  # Output: 3
  ```

- To find the string length of the first element:

  ```bash
  echo "${#Fruits}"     # Output: 5 (length of "Apple")
  ```

- To find the length of a specific element:

  ```bash
  echo "${#Fruits[3]}"  # Output: 0 (if index 3 is not set, it returns 0)
  ```

- To access a range of elements (for example, starting from index 3 and including 2 elements):

  ```bash
  echo "${Fruits[@]:3:2}"  # Output: (empty if there are fewer than 2 elements starting at index 3)
  ```

- To get the indices (keys) of all elements:

  ```bash
  echo "${!Fruits[@]}"  # Output: 0 1 2
  ```

## Operations on Arrays

You can perform various operations on arrays, such as pushing new elements, removing elements, and more.

- **Push an element to an array:**

  ```bash
  Fruits=("${Fruits[@]}" "Watermelon")    # Adds "Watermelon"
  Fruits+=('Watermelon')                  # Adds "Watermelon" again
  ```

- **Remove elements based on a regex match:**

  ```bash
  Fruits=( "${Fruits[@]/Ap*/}" )  # Removes elements that start with "Ap"
  ```

- **Remove an element at a specific index:**

  ```bash
  unset Fruits[2]  # Removes the element at index 2 (i.e., "Orange")
  ```

- **Duplicate the array:**

  ```bash
  Fruits=("${Fruits[@]}")  # Makes a copy of the entire array
  ```

- **Concatenate two arrays:**

  ```bash
  Fruits=("${Fruits[@]}" "${Veggies[@]}")  # Merges the Fruits and Veggies arrays
  ```

- **Read from a file into an array:**

  ```bash
  lines=(`cat "logfile"`)  # Reads the contents of "logfile" into the array 'lines'
  ```

## Iterating Over Arrays

To iterate over an array, you can use a `for` loop.

```bash
for i in "${Fruits[@]}"; do
  echo "$i"  # Output each element of the array
done
```

This loop will print each element in the `Fruits` array on a new line.

---


# Dictionaries (Associative Arrays) in Bash

In Bash, associative arrays (or dictionaries) are arrays where the indices (or keys) can be strings instead of integers. These allow you to store key-value pairs, making them ideal for tasks that require more flexible data storage.

## Defining a Dictionary

To declare an associative array (dictionary) in Bash, use the `declare -A` command.

### Example: Defining a dictionary of sounds

```bash
declare -A sounds
sounds[dog]="bark"
sounds[cow]="moo"
sounds[bird]="tweet"
sounds[wolf]="howl"
```

In this example, the keys (`dog`, `cow`, `bird`, `wolf`) are associated with their corresponding values (`bark`, `moo`, `tweet`, `howl`).

## Working with Dictionaries

Once a dictionary is defined, you can perform several operations like accessing values, iterating over keys or values, and modifying the dictionary.

### Accessing Values

To access the value associated with a specific key:

```bash
echo "${sounds[dog]}"  # Output: bark
```

### Accessing All Values

To print all the values in the dictionary:

```bash
echo "${sounds[@]}"  # Output: bark moo tweet howl
```

### Accessing All Keys

To print all the keys in the dictionary:

```bash
echo "${!sounds[@]}"  # Output: dog cow bird wolf
```

### Getting the Number of Elements

To get the number of key-value pairs in the dictionary:

```bash
echo "${#sounds[@]}"  # Output: 4
```

### Deleting a Key-Value Pair

To delete a specific key-value pair:

```bash
unset sounds[dog]  # Removes the key "dog" and its associated value "bark"
```

## Iterating Over Dictionaries

You can iterate over the dictionary in various ways, depending on whether you want to loop through the keys or the values.

### Iterating Over Values

To iterate over and print all values in the dictionary:

```bash
for val in "${sounds[@]}"; do
  echo "$val"  # Output: bark moo tweet howl
done
```

### Iterating Over Keys

To iterate over and print all keys in the dictionary:

```bash
for key in "${!sounds[@]}"; do
  echo "$key"  # Output: dog cow bird wolf
done
```

### Summary

- Dictionaries (associative arrays) allow you to map strings (keys) to values.
- Use `declare -A` to define an associative array.
- Access and modify values using the key.
- Iterate over keys or values using `for` loops.
- Use `unset` to remove key-value pairs.

Associative arrays are a powerful feature in Bash, making them ideal for situations where key-value pair storage and retrieval is needed.

---


# Bash Options and Glob Options

Bash provides several options that allow you to customize the behavior of the shell. Additionally, globbing options control how file patterns (wildcards) are expanded.

## Shell Options

You can enable or disable shell options using the `set` and `shopt` commands.

### `set` Command Options

The `set` command modifies the shell's behavior. Here are some commonly used options:

#### `noclobber`
```bash
set -o noclobber  # Avoid overwriting files with '>' operator
```
This option prevents files from being overwritten by redirection (e.g., `echo "hi" > foo`). If a file already exists, this option will stop the shell from overwriting it.

#### `errexit`
```bash
set -o errexit  # Exit the script immediately if any command returns a non-zero status
```
With this option enabled, the script will terminate as soon as any command fails (returns a non-zero status). This helps avoid cascading errors in scripts.

#### `pipefail`
```bash
set -o pipefail  # Causes the pipeline to return the exit status of the last failed command in the pipeline
```
By default, in a pipeline of commands (e.g., `command1 | command2`), the exit status of the pipeline is the exit status of the last command. Enabling `pipefail` causes the pipeline to return the status of the last command that failed, making error detection more accurate.

#### `nounset`
```bash
set -o nounset  # Exposes errors when referencing unset variables
```
With this option, any reference to an unset variable will cause the script to exit with an error. This is useful for catching bugs due to typos or missing variables.

## Glob Options

Bash also provides several `shopt` options that influence how globbing (wildcard matching) works.

### `shopt` Command Options

The `shopt` command modifies the behavior of the shell's pattern matching.

#### `nullglob`
```bash
shopt -s nullglob  # Non-matching globs are removed (e.g., '*.foo' returns an empty string if no matches)
```
With `nullglob`, if a pattern doesn't match any files, it is removed (i.e., expanded to an empty string), instead of being returned as the original pattern.

#### `failglob`
```bash
shopt -s failglob  # Non-matching globs throw an error
```
When `failglob` is enabled, if a pattern doesn't match any files, the shell will return an error.

#### `nocaseglob`
```bash
shopt -s nocaseglob  # Case-insensitive globbing
```
With `nocaseglob`, file name matching ignores case, so `*.sh` will match files like `file.SH`, `file.sh`, etc.

#### `dotglob`
```bash
shopt -s dotglob  # Wildcards match dotfiles (files starting with '.')
```
Enabling `dotglob` allows wildcards to match files that start with a dot (`.`), such as `.bashrc`.

#### `globstar`
```bash
shopt -s globstar  # Enable recursive globbing with '**'
```
With `globstar`, you can use the `**` pattern for recursive matches. For example, `lib/**/*.rb` will match all `.rb` files in the `lib` directory and its subdirectories.

### Summary

- **Shell Options**:
  - `noclobber`: Prevent file overwriting with redirection.
  - `errexit`: Exit on command errors.
  - `pipefail`: Return the exit status of the last failed command in a pipeline.
  - `nounset`: Expose errors for unset variables.

- **Globbing Options**:
  - `nullglob`: Remove unmatched globs.
  - `failglob`: Throw an error on unmatched globs.
  - `nocaseglob`: Perform case-insensitive globbing.
  - `dotglob`: Match dotfiles with globs.
  - `globstar`: Enable recursive globbing with `**`.

---

# History Expansion in Bash

Bash provides several mechanisms to work with command history, making it easier to re-execute and modify past commands. Below is a detailed explanation of the different types of history expansions and operations.

## Commands

### `history`
```bash
history  # Displays the command history
```
The `history` command shows the list of previously executed commands in the shell.

### `shopt -s histverify`
```bash
shopt -s histverify  # Don’t execute expanded result immediately
```
This option allows you to verify the expanded result of a command before it is executed. It prevents the shell from running the command immediately after expansion.

## Expansions

Bash supports several types of history expansions to quickly reuse and modify past commands.

### `!$`
```bash
!$  # Expands to the last parameter of the most recent command
```
Expands to the last argument (parameter) of the previous command.

### `!*`
```bash
!*  # Expands to all parameters of the most recent command
```
Expands to all parameters of the most recent command, excluding the command itself.

### `!-n`
```bash
!-n  # Expands to the nth most recent command
```
Expands to the nth most recent command, where `n` is a positive integer.

### `!n`
```bash
!n  # Expands to the nth command in history
```
Expands to the nth command in history, where `n` is a command number (as shown by the `history` command).

### `!<command>`
```bash
!<command>  # Expands to the most recent invocation of <command>
```
Expands to the most recent command that starts with `<command>`.

## Operations

### `!!`
```bash
!!  # Execute the last command again
```
Repeats the most recent command.

### `!!:s/<FROM>/<TO>/`
```bash
!!:s/<FROM>/<TO>/  # Replace the first occurrence of <FROM> with <TO> in the last command
```
Replaces the first occurrence of `<FROM>` with `<TO>` in the most recent command.

### `!!:gs/<FROM>/<TO>/`
```bash
!!:gs/<FROM>/<TO>/  # Replace all occurrences of <FROM> with <TO> in the last command
```
Replaces all occurrences of `<FROM>` with `<TO>` in the most recent command.

### `!$:t`
```bash
!$:t  # Expands only the basename of the last parameter of the most recent command
```
Expands to the basename of the last argument in the most recent command.

### `!$:h`
```bash
!$:h  # Expands only the directory of the last parameter of the most recent command
```
Expands to the directory portion of the last argument in the most recent command.

## Slices

History expansions can also be used to select specific tokens from the most recent command.

### `!!:n`
```bash
!!:n  # Expands to the nth token from the most recent command (0 for command itself)
```
Expands to the nth token (word) from the most recent command, where `n` is a non-negative integer.

### `!^`
```bash
!^  # Expands to the first argument of the most recent command
```
Expands to the first argument of the most recent command.

### `!$`
```bash
!$  # Expands to the last token of the most recent command
```
Expands to the last token (argument) of the most recent command.

### `!!:n-m`
```bash
!!:n-m  # Expands to a range of tokens (from nth to mth) from the most recent command
```
Expands to a range of tokens, from the nth to the mth, from the most recent command.

### `!!:n-$`
```bash
!!:n-$  # Expands from the nth token to the last token from the most recent command
```
Expands from the nth token to the last token in the most recent command.

## Summary of History Expansion

- `!$`: Last argument of the previous command.
- `!*`: All arguments from the last command.
- `!-n`: nth most recent command.
- `!n`: nth command in history.
- `!<command>`: Most recent invocation of `<command>`.
- `!!`: Repeat the last command.
- `!!:s/<FROM>/<TO>/`: Replace `<FROM>` with `<TO>` in the last command.
- `!!:gs/<FROM>/<TO>/`: Replace all occurrences of `<FROM>` with `<TO>` in the last command.
- `!$:t`: Basename of the last argument.
- `!$:h`: Directory of the last argument.
- `!!:n`: nth token in the last command.
- `!^`: First argument from the last command.
- `!!:n-m`: Range of tokens from nth to mth in the last command.
- `!!:n-$`: Tokens from nth to the last in the last command.

These expansions make it easy to manipulate and re-execute past commands, improving efficiency and workflow in the shell.

---

# Miscellaneous Bash Tips and Techniques

This section covers various advanced Bash techniques and commands that are useful in day-to-day scripting, including numeric calculations, subshells, redirection, error handling, string manipulation, and more.

## Numeric Calculations

Bash allows simple arithmetic operations using `$(( ... ))`.

### Example:
```bash
$((a + 200))       # Add 200 to $a
$(($RANDOM%200))   # Generate a random number between 0 and 199
```

### Declare Integer Variables:
```bash
declare -i count  # Declare as type integer
count+=1          # Increment the count by 1
```

## Subshells

A subshell allows you to run commands in a child shell without affecting the parent shell.

### Example:
```bash
(cd somedir; echo "I'm now in $PWD")
pwd  # Still in the first directory
```

## Redirection

Redirection allows you to control where the output or errors of commands go.

### Examples:
```bash
python hello.py > output.txt        # Redirect stdout to a file
python hello.py >> output.txt       # Append stdout to a file
python hello.py 2> error.log        # Redirect stderr to a file
python hello.py 2>&1                # Redirect stderr to stdout
python hello.py 2>/dev/null         # Discard stderr
python hello.py >output.txt 2>&1    # Redirect both stdout and stderr to a file
python hello.py &>/dev/null         # Discard both stdout and stderr
echo "$0: warning: too many users" >&2  # Print to stderr
python hello.py < foo.txt          # Feed input from a file
diff <(ls -r) <(ls)                # Compare stdout without using files
```

## Inspecting Commands

Use the `command` keyword to inspect commands.

### Example:
```bash
command -V cd  # Show the type of command 'cd'
# Output: "cd is a function/alias/whatever"
```

## Trap Errors

You can use the `trap` command to capture errors or specific events.

### Example:
```bash
trap 'echo Error at about $LINENO' ERR  # Trap errors and print line number

# Define a custom error handler
traperr() {
  echo "ERROR: ${BASH_SOURCE[1]} at about ${BASH_LINENO[0]}"
}

# Enable error tracing
set -o errtrace
trap traperr ERR
```

## Case/Switch Statements

The `case` statement is a more advanced version of `if-else`, useful for matching patterns.

### Example:
```bash
case "$1" in
  start | up)
    vagrant up
    ;;
  *)
    echo "Usage: $0 {start|stop|ssh}"
    ;;
esac
```

## Source Relative Files

To source files relative to the script's directory:

### Example:
```bash
source "${0%/*}/../share/foo.sh"
```

## `printf` Formatting

The `printf` command provides formatted output.

### Examples:
```bash
printf "Hello %s, I'm %s" Sven Olga
# Output: "Hello Sven, I'm Olga"

printf "1 + 1 = %d" 2
# Output: "1 + 1 = 2"

printf "This is how you print a float: %f" 2
# Output: "This is how you print a float: 2.000000"

printf '%s\n' '#!/bin/bash' 'echo hello' > file  # Format string applied to each argument
printf '%i+%i=%i\n' 1 2 3 4 5 9
# Output: "1+2=3", "4+5=9"
```

## Transforming Strings

You can manipulate strings using the `tr` command with various options.

### Example:
```bash
echo "Welcome To Devhints" | tr '[:lower:]' '[:upper:]'
# Output: "WELCOME TO DEVHINTS"
```

### `tr` Options:
- `-c`: Apply operations to characters not in the set.
- `-d`: Delete characters.
- `-s`: Replace repeated characters with a single occurrence.
- `-t`: Truncate characters.

Common character classes:
- `[:upper:]`: Uppercase letters
- `[:lower:]`: Lowercase letters
- `[:digit:]`: Digits
- `[:space:]`: Whitespace
- `[:alpha:]`: Letters
- `[:alnum:]`: Alphanumeric (letters and digits)

## Getting Directory of Script

You can get the directory of the current script using `${0%/*}`.

### Example:
```bash
dir=${0%/*}
```

## Getting Options from Command Line

You can parse command line options using a `while` loop and a `case` statement.

### Example:
```bash
while [[ "$1" =~ ^- && ! "$1" == "--" ]]; do 
  case $1 in
    -V | --version)
      echo "$version"
      exit
      ;;
    -s | --string)
      shift; string=$1
      ;;
    -f | --flag)
      flag=1
      ;;
  esac
  shift
done
if [[ "$1" == '--' ]]; then shift; fi
```

## Heredoc

Heredoc allows you to redirect multiple lines of text into a command.

### Example:
```bash
cat <<END
hello world
END
```

## Reading Input

Use `read` to capture user input.

### Examples:
```bash
echo -n "Proceed? [y/n]: "
read -r ans  # Disables backslash interpretation
echo "$ans"

read -n 1 ans  # Read a single character
```

## Special Variables

Bash has several special variables for handling task statuses, process IDs, and more.

- `$?`: Exit status of last command
- `$!`: PID of last background task
- `$$`: PID of current shell
- `$0`: Name of the shell script
- `$_`: Last argument of the previous command
- `${PIPESTATUS[n]}`: Return status of the nth command in a pipeline

### Example:
```bash
if ping -c 1 google.com; then
  echo "You have a working internet connection"
fi

if grep -q 'foo' ~/.bash_history; then
  echo "You appear to have typed 'foo' in the past"
fi
```

## Go to Previous Directory

You can use `cd -` to switch back to the previous directory.

### Example:
```bash
pwd  # /home/user/foo
cd bar/
pwd  # /home/user/foo/bar
cd -
pwd  # /home/user/foo
```
---

## Conclusion

Bash scripting is powerful for automating tasks and performing advanced operations. With features like string manipulation, functions, arrays, and conditionals, you can build complex scripts to handle a variety of tasks. Keep practicing these concepts to become proficient in Bash scripting.
