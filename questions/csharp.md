# C# Interview Questions

## Object-Oriented Programming (OOP)
*   **Fundamental OOP concepts:**
    *   Encapsulation
    *   Abstraction
    *   Inheritance
    *   Polymorphism
*   **What is data encapsulation?**

## Basic C#
*   **Value vs Reference type:** What is the difference between a value type and a reference type? Give examples. In what cases should we use a value type?
    *   *Note:* Value types have fixed memory allocations.
*   **Nullable types:** What is the `Nullable` type? What types can be used with it?
*   **Const vs Readonly:** What is the difference between `const` and `readonly`?
*   **Type declarations:** Explain differences between explicit typing, `var`, and `dynamic`.
*   **Exceptions in loops:** Will this code throw an exception? `int i=1; while(1>0) {i++;}`
    *   *Note:* To intentionally throw an overflow exception, use a `checked` block.
*   **Loops:** Explain `break`, `continue`, and `yield`.
*   **Records:** What is a record? Are records immutable?
*   **Generics:**
    *   What are generics?
    *   Name some standard generics in .NET.
    *   How do you restrict the types passed in (generic constraints)?
*   **Methods:** How would you return multiple values from a method?
*   **IDisposable:** What is an `IDisposable` interface and when should you use it?
    *   *Note:* It is mainly used to dispose of unmanaged resources.

## Delegates, Events, and Closures
*   **Delegates:** What is a delegate?
*   **Built-in delegates:** Explain the difference between `Func`, `Action`, and `Predicate`.
*   **Closures:** What is a closure?
    *   *Note:* A common pitfall is passing a loop iterator variable into a closure.
*   **Events:** What is an `event` and why do we have this keyword in C#?
*   **EventHandlerList:** What is `EventHandlerList` and how do you use it?

## Exception Handling
*   How is exception handling done in C#?
*   Is there any exception in .NET which will not be caught?
*   What is the difference between `throw ex;` and `throw;`?

## Inheritance and Polymorphism
*   **Polymorphism:** What is polymorphism?
*   **Keywords:** What keywords can be used in C# in terms of inheritance?
*   **Abstract class vs Interface:** What are the differences between an abstract class and an interface?
*   **Explicit Interface:** What is explicit interface method implementation?
*   **Override vs New:** What is the difference between `override` and `new`?
*   **Overloaded vs Overridden:** What is the difference between overloaded and overridden methods?
*   **Initialization order:** In what order is an object initialized?
*   **Virtual methods in constructors:** What is the problem with calling virtual methods in the constructor?

## Reflection
*   What is Reflection? Why do we have it?

## Threading and Asynchrony
*   **Thread vs Process:** What is the difference between a Thread and a Process?
*   **Communication:** How can threads communicate with each other? How can processes communicate with each other?
*   **Creating Threads:** How can we create a thread in C#?
    *   Examples: `new Thread()`, `ThreadPool`, `Parallel.For`, `Parallel.ForEach` (TPL), `ParallelEnumerable.AsParallel` (PLINQ), `TaskFactory.StartNew`, `Task.Run`.
*   **CancellationToken:** When and how should you use a `CancellationToken`?
*   **Async/Await:** Explain how `async`/`await` works under the hood.
*   **Foreground vs Background:** What is the difference between foreground and background threads?
*   **Task.Run:** How does `Task.Run` work? Does it create new threads? Is the executed thread a background or foreground thread?
    *   *Note:* It queues the specified work to run on the `ThreadPool`, and ThreadPool threads are background threads.
*   **Concurrency Issues:** Explain what a deadlock and a race condition are. How would you avoid them?
*   **ThreadLocal:** What is `ThreadLocal`? How does it help in preventing deadlocks?
*   **Synchronization Primitives:** Explain how to use `SemaphoreSlim` (and why you might use it instead of `lock`).
*   **Synchronization Concepts:** Explain `lock`, `Monitor`, `ConcurrentDictionary`, and `ThreadStatic`.
*   **Volatile:** Explain the `volatile` keyword in C#. When do we use it?

## LINQ
*   What is LINQ?
*   Can you explain what `IQueryable` is and how it differs from `IEnumerable` in C#?

## Memory Management
*   How does the garbage collector (GC) work in .NET?
*   What is a memory leak? How can it occur in a managed environment?
