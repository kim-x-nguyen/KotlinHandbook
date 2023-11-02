# Kotlin Fundamentals

## Variables and Constants in Kotlin

Kotlin uses two keywords to declare variables: val and var.

`val`: This stands for "value," and it's used for declaring read-only (immutable) variables. Once you assign a value to a val, you can't change it. It's like a promise you make to yourself that this thing ain't gonna change.

```kotlin
val pi = 3.14159
```

`var`: This one's called a "variable" for a reason. You can change its value after you've declared it. It's like having the power to switch things up whenever you want.

```kotlin
var age = 30
age = 31 // Totally fine!
```

So, in a nutshell, val for things that stay the same, and var for things that can change. Simple as that, my friend!

## Data Types in Kotlin

In Kotlin, we've got some basic data types you need to know:

- Byte: 8-bit signed integer
- Short: 16-bit signed integer
- Int: 32-bit signed integer
- Long: 64-bit signed integer
- Float: 32-bit floating point number
- Double: 64-bit floating point number
- Boolean: true or false
- Char: a single 16-bit Unicode character
- String: a sequence of characters

```kotlin
val myByte: Byte = 13
val myShort: Short = 125
val myInt: Int = 123123123
val myLong: Long = 12_039_812_309_487_120
val myFloat: Float = 13.37F
val myDouble: Double = 3.14159265358979323846
val myBoolean: Boolean = true
val myChar: Char = 'a'
val myString: String = "Hello, world!"
```

## Type Inference in Kotlin

Kotlin is a statically typed language, which means that you have to declare the type of every variable you create. But, Kotlin also has something called type inference, which means that the compiler can figure out the type of a variable for you.

```kotlin
val myByte = 13 // The compiler knows this is an Int
val myBoolean = true // The compiler knows this is a Boolean
val myChar = 'a' // The compiler knows this is a Char
val myString = "Hello, world!" // The compiler knows this is a String
```

## Type Conversion in Kotlin

Kotlin is a strongly typed language, which means that you can't just convert any type to any other type. You can only convert types that are compatible with each other.

Here are some common type conversions:

1. Numeric Types:
  You can usually convert smaller numeric types to larger ones without losing data. For example, you can convert Int to Long or Float to Double.
  
    ```kotlin
    val myInt = 123
    val myLong = myInt.toLong()
    ```

2. Strings:
  You can convert numeric types to strings and vice versa using toString() and toDouble(), toInt(), etc. For example:

    ```kotlin
    val num: Int = 42
    val str: String = num.toString()
    val num2: Int = str.toInt()
    ```

3. Char and Numeric Types:
  You can convert a Char to its corresponding numeric value (Unicode code point) and vice versa. For example:

    ```kotlin
    val char: Char = 'A'
    val code: Int = char.toInt() // Converts 'A' to 65 (Unicode code point)
    val char2: Char = code.toChar() // Converts 65 back to 'A'
    ```

4. Boolean:
   you can convert certain types to a Boolean using type casting or other methods, but the conversion might not always be straightforward. Here are some common conversions:

   - Numeric Types: You can often convert numeric types to Boolean in a way that treats 0 as false and non-zero values as true. For example:

    ```kotlin
    val num: Int = 42
    val bool: Boolean = num != 0 // Converts to true because 42 is non-zero
    ```

   - Strings: You can convert a String to a Boolean based on its content. For example, you might compare it to specific values. However, not all strings can be directly converted to a Boolean. Converting a string with an unexpected value may result in an exception. For example:

    ```kotlin
    val str: String = "true"
    val bool: Boolean = str.toBoolean() // Converts to true

    val str2: String = "abc"
    val bool2: Boolean = str2.toBoolean() // Throws an exception because "abc" is not a valid Boolean value
    ```

   - Nullable Types: If you have a nullable type, you can use the ?: operator to provide a default value when the value is null. For example:

    ```kotlin
    val maybeNum: Int? = null
    val boolFromNullable = maybeNum != null
    ```

5. Explicit Conversions:
  You can convert numeric types to each other explicitly using the toByte(), toShort(), toInt(), toLong(), toFloat(), toDouble(), and toChar() methods.

    ```kotlin
    val myInt = 123
    val myLong = myInt.toLong()
    ```

6. Implicit Conversions:
  You can convert numeric types to each other implicitly if there's no risk of losing data. For example, you can assign an Int to a Long without any problems. Implicit type casting can make code more concise and convenient but should be used with caution, especially when dealing with narrowing conversions (converting larger types to smaller ones), as it may lead to data loss or unexpected behavior. In such cases, explicit type casting should be used to ensure correctness and avoid potential issues.

    ```kotlin
    val numInt: Int = 42
    val numDouble: Double = numInt // Implicit type casting from Int to Double
    ```

## Null Safety in Kotlin

In some languages, a reference type variable can be declared without providing an initial explicit value. In these cases, the variables usually contain a null value. Kotlin variables can't hold null values by default. This means that the following snippet is invalid:

```kotlin
// Fails to compile
val languageName: String = null
```

If you want to declare a variable that can hold a null value, you need to explicitly specify that it's nullable by adding a question mark (?) after the type name. For example:

```kotlin
val languageName: String? = null
```

## Kotlin Operators

Kotlin has a variety of operators that you can use to perform operations on variables and values. Here are some of the most common ones:

- Arithmetic Operators: +, -, *, /, %
- Assignment Operators: =, +=, -=, *=, /=, %=
- Comparison Operators: ==, !=, >, <, >=, <=
- Increment and Decrement Operators: ++, --
- Logical Operators: &&, ||, !
- Bitwise Operators: &, |, ^, <<, >>, >>>

## Loops and Branching in Kotlin

Kotlin has a variety of control flow statements that you can use to control the flow of your program. Here are some of the most common ones:

- If Statements: You can use if statements to execute a block of code if a condition is true. For example:

    ```kotlin
    val num = 42
    if (num > 0) {
        println("Positive number!")
    }
    ```

- If-Else Statements: You can use if-else statements to execute one block of code if a condition is true and another block of code if it's false. For example:

    ```kotlin
    val num = 42
    if (num > 0) {
        println("Positive number!")
    } else {
        println("Negative number!")
    }
    ```

- If-Else-If Statements: You can use if-else-if statements to execute one block of code if a condition is true, another block of code if another condition is true, and so on. For example:

    ```kotlin
    val num = 42
    if (num > 0) {
        println("Positive number!")
    } else if (num < 0) {
        println("Negative number!")
    } else {
        println("Zero!")
    }
    ```

- When Statements: You can use when statements to execute a block of code based on the value of a variable. For example:

    ```kotlin
    val num = 42
    when (num) {
        0 -> println("Zero!")
        1 -> println("One!")
        2 -> println("Two!")
        else -> println("Other!")
    }
    ```

- For Loops: You can use for loops to iterate over a range of values. For example:

    ```kotlin
    for (i in 0..10) {
        println(i)
    }
    ```

- While Loops: You can use while loops to execute a block of code while a condition is true. For example:

    ```kotlin
    var i = 0
    while (i < 10) {
        println(i)
        i++
    }
    ```

- Do-While Loops: You can use do-while loops to execute a block of code while a condition is true, and then check the condition after the block of code has been executed. For example:

    ```kotlin
    var i = 0
    do {
        println(i)
        i++
    } while (i < 10)
    ```

- Break Statements: You can use break statements to exit a loop early. For example:

    ```kotlin
    for (i in 0..10) {
        if (i == 5) {
            break
        }
        println(i)
    }
    ```

- Continue Statements: You can use continue statements to skip the rest of the current iteration of a loop and continue with the next iteration. For example:

    ```kotlin
    for (i in 0..10) {
        if (i == 5) {
            continue
        }
        println(i)
    }
    ```

- Return Statements: You can use return statements to exit a function early. For example:

    ```kotlin
    fun isEven(num: Int): Boolean {
        if (num % 2 == 0) {
            return true
        }
        return false
    }
    ```

- Throw Statements: You can use throw statements to throw an exception. For example:

    ```kotlin
    fun divide(a: Int, b: Int): Int {
        if (b == 0) {
            throw Exception("Cannot divide by zero!")
        }
        return a / b
    }
    ```

- Try-Catch Statements: You can use try-catch statements to handle exceptions. For example:

    ```kotlin
    try {
        val result = divide(10, 0)
        println(result)
    } catch (e: Exception) {
        println(e.message)
    }
    ```

- Finally Statements: You can use finally statements to execute a block of code after a try-catch statement, regardless of whether an exception was thrown or not. For example:

    ```kotlin
    try {
        val result = divide(10, 0)
        println(result)
    } catch (e: Exception) {
        println(e.message)
    } finally {
        println("Done!")
    }
    ```

- Return@Labels: You can use return@labels to return from a lambda expression or an anonymous function. For example:

    ```kotlin
    fun printNumbers() {
        listOf(1, 2, 3, 4, 5).forEach {
            if (it == 3) {
                return@forEach
            }
            println(it)
        }
    }
    ```

## Functions in Kotlin

Functions are blocks of code that perform a specific task. They can be called from other parts of your program to perform that task whenever you need it. Functions can also take parameters and return values.

Here's an example of a function that takes two parameters type Int and returns the sum of those two numbers as an Int:

```kotlin
fun sum(a: Int, b: Int): Int {
    return a + b
}
```

You can call this function like this:

```kotlin
val result = sum(1, 2)
println(result) // Prints 3
```

You can also use named arguments to make your code more readable:

```kotlin
val result = sum(a = 1, b = 2)
println(result) // Prints 3
```

If a function doesn't return a value, you can use the Unit type to indicate that. Unit in Kotlin corresponds to the void in Java. Like void, Unit is the return type of any function that does not return any meaningful value, and it is optional to mention the Unit as the return type. But unlike void, Unit is a real class (Singleton) with only one instance. So, you can use it like any other class.

```kotlin
fun printHello(): Unit {
    println("Hello, world!")
}
```

or simply

```kotlin
fun printHello() {
    println("Hello, world!")
}
```

Default arguments are values that are used when you don't provide a value for a parameter. For example:

```kotlin
fun sum(a: Int = 0, b: Int = 0): Int {
    return a + b
}
```

Lambda expressions are anonymous functions that can be used as values. They are useful for writing code that can be passed around as a variable. For example:

```kotlin
val sum = { a: Int, b: Int -> a + b } // Let the compiler figure out the return type

val substraction: (Int, Int) -> Int = { a, b -> a - b } // Explicitly declare the return type
```

The `it` keyword is used to refer to the current lambda expression parameter when it's the only parameter in the function. For example:

```kotlin
val square: (Int) -> Int = { it * it }
```

Lambda expressions can also be used as higher-order functions, which are functions that take other functions as parameters. This is useful for writing code that can be reused in different contexts. For example:

```kotlin
fun calculate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

val sum = calculate(a = 1, b = 2, operation = { a, b -> a + b })
```

When the last parameter of a function is a lambda expression, you can move the lambda expression outside the parentheses. This is called trailing lambda syntax. For example:

```kotlin
fun calculate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

val sum = calculate(1, 2) { a, b -> a + b }
```

The `operation` function can be any function that takes two Int parameters and returns an Int. This means that you can pass any function that matches this signature, including lambda expressions. For example:

```kotlin
fun calculate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

val sum = calculate(1, 2) { a, b -> a + b }
val substraction = calculate(1, 2) { a, b -> a - b }
val multiplication = calculate(1, 2) { a, b -> a * b }
val division = calculate(1, 2) { a, b -> a / b }
```