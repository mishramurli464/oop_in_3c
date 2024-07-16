# oop_in_3c

Object-Oriented Programming (OOP) is a paradigm that uses objects and classes to design and structure code. C# is inherently an object-oriented language and supports all OOP principles, including encapsulation, inheritance, and polymorphism.   
## 1) Encapsulation
Encapsulation is the concept of wrapping data (fields) and methods (functions) together as a single unit. In C#, you achieve this using classes and access modifiers.  
without field there is no use of method similarly viceversa.
```c#
using System;

public class Person
{
    // Fields (private to encapsulate data)
    private string name;
    private int age;

    // Properties (to provide controlled access to fields)
    public string Name
    {
        get { return name; }
        set { name = value; }
    }

    public int Age
    {
        get { return age; }
        set
        {
            if (value >= 0)
            {
                age = value;
            }
        }
    }

    // Constructor
    public Person(string name, int age)
    {
        this.name = name;
        this.age = age;
    }

    // Method
    public void Introduce()
    {
        Console.WriteLine($"Hello, my name is {name} and I am {age} years old.");
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        // Create a new Person object
        Person person = new Person("Alice", 30);
        person.Introduce();

        // Access and modify properties
        person.Name = "Bob";
        person.Age = 35;
        person.Introduce();
    }
}

```

```

Modifier	Accessible Within Class	Accessible Within Derived Class	Accessible Within Assembly	Accessible Outside Assembly
public	Yes	Yes	Yes	Yes
private	Yes	No	No	No
protected	Yes	Yes	No	No
internal	Yes	Yes	Yes	No
protected internal	Yes	Yes	Yes	No
private protected	Yes	Yes	No	No

```
