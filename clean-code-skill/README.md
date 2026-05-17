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

This skill is designed to be evaluated against **21 comprehensive test cases** covering:
- **Multiple programming languages** (Python, JavaScript, Java, Go, C#, Ruby, TypeScript)
- **12+ categories of code quality issues**
- **Real-world code patterns** from various domains
- **All 17 chapters** from "Clean Code" including newly added Chapter 10 (Classes)
- **Advanced topics**: Testing, Boundaries, Concurrency, Systems, Emergence, Heuristics
- **55+ numbered heuristics** with accurate categorization (G1-G36, N1-N7, F1-F4, C1-C5, T1-T9)
- **Parameter heuristics**: Correct parameter count (0-1 ideal, max 2-3)
- **Case studies**: Patterns from Args, JUnit, and SerialDate

## Key Corrections & Improvements

### Phase 1: Initial Corrections
✅ **Fixed**: Parameter count (was "max 4" → now "0-1 ideal, max 2-3")
✅ **Added**: Chapter 8 (Boundaries) - external dependencies, wrappers
✅ **Added**: Chapter 9 (Testing) - F.I.R.S.T, TDD
✅ **Added**: Chapter 13 (Concurrency) - threading, synchronization

### Phase 2: Expanded Coverage
✅ **Added**: Chapter 11 (Systems) - DI, factories, system evolution
✅ **Added**: Chapter 12 (Emergence) - Kent Beck's 4 rules of simple design
✅ **Expanded**: Chapter 17 (Heuristics) from generic to **55+ specific numbered rules**
  - **G Rules (G1-G36)**: General heuristics
  - **N Rules (N1-N7)**: Naming heuristics
  - **F Rules (F1-F4)**: Function heuristics
  - **C Rules (C1-C5)**: Comment heuristics
  - **T Rules (T1-T9)**: Test heuristics
✅ **Added**: Chapters 14-16 (Case Studies) - practical refactoring
✅ **Expanded**: Test cases from 15 to **20**

### Phase 3: Precision & Organization Refinements
✅ **Fixed**: Heuristics organization - corrected G29-G31 to proper G Rules (not test rules)
✅ **Refined**: G22 - Now correctly nuanced: polimorphism preferred for type checking (not all if/else)
✅ **Added**: Chapter 10 (Classes) - SRP, cohesion, class organization
✅ **Added**: Test case 20 - Focuses on Chapter 10 (Classes), SRP violations, low cohesion
✅ **Expanded**: Total test cases to **21** with complete chapter coverage
✅ **Verified**: All heuristics accurately categorized per original book structure
✅ **Aligned**: All recommendations match Robert C. Martin's exact guidance
