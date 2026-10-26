# C# Fundamentals and OOP Exercises

![C#](https://img.shields.io/badge/C%23-239120?logo=csharp&logoColor=white)
![.NET](https://img.shields.io/badge/.NET%20Core-3.1-512BD4)

Small console projects written while learning **C#** in January 2021. They build up from methods and collections to the core ideas of **object-oriented programming**: classes and properties, inheritance, interfaces, polymorphism and programming against abstractions.

---

## Projects

| Project | Topic | What it shows |
|---|---|---|
| [`Methods`](Methods) | Methods, arrays | A `Product` class, an array of products iterated with `foreach`, and a `ProductManager` with `Add` / `Update` methods |
| [`Collections`](Collections) | Collections | Creating a `List<string>`, reading by index and adding items |
| [`OOP1`](OOP1) | Classes and objects | Properties, two ways of creating objects (property assignment and object initializer), passing objects to a manager class |
| [`OOP2`](OOP2) | Inheritance | `Customer` base class with `IndividualCustomer` and `CoorporateCustomer` subclasses; a manager that accepts the base type |
| [`OOP3`](OOP3) | Interfaces and polymorphism | Loan application example built on interfaces (details below) |

## OOP3: loan application with interfaces

The most complete example models a bank's loan application flow with two independent abstractions:

```
IKrediManager (loan type)          ILoggerService (logging)
 ├── IhtiyacKrediManager  (personal)  ├── DatabaseLoggerService
 ├── TasitKrediManager    (vehicle)   └── FileLoggerService
 └── KonutKrediManager    (mortgage)

BasvuruManager (application service)
 ├── BasvuruYap(IKrediManager, ILoggerService)
 │     → calculates the loan and logs the application
 └── KrediOnBilgilendirmesiYap(List<IKrediManager>)
       → runs a pre-information calculation for several loan types
```

`BasvuruManager` depends only on the interfaces, so any loan type can be combined with any logger without changing its code. This is the **dependency inversion** idea in its simplest form, and the basis for the layered and dependency-injected designs used in later projects.

## Running a project

Requires the [.NET SDK](https://dotnet.microsoft.com/download). The projects target .NET Core 3.1; to run them on a current SDK, change `<TargetFramework>` in the `.csproj` to your installed version (for example `net8.0`).

```bash
git clone https://github.com/eceakin/Methods.git
cd Methods
dotnet run --project OOP3
```

Or open `Methods.sln` in Visual Studio and set the project you want as the startup project.

> **Note:** the `Methods` project is unfinished and does not compile yet: `ProductManager.Add` has an incomplete `Console.WriteLine` call, and `Program` calls `Add()` without a product. The other four projects are independent and can be run on their own.

## Tech stack

C# · .NET Core 3.1 · Console applications
