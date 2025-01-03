# React Native useCallback Stale Closure with Nested Function

This repository demonstrates a subtle bug in React Native related to the use of the `useCallback` hook with a function containing a nested function that accesses a state variable.  The problem arises because of stale closures.

## Problem Description

When a nested function inside a `useCallback` relies on a state variable, it captures the state's value at the time `useCallback` is initially called, not when the nested function is executed.  This leads to the function using outdated state values, resulting in unexpected behavior.  See the `bug.js` file for a demonstration of the issue.

## Solution

The solution involves ensuring the state variable is accessed directly within the callback or by passing it as an argument to the nested function. Passing the state variable to the nested function eliminates the stale closure problem. See `bugSolution.js` for the corrected code.