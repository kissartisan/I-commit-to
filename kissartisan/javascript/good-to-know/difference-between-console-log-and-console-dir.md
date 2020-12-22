## Difference between console.log() vs console.dir()
- Main difference:
*console.log prints the element in an HTML-like tree*
WHILE
*console.dir prints the element in a JSON-like tree*
- Specifically, console.log gives special treatment to DOM elements, whereas console.dir does not. This is often useful when trying to see the full representation of the DOM JS object.

Useful thread: https://stackoverflow.com/questions/11954152/whats-the-difference-between-console-dir-and-console-log
