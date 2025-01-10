# Objective-C Crash with performSelector:withObject:afterDelay: on deallocated object

This repository demonstrates a common but easily overlooked bug in Objective-C related to the `performSelector:withObject:afterDelay:` method.  If the object on which you're performing the selector is deallocated before the delay expires, your app will crash.  This example shows the problem and a robust solution.

## How to Reproduce

1. Clone this repository.
2. Open the project in Xcode.
3. Run the project. You should observe a crash after a short delay.
4. Uncomment the solution code in `bugSolution.m` and rerun. The crash should be resolved.

## Solution

The solution involves using a mechanism to ensure the object still exists before executing the selector.  Using a weak reference, we can check if the object has already been deallocated and avoid the crash.