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
} // end class
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
  - `String.toLowerCase();` = lowercases a String
  - `String.toUpperCase();` = all capitals
- Escape sequences:
  - `\"` prints "
  - `\t` TAB
  - `\n` new line, line break, hard return
  - `\\` prints \

###Operators
PEMDAS (parenthesis, exponents, multiplication, division, addition, subtraction)
| Standard:               | Compound: |
|-------------------------|-----------|
| `=` assignment          |           |
| `+` addition            | `+=`      |
| `-` subtraction         | `-=`      |
| `*` mulitplication      | `*=`      |
| `/` division            | `/=`      |
| `%` modulus (remainder) | `%=`      |
- Double: 
  - `==` comparison
  - `++` increment (`++x` = increments BEFORE use; `x++` increments AFTER use)
  - `--` decrement (`--x` = decrements BEFORE use; `x--` decrements AFTER use)
- Compound ( implies a type cast : `j+=x` == `j = (int)(j+x)` ):

###Math Methods
- abs(x) = absolute value of x
- pow(x, y) = x to the power of y
- sqrt(x) = square root of x
- ceil(x) = returns next highest whole number
- floor(x) = returns next lowest whole number
- min(x, y) = returns minimun of x or y
- max(x, y) = returns maximum of x or y
- random() = returns random double between 0<=r<1
- round(x) = rounds to nearest whole number
- PI = returns 3.14159625...
- log(x) = log base e of x
- sin(x) = sin of angle x (in rad)
- cos(x) = cos of angle x (in rad)
- tan(x) = tan of angle x (in rad)
- asin(x) = arcsine of x in range -PI/2 to PI/2
- acos(x) = arccosine of x in range -PI/2 to PI/2
- atan(x) = arctan of x in range -PI/2 to PI/2
- toDegrees(angRad) = converts radians into degrees
- toRadians(angDeg) = converts degrees into radians
