# React useState Hook with stale closure in useEffect

This example demonstrates a common issue in React applications where the `useState` hook's value is incorrectly updated within the `useEffect` hook because it's based on the previous state value, which might be outdated when the update function eventually executes. This is particularly problematic with asynchronous operations.

## Bug Description
The `MyComponent` attempts to increment a counter every second using `setInterval`. However, it uses the `count` value from the closure, which might not reflect the latest state. This results in the counter not incrementing reliably or accurately and potentially stuck at the initial value or incrementing inconsistently.

## Solution
The correct approach is to use the `setCount` function as a state update function.  The updated `setCount` always applies the change using the latest state value available, resolving the stale closure problem.