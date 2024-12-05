# What are Regular Expressions?

Regular expressions (or Regex) are text patterns that you may use to search documents and find exactly what you're looking for.

## Why should I learn how to use them?

Even if you don't plan on using them anytime soon, knowing how to utilize them is a valuable skill. It will improve your CTF (Capture the Flag) skills and maybe make you a better developer if that is your objective. You invest a little time studying it and end up saving a lot of time by applying it.

## Topics Covered:
- [Regular Expresssions](#what-are-regular-expressions)
- [Searching](#searching-with-regular-expressions)
- [wildcard and Characters](#wildcards-and-optional-characters-in-regular-expressions)
- [Metacharacters and Repetitions](#using-metacharacters-and-repetitions-in-regular-expressions)
- [ Beginning and End of](#matching-the-beginning-and-end-of-a-line)
- [A Powerful Tool](#regular-expressions-a-powerful-tool)
- [Regex cheatsheet](#regular-expression-cheat-sheet)
- [Advanced regex for Matching Common Patterns](#advanced-regular-expressions-for-matching-common-patterns)

## I know all that, but I'm lazy.

This is a tutorial for lazy people. There is some reading first, followed by hands-on learning.


## Where's the 'Deploy' button?

There's no machine to deploy. There are two ways to test your expressions:

1. Create a text file with some test paragraphs (on a Unix machine) and then use `egrep <pattern> <file>` to see what matches and what doesn't.
2. Use an online editor like [https://regexr.com/](https://regexr.com/). You can add your own text in the "Text" field, and then type your expressions (patterns) in the "Expression" field.
---

# Searching with Regular Expressions

When searching for a specific string in a file or block of text, you can search for it as is using:
```
`grep 'string' <file>`
```
But what happens if you want to search for patterns of text? For example, you might be looking for a word that starts with a specific letter, or any words that end with numbers. That's where Regular Expressions (Regex) come in.

## Using Charsets in Regex

Both of the aforementioned problems can be solved by using **Charsets**. A charset is defined by enclosing the character(s) or range of characters you want to match in square brackets `[ ]`. The search will then find every occurrence of the pattern you have defined in the file/text you are searching.

### Examples of Charsets:
- `[abc]` will match **a**, **b**, and **c** (every occurrence of each letter).
- `[abc]zz` will match **azz**, **bzz**, and **czz**.

### Ranges in Charsets:
You can use a **dash** `-` to define ranges:
- `[a-c]zz` is the same as `[abc]zz` above.

You can also combine multiple ranges:
- `[a-cx-z]zz` will match **azz**, **bzz**, **czz**, **xzz**, **yzz**, and **zzz**.

### Matching Any Alphabetical Character:
To match any alphabetical character:
- `[a-zA-Z]` will match any **single letter** (both lowercase and uppercase).

### Matching Numbers in Charsets:
You can use numbers as well:
- `file[1-3]` will match **file1**, **file2**, and **file3**.

### Excluding Characters from Charsets:
Use the **caret symbol** `^` to exclude characters from a charset, and include everything else:
- `[^k]ing` will match **ring**, **sing**, **$ing**, but not **king**.

You can also exclude entire charsets, not just single characters:
- `[^a-c]at` will match **fat** and **hat**, but not **bat** or **cat**.

## Important Notes:
1. **Strings vs. Charsets**: Don't confuse strings with charsets. The charset `[abc]` will match the string **abc**, but also **cba** and **ca**. It doesn't match the string exactly but rather every occurrence of the specified characters in that string.
   
2. **Order of Characters**: When specifying charsets, you should type the letters in the same order as they appear in the question. Otherwise, you may end up with a correct solution that isn't the right answer.

3. **Efficiency in Regex**: When answering questions, the right solution is usually the most efficient regex. Efficiency means two things:
   1. **Be specific**: For example, if the question only requires you to match characters from **a** to **c**, use the charset `[a-c]`, not `[a-z]`.
   2. **Don't be overly specific**: If a question asks you to match **a**, **c**, **f**, **r**, **s**, and **z**, using `[a-z]` is more efficient than matching each character individually.

## Final Tip:
Remember, there isn’t always just one "correct" solution. If you test your solution and it works, take a break, come back later, or ask for a hint in a community like Discord. Don’t get frustrated if the path seems tricky—Regex is about experimentation and optimization!

---
# Wildcards and Optional Characters in Regular Expressions

## Matching Any Single Character with the Dot `.`

The wildcard used to match **any single character** (except the line break) is the **dot** `.`. This means that the pattern `a.c` will match any occurrence of **a**, followed by any single character, and then **c**.

### Examples:
- `a.c` will match:
  - **aac**
  - **abc**
  - **a0c**
  - **a!c**
  
### Important Note:
- The dot `.` matches any character except the line break. If you want to match a literal dot in a string, you need to escape it using a backslash `\`.

## Making a Character Optional with the Question Mark `?`

You can set a character as **optional** in your pattern by using the **question mark** `?`. This means that the character before the `?` is optional, and the pattern will match with or without it.

### Example:
- `abc?` will match:
  - **ab** (since the `c` is optional)
  - **abc** (since the `c` is present)

### Important Note:
- The `?` applies only to the character directly before it. In the pattern `abc?`, only the **`c`** is optional, so the pattern will match both **ab** and **abc**.

## Escaping Special Characters

If you want to search for a **literal dot** (i.e., a dot character `.`) rather than the wildcard behavior, you need to **escape it** using a backslash `\`.

### Example:
- `a.c` will match:
  - **abc**
  - **a@c**
  - **a0c**
  
But, if you want to match the literal string **a.c**, you need to escape the dot:

- `a\.c` will match:
  - **a.c** (but not `aac`, `abc`, etc.)


---

# Using Metacharacters and Repetitions in Regular Expressions

## Matching Common Character Types with Metacharacters

There are simpler ways to match larger charsets using specific **metacharacters**. Here’s a breakdown:

- **`\d`**: Matches any **digit** (0-9).
  - Example: `\d` will match `9`, `0`, etc.
  
- **`\D`**: Matches a **non-digit** (anything that's not 0-9).
  - Example: `\D` will match `A`, `@`, or `!`.
  
- **`\w`**: Matches any **alphanumeric character** (letters and digits) or an underscore `_`.
  - Example: `\w` will match `a`, `3`, or `_`.
  
- **`\W`**: Matches a **non-alphanumeric character** (anything that’s not a letter, digit, or underscore).
  - Example: `\W` will match `#`, `@`, or `!`.
  
- **`\s`**: Matches a **whitespace character** (spaces, tabs, or line breaks).
  - Example: `\s` will match a space between words.
  
- **`\S`**: Matches **anything that’s not a whitespace character**.
  - Example: `\S` will match `a`, `!`, `3`, etc., but not a space.

### Important Note:
- **Underscores (`_`)** are included in the `\w` metacharacter (alphanumeric characters and underscores), but not in `\W`. So, `\w` will match `_`, while `\W` will not.

## Using Repetitions to Match Multiple Characters

You can use repetitions to match many characters of the same type in a row. Here’s how to specify the number of times you want the preceding character or pattern to appear:

- **`{n}`**: Matches exactly **n** occurrences of the preceding pattern.
  - Example: `z{2}` will match exactly **zz**.
  - Command example: `grep 'z{2}' file.txt` will match **zz** in the file.

- **`{n,m}`**: Matches between **n** and **m** occurrences of the preceding pattern.
  - Example: `z{1,3}` will match **z**, **zz**, or **zzz**.
  - Command example: `grep 'z{1,3}' file.txt` will match **z**, **zz**, or **zzz** in the file.

- **`{n,}`**: Matches **n or more** occurrences of the preceding pattern.
  - Example: `z{2,}` will match **zz**, **zzz**, **zzzz**, etc.
  - Command example: `grep 'z{2,}' file.txt` will match **zz**, **zzz**, **zzzz**, and so on.

- **`*`**: Matches **0 or more** occurrences of the preceding pattern.
  - Example: `a*` will match an empty string, `a`, `aa`, `aaa`, etc.
  - Command example: `grep 'a*' file.txt` will match zero or more **a** characters in the file.

- **`+`**: Matches **1 or more** occurrences of the preceding pattern.
  - Example: `a+` will match `a`, `aa`, `aaa`, etc., but not an empty string.
  - Command example: `grep 'a+' file.txt` will match one or more **a** characters in the file.

### Examples of Using `grep` with Repetitions:

1. **Match exactly 2 `z`s:**
   ```bash
   grep 'z{2}' file.txt
   ```
   This will match **zz** in the file.

2. **Match 1 to 3 `z`s:**
   ```bash
   grep 'z{1,3}' file.txt
   ```
   This will match **z**, **zz**, or **zzz** in the file.

3. **Match 2 or more `z`s:**
   ```bash
   grep 'z{2,}' file.txt
   ```
   This will match **zz**, **zzz**, **zzzz**, etc.

4. **Match 0 or more `a`s:**
   ```bash
   grep 'a*' file.txt
   ```
   This will match **a**, **aa**, **aaa**, or even an empty string.

5. **Match 1 or more `a`s:**
   ```bash
   grep 'a+' file.txt
   ```
   This will match **a**, **aa**, **aaa**, etc., but not an empty string.

---

# Matching the Beginning and End of a Line

Sometimes it is very useful to specify that you want to search for a certain pattern at the **beginning** or the **end** of a line. We can do this using the following special characters:

- **`^`**: Matches the **start of a line**.
- **`$`**: Matches the **end of a line**.

### Examples:

- **`^abc`**: This pattern will match any line that starts with **abc**.
  - Example: It will match the line **abc123** but not **123abc**.

- **`xyz$`**: This pattern will match any line that ends with **xyz**.
  - Example: It will match the line **abcxyz** but not **xyzabc**.

### Important Note:
- The **caret `^`** symbol is used to specify the beginning of a line or word, but when enclosed in **square brackets**, it is used to **exclude** characters from a charset (as mentioned previously).

---

# Using Parentheses for Grouping and "Either/Or" Patterns

In Regular Expressions, you can also **group** patterns together by enclosing them in **parentheses** `()`.

### Grouping Patterns:

Parentheses can be used to define an **either/or** pattern, where you want to match one of several possible options. You can do this using the **pipe `|`** symbol.

### Examples of "Either/Or" Pattern:

- **`(day|night)`**: This pattern will match either **day** or **night**.
  - Example: It will match **during the day** and **during the night**.

### Repeating Patterns:

Parentheses can also be used to repeat patterns a specified number of times. You can combine them with repetition metacharacters like `{}` to match repeated occurrences of a group.

### Example of Repeating Pattern:

- **`(no){5}`**: This pattern will match the string **nonononono** (the word **no** repeated exactly 5 times).
  - Example: It will match **nonononono** but not **no** or **nononono**.

---

# `grep` Examples :

1. **Matching lines that start with `abc`**:
   ```bash
   grep '^abc' file.txt
   ```
   This will match lines like **abc123** but not **123abc**.

2. **Matching lines that end with `xyz`**:
   ```bash
   grep 'xyz$' file.txt
   ```
   This will match lines like **abcxyz** but not **xyzabc**.

3. **Matching either `day` or `night`**:
   ```bash
   grep '(day|night)' file.txt
   ```
   This will match lines containing **day** or **night**, such as **during the day** or **during the night**.

4. **Matching the word `no` repeated 5 times**:
   ```bash
   grep '(no){5}' file.txt
   ```
   This will match **nonononono** but not **no** or **nononono**.

---
# Regular Expression Cheat Sheet

This cheat sheet covers common regular expression (regex) elements and their applications, making it a useful resource for both new and experienced users.

---

## Character Classes
Character classes match specific types of characters.

| Regex | Matches | Example |
|-------|---------|---------|
| `.`   | Any character except newline | `a.b` matches `acb`, `a1b`, etc. |
| `\w`  | Word character (alphanumeric + underscore) | `\w+` matches `hello_123` |
| `\d`  | Any digit (0-9) | `\d{2}` matches `23` |
| `\s`  | Any whitespace character (spaces, tabs, newlines) | `\s+` matches one or more spaces |
| `\W`  | Any non-word character (not alphanumeric or underscore) | `\W` matches `#`, `%`, etc. |
| `\D`  | Any non-digit character | `\D{3}` matches `abc` |
| `\S`  | Any non-whitespace character | `\S+` matches `hello` |

---

## Character Sets and Negations
These match specific characters or exclude certain characters.

| Regex  | Matches | Example |
|--------|---------|---------|
| `[abc]` | Any of `a`, `b`, or `c` | `[abc]` matches `a`, `b`, or `c` |
| `[^abc]` | Any character except `a`, `b`, or `c` | `[^abc]` matches `d`, `e`, `1`, etc. |
| `[a-g]` | Any character between `a` and `g` | `[a-g]` matches `d`, `f`, etc. |

---

## Anchors
Anchors match positions in the string (start or end).

| Regex  | Matches | Example |
|--------|---------|---------|
| `^abc$` | String starting with `abc` and ending with `abc` | `^abc$` matches `abc`, but not `abcd` |
| `\b`   | Word boundary (positions between word and non-word characters) | `\bword\b` matches `word` in `word test` |
| `\B`   | Non-word boundary (positions not between word and non-word characters) | `\Bword\B` matches `word` in `password` |

---

## Escaped Characters
Escaped characters match special symbols literally.

| Regex | Matches | Example |
|-------|---------|---------|
| `\.`  | Literal dot `.` | `\.` matches `.` |
| `\*`  | Literal asterisk `*` | `\*` matches `*` |
| `\\`  | Literal backslash `\` | `\\` matches `\` |
| `\t`  | Tab character | `\t` matches a tab |
| `\n`  | Newline character | `\n` matches a newline |
| `\r`  | Carriage return | `\r` matches a carriage return |

---

## Groups & Lookaround
Groups allow you to capture and reference parts of the string. Lookaround allows checking conditions without consuming characters.

| Regex             | Matches | Example |
|-------------------|---------|---------|
| `(abc)`           | Capture group for `abc` | `(abc)` matches `abc` |
| `\1`              | Backreference to group #1 | `(\w+)\1` matches two identical words like `hellohello` |
| `(?:abc)`         | Non-capturing group | `(?:abc)` matches `abc` without capturing it |
| `(?=abc)`         | Positive lookahead (asserts `abc` follows) | `\d(?=abc)` matches `3` in `3abc` |
| `(?!abc)`         | Negative lookahead (asserts `abc` does not follow) | `\d(?!abc)` matches `4` in `4xyz` |

---

## Quantifiers & Alternation
Quantifiers match a specific number or range of characters. Alternation provides the ability to match one of many patterns.

| Regex       | Matches | Example |
|-------------|---------|---------|
| `a*`        | Zero or more `a`s | `a*` matches ``, `a`, `aa`, etc. |
| `a+`        | One or more `a`s | `a+` matches `a`, `aa`, etc. |
| `a?`        | Zero or one `a` | `a?` matches ``, `a` |
| `a{5}`      | Exactly five `a`s | `a{5}` matches `aaaaa` |
| `a{2,}`     | Two or more `a`s | `a{2,}` matches `aa`, `aaa`, etc. |
| `a{1,3}`    | Between one and three `a`s | `a{1,3}` matches `a`, `aa`, `aaa` |
| `a+?`       | Match as few `a`s as possible | `a+?` matches `a` before `aa` |
| `ab|cd`     | Match `ab` or `cd` | `ab|cd` matches `ab` or `cd` |

---

# Regular Expressions: A Powerful Tool

Regular expressions (regex) are extremely strong, even in their most basic form. They can assist you in searching, matching, and manipulating text in an efficient and effective manner.

## Learning and Practicing Regex

There are numerous **online resources** accessible for studying and practicing regular expressions, which I strongly recommend using. The more you practice, the more confident you will get in using regex to tackle text-related difficulties.


## Using Preset Expressions

If you need to search for anything specific, such as a **e-mail address**, it's generally better to use existing **preset expressions** rather than generating your own from start. These preset phrases have been thoroughly vetted and will save you time by ensuring that you cover edge circumstances that would otherwise be overlooked.

For example, instead of creating your own regex to validate an email address, you can use existing patterns that fit the overall structure of an email and have already been optimized for correctness.

## Be Specific, But Not Too Specific

When utilizing regular expressions, it is critical to **be specific** while **not excessively specific**. If you make your regex pattern too elaborate or intricate, you may end up with an unduly convoluted solution when simpler, more efficient solutions are available.

### Example:
- Instead of writing a regex that matches every character combination in a URL, use a more general pattern like `https?://[a-zA-Z0-9./-]+`, which is concise and effective.

In short, **balance is key**. Specificity is important, but over-complication will lead to harder-to-maintain and less efficient solutions.

---


# Advanced Regular Expressions for Matching Common Patterns

Regular expressions (regex) are a powerful tool for matching patterns in text. They may be used to find a variety of data in a string, including **email addresses**, **IP addresses**, **phone numbers**, **URLs**, and many others. Here are some regularly used regex patterns to help you identify specific data.

---

## 1. **IPv4 Address**
**Purpose**: To match an IPv4 address.

**Regex**:
```regex
^([0-9]{1,3}\.){3}[0-9]{1,3}$
```

**Example**: 
- Matches: `192.168.1.1`
- Non-matches: `999.999.999.999`, `192.168.1`

---

## 2. **IPv6 Address**
**Purpose**: To match an IPv6 address.

**Regex**:
```regex
^([0-9a-fA-F]{1,4}:){7}[0-9a-fA-F]{1,4}$
```

**Example**: 
- Matches: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
- Non-matches: `256.256.256.256`

---

## 3. **Email Address**
**Purpose**: To match a general email address.

**Regex**:
```regex
^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```

**Example**: 
- Matches: `user@example.com`, `name123@mail.co.uk`
- Non-matches: `user@com`, `@example.com`

---

## 4. **Phone Number (US Format)**
**Purpose**: To match US phone numbers in various formats.

**Regex**:
```regex
^\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}$
```

**Example**: 
- Matches: `(123) 456-7890`, `123-456-7890`
- Non-matches: `12345`, `123456789`

---

## 5. **URL with Parameters**
**Purpose**: To match a URL with query parameters.

**Regex**:
```regex
https?:\/\/[^\s/?#]+(?:[/?#][^\s]*)?
```

**Example**: 
- Matches: `https://www.example.com?param=1`
- Non-matches: `example.com`

---

## 6. **Hexadecimal Color Code**
**Purpose**: To match hex color codes.

**Regex**:
```regex
^#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})$
```

**Example**: 
- Matches: `#FF5733`, `#a3c`
- Non-matches: `#GGGGGG`, `#1234`

---

## 7. **Base64 Encoded String**
**Purpose**: To detect Base64 encoded strings.

**Regex**:
```regex
^[A-Za-z0-9+/=]{4,}$
```

**Example**: 
- Matches: `U29mdWxlciBFbWFpbCBEYXRh`
- Non-matches: `U+29%`

---

## 8. **SQL Injection Pattern**
**Purpose**: To detect potential SQL injection attempts.

**Regex**:
```regex
(=|--|\*|\b(SELECT|INSERT|DELETE|UPDATE|DROP|WHERE|OR)\b)
```

**Example**: 
- Matches: `DROP TABLE`, `SELECT * FROM users`
- Non-matches: `username=admin`

---

## 9. **Cross-Site Scripting (XSS) Pattern**
**Purpose**: To detect potential XSS payloads.

**Regex**:
```regex
<script.*?>.*?</script> 
```

**Example**: 
- Matches: `<script>alert("XSS")</script>`
- Non-matches: `alert("XSS")`

---

## 10. **HTML Tag**
**Purpose**: To match basic HTML tags.

**Regex**:
```regex
^<([a-zA-Z]+)([^<]+)*>.*<\/\1>$
```

**Example**: 
- Matches: `<div>content</div>`
- Non-matches: `<div><div>content</div>`

---

## 11. **UUID (Universally Unique Identifier)**
**Purpose**: To match a UUID, often used for session identifiers.

**Regex**:
```regex
^[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{4}-[a-fA-F0-9]{12}$
```

**Example**: 
- Matches: `123e4567-e89b-12d3-a456-426614174000`
- Non-matches: `123e4567-e89b-12d3-a456`

---

## 12. **Credit Card Number**
**Purpose**: To match credit card numbers.

**Regex**:
```regex
^(4[0-9]{12}(?:[0-9]{3})?$)|(^5[1-5][0-9]{14}$)
```

**Example**: 
- Matches: `4111111111111111`, `5105105105105100`
- Non-matches: `1234567890123456`

---

## 13. **Social Security Number (SSN)**
**Purpose**: To match a US Social Security Number.

**Regex**:
```regex
^\d{3}-\d{2}-\d{4}$
```

**Example**: 
- Matches: `123-45-6789`
- Non-matches: `123456789`

---

## 14. **Date (YYYY-MM-DD Format)**
**Purpose**: To match a date in `YYYY-MM-DD` format.

**Regex**:
```regex
^\d{4}-\d{2}-\d{2}$
```

**Example**: 
- Matches: `2024-12-05`
- Non-matches: `12-05-2024`

---

## 15. **Time (HH:MM:SS Format)**
**Purpose**: To match time in `HH:MM:SS` format.

**Regex**:
```regex
^([01]?[0-9]|2[0-3]):([0-5]?[0-9]):([0-5]?[0-9])$
```

**Example**: 
- Matches: `12:30:45`
- Non-matches: `25:00:00`

---

## 16. **JSON String**
**Purpose**: To match a JSON-like string.

**Regex**:
```regex
^\{(?:[^{}]|(?R))*\}$
```

**Example**: 
- Matches: `{"key":"value"}`
- Non-matches: `key:value`

---

## 17. **Word Boundary (Exact Match)**
**Purpose**: To match exact words in a string.

**Regex**:
```regex
\bword\b
```

**Example**: 
- Matches: `The word is here.`
- Non-matches: `word123`, `123word`

---

## 18. **Non-Alphanumeric Characters**
**Purpose**: To match non-alphanumeric characters (useful for sanitizing input).

**Regex**:
```regex
[^a-zA-Z0-9]
```

**Example**: 
- Matches: `@`, `#`, `!`
- Non-matches: `abc123`

---

## 19. **File Path**
**Purpose**: To match file paths.

**Regex**:
```regex
^([A-Za-z]:\\|\/)?([A-Za-z0-9-_]+\/)*[A-Za-z0-9-_]+\.(txt|html|pdf|docx)$
```

**Example**: 
- Matches: `C:\files\document.txt`, `/home/user/file.html`
- Non-matches: `file.docx/`, `\\files`

---

## 20. **Word with Specific Length (e.g., 8 Characters)**
**Purpose**: To match a word with a specific length.

**Regex**:
```regex
^\w{8}$
```

**Example**: 
- Matches: `password`
- Non-matches: `pass`, `superlongword`

---


# Conclusion

These regular expressions are only a few of the most popular patterns you may encounter. While regex is highly strong, it is critical to use it properly and efficiently. For difficult tasks, it is generally preferable to leverage existing, well-tested regex patterns (such as email addresses or IP addresses) rather than constructing one from scratch. Always keep performance in mind when testing your regular expressions!


By utilizing the full power of regular expressions and knowing when to employ preset patterns, you may rapidly solve many text processing problems without reinventing the wheel.
