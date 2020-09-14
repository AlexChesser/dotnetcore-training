## Introduction

This is a default dotnetcore project. The absoloute minumum amount of code you need to create a program.

## Key features

The `CSPROJ` file (C SHARP PROJECT) is required by the compiler so it knows what to build.

The critical portion of the application is the `static` function `Main` found in the `Program.cs` file. 

> **what is a static method?**    
> The static keyword denotes that a member variable, or method, can be accessed without requiring an instantiation of the class to which it belongs. In simple terms, it means that you can call a method, even if you've never created the object to which it belongs!

## What is in the CSPROJ?

```
<!-- create a project that uses .NET -->
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- make it a standalone EXE -->
    <OutputType>Exe</OutputType>
    <!-- use the netcoreapp3.1 framework -->
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

## What is in the program?
```
namespace CoreConsole {
    // this class can be named whatever you'd like
    class Program {
        // the only thing that really matters here is
        // the static void named Main taking an array string
        static void Main(string[] args) {
            System.Console.WriteLine("Hello World!");
        }
    }
}
```