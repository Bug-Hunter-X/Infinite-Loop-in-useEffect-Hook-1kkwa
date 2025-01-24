# Infinite Loop in useEffect Hook

This repository demonstrates a common error in React's `useEffect` hook that can lead to an infinite loop.  The issue stems from the effect function being called after every render, creating an unintended cycle.  This can easily happen when the effect depends directly or indirectly on the state it modifies.

## Bug Description

The provided `bug.js` file contains a component where the `useEffect` hook logs the current count after each render. While seemingly harmless, this dependency creates an infinite loop in React 18 and 19 because the `count` value changes with every click, triggering a re-render, leading to an endless loop of renders and effect executions.

## Solution

The `bugSolution.js` file provides a solution by adding a dependency array to the `useEffect` hook. This array specifies that the effect should only run when the `count` value changes. By only running on changes to the specific values within the dependency array, it prevents the unnecessary re-renders which caused the infinite loop.

## How to reproduce

1. Clone this repository
2. Run `npm install`
3. Run `npm start`
4. Observe the infinite loop in the console with `bug.js`
5. Switch to `bugSolution.js` to observe the corrected behaviour.