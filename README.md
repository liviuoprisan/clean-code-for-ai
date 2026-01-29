# Clean Code Principles for AI

Clean code rules for AI coding assistants. Teaches agents to write maintainable code focused on simplicity, small functions, and clear naming.

## How to Use

**Cursor:** Copy this file to `.cursor/rules/clean-code.md` in your project root

**Claude Code:** Copy this file to:
- Project: `.claude/rules/clean-code.md`
- User-level: `~/.claude/rules/clean-code.md` (applies to all your projects)

## Good Practices
- Extract method
- Extract class
- Beautify code - replace complex statements with well-named methods
- Keep line length under 80-120 characters
- Write tests (TDD when possible)
- Focus on maintainable code, not micro speed optimizations
- Use exceptions, not error codes
- Continuous refactoring as you work unless working with fragile or big systems

## Key Mindset
- Maintainable code is about empathy - Will a person understand this code the first time they read it?
- Maintainability over cleverness
- Maintainability over premature optimization
- Simplicity over complexity
- Small and focused over big and general
- Express intent through code, not comments
- Refactor continuously while working (unless told otherwise; in practice it's harder to do on big fragile code bases)

## Core Mantras

- Small Everything - Maintainability comes in small packages
- KISS - Keep It Simple, Stupid
- DRY - Don't Repeat Yourself
- YAGNI - You Ain't Gonna Need It. Focus on the Present
- Encapsulation - Hide state, expose behavior

## Functions & Classes

### Size Matters Most
- **Functions**: 5-10 lines ideal, 20 lines maximum
- **Classes**: 50 lines ideal, 100 lines maximum
- Small is maintainable. Always prefer smaller.

### Single Responsibility Principle (SRP)
- One function does ONE thing
- One class does ONE thing
- One line does ONE thing
- Extract until you can't extract anymore

### Extract Method - Your Main Tool
- Complex code? Extract to a method
- Hard to read? Extract to a method
- Doing multiple things? Extract to methods
- Same for extract class when appropriate

## Naming

### Parts of Speech
- **Classes**: Nouns (User, Price, OrderService)
- **Methods**: Verbs (getUser, createOrder, calculateTotal)
- **Variables**: Nouns (userName, totalPrice)
- **Booleans**: Predicates (isValid, hasPermission, canEdit)

### Name Size
- Variables: Bigger scope = longer name
- Methods: Bigger scope = shorter name
- Be verbose and explicit over cryptic
- No abbreviations

### Express Intent
- Names show WHAT not HOW (writeToFile not useFileBuffer)
- Names (for variables, methods, classes) are your main communication tool
- Take advantage of naming opportunities
- If needed create naming opportunities with extract method

## Parameters
- **0-3 parameters maximum**, prefer 0
- Same-type parameters are confusing
- Many parameters? Use "Introduce Parameter Object"
- Avoid boolean and null parameters - create two methods instead

## Code Structure

### Code blocks
- Prefer one level of indentation when possible in code blocks - methods, ifs, loops... 
- Avoid going two or more levels deep
- Extract nested code or use early returns
- Avoid else blocks
- Prefer validate for positive cases (if something, not if !something)
- Keep consistent with true/false returns
- Avoid big blocks of code inside conditionals using extract method

### Beautify Predicates
- Complex conditionals? Extract to boolean method
- `if (isProcessRunning())` not `if (p.sts == 1)`

### One Statement Per Line
- No multiple assignments
- No chaining operations
- Exception: builders and fluent APIs

## Principles

### Low Coupling, High Cohesion
- Classes should know little about others
- Pass primitives, not entire objects (when reasonable)
- Things that change together should be together
- Extract class to increase cohesion

### Tell Don't Ask
- Tell objects what to do, don't ask for their state
- Avoid: `user.getUserManager().getLoginManager().allowLogin()`
- Prefer: `user.allowLogin()`

### Law of Demeter (One Dot Per Line)
- Preferably only call methods on: parameters, objects you created, class properties, globals
- Preferably don't chain through multiple objects to avoid coupling

### Command-Query Separation - two type of methods:
- **Commands**: Change state, return nothing
- **Queries**: Return data, change nothing

## What to Avoid

### Comments
- Comments lie and rot
- Express intent through code, not comments
- Exception: Regex explanations, public APIs, warnings about consequences
- Delete commented-out code unless needed by the team

### Complexity
- Avoid complex patterns and polymorphism unless essential
- Simple switch > Complex polymorphism
- Common language features > Language-specific features
- Functional programming features are often harder to maintain

### Don't be premature
- Avoid premature optimization: optimize code when needed by testing the system to see where it needs optimizations most
- Avoid premature flexibilization: don't create useless interfaces and abstract classes

### Inheritance
- Prefer composition over inheritance
