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
- **`String`** : array of characters (not a Primitive Type)

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
- Escape sequences:
  - `\"` prints "
  - `\t` TAB
  - `\n` new line, line break, hard return
  - `\\` prints \
- Comparison:
  - `String.equals( "Test" );` : comparison operator for Strings
  - `String.equalsIgnoreCase( "Test" );` : comparison operator that ignores case

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
- Simple:
  - `Math.abs(x);` = absolute value of x
  - `Math.pow(x, y);` = x to the power of y
  - `Math.sqrt(x);` = square root of x
  - `Math.ceil(x);` = returns next highest whole number
  - `Math.floor(x);` = returns next lowest whole number
  - `Math.min(x, y);` = returns minimum of x or y
  - `Math.max(x, y);` = returns maximum of x or y
  - `Math.round(x);` = rounds to nearest whole number
  - `Math.random();` = returns random `double` between 0<=r<1
  - `Math.PI;` = returns 3.14159625...
- Advanced:
  - `Math.log(x);` = log base e of x
  - `Math.sin(x);` = sin of angle x (in rad)
  - `Math.cos(x);` = cos of angle x (in rad)
  - `Math.tan(x);` = tan of angle x (in rad)
  - `Math.asin(x);` = arcsine of x in range -PI/2 to PI/2
  - `Math.acos(x);` = arccosine of x in range -PI/2 to PI/2
  - `Math.atan(x);` = arctan of x in range -PI/2 to PI/2
  - `Math.toDegrees(angRad);` = converts radians into degrees
  - `Math.toRadians(angDeg);` = converts degrees into radians

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
  
  } // end main method
} // end ClassName
```

## Control Structures

### *if* statements
```java
if ( condition ) {
  command;
} else if ( condition2 ) {
  command2;
} else {
  defaultCommand;
}
```

### *switch* and *char*

### *for* loops

### *while* loops

## Classes and Objects
