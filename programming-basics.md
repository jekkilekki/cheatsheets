# Programming Basics Cheatsheet
A quick-reference glossary-like collection of basic programming terms and commands.

### Variables
A `variable` is basically like a container that holds a certain value that may be replaced or changed within the program. Consider a login form:

| `username`   | Holds your username (and varies between users)       |
|--------------|------------------------------------------------------|
| `password`   | Holds your password (and varies between users)       |

- Naming:
  - Typically begin with letter or underscore _ and can't contain punctuation except _ (and $ in some languages)
  - `camelCasingNamingConventions`
  - `underscoring_naming_conventions`

##### Strings
Strings are special kinds of variables that usually contain sentences or phrases that may be "spoken" or output by the program. There are often String methods in various programming languages that help programmers manipulate them. Because Strings are enclosed in quotation marks, additional quotation marks (and other special characters) within the String need to be "escaped" before they are used.

- Escape sequences:
  - `\'` prints '
  - `\"` prints "
  - `\t` TAB
  - `\n` new line, line break, hard return
  - `\\` prints \

##### Characters
Characters are LIKE Strings, except they are only a single letter of a String. Actually Strings can be considered arrays of Characters and can often be manipulated with Array methods.

### Operators
When using math operators, follow the Order of Operations specified by PEMDAS:
PEMDAS (parenthesis, exponents, multiplication, division, addition, subtraction)

| Standard:               | Compound: | Double:         | Comparison:                   |
|-------------------------|-----------|-----------------|-------------------------------|
| `=` assignment          |           | `==` comparison | `==` equivalent               |
| `+` addition            | `+=`      | `++` increment  | `>` greater than              |
| `-` subtraction         | `-=`      | `--` decrement  | `>=` greater than or equal to |
| `*` mulitplication      | `*=`      | `&&` AND        | `<` less than                 |
| `/` division            | `/=`      | `||` OR         | `<=` less than or equal to    |
| `%` modulus (remainder) | `%=`      | `&|` AND/OR     | `!` not (negation)            |

Notes: 
- `++x || --x` : increments or decrements BEFORE use 
  - Ex: `int x = 103; System.out.println( ++x );` outputs 104 (and stores 104)
- `x++ || x--` : increments or decrements AFTER use
  - Ex: `int x = 103; System.out.println( x++ );` outputs 103 (and stores 104)

##### Math Methods
Many programming languages have specialized Math methods to perform special functions. The following is a table that shows some of the uses of Math methods in `Java`:

| Simple:                                             | Advanced:                                           |
|-----------------------------------------------------|-----------------------------------------------------|
| `Math.abs(x);` = absolute value of x                | `Math.log(x);` = log base e of x                    |
| `Math.pow(x, y);` = x to the power of y             | `Math.sin(x);` = sin of angle x (in rad)            |
| `Math.sqrt(x);` = square root of x                  | `Math.cos(x);` = cos of angle x (in rad)            |
| `Math.ceil(x);` = returns next highest whole number | `Math.tan(x);` = tan of angle x (in rad)            |
| `Math.floor(x);` = returns next lowest whole number | `Math.asin(x);` = arcsine in range -PI/2 to PI/2    |
| `Math.min(x, y);` = returns minimum of x or y       | `Math.acos(x);` = arccosine in range -PI/2 to PI/2  |
| `Math.max(x, y);` = returns maximum of x or y       | `Math.atan(x);` = arctan in range -PI/2 to PI/2     |
| `Math.round(x);` = rounds to nearest whole number   | `Math.toDegrees(angRad);` = radians to degrees      |
| `Math.random();` = returns random `double` 0<=r<1   | `Math.toRadians(angDeg);` = degrees to radians      |
| `Math.PI;` = returns 3.14159625...                  |                                                     |

### Input/Output
```java
import java.util.Scanner;

public class ClassName {
  public static void main( String[] args ) {
  
    Scanner s = new Scanner( System.in ); // creates a new Keyboard Reader Object (Scanner)
    
    System.out.print( "Enter your int here: " );
    int i = s.nextInt(); // can be used mulitple times if multiple values separated by whitespace
    
    System.out.print( "Enter your decimal here: " );
    double d = s.nextDouble(); // can be used mulitple times if multiple values separated by whitespace
    
    System.out.print( "Enter you String here: " );
    String str = s.next(); // inputs up to the first whitespace - use multiple Scanner.next(); for if more inputs
    
    System.out.print( "Enter your line here: " );
    String line = s.nextLine();
    char ch = line.charAt(0); // gets the first letter (char) of the line
  
  } // end main method
} // end ClassName
```

### Control Structures
Control structures include Conditional statements that may be used to fork a program into various different functions. For example: 
`IF A is true, do function A, ELSE IF B is true, do function B, ELSE do function C (last, base case)` 

  - **Scope:** variables declared in/during *any* Control Structures only pertain to *that* particular Control Structure
  - **Nesting:** "nested ifs" and "nested loops" are ifs *within* if statements and loops *within* loops. Examples below:

##### `if` statements
```java
if ( condition ) {
  command;
} else if ( condition2 ) {
  command2;
} else {
  defaultCommand;
}

// Nested if
if ( condition ) {
  if ( condition ) {
    command;
  } else {
    command;
  }
} else {
  command;
}
```

### `switch`
Similar to *if*, allows for multiple (specified) cases.

- **`int`** switch
```java
Scanner s = new Scanner( System.in );
int choice = s.nextInt();

switch( choice ) {
  case 1: // First choice
    command;
    break; // breaks out of the switch structure
  case 2: // Second choice
    command;
    break;
  default: // Fallback and Error catching
    command;
}
```

- **`char`** switch
```java
Scanner s = new Scanner( System.in );
String choice = s.nextLine();
char ch = choice.charAt(0);

switch( ch ) {
  case 'A':
  case 'a':
    command;
    break;
  case 'B':
  case 'b':
    command;
    break;
  default:
    command;
}
```

- **`String`** switch (from Java 7.0)
```java
Scanner s = new Scanner( System.in );
String choice = s.nextLine();

switch( choice ) {
  case "Hello":
    command;
    break;
  case "Good bye":
    command;
    break;
  default:
    command;
}
```

### Loops
Loops are used when we want to repeat a certain action (or series of actions) over and over for a certain period (`for` loops), or until a certain conditional is satisfied (`while` loops).

- Notes about loops:
  - Loops generally contain 3 parts:
    1. Starting expression *(at which __value__ should the loop begin?)*
    2. Control expression *(for __how long__ will the loop continue?)*
    3. Step expression *(by how much should the variable __change__ each time?)*
  - `break;` in the loop will exit it regardless of the condition
  - `continue;` the remaining loop code will be skipped this time, but the loop will continue
  - The loop control expression (condition) **_must_** eventually become false or you will have an "infinite loop" 
  - Loops without {} braces are understood to contain *only the __very next__ line* of code and no more
  
##### `for` loops

```java
for ( int i = x; i <= y; i++ ) {
  commandToRepeat;
}

// Nested loop
for ( int i = 0; i < 5; i++ ) {
  commandToRepeat;    // executes 5 times
  for ( int j = 0; j < 8; j++ ) {
    commandToRepeat;  // executes 40 times
  }
}
```

##### `while` and `do while` loops
```java
while ( condition ) {
  command;
}

// Do while
do {
  command;
} while ( condition );
```

- Notes: 
  - Starting expression and Step expression are *not* part of the loop
  - The `do while` loop will execute *at least* once even if the condition is `false` from the start
- Difference between `while` and `do while`:
  - `while` : condition is tested at the **start** of the loop
  - `do while` : condition is tested at the **end** of the loop

### Functions
Functions a used when we want to encapsulate a certain algorithm (series of program steps) into a single "command" that we can use over and over again through the program. Generally, functions look like this:

```javascript
function doSomething() {
  actionOne;
  actionTwo;
  actionThree;
  finalAction;
}
```

##### Using Parameters
Sometimes, our functions need a little additional information in order to perform their work on different parts of the program. This additional information is often interchangeable, and when passed into the function is called a `parameter`.

The following is an example of a song function using parameters:

```php
function Chorus( animal, sound ) {
  echo "Old MacDonald had a farm. E-I-E-I-O.";
  echo "And on that farm, he had a " . animal . ". E-I-E-I-O.";
  echo "With a " . sound . ", " . sound . " here, and a " . sound . ", " . sound . " there,";
  echo "Here a " . sound . ", there a " . sound . ", everywhere a " . sound . ", " . sound . ".";
  echo "Old MacDonald had a farm. E-I-E-I-O.";
}

Chorus( "cow", "moo" );
Chorus( "pig", "oink" );
```
