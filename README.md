# AgentSwift

A Swift code analysis and refactoring toolkit built on SwiftSyntax. Detects code issues, style problems, and suggests improvements.

## Features

SwiftCodeChecker can detect various issues in Swift code, including:

- **Syntax and Compilation Issues**: Identify syntax errors and compilation problems
- **Unused Variables**: Find variables that are declared but never used
- **Immutable Assignments**: Detect attempts to modify immutable values (let constants)
- **Unreachable Code**: Identify code that will never be executed
- **Force Unwraps**: Highlight potentially unsafe force unwraps of optionals
- **Operator Precedence**: Find ambiguous operator precedence that might lead to unexpected behavior
- **Code Style**: Check for proper formatting, indentation, and whitespace
- **Refactoring Opportunities**: Identify duplicate code and large functions/classes that could be refactored
- **Symbol Usage**: Analyze how symbols are used in your codebase
- **Macro Usage**: Validate proper usage of Swift macros

## Installation

### Using Swift Package Manager

Add SwiftCodeChecker to your `Package.swift` file:

```swift
dependencies: [
    .package(url: "https://github.com/AgentiLoop/AgentSwift.git", from: "1.1.11")
]
```

### Building from Source

```bash
git clone https://github.com/AgentiLoop/AgentSwift.git
cd AgentSwift
swift build
```

## Usage

### Command Line

The package includes two executable targets:

1. `swift-checker-demo`: Demonstrates the functionality with a sample file
2. `swift-checker-test`: Runs a comprehensive test suite

Run them using:

```bash
swift run swift-checker-demo
swift run swift-checker-test
```

You can also analyze specific files and generate reports:

```bash
# Analyze a specific file
swift run swift-checker-demo path/to/your/file.swift

# Generate a Markdown report
swift run swift-checker-demo --report path/to/your/file.swift

# Specify a custom report output path
swift run swift-checker-demo --report report.md path/to/your/file.swift
```

For convenience, you can also use the provided wrapper script:

```bash
# Make the script executable
chmod +x swift-code-checker.swift

# Run the checker on a file
./swift-code-checker.swift path/to/your/file.swift

# Generate a report
./swift-code-checker.swift --report path/to/your/file.swift
```

### As a Library

```swift
import xcf_swift

let checker = SwiftCodeChecker()

// Run individual checks
let syntaxIssues = try checker.checkSwiftSyntax(at: "path/to/your/file.swift")
let unusedVars = try checker.checkUnusedVariables(at: "path/to/your/file.swift")
let styleIssues = try checker.checkCodeStyle(at: "path/to/your/file.swift")

// Or run all checks at once
let allIssues = try checker.runAllChecks(at: "path/to/your/file.swift")

// Process the issues
for issue in allIssues {
    print("[\(issue.severity)] Line \(issue.line):\(issue.column) - \(issue.description)")
}
```

## Available Checks

| Check | Description |
|-------|-------------|
| `checkSwiftSyntax` | Basic syntax and parsing errors |
| `checkUnusedVariables` | Variables declared but never used |
| `checkImmutableAssignments` | Attempts to modify immutable values |
| `checkUnreachableCode` | Code that will never be executed |
| `checkForceUnwraps` | Force unwraps of optional values |
| `checkOperatorPrecedence` | Ambiguous operator precedence issues |
| `checkCodeStyle` | Code formatting and style issues (standalone) | 
| `checkRefactoringOpportunities` | Code that could benefit from refactoring |
| `checkSymbolUsage` | Analysis of how symbols are used |
| `checkMacroUsage` | Validation of Swift macro usage |
| `checkMemoryLeaks` | Potential memory leaks |
| `checkEmptyCatchBlocks` | Empty catch blocks |
| `checkMagicNumbers` | Hardcoded magic numbers |
| `checkOptionalChainingDepth` | Excessive optional chaining |

## Requirements

- Swift 6.4+
- macOS 14+

## Part of AgentiLoop Agent!

AgentSwift is one of the open-source building blocks of **[AgentiLoop Agent!](https://github.com/AgentiLoop/Agent)**, the native AI agent for macOS 14.6+ on Apple Silicon and Intel. Agent! codes in Xcode, drives any Mac app, runs shell as you or as root, and works with 23 LLM providers plus on-device Apple Intelligence.

🌐 [agentiloop.ai](https://agentiloop.ai/) · ⬇️ [Download Agent!](https://github.com/AgentiLoop/Agent/releases/latest) · 🍺 `brew install --cask agentiloop-agent` · 💻 CLIs: [Rust](https://github.com/AgentiLoop/AgentiLoopCLI) / [Go](https://github.com/AgentiLoop/AgentiLoopGo)

**More Agent! packages:** [AgentAccess](https://github.com/AgentiLoop/AgentAccess) · [AgentAudit](https://github.com/AgentiLoop/AgentAudit) · [AgentColorSyntax](https://github.com/AgentiLoop/AgentColorSyntax) · [AgentD1F](https://github.com/AgentiLoop/AgentD1F) · [AgentEventBridges](https://github.com/AgentiLoop/AgentEventBridges) · [AgentLLM](https://github.com/AgentiLoop/AgentLLM) · [AgentMCP](https://github.com/AgentiLoop/AgentMCP) · [AgentTerminalNeo](https://github.com/AgentiLoop/AgentTerminalNeo) · [AgentTools](https://github.com/AgentiLoop/AgentTools) · [AgentScripts](https://github.com/AgentiLoop/AgentScripts)

## License

This project is licensed under the MIT License - see the LICENSE file for details. 

---

Copyright © 2026 AgentiLoop.ai, a Logos InkPen LLC company. All rights reserved.
