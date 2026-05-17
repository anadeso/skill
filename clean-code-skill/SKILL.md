---
name: clean-code-analyzer
description: Use this skill whenever you need to review code for quality and maintainability issues. Trigger when users ask to improve code readability, identify coding problems, refactor code, or analyze code for best practices. Analyzes code against ALL 17+ chapters from "Clean Code" by Robert C. Martin including: naming conventions, function design, comments, formatting, error handling, code structure, classes, boundaries/dependencies, testing, concurrency, system architecture, simple design rules, and 55+ specific heuristics (G1-G36, N1-N7, F1-F4, C1-C5, T1-T9).
---

# Clean Code Analyzer

Analyze code for quality issues based on Clean Code principles. This skill helps developers identify and fix problems related to naming, function size, comments, formatting, error handling, and overall code structure.

## Clean Code Principles to Check

### 1. **Meaningful Names** (Chapter 2)
- Variables, functions, and classes should have clear, intention-revealing names
- Avoid disinformation and don't add unnecessary context
- Use pronounceable names that reveal intent
- Avoid magic numbers - use named constants instead
- Methods should have action-oriented names (verbs)
- Classes should have noun names

**Issues to look for:**
- Single-letter variable names (except loop counters)
- Ambiguous or unclear names
- Names with misleading information
- Magic numbers in code
- Inconsistent naming conventions

### 2. **Functions** (Chapter 3)
- Keep functions small (ideally < 20 lines)
- Functions should do one thing well
- One level of abstraction per function
- Avoid long parameter lists (ideally 0-1 parameter, max 2-3)
  - Niladic (0): Best - no parameters
  - Monadic (1): Good - single parameter
  - Dyadic (2): Acceptable - two parameters
  - Triadic (3+): Avoid - hard to reason about
  - 4+ parameters: Problematic - consider refactoring
- Avoid output parameters or passing data through objects
- Use exceptions instead of error codes

**Issues to look for:**
- Functions that are too long
- Functions doing multiple things
- High cyclomatic complexity
- Too many parameters
- Functions with side effects
- Inconsistent levels of abstraction

### 3. **Comments** (Chapter 4)
- Good code doesn't need comments; it should be self-documenting
- Comments should explain WHY, not WHAT
- Avoid redundant, misleading, or outdated comments
- Use comments only when code intention isn't clear

**Issues to look for:**
- Obvious comments that repeat code
- Lack of critical documentation
- TODO comments left behind
- Comments about what the code does (should be clear from code)
- Outdated or conflicting comments

### 4. **Formatting** (Chapter 5)
- Code should be formatted for readability
- Related concepts should be close together
- Unrelated concepts should be separated by blank lines
- Consistent indentation and spacing
- Keep lines reasonably short
- Class members should be organized logically

**Issues to look for:**
- Inconsistent indentation
- Too much nesting
- Very long lines
- Poor organization of class members
- Inconsistent blank line usage

### 5. **Error Handling** (Chapter 7)
- Use exceptions instead of error codes
- Provide context in exception messages
- Avoid returning null - throw exception or use Optional pattern
- Don't return empty collections - return empty, not null
- Use checked exceptions carefully

**Issues to look for:**
- Bare except/catch blocks
- Silent exception swallowing
- Returning null or error codes
- Exception messages that don't provide context
- Overly broad exception catching
- Not cleaning up resources (no finally/try-with-resources)

### 6. **Code Structure & DRY** (Chapter 1, Throughout)
- Don't Repeat Yourself (DRY)
- Keep functions at similar level of abstraction
- Minimize coupling between modules
- Use dependency injection
- Avoid hardcoding values
- Proper separation of concerns

**Issues to look for:**
- Code duplication
- Magic strings or numbers
- High coupling/low cohesion
- Mixing different abstraction levels
- Tightly coupled dependencies
- Violated single responsibility principle

### 7. **Classes & Objects** (Chapter 6)
- Classes should be small and focused
- Public methods should be fewer than private methods
- Avoid feature envy (accessing other object's data)
- Avoid data clumps (related data that should be grouped)
- Maintain proper encapsulation

**Issues to look for:**
- Large classes with multiple responsibilities
- Too many public methods
- Data classes with just getters/setters (missing behavior)
- Feature envy (accessing other object internals)
- Inconsistent access modifiers

### 8. **Boundaries** (Chapter 8)
- Use wrapper/adapter patterns for external dependencies
- Learning tests to understand third-party code
- Isolate third-party code from core business logic
- Control dependencies through interfaces
- Avoid leaking third-party code into your domain

**Issues to look for:**
- Direct dependency on external libraries
- Third-party code spread throughout codebase
- Hard to replace or upgrade dependencies
- No abstraction layer over external code
- Learning tests missing for critical dependencies

### 9. **Testing** (Chapter 9)
- Tests are as important as production code
- F.I.R.S.T. principle:
  - **Fast**: Tests should run quickly
  - **Independent**: Tests shouldn't depend on each other
  - **Repeatable**: Can run in any environment
  - **Self-Checking**: Pass or fail clearly
  - **Timely**: Written close to production code
- Three Laws of TDD:
  - Write no production code without a failing test
  - Don't write more test than needed to fail
  - Don't write more production code than needed to pass
- One concept per test
- Clear test names revealing what's being tested
- Avoid test pollution and setup complexity

**Issues to look for:**
- Missing test coverage
- Tests that depend on each other
- Slow tests
- Unclear test names
- Too many assertions per test
- Test setup that's overly complex
- Tests that don't verify actual behavior

### 10. **Classes** (Chapter 10)
- Keep classes small - single responsibility principle (SRP)
- Class name should describe its purpose
- Measure class size by number of responsibilities, not lines of code
- Classes should have high cohesion (related methods and fields)
- Maintain proper method organization (public before private)
- Classes should be organized for change
- Avoid "god classes" with too many responsibilities
- Instance variables should be private
- Methods should work with the class's data
- Dependent classes should be clearly listed at top

**Issues to look for:**
- Classes too large (multiple responsibilities)
- Low cohesion - unrelated methods
- Poor organization of members
- Public instance variables
- Too many instance variables
- Methods that don't use class data
- Difficult to understand class purpose
- Hard to extend or modify class
- Methods scattered without logical grouping
- Comments needed to explain class organization

### 11. **Systems** (Chapter 11)
- Separate construction from use of objects
- Dependency injection for managing dependencies
- Factories and dependency containers
- Cross-cutting concerns through AOP or middleware
- System evolution - design for change
- Scale from simple to complex gradually
- Avoid premature optimization
- Use naming conventions to reveal intent
- Keep system architecture visible in code
- Decouple subsystems

**Issues to look for:**
- Mixing construction with business logic
- Hard-wired dependencies throughout code
- No dependency injection or inversion of control
- Factories not used for complex object creation
- Cross-cutting concerns scattered everywhere
- No clear separation of concerns
- Tightly coupled modules
- Hard to understand overall system architecture
- Configuration mixed with logic
- Difficult to replace components

### 12. **Emergence** (Chapter 12)
**Kent Beck's 4 Rules of Simple Design (in priority order):**
1. **All tests pass** - Code must be functional and correct
2. **No duplication** - DRY principle, eliminate code repetition
3. **Expresses intent** - Code is clear, self-documenting
4. **Minimal classes/methods** - Fewest elements possible

These rules applied iteratively lead to emergent design without over-engineering.

**Issues to look for:**
- Failing or missing tests
- Duplicated code and logic
- Code that obscures intent
- Over-engineered solutions with unnecessary classes
- Premature abstraction
- Classes/methods that don't serve a clear purpose
- Complexity that doesn't add value

### 13. **Concurrency** (Chapter 13)
- Concurrency is hard - minimize it where possible
- Keep concurrency code separate from business logic
- Understand concurrency mechanisms (threading, locks, semaphores)
- Protect shared data with proper synchronization
- Know the risks: race conditions, deadlocks, starvation
- Consider thread-safe collections and modern concurrency patterns
- Test concurrent code thoroughly

**Issues to look for:**
- Unprotected shared mutable state
- Mixing concurrency with business logic
- Missing synchronization primitives
- Potential deadlocks
- Race conditions
- Thread pools without proper management
- Inadequate testing of concurrent code

### 17. **Heuristics** (Chapter 17 - 55+ Numbered Rules)

**G Rules (General - G1 to G36):**
- **G1**: Multiple languages in one file - use single language per file
- **G2**: Obvious behaviour is unimplemented - do what's expected
- **G3**: Incorrect boundary behavior - handle edge cases correctly
- **G4**: Overridden safeties and guards - don't disable safety features
- **G5**: Duplication - apply DRY principle rigorously
- **G6**: Code at wrong level of abstraction - keep consistent levels
- **G7**: Too many parameters - ideally 0-1, max 2-3, never 4+
- **G8**: Dead code - delete unused code immediately
- **G9**: Vertical separation - put related concepts close together
- **G10**: Inconsistency - be consistent in similar operations
- **G11**: Clutter - remove variables/functions that serve no purpose
- **G12**: Artificial coupling - unrelated things shouldn't depend
- **G13**: Feature envy - functions shouldn't access other class internals
- **G14**: Selector arguments (flags) - split function instead of using flags
- **G15**: Obscured intent - make intent clear in code
- **G16**: Misplaced responsibility - put code where it's expected
- **G17**: Inappropriate static - prefer non-static when possible
- **G18**: Use explanatory variables - extract to named variables
- **G19**: Function names should say what they do - descriptive names
- **G20**: Understand the algorithm - know what code does
- **G21**: Make logical dependencies physical - show dependencies
- **G22**: Prefer polymorphism to if/else for type checking - use inheritance for type switching (not absolute rule for all if/else)
- **G23**: Prefer exceptions to returning error codes - use exceptions
- **G24**: Extract try/catch blocks - keep error handling separate
- **G25**: Don't return null - throw exception or use Optional
- **G26**: Don't pass null - avoid null parameters
- **G27**: Avoid encoding - no Hungarian notation
- **G28**: Names should convey intent - choose meaningful names
- **G29**: Avoid negative conditionals - use positive form when possible (e.g., if valid instead of if not invalid)
- **G30**: Functions should have no side effects - be predictable
- **G31**: Hidden temporal couplings - reveal dependencies (not related to tests, but general rule)
- **G32**: Don't be arbitrary - choose conventions for good reasons
- **G33**: Encapsulate boundary conditions - centralize handling
- **G34**: Functions should descend only one level of abstraction - keep abstraction level consistent
- **G35**: Keep configurable data at high levels - configuration above implementation
- **G36**: Avoid transitive navigation - don't chain method calls (Law of Demeter)

**N Rules (Names - N1 to N7):**
- **N1**: Choose descriptive names - clarity is essential
- **N2**: Names at appropriate level of abstraction - use domain language
- **N3**: Use standard nomenclature - follow industry conventions
- **N4**: Unambiguous names - no confusion possible
- **N5**: Use long names for long scopes - short names for short scopes
- **N6**: Avoid encoding - names, not codes
- **N7**: Names should describe side effects - reveal what function does

**F Rules (Functions - F1 to F4):**
- **F1**: Too many arguments - reduce parameter count
- **F2**: Output arguments - use return values, not output params
- **F3**: Flag arguments - split function, don't use boolean flags
- **F4**: Dead functions - delete unused functions

**C Rules (Comments - C1 to C5):**
- **C1**: Inappropriate information - comments for intent, not facts
- **C2**: Obsolete comment - keep comments updated
- **C3**: Redundant comments - don't explain obvious code
- **C4**: Poorly written comments - write clearly or don't write
- **C5**: Commented-out code - delete it, use version control

**T Rules (Tests - T1 to T9):**
- **T1**: Insufficient tests - cover all code paths
- **T2**: Use coverage tool - know coverage percentage
- **T3**: Don't skip trivial tests - test everything
- **T4**: Ignored test - fix or delete, don't ignore
- **T5**: Test boundary conditions - edge cases matter
- **T6**: Exhaustively test near bugs - bug-prone areas need tests
- **T7**: Patterns of failure are revealing - analyze test patterns
- **T8**: Test coverage patterns - coverage should be uniform
- **T9**: Tests should be fast - slow tests aren't run

### Practical Case Studies (Chapters 14-16)
- **Chapter 14 - Args**: Parsing command-line arguments - demonstrates refactoring for clarity
- **Chapter 15 - JUnit**: Refactoring test framework code - real-world refactoring example
- **Chapter 16 - SerialDate**: Improving production code quality - comprehensive refactoring case study

These chapters illustrate how to apply Clean Code principles to real production code through comprehensive refactoring.

## Analysis Output Format

Always format your analysis using this structure:

### Code Quality Issues

#### Naming Problems
- **Issue**: [specific problem with names]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Function Issues
- **Issue**: [problem with function design]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Comment Issues
- **Issue**: [problem with comments]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Formatting Issues
- **Issue**: [formatting problem]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Error Handling Issues
- **Issue**: [error handling problem]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Structure & DRY Issues
- **Issue**: [structural problem or duplication]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Class & Object Issues
- **Issue**: [class design problem]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Class Organization Issues (Chapter 10)
- **Issue**: [class size, cohesion, or organization problem]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Boundaries & External Dependencies Issues
- **Issue**: [boundary/wrapper problem]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Testing Issues
- **Issue**: [test design problem]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

#### Concurrency Issues
- **Issue**: [threading/concurrency problem]
- **Location**: [file/line if possible]
- **Severity**: High/Medium/Low
- **Suggestion**: [how to fix it]

### Summary
- **Total Issues Found**: [count]
- **Critical Issues**: [count]
- **Overall Code Quality**: [assessment]
- **Top Priority Fixes**: [list 2-3 most impactful improvements]

## Analysis Guidelines

1. **Be thorough but practical** - Focus on issues that have real impact on code quality and maintenance
2. **Explain the reasoning** - Help the user understand WHY it's a problem, not just that it is one
3. **Provide actionable suggestions** - Each issue should come with a concrete improvement
4. **Consider context** - Some "violations" may be acceptable in specific contexts; note when that's the case
5. **Prioritize** - Focus on high-impact issues first (function size, naming, error handling)
6. **Be encouraging** - Point out positive aspects of the code too, not just problems

## When to Trigger

This skill should be invoked when users:
- Ask to "review my code for quality"
- Want to "improve code readability"
- Request "clean code analysis"
- Say "identify coding issues"
- Ask "how can I make this better?"
- Want "refactoring suggestions"
- Request "code quality assessment"
- Are doing "code review"
- Ask about "best practices"
- Want to "reduce technical debt"
- Request "clean code improvements"
