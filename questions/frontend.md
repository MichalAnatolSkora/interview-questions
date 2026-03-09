# Frontend and Web Interview Questions

## JavaScript
*   **Event Loop:** Explain the Event Loop in JavaScript. How does it handle task queues and microtasks?
*   **HTTP/REST:** What are the principles of RESTful APIs? Explain common HTTP methods and status codes.

## TypeScript
*   **Purpose:** How does TypeScript work under the hood, and why was it created?
*   **Execution Order Puzzle:** Determine the order of execution in the console for the following snippet:
    ```javascript
    (function() {
        setTimeout(function() { console.log(1) }, 0); 
        Promise.resolve().then(() => console.log(2));
        new Promise((resolve, reject) => resolve()).then(() => console.log(3));
        console.log(4);
    })();
    ```
    *   *Note:* The order of execution depends on synchronous execution (call stack), microtasks (Promises), and macrotasks (setTimeout). Output: 4, 2, 3, 1.
