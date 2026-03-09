# .NET and ASP.NET Core Interview Questions

## General .NET Framework & .NET Core
*   **What is .NET?** Can you give an overview of the .NET framework? 
*   **Core vs Framework:** How does the traditional .NET Framework compare to .NET Core and .NET 5/6/7/8?
*   **What is IL (Intermediate Language)?**
*   **What is CLR (Common Language Runtime)?**
*   **What is AOT (Ahead-of-Time) compilation?** Why use it?
*   **Languages:** What are the primary languages used in .NET? Which ones have you worked with, and which do you prefer?
*   **C# Features:** What are some of the new features introduced in the latest version of C#? Can you provide examples of how you've used them?

## ASP.NET Core
*   **DelegatingHandler:** What is `DelegatingHandler` in ASP.NET Core? How and when is it used?
*   **Controllers:** What is the difference between `Controller` and `ControllerBase`?
*   **Dependency Injection:** Explain Dependency Injection (DI) in ASP.NET Core. What are the service lifetimes (`Transient`, `Scoped`, `Singleton`)?
*   **Background Tasks:** What is a `BackgroundService` and how do you implement background tasks in ASP.NET Core?
*   **Request Pipeline:** What is the difference between a Filter and a Middleware?

## Entity Framework Core (EF Core)
*   **General Concepts:** What is Entity Framework Core?
*   **Relationships:** How do you configure a Many-to-Many relationship in EF Core?
*   **Tracking:** What is `AsNoTracking()` in Entity Framework and when should you use it?
    *   *Answer:* It tells EF Core not to track the returned entities in its Change Tracker. It improves performance and reduces memory usage for read-only queries because EF doesn't need to set up tracking information.
*   **LINQ Translation:** How does Entity Framework translate LINQ into SQL?
    *   *Answer:* EF Core uses a Query Provider that takes an Expression Tree (built from `IQueryable` LINQ methods), parses it, and translates it into a SQL syntax tree specific to the database provider (e.g., SQL Server, PostgreSQL). Then it executes the SQL and maps the resulting data reader back conceptually to C# objects.
*   **Joins in EF Core:** What type of SQL JOIN is generated when navigating relationships in EF Core?
    *   *Answer:* If the relationship is required (e.g., a non-nullable foreign key), EF Core generates an `INNER JOIN`. If the relationship is optional (e.g., a nullable foreign key), EF Core generates a `LEFT JOIN`. Using `.Include()` also typically generates `LEFT JOIN`s unless EF can prove the relationship is required.
