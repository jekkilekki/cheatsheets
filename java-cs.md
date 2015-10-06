# Java Cheatsheet
A quick-reference glossary-like collection of Java terms and commands.

```java
import packageName.subpackageName.ClassName;

public class ClassName {
  public static void main( String[] args ) {
    /** 
     *  A Java Documentation comment 
     * 
     *  @return nothing
     *  @param String
     */
    
    System.out.print( "The cursor stays on this line after printing." );
    System.out.println( "The cursor moves down a line after printing." );
    
  } // end main method
} // end ClassName
```

###Variable Types
- `byte` : 8-bit integer (-128 to 127)
- `short` : 16-bit integer (-32768 to 32767)
- **`int`** : 32-bit integer (-2^31 to 2^31-1)
- `long` : 64-bit integer (-2^63 to 2^63-1)
- `float` : 32-bit decimal (floating point) number
- **`double`** : 64-bit decimal (floating point) number
- **`boolean`** : true/false 
- `char` : 16-bit Unicode character ('\u0000' (0) to '\uffff' (65,535))
  - enclosed in *single* quotes
- **`String`** : array of characters (not a Primitive Type)
  - enclosed in *double* quotes

#####Variable Specifics
- Naming:
  - Begin with letter or underscore _ and can't contain punctuation except _
  - `camelCasingNamingConventions`
  - `underscoring_naming_conventions`
  - `final int ALL_CAPS` : Constant (unchangeable) variables
- Declaring:
  - `int variableName;` Declaration
  - `variableName = 2;` Assignment
  - `int variableName = 2;` Declaration + Assignment
- Casting:
  - Change variable types to avoid losing data
  - `int j = (int) 6.0;` casts a double to an int (or int would cut off at the decimal point)

###Strings
- Declaring:
  - `String s1; s1 = "value";`
  - `String s2 = new String( "value" );`
  - `String s3 = "value";`
- Methods:
  - `+` : Concatenation (adding Strings together)
  - `String.length();` : returns the number of characters in a String
  - `String.substring(start [,end]);` : prints part of a String
  - `String.toLowerCase();` : lowercases a String
  - `String.toUpperCase();` : all capitals
  - `String.charAt(x);` : returns a `char` at the index of `x` within the String
- Escape sequences:
  - `\"` prints "
  - `\t` TAB
  - `\n` new line, line break, hard return
  - `\\` prints \
- Comparison:
  - `String.equals( "Test" );` : comparison operator for Strings
  - `String.equalsIgnoreCase( "Test" );` : comparison operator that ignores case

####Advanced `String` Methods:

- `@return int`

| Searches __left to right__ for `@param`   | Searches __right to left__ for `@param`       |
|-------------------------------------------|-----------------------------------------------|
| `String.indexOf( String str );`           | `String.lastIndexOf( String str );`           |
| `String.indexOf( String str, int from );` | `String.lastIndexOf( String str, int from );` |
| `String.indexOf( char ch );`              | `String.lastIndexOf( char ch );`              |
| `String.indexOf( char ch, int from );`    | `String.lastIndexOf( char ch, int from );`    |
| `String.indexOf( int ascii );`            | `String.lastIndexOf( int ascii );`            |
| `String.indexOf( int ascii, int from );`  | `String.lastIndexOf( int ascii, int from );`  |

- `@return int`
  - `String.compareTo( Object obj );` : alphabetical order (-int = Str is before `obj`; +int = Str is after `obj`; 0 = Str equals `obj`)
- `@return char`
  - `String.charAt( int index );`
- `@return String`
  - `String.replace( char old, char new );`
  - `String.replace( String old, String new );`
  - `String.trim();` : removes whitespace from beginning/end of String (interior whitespace ignored)
- `@return boolean`
  - `String.contains( String str );` : returns `true` if `str` is in the String
  - `String.startsWith( String str );`
 
####Parsing `Strings` with `Scanner`

__`define: delimiter`__ : a series of characters that separates txt in a `Scanner` into separate objects

```php
// Code                                                       // Position after execution
Scanner sc = new Scanner( "A string for testing scanner" );   // |A string for testing scanner
System.out.println( sc.next() ); // prints A                  // A| string for testing scanner
System.out.println( sc.findInLine( "ri" )); // prints ri      // A stri|ng for testing scanner
String ns = sc.next();                                        // A stri|ng for testing scanner
System.out.println( ns ); // prints ng                        // A string| for testing scanner
sc.useDelimiter( "r\\s+" );                                   // A string| for testing scanner
System.out.println( sc.next() ); // prints fo                 // A string fo|r testing scanner
sc.skip( "r\\s*test" );                                       // A string for test|ing scanner
System.out.println( sc.next() ); // prints ing scanner        // A string for testing scanner|
```

###`char`
```java
char ch = "A";      // illegal because "A" is a String - double quotes
String s = 'B';     // illegal because 'B' is a char - single quotes
char ch = 'C'; 
int i = ch;         // legal because 'C' has an ASCII int value of 67
int j = 68;
char ch = (char) j; // legal IF cast to char (illegal otherwise) and j < 65536 (max ASCII value)
```
- Conversion:
  - String to `char` : `String s = "W"; char ch = s.charAt(0);`
  - `char` to String : `char ch = 'X'; String s = "" + ch; // Concatenate char to an empty String`
  - Capital to small : `char big = 'H'; char sm = (char)(big + 32); // increases ASCII value to lowercase`
  - `Character.toLowerCase(ch);`
  - `Character.toUpperCase(ch);`
- What are you? (returns true/false):
  - `Character.isDigit(ch);`
  - `Character.isLetter(ch);`
  - `Character.isLetterOrDigit(ch);`
  - `Character.isWhitespace(ch);`
  - `Character.isLowerCase(ch);`
  - `Character.isUpperCase(ch);`

###Operators
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
- Compound operators *imply* a type cast : `( j+=x ) == ( j = (int)(j+x) )`
- `++x || --x` : increments or decrements BEFORE use 
  - Ex: `int x = 103; System.out.println( ++x );` outputs 104 (and stores 104)
- `x++ || x--` : increments or decrements AFTER use
  - Ex: `int x = 103; System.out.println( x++ );` outputs 103 (and stores 104)

###Math Methods

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

###Input
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

#Control Structures
  - **Scope:** variables declared in/during *any* Control Structures only pertain to *that* particular Control Structure
  - **Nesting:** "nested ifs" and "nested loops" are ifs *within* if statements and loops *within* loops. Examples below

###`if` statements
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

###`switch`
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

###Loops

- Notes about loops:
  - Loops generally contain 3 parts:
    1. Starting expression *(at which __value__ should the loop begin?)*
    2. Control expression *(for __how long__ will the loop continue?)*
    3. Step expression *(by how much should the variable __change__ each time?)*
  - `break;` in the loop will exit it regardless of the condition
  - `continue;` the remaining loop code will be skipped this time, but the loop will continue
  - The loop control expression (condition) **_must_** eventually become false or you will have an "infinite loop" 
  - Loops without {} braces are understood to contain *only the __very next__ line* of code and no more
  
####`for` loops

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

####`while` and `do while` loops
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

#Classes and Objects
