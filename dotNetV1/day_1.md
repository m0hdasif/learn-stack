# **Day 1: Introduction to .NET, C#, and Setting Up Your Development Environment**

---

## **1.1 What is .NET and C#?**

### **.NET Framework**
- **.NET** is a **cross-platform** framework developed by Microsoft that is used for building various types of applications, such as web, desktop, cloud, and mobile applications.
- It's open-source and can be used on **Windows, macOS, and Linux**.

### **C# Language**
- **C#** (pronounced "C-sharp") is a modern, **object-oriented** programming language created by Microsoft.
- It is commonly used for developing applications in the **.NET ecosystem**.
- C# is known for its simplicity, strong typing, and rich library support.

---

## **1.2 Setting Up Your Development Environment**

### **Step 1: Install .NET SDK**
- Go to the official [Download .NET](https://dotnet.microsoft.com/download) page.
- Download and install the latest **.NET SDK** (e.g., .NET 6 or .NET 7).
- The SDK includes everything you need to develop, build, and run .NET applications.

### **Step 2: Install Visual Studio or VS Code**
- **Visual Studio** (Windows/macOS): A full-featured IDE with built-in support for C# and .NET.
- **Visual Studio Code** (Cross-platform): A lightweight code editor with C# support via the **C# extension**.

> **Tip**: Visual Studio is recommended for beginners due to its rich features like debugging, IntelliSense, and built-in project templates.

---

## **1.3 Creating Your First C# Program**

Let’s create a basic **console application** to get started.

### **Step 1: Create a New Console Application**
Open your terminal/command prompt and run:
```bash
dotnet new console -n HelloWorldApp
```

### **Step 2: Explore the Program.cs File
- Open the Program.cs file in your project folder (HelloWorldApp), and you should see the following code:
```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Hello, World!");
    }
}
```

### **Step 3: Run Your Application
- Navigate to the HelloWorldApp directory using the terminal or command prompt:
```bash
cd HelloWorldApp
dotnet run
```
This should print Hello, World! to the console.

## **1.4 C# Basics: Syntax & Best Practices**

### **Variables and Data Types**
C# is **statically typed**, which means you have to declare the type of each variable. Here are some basic types:

```csharp
int age = 25;               // Integer
double price = 99.99;       // Double for floating-point numbers
bool isActive = true;       // Boolean value (true/false)
string name = "Alice";      // String (sequence of characters)
char initial = 'A';         // Single character
```
### Constant Variables

```csharp
const int maxRetries = 5;   
```

### String Interpolation

```csharp

string firstName = "John";
int age = 30;
Console.WriteLine($"My name is {firstName}, and I am {age} years old.");
```

### Variable Naming Conventions
- CamelCase: For local variables and method parameters.
Example: int totalAmount
- PascalCase: For classes, methods, and properties.
Example: public class Person { public string Name { get; set; } }
- Uppercase: For constants.
Example: const int MAX_RETRIES = 3;

## **1.5 Object-Oriented Programming (OOP) Basics in C#**

C# is **object-oriented**, meaning that everything is built around **objects** and **classes**.

### **Class and Object Example**

#### Class Definition
```csharp
public class Person
{
    public string Name { get; set; }  // Property
    public int Age { get; set; }      // Property

    // Method
    public void Introduce()
    {
        Console.WriteLine($"Hello, my name is {Name} and I am {Age} years old.");
    }
}
// Creating an Object (Instance of the Class)
Person person1 = new Person();  // Creating an instance of the Person class
person1.Name = "Alice";
person1.Age = 28;
person1.Introduce();  // Output: Hello, my name is Alice and I am 28 years old.
```

## **1.6 New C# Features (C# 9, C# 10, C# 11)**

### **1.6.1 Init-Only Properties (C# 9)**
You can create properties that can only be set during initialization (using `init`), but not modified later.

```csharp
public class Product
{
    public string Name { get; init; }
    public double Price { get; init; }
}

var product = new Product { Name = "Laptop", Price = 1200 };
// product.Name = "Tablet"; // Error: Cannot modify after initialization
```

### **1.6.2 Records (C# 9)**

Records are a special type of class that is **immutable by default** and provides built-in **value-based equality**.

```csharp
public record Person(string Name, int Age);

var person1 = new Person("Alice", 30);
var person2 = new Person("Alice", 30);

Console.WriteLine(person1 == person2);  // Output: True
```
### **1.6.3 Top-Level Statements (C# 9)**

You can omit the `Main` method for simple applications, reducing boilerplate code.

```csharp
Console.WriteLine("Hello, World!");  // No need for Main() method or class
```
### **1.6.4 Nullable Reference Types (C# 8/9)**

Enable **nullable reference types** to make your code more **null-safe**.

```csharp
#nullable enable

public class Person
{
    public string? Name { get; set; } // Nullable reference type
    public int Age { get; set; }
}
```
#### Note: When #nullable enable is used, the compiler will warn you about potential null reference


Simplifies namespaces by allowing them to span the entire file, eliminating the need for curly braces.

```csharp
namespace MyApp;  // No curly braces needed

public class Person
{
    public string Name { get; set; }
}
```
### Commonly Used Namespaces in C#:
- System: Contains fundamental classes like String, Console, Math, etc.
- System.Collections: Contains collection types like List, Dictionary, etc.
- System.IO: Provides classes for file operations like FileStream, StreamReader, etc.
- System.Threading: Provides classes for working with threads and asynchronous programming.
#### **Note**: C#: Namespaces do not require a specific file structure. You can organize your files in directories as needed, but the namespace itself does not depend on the folder structure.

#### Note: C#: Namespaces can be nested within each other, and you can have multiple namespaces in the same file.
```csharp
namespace MyApp
{
    namespace Models
    {
        public class User { }
    }
}
```
#### Note: C#: Namespaces do not directly control visibility. Visibility is controlled by access modifiers (public, private, internal, etc.). Namespaces simply group types together.

### Nested Namespace like this
```csharp
namespace MyApp.UI.Views
{
    public class MainView { }
}

namespace MyApp.UI.Controllers
{
    public class MainController { }
}
```

### **1.7 Use of `var`**

### **When to Use `var` in C#**
- **Use `var` when the type is clear** from the right-hand side of the assignment or when the type is too long to type out.
- **Avoid `var` when the type is not obvious**, as it could lead to confusion about what type is being used.

### **Advantages of Using `var`**
1. **Cleaner Code**: Reduces redundancy, making code more concise, especially when the type is already implied.
2. **Easy Maintenance**: If the type on the right-hand side changes, `var` ensures that the variable will always use the new type without needing to manually adjust the left-hand side.

### **Examples of When to Use `var`**:

#### **1. When the Type is Clear**:
```csharp
var number = 10;
var user = new User()
var query = from user in users
            where user.Age > 18
            select user;   // linq queries

```

#### **2 Not recommended because the type is unclear
```csharp
var result = GetUserData(); 
```

## **1.8 Try-Catch for Exception Handling**

### **What is Exception Handling?**
Exception handling in C# is done using `try`, `catch`, and `finally` blocks. It helps ensure that your program continues running smoothly even when errors occur.

### **Example of Try-Catch**:
```csharp
try
{
    int result = 10 / 0;  // Division by zero will cause an exception
}
catch (DivideByZeroException ex)
{
    Console.WriteLine("Error: " + ex.Message);  // Handles the division by zero exception
}
finally
{
    Console.WriteLine("This block runs regardless of exceptions.");
}
```
#### Best Practices:
- Always handle specific exceptions first (e.g., DivideByZeroException).
- Avoid using catch (Exception ex) unless absolutely necessary, as it can catch unexpected errors.
- Use the finally block for cleanup actions such as closing files or releasing resources.

### 1.9 Collections
#### **1.9.1 Arrays**
Arrays are fixed-size collections of elements of the same type. The size of the array is defined when it's created and cannot be changed.

#### **Array Example**:
```csharp
int[] numbers = { 1, 2, 3, 4, 5 };
Console.WriteLine(numbers[0]);  // Output: 1
```

#### 1.9.2 **List**
A List<T> is a dynamic collection that can grow or shrink as needed. It's part of the System.Collections.Generic namespace.

```csharp
List<int> numbers = new List<int> { 1, 2, 3 };
numbers.Add(4);  // Adds an item to the list
numbers.RemoveAt(0);  // Removes the item at index 0
Console.WriteLine(numbers[0]);  // Output: 2
Console.WriteLine(numbers.Contains(3)) // True
```

#### 1.9.3 Dictionaries
A Dictionary<TKey, TValue> is a collection of key-value pairs, where each key is unique. It is part of the System.Collections.Generic namespace.

```csharp
Dictionary<string, string> capitals = new Dictionary<string, string>();
capitals.Add("USA", "Washington, D.C.");
capitals.Add("Canada", "Ottawa");
Console.WriteLine(capitals["USA"]);  // Output: Washington, D.C.

 // Create a dictionary with string keys and integer values
Dictionary<string, int> dictionary = new Dictionary<string, int>
{
    { "apple", 1 },
    { "banana", 2 },
    { "cherry", 3 }
};
Console.WriteLine(dictionary.ContainsKey("banana")) // Output: true
```

#### 1.9.4 Queue: Represents a first-in, first-out (FIFO) collection.
```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Queue<int> queue = new Queue<int>();

        // Enqueue elements
        queue.Enqueue(10);
        queue.Enqueue(20);
        queue.Enqueue(30);

        // Peek the front element
        Console.WriteLine("Peek: " + queue.Peek()); // Output: 10  and Throws an InvalidOperationException if the queue is empty.


        // Dequeue elements
        Console.WriteLine("Dequeue: " + queue.Dequeue()); // Output: 10 and Throws an InvalidOperationException if the queue is empty.

        Console.WriteLine("Dequeue: " + queue.Dequeue()); // Output: 20

        // Check if an item exists
        Console.WriteLine("Contains 30: " + queue.Contains(30)); // Output: True

        // Get the number of elements in the queue
        Console.WriteLine("Queue count: " + queue.Count); // Output: 1

        // Clear the queue
        queue.Clear();
        Console.WriteLine("Queue count after clearing: " + queue.Count); // Output: 0
        //ToArray() – Convert the queue to an array.
        //TrimExcess() – Optimize memory usage by trimming excess capacity.
    }
}

```
#### 1.9.5 Stack: Represents a last-in, first-out (LIFO) collection.

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Stack<int> stack = new Stack<int>();

        // Push elements onto the stack
        stack.Push(10);
        stack.Push(20);
        stack.Push(30);

        // Peek at the top element
        Console.WriteLine("Peek: " + stack.Peek()); // Output: 30
        //Throws an InvalidOperationException if the stack is empty.

        // Pop elements from the stack
        Console.WriteLine("Pop: " + stack.Pop()); // Output: 30
        Console.WriteLine("Pop: " + stack.Pop()); // Output: 20
        //Throws an InvalidOperationException if the stack is empty.

        // Check if an item exists
        Console.WriteLine("Contains 10: " + stack.Contains(10)); // Output: True

        // Get the number of elements in the stack
        Console.WriteLine("Stack count: " + stack.Count); // Output: 1

        // Clear the stack
        stack.Clear();
        Console.WriteLine("Stack count after clearing: " + stack.Count); // Output: 0

        //ToArray() – Convert the stack to an array.
        //TrimExcess() – Optimize memory usage by trimming excess capacity.
    }
}

```


### 1.10 File Handling
```csharp
using System.IO;

public class FileExample
{
    public void WriteToFile(string fileName, string content)
    {
        File.WriteAllText(fileName, content);  // Writing content to a file
    }

    public string ReadFromFile(string fileName)
    {
        return File.ReadAllText(fileName);  // Reading content from a file
    }

    public void AppendToFile(string filePath, string content)
    {
        File.AppendAllText(filePath, content);
       
    }

    public void DeleteFile(string filePath)
    {
    
        // Check if the file exists
        if (File.Exists(filePath))
        {
            File.Delete(filePath);
            Console.WriteLine("File deleted successfully.");
        }
        else
        {
            Console.WriteLine("File does not exist.");
        }
       
    }
}
```