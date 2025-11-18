# Store and Retrieve Data Using Literal and Variable Values in C#

This challenge will be partially completed on the Microsoft Learn platform. Follow these instructions to complete the challenge:

1. Go to [https://learn.microsoft.com/training/modules/csharp-literals-variables/](https://learn.microsoft.com/training/modules/csharp-literals-variables/) and complete all the tasks for the "Store and Retrieve Data Using Literal and Variable Values in C#" module. This is **required** to earn the "Write Your First Code Using C#" trophy on Microsoft Learn, and qualify for the certification exam.

# Store and retrieve data using literal and variable values in C#

Use data in your applications by creating literal values and variable values of different data types.

## Learning objectives

After you complete this module, you'll be able to:

- Create literal values for five basic data types
    
- Declare and initialize variables
    
- Retrieve and set values in variables
    
- Allow the compiler to determine the data type for your variable when initializing

## Prerequisites

- Must understand basic C# syntax rules
    
- Must understand how to use Console.WriteLine()

## This module is part of these learning paths

- [Write your first code using C# (Get started with C#, Part 1)](https://learn.microsoft.com/training/paths/get-started-c-sharp-part-1/)

# Introduction

- 3 minutes

Many of the applications that you'll build in C# will require you to work with data. Sometimes that data will be hard-coded in your application. Hard-coded values are values that are constant and unchanged throughout the execution of the program. For example, you may need to print a message to the user when some operation succeeds. A "success" message would likely be the same every time the application is executed. This hard-coded value can also be called a constant, or a literal value.

Suppose you want to display a formatted message to the end user containing different types of data. The message would include hard-coded strings combined with information your app collects from the user. To display a formatted message, you'll need to create both hard-coded values and define variables that can store data of a certain type, whether numeric, alphanumeric, and so on.

In this module, you'll create literal values that contain different data types. You'll create variables that can hold certain data types, set those variables with a value, then retrieve those values later in code. And finally, you'll learn how you can simplify your code by allowing the compiler to shoulder some of the work.

By the end of this module, you'll be able to create literal values and store and retrieve data in variables.

## Learning objectives

In this module, you will:

- Create literal values for five basic data types
- Declare and initialize variables
- Retrieve and set values in variables
- Allow the compiler to determine the data type for your variable when initializing

## Prerequisites

- Must understand basic C# syntax rules
- Must understand how to use [Console.WriteLine()](https://learn.microsoft.com/en-us/dotnet/api/system.console.writeline#system-console-writeline)
- Beginner level experience with a .NET editor

# Exercise - Print literal values

- 10 minutes

In this exercise, you'll print messages containing other types of data and learn why data types are so important in C#.

## What is a literal value?

A literal value is a constant value that never changes. Previously, you displayed a literal string to the output console. In other words, you literally wanted that string of alphanumeric characters `H`, `e`, `l`, `l`, `o`, and so on, displayed in the output console.

Use the string data type whenever you have alphanumeric words, phrases, or data for presentation, not calculation. What other kinds of literal data can you print to output?

## Exercise - Print different literal data types

There are many data types in C#. But as you're getting started, you only need to know about five or six data types since they cover most scenarios. Let's display a literal instance of data type to output.

A C# code editor is available to use directly in the browser: [C# Code Editor](https://microsoftlearning.github.io/c-sharp-minor/). This editor provides a lightweight environment for writing, running, and testing C# code without needing to install any software on your local computer.

### Use character literals

If you only wanted a single alphanumeric character printed to screen, you could create a **char literal** by surrounding one alphanumeric character in single quotes. The term `char` is short for _character_. In C#, this data type is officially named "char", but frequently referred to as a "character".

1. Open the [C# Code Editor](https://microsoftlearning.github.io/c-sharp-minor/) in a new browser window or tab.
    
    You can position the browser windows side-by-side so that you can refer to these instructions while you work in the C# Code Editor.
    
1. Add the following line of code in the code editor:
    
    ```C#
    Console.WriteLine('b');
    ```
    
2. Observe the code you entered.
    
    Notice that the letter `b` is surrounded with single quotation marks `'b'`. Single quotes create a character literal. Recall that using double quotation marks creates a `string` data type.
    
1. Press the ▶️ Run button to run your code. You should see the following result in the output window:
    
    ```
    b
    ```
    

If you enter the following code:

```C#
Console.WriteLine('Hello World!');
```

You would get the following error:

```
CS1012: Too many characters in character literal
```

Notice the single quotation marks surrounding `Hello World!`. When you use single quotation marks, the C# compiler expects a single character. However, in this case, the character literal syntax was used, but 12 characters were supplied instead!

Just like the `string` data type, you use `char` whenever you have a single alphanumeric character for presentation (not calculation).

### Use integer literals

If you want to display a numeric whole number (no fractions) value in the output console, you can use an **int literal**. The term `int` is short for integer, which you may recognize from studying math. In C#, this data type is officially named "int", but frequently referred to as "integer". An `int` literal requires no other operators like the `string` or `char`.

1. Add the following line of code in the code editor:
    
    ```C#
    Console.WriteLine(123);
    ```
    
2. Press the ▶️ Run button to run your code. You should see the following result in the output console:
    
    ```
    123
    ```
    
![](https://i.imgur.com/CrGBL1n.png)

### Use floating-point literals

A floating-point number is a number that contains a decimal, for example 3.14159. C# supports three data types to represent decimal numbers: `float`, `double`, and `decimal`. Each type supports varying degrees of precision.

```
Float Type    Precision
----------------------------
float         ~6-9 digits
double        ~15-17 digits
decimal        28-29 digits
```

Here, precision reflects the number of digits past the decimal that are accurate.

1. Add the following line of code in the code editor:
    
    ```C#
    Console.WriteLine(0.25F);
    ```
    
    To create a `float` literal, append the letter `F` after the number. In this context, the `F` is called a _literal suffix_. The literal suffix tells the compiler you wish to work with a value of `float` type. You can use either a lower-case `f` or upper-case `F` as the literal suffix for a `float`.
    
2. Press the ▶️ Run button to run your code. You should see the following result in the output console:

    ```
    0.25
    ```

![](https://i.imgur.com/FcWHSYW.png)

>   Notice that the `float` data type is the least precise, so it's best to use this data type for fixed fractional values to avoid unexpected computation errors.

3. Add the following line of code in the code editor:

    ```C#
    Console.WriteLine(2.625);
    ```
    
    To create a `double` literal, just enter a decimal number. The compiler defaults to a `double` literal when a decimal number is entered without a literal suffix.
    
4. Press the ▶️ Run button to run your code. You should see the following result in the output window:

    ```
    2.625
    ```
    
5. Add the following line of code in the code editor:

    ```C#
    Console.WriteLine(12.39816m);
    ```
    
    To create a decimal literal, append the letter `m` after the number. In this context, the `m` is called a _literal suffix_. The literal suffix tells the compiler you wish to work with a value of `decimal` type. You can use either a lower-case `m` or upper-case `M` as the literal suffix for a `decimal`.
    
6. Press the ▶️ Run button to run your code. You should see the following result in the output console:

    ```
    12.39816
    ```
    

### Use Boolean literals

If you wanted to print a value representing either `true` or `false`, you could use a **bool literal**.

The term `bool` is short for _Boolean_. In C#, they're officially referred to as "bool", but often developers use the term "Boolean".

1. Add the following lines of code in the code editor:

    ```C#
    Console.WriteLine(true);
    Console.WriteLine(false);
    ```
    
2. Press the ▶️ Run button to run your code. You should see the following result in the output console:

    ```
    True
    False
    ```
    
![](https://i.imgur.com/U6fhv09.png)

The `bool` literals represent the idea of truth and falsehood. You'll use `bool` values extensively when you start to add decision logic to your applications. You'll evaluate expressions to see whether the expression is true or false.

### Why emphasize data types?

Data types play a central role in C#. In fact, the emphasis on data types is one of the key distinguishing features of C# compared to other languages like JavaScript. The designers of C# believed they can help developers avoid common software bugs by _enforcing_ data types. You'll see this concept unfold as you learn more about C#.

### Data types define capabilities

Earlier, you saw that `string`s and `char`s are used for "presentation, not calculation". If you need to perform a mathematical operation on numeric values, you should use an `int` or `decimal`. If you have data that is used for presentation or text manipulation, you should use a `string` or `char` data type.

Suppose you needed to collect data from a user, like a phone number or postal code. Depending on the country/region where you live, that data may consist of numeric characters. However, since you rarely perform mathematical calculations on phone numbers and postal codes, you should prefer to use a `string` data type when working with them.

The same can be said of `bool`. If you need to work with the words `"true"` and `"false"` in your application, you would use a `string`. However, if you need to work with the concept of `true` or `false` when performing an evaluation, you use a `bool`.

It's important to know that these values may look like their string literal equivalents. In other words, you may think these statements are the same:

```C#
Console.WriteLine("123");
Console.WriteLine(123);

Console.WriteLine("true");
Console.WriteLine(true);
```

![](https://i.imgur.com/Xz48n7v.png)

However, it's only the displayed output that appears to be similar. The fact is that the kinds of things you can do with the underlying `int` or `bool` will be different than their `string` equivalent.
## Recap

The main takeaway is that there are many data types, but you'll focus on just a few for now:

- `string` for words, phrases, or any alphanumeric data for presentation, not calculation
- `char` for a single alphanumeric character
- `int` for a whole number
- `decimal` for a number with a fractional component
- `bool` for a `true`/`false` value

# Declare variables

- 6 minutes

A literal is _literally_ a hard-coded value. Hard-coded values are values that are constant and unchanged throughout the execution of the program. However, most applications will require you to work with values that you don't know much about ahead of time. In other words, you'll need to work with data that comes from users, from files, or from across the network.

When you need to work with data that isn't hard-coded, you'll declare a variable.

## What is a variable?

A **variable** is a container for storing a type of value. Variables are important because their values can change, or vary, throughout the execution of a program. Variables can be assigned, read, and changed. You use variables to store values that you intend to use in your code.

A variable name is a human-friendly label that the compiler assigns to a memory address. When you want to store or change a value in that memory address, or whenever you want to retrieve the stored value, you just use the variable name you created.

### Declare a variable

To create a new variable, you must first declare the data type of the variable, and then give it a name.

```C#
string firstName;
```

In this case, you're creating a new variable of type `string` called `firstName`. From now on, this variable can only hold string values.

You can choose any name as long as it adheres to a few C# syntax rules for naming variables.

### Variable name rules and conventions

A software developer once famously said "The hardest part of software development is naming things." Not only does the name of a variable have to follow certain syntax rules, it should also be used to make the code more human-readable and understandable. That's a lot to ask of one line of code!

Here's a few important considerations about variable names:

- Variable names can contain alphanumeric characters and the underscore character. Special characters like the hash symbol `#` (also known as the number symbol or pound symbol) or dollar symbol `$` are not allowed.
- Variable names must begin with an alphabetical letter or an underscore, not a number.
- Variable names are case-sensitive, meaning that `string Value;` and `string value;` are two different variables.
- Variable names must **not** be a C# keyword. For example, you cannot use the following variable declarations: `decimal decimal;` or `string string;`.

There are coding conventions that help keep variables readable and easy to identify. As you develop larger applications, these coding conventions can help you keep track of variables among other text.

Here are some coding conventions for variables:

- Variable names should use **camel case**, which is a style of writing that uses a lower-case letter at the beginning of the first word and an upper-case letter at the beginning of each subsequent word. For example, `string thisIsCamelCase;`.
- Variable names should begin with an alphabetical letter. Developers use the underscore for a special purpose, so try to not use that for now.
- Variable names should be descriptive and meaningful in your app. Choose a name for your variable that represents the kind of data it will hold.
- Variable names should be one or more entire words appended together. Don't use contractions or abbreviations because the name of the variable (and therefore, its purpose) may be unclear to others who are reading your code.
- Variable names shouldn't include the data type of the variable. You might see some advice to use a style like `string strValue;`. That advice is no longer current.

The example `string firstName;` follows all of these rules and conventions, assuming you want to use this variable to store data that represents someone's first name.

### Variable name examples

Here's a few examples of variable declarations using the data types you learned about thus far:

```C#
char userOption;

int gameScore;

decimal particlesPerMillion;

bool processedCustomer;
```

## Recap

Here's what you've learned so far about variables:

- Variables are temporary values you store in the computer's memory.
- Before you can use a variable, you have to declare it.
- To declare a variable, you first select a data type for the kind of data you want to store, and then give the variable a name that follows the rules.

Now that you know how to declare a variable, let's learn how to set, retrieve, and initialize the value of a variable.

# Exercise - Setting and getting values from variables

- 10 minutes

Because variables are temporary storage containers for data, they're meant to be _written to_ and _read from_. You'll get a chance to do both in the following exercise.

## Exercise - Working with variables

In this exercise, you'll declare a variable, assign it a value, retrieve its value, and more.

### Create your first variable

First, let's clear the code you wrote previously and create a variable.

1. Select all of the code in the [C# Code Editor](https://microsoftlearning.github.io/c-sharp-minor/), and press Delete or Backspace to delete it.
    
2. Enter the following code in the code editor:
    
    ```C#
    string firstName;
    firstName = "Bob";
    ```

![](https://i.imgur.com/r2Uoixa.png)

To declare a variable, you enter the data type you want to use followed by a name for the variable. To assign a value to a variable, you use the _assignment operator_, which is a single equals character `=`.

 > Note
 >    Assigning a value is also referred to as "setting the variable", or simply, a "set" operation.

### Improperly assign a value to a variable

It's important to notice that assignment happens from right to left. In other words, the C# compiler must first understand the value on the right side of the assignment operator, then it can perform the assignment to the variable on the left side of the assignment operator. If you reverse the order, you'll confuse the C# compiler.

1. Modify the code you wrote to match the following code:
    
    ```C#
    string firstName;
    "Bob" = firstName;
    ```
    
2. Now, run the code. You'll see the following error in the output console:

    ```
    CS0131: The left-hand side of an assignment must be a variable, property or        indexer
    ```


### Improperly assign a value of the incorrect data type to the variable

You learned that C# was designed to enforce types. When you're working with variables, _enforcing types_ means you can't assign a value of one data type to a variable declared to hold a different data type.

1. Modify the code you wrote to match the following code:
    
    ```C#
    int firstName;
    firstName = "Bob";
    ```
    
2. Now, run the code. You'll see the following error in the output console:
    
    Output
    
    ```
    CS0029: Cannot implicitly convert type 'string' to 'int'
    ```
    

The error message hints at what the C# compiler tries to do behind the scenes. It tried to "implicitly convert" the string "Bob" to be an int value; however, that is impossible. Even so, C# tried to do the conversion but fails since there's no numeric equivalent for the word "Bob".

You'll learn more about implicit and explicit type conversion later. For now, just remember that a variable can only hold values matching its specified data type.

## Retrieve a value you stored in the variable

To retrieve a value from a variable, you just use the name of the variable. This example will set a variable's value, then retrieve that value and display it in the console.

1. Modify the code you wrote to match the following code:
    
    ```C#
    string firstName;
    firstName = "Bob";
    Console.WriteLine(firstName);
    ```
    
2. Now, run the code. You'll see the following result in the output console:
    
    Output

![](https://i.imgur.com/Rd9l8JZ.png)

```
Bob
```


Retrieving a value from a variable is also referred to as "getting the variable", or simply, a "get" operation.

As you write lines of code, you'll see that the compiler is checking your code and spotting possible mistakes. The compiler is a great tool to help you get code correct sooner. Now that you're familiar with different types of errors, you can quickly fix mistakes with the help of the compiler's error messages.

### Reassign the value of a variable

You can reuse and reassign the variable as many times as you want. This example illustrates that idea.

1. Modify the code you wrote to match the following code:
    
    ```C#
    string firstName;
    firstName = "Bob";
    Console.WriteLine(firstName);
    firstName = "Liem";
    Console.WriteLine(firstName);
    firstName = "Isabella";
    Console.WriteLine(firstName);
    firstName = "Yasmin";
    Console.WriteLine(firstName);
    ```
    
1. Now, run the code. You'll see the following result in the output console:
    
    ```
    Bob
    Liem
    Isabella
    Yasmin
    ```
    

### Initialize the variable

You must _set_ a variable to a value before you can _get_ the value from the variable. Otherwise, you'll see an error.

1. Modify the code you wrote to match the following code:
    
    ```C#
    string firstName;
    Console.WriteLine(firstName);
    ```
    
1. Now, run the code. You'll see the following result in the output console:
    
    ```
    CS0165: Use of unassigned local variable 'firstName'
    ```
    

To avoid the possibility of an unassigned local variable, it is recommended that you set the value as soon as possible after you declare it.

In fact, you can perform both the declaration and setting the value of the variable in one line of code. This technique is called _initializing_ the variable.

1. Modify the code you wrote to match the following code:

    ```C#
    string firstName = "Bob";
    Console.WriteLine(firstName);
    ```
    
2. Now, run the code. You should see the following output:
    
    ```
    Bob
    ```
    

## Recap

Here's what you've learned about working with variables so far:

- You must assign (set) a value to a variable before you can retrieve (get) a value from a variable.
- You can initialize a variable by assigning a value to the variable at the point of declaration.
- Assignment happens from right to left.
- You use a single equals character as the assignment operator.
- To retrieve the value from the variable, you merely use the variable's name.

