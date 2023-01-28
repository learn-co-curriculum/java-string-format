# String Format

## Learning Goals

- Learn about the various ways to format a `String`

## Introduction

Sometimes we want to format a `String` a certain way. For example, we might want
to insert so many spaces between words when printing a `String` value. Let's
look at ways we can format a `String` to ensure it will print out to the console
a certain way!

## The `format()` method

| String Method                                              | Description                                                          |
|------------------------------------------------------------|----------------------------------------------------------------------|
| public static String format(String format, Object... args) | Returns a formatted string using the specified format and arguments. |



The `String` class has a static method to help format a `String` value called
`format()`! To help explain how to use the `format()` method, let's look at an
example:

```java
public class StringExample {
    public static void main(String[] args) {
        String bootcamp = "Flatiron School";
        
        // Concatenate two strings using the format() method
        String string1 = String.format("%s is the best!", bootcamp);
        
        System.out.println(string1);
    }
}
```

The code above will have the following output:

```text
Flatiron School is the best!
```

As we can see in the example above, the `format()` method is a static method.
Remember this means it does not need a `String` instance to be called, we invoke
the method through the class name i.e. `String.format("%s is the best!", bootcamp)`. In this
case we see the `format()` method takes in two parameters, a `String` that we
want to format and the object we want to inject into the string. In the
example, the object just happens to be another `String` but it could be an
`Integer` or a `Float`. 

We also see in the `String` that we want to format a
character that looks like this: `%s`, which is called a **format specifier**. A format specifier
indicates how an argument should be processed and where it should be inserted in the string.
The `s` that follows the `%` is a conversion character. **Conversion characters** 
are only valid for certain data
types and signal that a certain object will be placed within the `String` at the
spot where the conversion character appears. Therefore, the `%s` says that
another `String` will be placed where the `%s` appears. In the example above, we
see that the `%s` is in the beginning, and will be replaced with the `bootcamp`
value. Hence, the output "Flatiron School is the best!" is printed to the
console. It should be noted that when conversion characters are used, the second
parameter must be the correlating data type.

Here are some of the conversion characters we may see:

| Conversion Character | Data Type              |
|----------------------|------------------------|
| s                    | String                 |
| d                    | Integer                |
| f                    | Floating-Point Numbers |
| n                    | New line               |
| b                    | Boolean                | 


Let's look again at the `format` method signature:

`public static String format(String format, Object... args)`

The second parameter is listed as `Object... args`.  The three dots `...` in Java are called
**Variable Arguments** or **varargs**.
Variable arguments allow the method to accept zero, one, or more arguments in that position.
Thus, we can call the `format` method passing the format string as the first argument, followed
by one, two, or even three additional objects as arguments as seen in the code below: 

```java
public class VarArgsExample {
    public static void main(String[] args) {
        String language = "Java";
        int year = 1996;
        String founder = "James Gosling";

        String s1 = String.format("The %s programming language", language );
        String s2 = String.format("The %s programming language was designed by %s", language, founder );
        String s3 = String.format("The %s programming language was designed by %s and released in %d", language, founder, year );

        System.out.println(s1);
        System.out.println(s2);
        System.out.println(s3);
    }
}
```

The program prints:

```text
The Java programming language
The Java programming language was designed by James Gosling
The Java programming language was designed by James Gosling and released in 1996
```

The number and type of additional arguments must match the number and type of format specifiers.


- the string `s1` contains 1 format specifier `%s`, so we pass one string as an additional argument (language).
- the string `s2` contains 2 format specifiers `%s %s`, so we pass two additional strings as arguments (language, founder).
- the string `s3` contains 3 format specifiers `%s %s %d`, so we pass two strings and one integer as additional arguments (language, founder, year).



### Comprehension Check

<details>
    <summary>What is printed by the following code?</summary>

  <p>ANSWER:<br>Amir is 24 years old. It is true that Amir is hungry.</p> 
  
</details>

```java
String name = "Amir";
int age = 24;
boolean isHungry = true;

String s = String.format("%s is %d years old. It is %b that %s is hungry.", name, age, isHungry, name);
System.out.println(s);
```

<details>
    <summary>The code below should print "Today is January 13, 2023." but there is an error in the code.
    Can you identify the error?  How would you fix it?</summary>

  <p>ANSWER:<br>The format specifier order is <code>%s %d, %d</code>, which means the
  argument order should be <code>String, int, int</code>,
  but the variable order passed to the format method are <code>int, String, int</code>.</p> 
  <p>The correct code is:<br>
   <code>String date = String.format("Today is %s %d, %d.", month, day, year);</code></p>

</details>

```java
int day = 13;
String month = "January";
int year = 2023;

String date = String.format("Today is %s %d, %d.", day, month, year);
System.out.println(date);
```

<details>
    <summary>Replace each "@" in the code below with the correct format specifier to produce the expected output:
    <br>I would like 3 slices of pizza, please.
    </summary>

  <p>ANSWER:<br><code>String order = String.format("I would like %d slices of %s, please.", 3, "pizza" );</code></p> 
  
</details>

```java
String order = String.format("I would like @ slices of @, please.", 3, "pizza" );
System.out.println(order);
```



### Format Specifier Rules

When we want to format a `String`, we can use the following syntax:

```text
%[flag][width][.precision]conversion-character
```

To break down the syntax some more:

- The **flag** specifier contains a set of characters to specify the
  format of the output. The character set very much depends on the data type
  that is to be formatted.
- The **width** specifier specifies the amount of characters we want to output
  when formatting the value.
- The **precision** specifier is usually used when the data type we are
  formatting is a `Float` and specifies how many decimal values should be
  printed.
- Notice that the flag, width, and precision specifiers are in brackets.
  These specifiers are optional whereas the `%` and the conversion character are
  required when formatting a `String`.

Let's explore these other optional specifiers some more with some examples:

```java
public class StringExample {
    public static void main(String[] args) {
        String bootcamp = "Flatiron School";
        String show = "Parks and Recreation";
        
        // Concatenate two strings using the format() method
        String string1 = String.format("%s is the best!", bootcamp);
        
        // Use multiple conversion characters
        String string2 = String.format("%s has %d seasons.", show, 7);
        
        // Use a floating-point number
        String string3 = String.format("An ice cream cone costs $%f", 2.99);
        
        System.out.println(string1);
        System.out.println(string2);
        System.out.println(string3);
    }
}
```

The above will print the following output:

```text
Flatiron School is the best!
Parks and Recreation has 7 seasons.
An ice cream cone costs $2.990000
```

As we can see with `string2`, we have multiple conversion characters. Since we
have a string conversion character `%s` and an integer conversion character `%d`, we need
to provide both a `String` and an `Integer` as parameters in the `format()`
method.

With `string3`, we see that we are going to print out a floating-point number,
so we use the `%f` character. Except, when we print `string3` to the console,
we get an output with more decimal values than we originally expected. We might
have only expected to see "An ice cream cone costs $2.99", but instead we see
"An ice cream cone costs $2.990000". This is because when we use the `format()`
method to print a `float`, we are printing a default of 6 decimal digits. In
order to specify how many decimal places we want, we need to adjust its
precision. To do so, we can do this:

```java
public class StringExample {
    public static void main(String[] args) {
        // Use a floating-point number with 2 decimal places
        String string3 = String.format("An ice cream cone costs $%.2f", 2.99);

        System.out.println(string3);
    }
}
```

Here, we are using the precision format specifier to specify we want to display
only a specific amount of decimal places. The precision format specifier always
starts with a dot `.` and can then be followed by the number of decimal places.
In this case, we specify a 2, therefore we should only print out to 2 decimal
places when printing the `float`:

```text
An ice cream cone costs $2.99
```

Now what if we want to print some whitespace in front of a given format
specifier? We can do so by specifying the width like this:

```java
public class StringExample {
    public static void main(String[] args) {
        // Use a floating-point number with 2 decimal places and a width of 14
        String string3 = String.format("An ice cream cone costs $%14.2f", 2.99);

        System.out.println(string3);
    }
}
```

By specifying a width, we are saying we want the output to take up a certain
amount of space. In this example, we are saying we want the "2.99" to take up 14
characters worth of space. Since there are 4 characters within "2.99", it will
prepend 10 spaces prior to printing the "2.99".

```text
An ice cream cone costs $          2.99
```

Cool! So we have seen the precision and width format specifiers, but what about
the flag specifier? Let's say we want to actually prepend "2.99" with leading
zeroes now instead of spaces. This is where we can specify a flag with `0` to
pad the output with zeroes:

```java
public class StringExample {
    public static void main(String[] args) {
        // Use a floating-point number with 2 decimal places and a width of 14
        // and leading zeroes
        String string3 = String.format("An ice cream cone costs $%014.2f", 2.99);

        System.out.println(string3);
    }
}
```

This will now output the following:

```text
An ice cream cone costs $00000000002.99
```

Some other flags include the following:

| Flags | Description                                      |
|-------|--------------------------------------------------|
| -     | Print the value left-justified                   |
| +     | Print the sign of the number (positive/negative) |
| 0     | Print the number with leading zeroes             |







## The `printf()` method

We might not always want to initialize a new `String` to just format it.
Sometimes we just want to print a formatted `String` if we do not care about
holding onto how it is formatted.

This is where the `printf()` comes into play!

The `printf()` method can be used instead of a `System.out.print()` or a
`System.out.println()` to print a formatted `String` using the same formatting
rules as above!

Consider the following:

```java
public class StringExample {
    public static void main(String[] args) {
        String bootcamp = "Flatiron School";
        String show = "Parks and Recreation";
        
        // Use printf() instead of String.format()
        System.out.printf("%s is the best!%n", bootcamp);
        System.out.printf("%s has %d seasons.%n", show, 7);
        System.out.printf("An ice cream cone costs $%014.2f%n", 2.99);
    }
}
```

Notice that the same formatting rules defined above are being used here as well!
We can still make use of the conversion characters, width, precision, and flags
as we do with the `format()` method. This is an easy way to simply print to
the console a formatted `String` without initializing a separate variable. Also
note the use of `%n` to write a new line out after each of the `printf()`
statements.

This will output the following:

```text
Flatiron School is the best!
Parks and Recreation has 7 seasons.
An ice cream cone costs $00000000002.99
```

NOTE: Without the `%n` format specifier, the output would all be on one line!

## Code Along

Let's transform a small example to line up 3 lines of output in two columns.
Create a new class in IntelliJ (or use the browser-based Java Visualizer) and copy the following code:

```java
public class StringPrecisionExample {
    public static void main(String[] args) {

        // The first string in each format string should be left aligned with a fixed width of 10 characters.
        // The prices should be formatted with 2 digits after the decimal point.

        String columnHeading = "%s %s";
        String productFormat = "%s $%f";

        System.out.printf(columnHeading, "PRODUCT", "PRICE");
        System.out.printf(productFormat, "Potatoes", 4.27);
        System.out.printf(productFormat, "Eggs", 3.99 );
    }
}
```

We would like the program to output:

```text
PRODUCT    PRICE
Potatoes   $4.27
Eggs       $3.99
```

However, it currently prints:

```text
PRODUCT PRICEPotatoes $4.270000Eggs $3.990000
```

### TASK #1

<details>
    <summary>
    Update the <code>columnHeading</code> and <code>productFormat</code>
    format strings to add a newline specifier at the end of the string.
    </summary>

  <p>ANSWER:<br><code>String columnHeading = "%s %s%n";</code><br><code>String productFormat = "%s $%f%n";</code></p> 

</details>

Confirm the program prints three separate lines of output:

```text
PRODUCT PRICE
Potatoes $4.270000
Eggs $3.990000
```

### TASK #2

<details>
    <summary>
    Update the <code>productFormat</code>
    format string to format the price with display 2 digits after the decimal point.
    </summary>

  <p>ANSWER:<br><code>String productFormat = "%s $%.2f%n";</code></p> 

</details>

Confirm the program output displays the price as shown:

```text
PRODUCT PRICE
Potatoes $4.27
Eggs $3.99
```

### TASK #3

<details>
    <summary>
    Update both the <code>columnHeading</code> and <code>productFormat</code>
    format strings to format the first string to have a width of 10 characters.
    </summary>

  <p>ANSWER:<br><code>String columnHeading = "%10s %s%n";</code><br><code>String productFormat = "%10s $%.2f%n";</code></p> 

</details>

Confirm the program output displays the output as shown below.
The first string in each line of output has padding on the left due to its width of 10 characters.

```text
   PRODUCT PRICE
  Potatoes $4.27
      Eggs $3.99
```

### TASK #4

<details>
    <summary>
    Update both the <code>columnHeading</code> and <code>productFormat</code>
    format strings to left align the first string, which will place the extra padding spaces on the right.
    </summary>

  <p>ANSWER:<br><code>String columnHeading = "%-10s %s%n";</code><br><code>String productFormat = "%-10s $%.2f%n";</code></p> 

</details>

Confirm the program output displays the output as shown below.

```text
PRODUCT    PRICE
Potatoes   $4.27
Eggs       $3.99
```

## RESOURCES

- [Java 17 String](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html)       
- [String format()](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#format(java.lang.String,java.lang.Object...))       
- [Format String](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Formatter.html#syntax)    
- [PrintStream printf()](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/io/PrintStream.html#printf(java.lang.String,java.lang.Object...))