```markdown
# DeepSeek-Reasonix Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill provides guidance on developing and contributing to the DeepSeek-Reasonix codebase, which is written in Go. It covers the repository's coding conventions, including file naming, import/export styles, and commit patterns. It also outlines workflows for common development tasks and describes the project's testing approach.

## Coding Conventions

### File Naming
- Use **snake_case** for all file names.
  - Example:  
    ```
    reasonix_core.go
    inference_engine.go
    ```

### Import Style
- Use **relative imports** within the project.
  - Example:
    ```go
    import "./utils"
    import "../models"
    ```

### Export Style
- Use **named exports** for functions, types, and variables.
  - Example:
    ```go
    // Exported function
    func RunInference(input string) Result {
        // ...
    }
    ```

### Commit Patterns
- Commits are of **mixed types**, with some using the `fix` prefix.
- Commit messages are concise, averaging around 50 characters.
  - Example:
    ```
    fix: handle nil pointer in inference engine
    update: improve logging for debug mode
    ```

## Workflows

### Code Contribution
**Trigger:** When adding new features or fixing bugs  
**Command:** `/contribute`

1. Create a new branch for your change.
2. Follow the snake_case convention for new files.
3. Use relative imports for internal modules.
4. Use named exports for all public functions and types.
5. Write or update tests in files matching `*.test.*`.
6. Commit changes with a descriptive message (preferably with a prefix like `fix:`).
7. Open a pull request for review.

### Bug Fixing
**Trigger:** When resolving a reported issue  
**Command:** `/fix-bug`

1. Identify the bug and create a branch named `fix_<short-description>`.
2. Apply the fix, ensuring code style conventions are followed.
3. Add or update relevant tests.
4. Use a commit message starting with `fix:`.
5. Submit a pull request referencing the issue.

### Testing
**Trigger:** When verifying code correctness  
**Command:** `/run-tests`

1. Locate or create test files matching the `*.test.*` pattern.
2. Write tests for new or modified code.
3. Run the tests using the project's preferred method (framework not specified; use `go test` by default).
4. Ensure all tests pass before merging changes.

## Testing Patterns

- Test files follow the `*.test.*` naming pattern (e.g., `inference_engine.test.go`).
- The specific testing framework is not detected; standard Go testing practices are assumed.
- Example test file:
    ```go
    // inference_engine.test.go
    package main

    import "testing"

    func TestRunInference(t *testing.T) {
        result := RunInference("test input")
        if result.Success != true {
            t.Errorf("Expected success, got %v", result.Success)
        }
    }
    ```

## Commands
| Command      | Purpose                                 |
|--------------|-----------------------------------------|
| /contribute  | Start a new feature or bugfix workflow  |
| /fix-bug     | Begin the process of fixing a bug       |
| /run-tests   | Run the test suite                      |
```
