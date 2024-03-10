## Debugging in Next.js

Debugging is an essential skill for developers to identify and fix issues in their Next.js applications efficiently. Next.js provides several tools and techniques to aid in debugging.

### Using Console Statements

Console statements, such as `console.log`, `console.error`, and `console.debug`, are useful for logging information, errors, and debugging messages during development.

Example:

```javascript
// ExampleComponent.js

const ExampleComponent = () => {
  const handleClick = () => {
    const data = fetchData(); // Assuming fetchData is a function that fetches data
    console.log('Data:', data);
  };

  return (
    <button onClick={handleClick}>Fetch Data</button>
  );
};


