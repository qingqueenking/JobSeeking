## Variables
* Naming
  * Variable names are case-sensitive.
  * A variable's name can be any legal identifier - an unlimited-length sequence of Unicode letters and digits, beginning with a letter, the dollar sign, or the underscore character. The convention, however, is not to use the dollar sign at all.
  * Subsequent characters may be letters, digits, dollar signs, or underscore characters.
  * If the name consists of only one word, spell that word in all lowercase letters. If it consists of more than one word, capitalize the first letter of each subsequent word.
  * If your variable stores a constant value, the convention changes slightly, capitalizing every letter and separating subsequent words with the underscore character. By convention, the underscore character is never used elsewhere.
* Primitive Data Types
  The Java Programming language is statically-typed, which means that all variables must first be declared before they can be used. <br>
  Data Type | Bits | Value Range | Default Value
  :----- | :-----: | :-----: | :-----:
  byte | 8 bits | 1 | 0
  short | 16 bits | 2 | 0
  int | 32 bits | 3 | 0
  long |  64 bits | 4 | 0L
  float | 32 bits | 5 | 0.0f
  double | 32 bits | 6 | 0.0d
  char | 16 bits | 7 | 1
  boolean | 1 bits | 8 | 0
  * Literals
    the source code representation of fixed values
  * Integer Literals
    An integer literal is of type long if it ends with the letter L or l; otherwise it is of type int. It is recommended that you use the upper case letter L because lowercase letter l is hard to distinguish from the digit 1. <br>
    The prefix 0x indicates hexadecimal and 0b indicates binary.
  * Floating-Point Literals
    A floating-point literal is of type float if it ends with the letter F or f; otherwise its type is double and it can optionally end with letter D or d.
* Kinds
  * Fields: Member variables in a class
    * Instance Variables (Non-Static Fields)
    * Class Variables (Static Fields)
  * Local Variables: variables in a method or block of code
  * Parameters: variables in method declarations
## Operators
* The Type Comparison Operator instanceof
  The instanceof operator compares an object to a specified type. You can use it to test if an object is an instance of a class, an instance of a subclass, or an instance of a class that implements a particular interface. <br>
  When using the instanceof operator, keep in mind that null is not an instance of anything.
* Bitwise and Bit Shift Operators
  << Signed left shift <br>
  \>\> Signed right shift <br>
  \>\>\> Unsigned right shift
## Classes
* Modifiers.
* The class name, with the initial letter capitalized by convention.
* The name of the class's parent, if any, preceded by the keyword extends. A class can only extend one parent.
* A comma-separated list of interfaces implemented by the class, if any, preceded by the keyword implements. A class can implement more than one interface.
* The class body, surrounded by braces, {}.
## Methods
* Modifiers.
* The return type.
* The first word in a method name should be a verb.
* The Parameter list in parenthesis - a comma-delimited list of input parameters proceeded by data types.
* An exception list.
* The method body, enclosed between braces.
## Access Modifiers
Modifier | Class | Package | Subclass | World
:- | :-: | :-: | :-: | :-:
public | Y | Y | Y | Y
protected | Y | Y | Y | N
default | Y | Y | N | N
private | Y | N | N | N
## Overloading methods
Methods within a class can have the same name if they have different parameter lists. <br>
The compiler does not consider return type when differentiating methods, so you cannot declare two methods with the same signature even if they have a different return type.
## Primitive Data Type vs. Reference Data Type
* Primitive arguments are passed into methods by value. This means that any changes to the values of the parameters exist only within the scope of the method. When the method returns, the parameters are gone and any changes to them are lost.
* Reference data type parameters are also passed into methods by value. This means that when the method returns, the passed-in reference still references the same object as before. However, the values of the object's fields can be changed in the method.
## Using the this keyword
Within an instance method or a constructor, this is a reference to the current object.
## Class Variables and Methods
```
ClassName.variableName
ClassName.methodName(args)
```
You can also refer to static variables and methods with an object reference, but this is discouraged because it does not make it clear that they are class variables or methods.
Not all combinations of instance and class variables and methods are allowed:
* Instance methods can access instance variables and instance methods directly.
* Instance methods can access class variables and class methods directly.
* Class methods can access class variables and class methods directly.
* Class methods cannot access instance variables or instance methods directly — they must use an object reference. Also, class methods cannot use the this keyword as there is no instance for this to refer to.
## Nested Classes
Nested classes are divided into two categories: static and non-static. Nested classes that are declared static are called static nested classes. Non-static nested classes are called inner classes.
```
class OuterClass {
  ...
  static class StaticNestedClass {
    ...
  }
  class InnerClass {
    ...
  }
}
```
* Static Nested Classes
As with class methods and variables, a static nested class is associated with its outer class. And like class methods, a static nested class cannot refer directly to instance variables or methods defined in its enclosing class: it can use them only through an object reference.
* Inner Classes
As with instance methods and variables, an inner class is associated with an instance of its enclosing class and has direct access to that object's methods and fields. Also, because an inner class is associated with an instance, it cannot define any static members itself. To instantiate an inner class, you must first instantiate the outer class.
  * Local classes: An inner class within the body of a method.
  * Anonymous classes: An inner class within the body of a method without naming the class.
    * The new operator
    * The name of an interface to implement or a class to extend
    * Parentheses that contain the arguments to a constructor
    * A body, which is a class declaration body
## Lambda Expressions
## When to Use Nested Classes, Local Classes, Anonymous Classes, and Lambda Expressions
* Local class: Use it if you need to create more than one instance of a class, access its constructor, or introduce a new, named type.
* Anonymous class: Use it if you need to declare fields or additional methods.
* Lambda expression: Use it if you are encapsulating a single unit of behavior that you want to pass to other code; Use it if you need a simple instance of a functional interface and none of the preceding criteria apply.
* Nested class: Use it if your requirements are similar to those of a local class, you want to make the type more widely available, and you don't require access to local variables or method parameters.
## Enum Types
An enum type is a special data type that enables for a variable to be a set of predefined constants.
