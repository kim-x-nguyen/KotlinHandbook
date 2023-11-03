# Kotlin - Intermaediate - Object Oriented Programming (OOP)

## 1. Classes

Classes are the blueprints of objects. They describe how an object should be created and what properties and methods it should have. Classes are defined using the `class` keyword.

```kotlin
class Person {
    // properties
    var name: String = ""
    var age: Int = 0

    // methods
    fun speak() {
        println("Hello!")
    }
}
```

### 2. Constructors

Constructors are special methods that are called when an object is created. They are used to initialize the properties of an object. In Kotlin, there are two types of constructors: primary and secondary.

#### 2.1 Primary Constructor

The primary constructor is part of the class header. It is declared after the class name and is surrounded by parentheses. The primary constructor does not contain any code. It only contains the properties of the class.

```kotlin
class Person constructor(firstName: String) { /*...*/ }
```

The `constructor` keyword can be omitted if the primary constructor does not have any annotations or visibility modifiers.

```kotlin
class Person(firstName: String) { /*...*/ }
```

If you want to run some code when an object is created, you can use the `init` block. The `init` block is executed after the primary constructor.

```kotlin
class Person(firstName: String) {
    init {
        println("Hello, $firstName!")
    }
}
```

If you want to use the constructor parameter as a property, you can use the `val` or `var` keyword.

```kotlin
class Person(val firstName: String) { /*...*/ }
```

You can also give them a default value.

```kotlin
class Person(val firstName: String = "John") { /*...*/ }
```

if the construtor has annotations or visibility modifiers, the `constructor` keyword is required.

```kotlin
class Person public constructor(firstName: String) { /*...*/ }
class Person @Inject constructor(firstName: String) { /*...*/ }
```

#### 2.2 Secondary Constructor

The secondary constructor is declared inside the class body. It is preceded by the `constructor` keyword. The secondary constructor can contain code. It is used to initialize the properties of the class.

```kotlin
class Person {
    // properties
    var name: String = ""
    var age: Int = 0

    // secondary constructor
    constructor(name: String, age: Int) {
        this.name = name
        this.age = age
    }
}
```

If the class has a primary constructor, each secondary constructor needs to delegate to the primary constructor. This can be done using the `this` keyword.

```kotlin
class Person(val name: String, val age: Int) {
    // secondary constructor
    constructor(name: String) : this(name, 0) // delegate to primary constructor
}
```

Even if the class does not have a primary constructor, the delegation to the primary constructor is still happening, and the initialization code of the primary constructor will be executed.

```kotlin
class Constructors {
    init {
        println("Init block") // initialization code of the primary constructor
    }

    constructor(i: Int) {
        println("Constructor $i") // initialization code of the secondary constructor
    }
}

fun main() {
    Constructors(1) // Init block, Constructor 1
}
```

### 3. Objects

Objects are instances of classes. They are created using the `object` keyword. Objects are useful when you want to create a singleton.

```kotlin
object Person {
    // properties
    var name: String = ""
    var age: Int = 0
}
```

You can create an object from a class by calling the constructor.

```kotlin
val person = Person()
```

Note that Kotlin does not have the `new` keyword.

### 4. Properties

Properties are variables that are defined inside a class. They are used to store the state of an object. Properties are defined using the `var` or `val` keyword.

```kotlin
class Person {
    // properties
    var name: String = ""
    var age: Int = 0
}
```

### 5. Methods

Methods are functions that are defined inside a class. They are used to define the behavior of an object. Methods are defined using the `fun` keyword.

```kotlin
class Person {
    // properties
    var name: String = ""
    var age: Int = 0

    // methods
    fun speak() {
        println("Hello!")
    }
}
```

### 6. Inheritance

Inheritance is a mechanism that allows you to define a new class based on an existing class. The new class is called the subclass, and the existing class is called the superclass. The subclass inherits all the properties and methods of the superclass. In Kotlin, you can use the `:` symbol to declare that a class inherits from another class.

```kotlin
open class Person {
    // properties
    var name: String = ""
    var age: Int = 0

    // methods
    fun speak() {
        println("Hello!")
    }
}

class Student : Person() {
    // properties
    var grade: Int = 0
}

fun main() {
    val student = Student()
    student.name = "John"
    student.age = 20
    student.grade = 12
    student.speak() // Hello!
}
```

The `open` keyword is used to allow the class to be inherited. By default, classes in Kotlin are final and cannot be inherited.

