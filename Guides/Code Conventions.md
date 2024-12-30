## General Rules

1. Use 4 spaces for indentation. Tabs are strictly prohibited.
2. Limit line length to 80 characters. Break longer lines into multiple lines.
3. Include comments for code components/modules.
4. Follow the DRY (Don't Repeat Yourself) principle to avoid code duplication.
5. Fail fast: Code should reveal its bugs as early as possible.
6. Avoid magic numbers. Use named constants instead.
7. Assign one purpose per variable.
8. Use whitespace and punctuation to improve readability.
9. Follow the Boy Scout Rule: Leave the code better than you found it.
10. Avoid global variables.
11. Functions should return results, not print them.
12. Avoid special case code.
13. Keep functions small and focused on a single task.
14. User version control systems (e.g., Git) consistently
15. Write self-documenting code where possible.
16. Follow the principle of least astonishment (POLA).
17. Use meaningful error messages and exceptions.

## Naming Conventions

1. Use clear, descriptive, and meaningful names for variables and functions.
2. Follow language-specific naming conventions:
    - JavaScript: `camelCase`
    - Python: `snake_case`
    - C++: `TurtleCase`
    - Enums: `UPPER_SNAKE_CASE`
    - CSS class names: `use hyphens (e.g., class-name)`
3. Use verb phrases for function names (e.g., `calculateTotal`, `fetchUserData`)
4. Use noun phrases for variable and class names (e.g., `userAccount`, `dataProcessor`)
5. Avoid abbreviations unless they are widely understood.

## Coding Style

1. In JavaScript, use `let` and `const`. The use of `var` is strictly prohibited.
2. Use compact braces:
```javascript
	if(condition){ 
		// code here 
	}
```

4. Spaces should not be present within parentheses or before semicolons/commas:
```javascript
	✔  for(int i=0; i<10; i++){ 
	✔  for(int i=0;i<10;i++){ 
	
	❌ for (int i=0;i<10;i++) 
	❌ for( int i=0;i<10;i++ ) 
	❌ for(int i=0 ;i<10 ;i++)
```
    
4. Separate complex calculations using parentheses or variables:
```javascript
	❌ let x = a+b+c/z; 
	✔  let x = (a+b+c)/z;
```

5. Use consistent formatting throughout the project.
6. Place opening braces on the same line for functions and control structures.
7. Use semicolons to terminate statements in languages that require or recommend them.


## Code Organization

1. Avoid deep nesting. Use inversion (invert the condition) when possible.
2. Merge related if statements.
3. Extract complex logic into separate methods and functions.
4. Group related code together.
5. Use design patterns appropriately to solve common problems.
6. Organize code into modules or components for better maintainability.
7. Keep a clear separation of concerns between different parts of your application.

## Readability

1. Don't use naming that only you understand.
2. Comment where needed, but prefer self-explanatory code.
3. Use good names that clearly convey the purpose of variables and functions.
4. The potential reader of your code is likely to be you in the future, so make it clear and understandable.
5. Use consistent and logical order for method/function parameters.
6. Avoid long parameter lists; consider using objects for multiple parameters.
7. Use meaningful constants instead of literal values.

## Testing and Debugging

1. Write unit tests for your code.
2. Use assertions to catch programmer errors early.
3. Use a debugger instead of print statements for complex debugging.
4. Write testable code by keeping functions pure when possible.
5. Implement logging for better debugging and monitoring in production.

## Performance and Optimization

1. Write correct code first, then optimize if necessary.
2. Use appropriate data structures for your use case.
3. Be mindful of time and space complexity in your algorithms.
4. Avoid premature optimization.
5. Profile your code to identify actual bottlenecks before optimizing.

## Security

1. Never store sensitive information (like passwords or API keys) in your code.
2. Sanitize and validate all user inputs.
3. Use parameterized queries to prevent SQL injection.
4. Keep dependencies up to date to avoid known vulnerabilities.
5. Follow the principle of least privilege in your application design.

-----

**Magic Numbers**
A magic number is a numeric literal that appears in code without any context or explanation.

```javascript
	function calculateCircleArea(radius){ 
		return 3.14159 * radius * radius; 
	}
```

`3.14159` is a magic number. It's not immediately clear what this number represents unless you're familiar with the value of pi.

```javascript
	const PI = 3.14159;

	function calculateCircleArea(radius) {
	    return PI * radius * radius;
	}
```


**Boy Scout Rule**
The Boy Scout Rule in programming is derived from the Boy Scouts' rule to "leave the campground cleaner than you found it." In software development, this principle is often stated as: "Always leave the code better than you found it."

This rule encourages developers to make small, incremental improvements to the codebase whenever they're working on it. The idea is that if everyone on the team follows this rule, the overall quality of the code will gradually improve over time, even as the codebase grows and evolves.

Here are some ways to apply the Boy Scout Rule:
1. Improve naming: If you encounter a variable or function with an unclear name, rename it to something more descriptive.
2. Add comments: If you spend time figuring out what a piece of code does, add a comment to explain it for the next person.
3. Refactor small bits: If you see a small opportunity for refactoring (like extracting a repeated piece of code into a function), do it.
4. Fix minor bugs: If you notice a small bug that's unrelated to your current task but quick to fix, go ahead and fix it.
5. Update outdated practices: If you see code using an outdated method or library, update it to the current best practice.
6. Improve formatting: If the code's formatting is inconsistent or hard to read, tidy it up.

Before:
```javascript
	function f(x) {
	    var res = x * 3.14159;
	    return res;
	}
```

After: 
```javascript
	/**
	 * Calculates the circumference of a circle.
	 * @param {number} radius - The radius of the circle.
	 * @returns {number} The circumference of the circle.
	 */
	function calculateCircumference(radius) {
	    const PI = Math.PI;
	    return 2 * PI * radius;
	}
```


### References & Inspiration
----

- https://youtu.be/-AzSRHiV9Cc?si=G4eTyFMgT6XlyLPD
- https://google.github.io/styleguide/