---
name: clean-code-analyzer
description: Use this skill whenever you need to review code for quality and maintainability issues. Trigger when users ask to improve code readability, identify coding problems, refactor code, or analyze code for best practices. Analyzes code against principles from "Clean Code" by Robert C. Martin - identifying violations of naming conventions, function complexity, code comments, error handling, and overall code structure quality.
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

### 17. **Heuristics** (Chapter 17 - Important Rules)

**General Rules:**
- Use names from the problem domain
- Avoid disinformation in names
- Make distinction meaningful
- Use pronounceable names
- Avoid encoding in names
- Avoid mental mapping
- Pick one word per concept
- Add meaningful context
- Don't add gratuitous context

**Function Rules:**
- Avoid side effects
- Don't pass flags to functions
- Use exceptions rather than return codes
- Extract try/catch blocks into separate functions
- Error handling should be one thing

**Comment Rules:**
- Avoid redundant comments
- Don't comment bad code - rewrite it
- Don't comment obvious code
- Don't use closing brace comments
- Don't comment unused code - delete it
- Use comments to explain business rules, intent
- Use comments for warnings

**Formatting Rules:**
- Keep lines short
- Use whitespace meaningfully
- Don't break indentation
- Space around operators
- No trailing spaces
- Align similar items

**Name Rules:**
- Classes: nouns (User, Customer)
- Methods: verbs (postPayment, deletePage)
- Boolean methods: is/has prefix (isValid, hasItems)
- Search-friendly names
- Consistency across codebase

**Object & Data Structure Rules:**
- Hide internal structure
- Prefer objects over primitive data
- Avoid feature envy
- Avoid data clumps
- Keep related data together
- Keep unrelated data separate

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
