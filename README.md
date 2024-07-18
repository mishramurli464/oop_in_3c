# oop_in_#c

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

    // Properties (to provide controlled access to fields/getter and setter is called as property)
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

![image](https://github.com/user-attachments/assets/d4701803-4975-4022-bd9a-eec574012873)

### Access Modifirs  
Constructors in C# are special methods that are invoked when an object of a class is created. They are used to initialize the object’s state, typically by setting the values of its fields or properties.   
**Types of Constructors**
1)Default Constructor   
A default constructor is one that takes no arguments. If no constructor is explicitly defined, the C# compiler automatically provides a default constructor that initializes the object’s   
fields to their default values.   
```c#
public class Person
{
    public string Name;
    public int Age;

    // Default constructor
    public Person()
    {
        Name = "Unknown";
        Age = 0;
    }
}

public class Program
{
    public static void Main()
    {
        Person person = new Person();
        Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
    }
}

```
2)Parameterized Constructor  
A parameterized constructor is one that takes arguments, allowing you to initialize the object with specific values.  
```c#
public class Person
{
    public string Name;
    public int Age;

    // Parameterized constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}

public class Program
{
    public static void Main()
    {
        Person person = new Person("Alice", 30);
        Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
    }
}
```
3)Static Constructor   
A static constructor is used to initialize static members of a class. It is called automatically before the first instance is created or any static members are accessed.  
```c#
public class Person
{
    public static int Population;

    // Static constructor
    static Person()
    {
        Population = 1000;
    }

    public string Name;
    public int Age;

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}

public class Program
{
    public static void Main()
    {
        Console.WriteLine($"Population: {Person.Population}");
        Person person = new Person("Alice", 30);
    }
}

```

## 2) Inheritance 
Inheritance allows a class to inherit fields and methods from another class. The class that inherits is called a derived class, and the class it inherits from is called a base class.  
(ex- vehicle- car,bus,bike)

```c#
using System;

// Base class
public class Vehicle
{
    public string Brand { get; set; }
    public int Year { get; set; }

    public Vehicle(string brand, int year)
    {
        Brand = brand;
        Year = year;
    }

    public void Start()
    {
        Console.WriteLine($"{Brand} is starting.");
    }

    public void Stop()
    {
        Console.WriteLine($"{Brand} is stopping.");
    }
}

// Derived class: Car
public class Car : Vehicle
{
    public int NumberOfDoors { get; set; }

    public Car(string brand, int year, int numberOfDoors)
        : base(brand, year)
    {
        NumberOfDoors = numberOfDoors;
    }

    public void Honk()
    {
        Console.WriteLine($"{Brand} is honking.");
    }
}

// Derived class: Bike
public class Bike : Vehicle
{
    public bool HasCarrier { get; set; }

    public Bike(string brand, int year, bool hasCarrier)
        : base(brand, year)
    {
        HasCarrier = hasCarrier;
    }

    public void RingBell()
    {
        Console.WriteLine($"{Brand} is ringing the bell.");
    }
}

// Derived class: Bus
public class Bus : Vehicle
{
    public int SeatingCapacity { get; set; }

    public Bus(string brand, int year, int seatingCapacity)
        : base(brand, year)
    {
        SeatingCapacity = seatingCapacity;
    }

    public void OpenDoors()
    {
        Console.WriteLine($"{Brand} bus is opening its doors.");
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        // Create an instance of the Car class
        Car car = new Car("Toyota", 2021, 4);

        // Access base class methods and properties
        car.Start();
        car.Stop();

        // Access derived class method
        car.Honk();

        // Create an instance of the Bike class
        Bike bike = new Bike("Honda", 2019, true);

        // Access base class methods and properties
        bike.Start();
        bike.Stop();

        // Access derived class method
        bike.RingBell();

        // Create an instance of the Bus class
        Bus bus = new Bus("Mercedes", 2020, 50);

        // Access base class methods and properties
        bus.Start();
        bus.Stop();

        // Access derived class method
        bus.OpenDoors();
    }
}

```


