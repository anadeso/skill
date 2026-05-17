# Clean Code Analyzer Skill

## Overview

This skill helps developers analyze code for quality issues based on the principles from "Clean Code" by Robert C. Martin. It identifies violations of best practices related to naming, function design, comments, formatting, error handling, and overall code structure.

## What It Does

When triggered, the skill analyzes code and identifies issues in these areas:

1. **Meaningful Names** - Variable, function, and class naming conventions
2. **Functions** - Function size, parameter count (ideally 0-1, max 2-3), and single responsibility
3. **Comments** - Redundant, misleading, or unhelpful comments
4. **Formatting** - Code layout, spacing, and organization
5. **Error Handling** - Exception handling patterns and null-safety
6. **Code Structure** - DRY principle, duplication, and separation of concerns
7. **Classes & Objects** - Class design, encapsulation, and responsibility
8. **Boundaries** - External dependencies, wrapper patterns, and isolation
9. **Testing** - F.I.R.S.T principle, TDD, and test design
10. **Concurrency** - Thread safety, shared state, and synchronization
11. **Heuristics** - Advanced rules and best practices (17 chapters worth)

## When to Use

Trigger this skill when you need to:
- Review code for quality issues
- Identify refactoring opportunities
- Check if code follows Clean Code principles
- Get suggestions for improving code readability
- Analyze for technical debt
- Perform code quality assessment

## Example Usage

```
"Please review this function for clean code issues"
"Analyze this class for code quality problems"
"Check my code for violations of Clean Code principles"
"Help me identify refactoring opportunities"
```

## Output

The skill provides structured analysis with:
- Specific issues identified by category
- Location of each issue (when possible)
- Severity level (High/Medium/Low)
- Actionable suggestions for improvement
- Summary of findings with top priority fixes

## Based On

- **Clean Code: A Handbook of Agile Software Craftsmanship** by Robert C. Martin
- Chapters cover: Meaningful Names, Functions, Comments, Formatting, Error Handling, and more

## Development Status

This skill is designed to be evaluated against **15 comprehensive test cases** covering:
- **Multiple programming languages** (Python, JavaScript, Java, Go, C#, Ruby, TypeScript)
- **10+ categories of code quality issues**
- **Real-world code patterns** from various domains
- **Advanced topics**: Testing, Boundaries, Concurrency, Heuristics
- **Parameter heuristics**: Correct parameter count recommendations (0-1 ideal, max 2-3)
- **Case studies**: Patterns inspired by real refactoring from Args, JUnit, and SerialDate examples

## Key Corrections & Improvements

✅ **Fixed**: Parameter count recommendation corrected from "max 4" to "ideally 0-1, max 2-3"
✅ **Added**: Chapter 8 (Boundaries) - external dependencies and wrapper patterns
✅ **Added**: Chapter 9 (Testing) - F.I.R.S.T principle and TDD
✅ **Added**: Chapter 13 (Concurrency) - threading and synchronization issues
✅ **Added**: Chapter 17 (Heuristics) - advanced naming, function, and formatting rules
✅ **Added**: Chapters 14-16 (Case Studies) - practical refactoring examples
✅ **Expanded**: Test cases from 10 to 15, including new domains
✅ **Verified**: All recommendations align with original "Clean Code" book by Robert C. Martin
