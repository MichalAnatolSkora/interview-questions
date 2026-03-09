# C# Interview Questions

## Object-Oriented Programming (OOP)
*   **Fundamental OOP concepts:**
    *   **Encapsulation:** Grouping data (state) and methods (behavior) within a single unit (class), hiding internal state from the outside.
    *   **Abstraction:** Hiding complex implementation details and showing only the essential features of an object.
    *   **Inheritance:** Mechanism where a new class inherits properties and behavior from an existing class.
    *   **Polymorphism:** The ability of different objects to respond in their own way to the same method call (e.g., via overriding or interfaces).
*   **What is data encapsulation?** As mentioned above, it's bundling data and methods into a single component and restricting direct access to some of the object's components (using access modifiers like `private`).

## Basic C#
*   **Value vs Reference type:** What is the difference between a value type and a reference type? Give examples. In what cases should we use a value type?
    *   *Answer:* Value types hold data directly (e.g., `int`, `bool`, `structs`) and are usually allocated on the stack. Reference types hold a memory address (reference) to the data (e.g., `class`, `string`, `arrays`) allocated on the heap. Use value types for small, immutable, simple data structures.
    *   *Note:* Value types have fixed memory allocations.
*   **Nullable types:** What is the `Nullable` type? What types can be used with it?
    *   *Answer:* A generic structure `Nullable<T>` (or `T?`) that allows value types (which normally cannot be null) to represent an undefined or null state.
*   **Const vs Readonly:** What is the difference between `const` and `readonly`?
    *   *Answer:* `const` is evaluated at compile-time and its value cannot change. `readonly` is evaluated at runtime, can be assigned in a constructor, and can have different values for different object instances.
*   **Type declarations:** Explain differences between explicit typing, `var`, and `dynamic`.
    *   *Answer:* Explicit (`int x`): type is known at compile time. `var`: implicitly typed; compiler infers the type at compile time. `dynamic`: type checking is deferred until runtime.
*   **Exceptions in loops:** Will this code throw an exception? `int i=1; while(1>0) {i++;}`
    *   *Answer:* No, by default in C#, an integer overflow silently wraps around to negative values.
    *   *Note:* To intentionally throw an overflow exception, use a `checked` block.
*   **Loops:** Explain `break`, `continue`, and `yield`.
    *   *Answer:* `break`: exits the innermost loop. `continue`: skips the rest of the current iteration and jumps to the next one. `yield` (with `return` or `break`): used in an iterator block to provide the next value or signal the end of iteration.
*   **Records:** What is a record? Are records immutable?
    *   *Answer:* A reference type that provides built-in functionality for encapsulating data with value-based equality. Yes, primarily designed to be immutable (though mutable properties can be created).
*   **Generics:**
    *   What are generics? *Answer:* Classes/methods decoupled from data types, allowing code reuse with type safety.
    *   Name some standard generics in .NET. *Answer:* `List<T>`, `Dictionary<TKey, TValue>`, `IEnumerable<T>`.
    *   How do you restrict the types passed in (generic constraints)? *Answer:* Using the `where` keyword (e.g., `where T : class`, `where T : new()`).
*   **Methods:** How would you return multiple values from a method?
    *   *Answer:* Using Tuples (`(int a, string b)`), `out` parameters, passing a reference type, or returning a custom object/record.
*   **IDisposable:** What is an `IDisposable` interface and when should you use it?
    *   *Answer:* Used to provide a mechanism for deterministic release of unmanaged resources (like file handles or database connections) through the `Dispose()` method, often combined with the `using` statement.
    *   *Note:* It is mainly used to dispose of unmanaged resources.

## Delegates, Events, and Closures
*   **Delegates:** What is a delegate?
    *   *Answer:* A type-safe function pointer. An object that holds a reference to a method with a specific signature.
*   **Built-in delegates:** Explain the difference between `Func`, `Action`, and `Predicate`.
    *   *Answer:* `Action` has no return type (returns void). `Func` returns a value of a specified type. `Predicate` is a specialized `Func` that takes one argument and always returns a `bool`.
*   **Closures:** What is a closure?
    *   *Answer:* When an inline function (like a lambda expression) captures and uses variables from its surrounding scope.
    *   *Note:* A common pitfall is passing a loop iterator variable into a closure (prior to C# 5.0).
*   **Events:** What is an `event` and why do we have this keyword in C#?
    *   *Answer:* An `event` is a special kind of multicast delegate that restricts outside access; external classes can only subscribe (`+=`) or unsubscribe (`-=`), but cannot invoke it directly or clear its invocation list.
*   **EventHandlerList:** What is `EventHandlerList` and how do you use it?
    *   *Answer:* A class (available in `System.ComponentModel`) used to efficiently store multiple event delegates for a component, saving memory when a class declares many events but only a few are actually subscribed to.

## Exception Handling
*   How is exception handling done in C#?
    *   *Answer:* Using `try`, `catch`, and `finally` blocks.
*   Is there any exception in .NET which will not be caught?
    *   *Answer:* Yes, e.g., `StackOverflowException` and `ExecutionEngineException` (historically), or when a fail-fast occurs (`Environment.FailFast()`). OutOfMemoryExceptions can sometimes be caught, but are very dangerous.
*   What is the difference between `throw ex;` and `throw;`?
    *   *Answer:* `throw ex;` resets the stack trace to the current line. `throw;` preserves the original stack trace.

## Inheritance and Polymorphism
*   **Polymorphism:** What is polymorphism?
    *   *Answer:* Literally "many forms." It allows derived classes to override methods of base classes, and allows code to treat derived objects as instances of their base class/interface.
*   **Keywords:** What keywords can be used in C# in terms of inheritance?
    *   *Answer:* `virtual`, `override`, `abstract`, `base`, `sealed`, `new` (hiding).
*   **Abstract class vs Interface:** What are the differences between an abstract class and an interface?
    *   *Answer:* An abstract class can have implementations, fields, and constructors. An interface (pre-C# 8) has only method signatures without implementation. A class can inherit only one abstract class but multiple interfaces.
*   **Explicit Interface:** What is explicit interface method implementation?
    *   *Answer:* Implementing an interface method by prefixing the method name with the interface name. It's used to resolve naming collisions and hides the method from the class's public API (it can only be called when the object is cast to the interface).
*   **Override vs New:** What is the difference between `override` and `new`?
    *   *Answer:* `override` replaces the inherited virtual method. `new` hides the inherited method (if you cast the object to the base class, the base method is called instead of the derived one).
*   **Overloaded vs Overridden:** What is the difference between overloaded and overridden methods?
    *   *Answer:* Overloaded: same method name but different signature (parameters) in the same class. Overridden: replacing a base class's virtual method implementation in a derived class.
*   **Initialization order:** In what order is an object initialized?
    *   *Answer:* Base class fields -> Derived class fields -> Base class constructor -> Derived class constructor.
*   **Virtual methods in constructors:** What is the problem with calling virtual methods in the constructor?
    *   *Answer:* The virtual method will execute on the derived class *before* the derived class's constructor has finished running, potentially accessing unitialized state.

## Reflection
*   What is Reflection? Why do we have it?
    *   *Answer:* Reflection allows inspecting metadata about assemblies, modules, and types at runtime, and dynamically invoking methods or instantiating objects. It is used for late binding, serialization, dependency injection frameworks, and testing tools.

## Threading and Asynchrony
*   **Thread vs Process:** What is the difference between a Thread and a Process?
    *   *Answer:* A process is an executing instance of an application with its own memory space. A thread is an execution path within a process; multiple threads share the same memory space.
*   **Communication:** How can threads communicate with each other? How can processes communicate with each other?
    *   *Answer:* Threads communicate via shared memory/variables (with synchronization). Processes communicate via Inter-Process Communication (IPC) mechanisms like pipes, sockets, shared memory, or memory-mapped files.
*   **Creating Threads:** How can we create a thread in C#?
    *   *Answer:* `new Thread()`, `ThreadPool`, `Parallel.For`, `Parallel.ForEach` (TPL), `ParallelEnumerable.AsParallel` (PLINQ), `TaskFactory.StartNew`, `Task.Run`.
*   **CancellationToken:** When and how should you use a `CancellationToken`?
    *   *Answer:* Used to signal that a task or operation should be canceled. Passed from a `CancellationTokenSource` down to asynchronous methods.
*   **Async/Await:** Explain how `async`/`await` works under the hood.
    *   *Answer:* The compiler transforms the `async` method into a state machine. `await` registers a continuation on the awaited task and yields control back to the caller until the task completes.
*   **Foreground vs Background:** What is the difference between foreground and background threads?
    *   *Answer:* A foreground thread keeps the application alive. A background thread will be terminated automatically when all foreground threads finish.
*   **Task.Run:** How does `Task.Run` work? Does it create new threads? Is the executed thread a background or foreground thread?
    *   *Answer:* It queues the specified work to run on the `ThreadPool`. It typically reuses existing threads rather than creating new ones. The threads are background threads.
*   **Concurrency Issues:** Explain what a deadlock and a race condition are. How would you avoid them?
    *   *Answer:* **Deadlock:** Two or more threads block each other permanently waiting for resources. Avoid by ordering locks or avoiding nested locks. **Race condition:** Output depends on the uncontrollable timing of thread execution. Avoid with proper synchronization (locks, concurrent collections).
*   **ThreadLocal:** What is `ThreadLocal<T>`? How does it help in preventing deadlocks?
    *   *Answer:* Provides storage for data that is local to an individual thread. By avoiding shared state, it eliminates the need for locks, thereby preventing deadlocks and race conditions.
*   **Synchronization Primitives:** Explain how to use `SemaphoreSlim` (and why you might use it instead of `lock`).
    *   *Answer:* `SemaphoreSlim` limits the number of threads that can access a resource simultaneously. Unlike `lock` (which allows only 1 thread and handles only synchronous code), `SemaphoreSlim` allows `N` threads and supports asynchronous waiting (`WaitAsync`).
*   **Synchronization Concepts:** Explain `lock`, `Monitor`, `ConcurrentDictionary`, and `ThreadStatic`.
    *   *Answer:* `lock`: Syntactic sugar over `Monitor.Enter/Exit` to ensure mutual exclusion. `Monitor`: Provides a mechanism to synchronize access to objects. `ConcurrentDictionary`: Thread-safe dictionary. `[ThreadStatic]`: Attribute indicating that a static field has a unique value per thread.
*   **Volatile:** Explain the `volatile` keyword in C#. When do we use it?
    *   *Answer:* Indicates that a field might be modified by multiple threads executing concurrently. It ensures that the most up-to-date value is always read from main memory, preventing compiler/CPU optimizations from caching it.

## LINQ
*   What is LINQ?
    *   *Answer:* Language Integrated Query. A set of language features granting native data querying capabilities directly in C# regardless of the data source (in-memory, database, XML).
*   Can you explain what `IQueryable` is and how it differs from `IEnumerable` in C#?
    *   *Answer:* `IEnumerable<T>` defines in-memory sequence operations (executed locally). `IQueryable<T>` derives from `IEnumerable` and is intended for out-of-memory queries (like databases). It builds expression trees that providers (like EF Core) translate into domain-specific queries (like SQL) for server-side execution.

## Memory Management
*   How does the garbage collector (GC) work in .NET?
    *   *Answer:* It automatically manages memory on the managed heap. It uses a generational algorithm (Gen 0, Gen 1, Gen 2) to identify objects that are no longer reachable from application roots and frees their memory during garbage collection cycles.
*   What is a memory leak? How can it occur in a managed environment?
    *   *Answer:* When objects are no longer needed but cannot be reclaimed by the GC because they are still referenced by reachable objects. Common causes: un-unsubscribed events, static collections growing infinitely, or not disposing unmanaged resources.
