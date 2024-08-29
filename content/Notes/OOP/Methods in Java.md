---
title: Methods in Java
draft: false
tags:
  - Java
  - Notes
  - OOP
description:
---
# Methods
>[!DEFINITION] Methods
>They're just functions but inside of classes. 
>>[!DEFINITION] Function 
>They're statements group together to perform a task.

Since methods are basically functions, they posses the same benefits and rules:
- Reusability
- Easier to debug
- One function one purpose
- ...and more!

Since [[Introduction to OOP#^593cb2|Java is purely OOP]], functions will be referred to as methods.

A method in Java is constructed with the formula:<br>
`<access modifier> <datatype> <name>(<parameters>){}`
```java
public static int methodName(int x, int y){}
 ```
>[!Reminder] Static methods
>[[Introduction to OOP]]

**Method signature** refers to the *name(parameters)* of the method. 
```java
sum(int x, int y)
```
**Formal Parameters** refers to the variables defined in the method headers. ^a3e637
```java 
(int x, int y)
```
Methods may or may not return a value. If it does not, `void`keyword has to be specified.
```java
public static void hello(){
	System.out.println("Hello everyone");
}
```
When the return value type is specified, the method **must** return a value. If not done correctly, such issue can arise.

*Snippet A: Improper return*
```java
public static int sign(int n){
	if (n > 0)
		return 1;
	else if (n == 0)
		return 0;
	else if (n < 0)
		return -1;
}
```
When the code is written this way, Java will think it is possible that the function may not return anything. Since there is no `else` statement, if every condition is evaluated to be `false`, the method will not return anything. 

To fix this, just change the last `else if` statement into `else`

*Since Java is a language that only uses OOP paradigm, wouldn't creating an object each time you want to access a method be a hassle?*<br>
Yes, that's why `static` keywords are introduced. It allows user to call methods without creating an instance.

```java
// if the method is a public static method
className.methodName(parameters);

// if the object is a public static object
static myClass myVeryOwnClass = new myClass();

className.objectName.methodName(parameters);

// instance method
objectName.methodName(parameters); 
```
If a method is called within the same class it is defined, it can be called directly. 
```java
public class Main{
	public static void main(String[] args){
		int a = 10;
		int b = c;
		int c = max(1,b);
		System.out.printf("%d is the max of the two", c);
	}
	private int max(){
		return (a>b) ? a : b; 
	}
}
```
# Scope of variables
>[!Definition] Local Variable
>A local variable is a variable that is declared inside a method/scope (e.g. *loops*) and is destroyed when the program leaves the scope. 

*Snippet B: accessing variable outside its scope*
```java
public static void main(String[] args){
	{
		int x = 5;
		System.out.println(x);
	}
	System.out.println(x); // error
}
```
*Snippet C: Declaring variable twice*
```java
public static void main(String[] args){
	{
		int x = 5;
		System.out.println(x);
	}
	{
		int x = 5;
		System.out.println(x);
		{
			int x = 5;
		}
	}
}
```
# Passing arguments
When passing an argument to a method, the order of the variables in the [[Methods in Java#^a3e637|formal parameters]] must match in order.

Since Java is a safer language than C++, there is no manual memory management - everything is done automatically. 

Primitive datatype are passed by value while objects are passed by reference. 

This means that any changes made inside a function does not affect the original variable. 

## Method overloading
Just like in C++, method overloading occurs when more than one functions have the same name but different signatures.

*Method 1: Changing the number of arguments*
```java
static int add(int a, int b){ return a+b; }
static int add(int a, int b, int c){ return a+b+c; }
```
*Method 2: Changing the datatype of the arguments*
```java
static int add(int a, int b, int c){ return a+b; }
static double add(double a, double b, double c){ return a+b+c; }
```

>[!Warning] Changing return type
>You cannot achieve method overloading by simply changing the return type.
>```java
>static int add(int a, int b){ return a+b; }
>// error
>static double add(int a, int b){ return a+b; }
>```

>[!WARNING] Ambiguous Invocation
>Ambiguous Invocation can happen if method overloading is done properly; two or more methods have the same name and *somewhat similar* signature.
>```java
>public double max(double x, int y){}
>public double max(int x, double y){}
>max(1,2);
>```
>In this case, since 1 and 2 can be [[Introduction to Java#Casting|widened]] to `double`, JAVA does not know which one to call.

# See next
[[]]