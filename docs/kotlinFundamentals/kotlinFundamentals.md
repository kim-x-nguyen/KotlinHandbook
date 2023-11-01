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


