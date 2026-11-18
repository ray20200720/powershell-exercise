# PowerShell Learning Tutorial

[繁體中文](README.zh-TW.md)

This project takes you from PowerShell fundamentals to writing reusable automation scripts through a series of progressive exercises. Each lesson introduces core concepts, provides runnable command examples, and offers hands-on tasks for practice.

## Learning Objectives

After completing this tutorial, you will be able to:

- Navigate files, work with objects, and use the pipeline in PowerShell.
- Look up command usage and combine commands to perform everyday administrative tasks.
- Write scripts using variables, conditionals, loops, functions, and error handling.
- Safely work with files, text, CSV, JSON, and system information.
- Write, test, and maintain simple automation tools.

## Audience and Environment

- Suitable for beginners; no prior programming experience is required.
- Windows PowerShell 5.1 or PowerShell 7 is recommended. Follow each lesson's notes for version-specific differences.
- Before practicing, run `$PSVersionTable` in a terminal to check your PowerShell version.
- Use a dedicated practice directory to avoid running exercises against important files or production environments.

## Learning Path

| Lesson | Topic | What You'll Learn |
| --- | --- | --- |
| 01 | Listing and navigating items | Use `Get-ChildItem`, paths, and basic filtering |
| 02 | Command discovery and help | Use `Get-Command`, `Get-Help`, parameters, and command conventions |
| 03 | Command syntax and naming conventions | Learn Verb-Noun naming, aliases, positional parameters, and common parameters |
| 04 | Paths and providers | Use `Test-Path`, relative and absolute paths, and understand the file system provider |
| 05 | The pipeline and objects | Pass objects through the pipeline and understand properties, methods, and pipeline behavior |
| 06 | Selecting, filtering, and sorting | Use commands such as `Select-Object`, `Where-Object`, and `Sort-Object` |
| 07 | Variables, types, and operators | Store, compare, and convert data, and use operators |
| 08 | Strings and formatting | Interpolate, split, replace, and format text |
| 09 | Arrays and hash tables | Create collections, access elements, and organize key-value data |
| 10 | Conditional logic | Use `if`, `elseif`, `else`, and `switch` |
| 11 | Loops and flow control | Use `foreach`, `for`, `while`, `break`, and `continue` |
| 12 | Introduction to functions | Package repeated tasks into reusable functions |
| 13 | Function parameters and scope | Design parameters, validate input, and understand variable scope |
| 14 | Working with files and directories | Create, copy, move, rename, and safely delete items |
| 15 | Text files, encoding, and regular expressions | Read and write text, handle encoding, and search with regular expressions |
| 16 | Working with CSV data | Import, filter, modify, and export tabular data |
| 17 | JSON and XML | Parse and generate common structured data formats |
| 18 | Error handling and debugging | Diagnose issues using `try`, `catch`, `finally`, and debugging tools |
| 19 | Output, reports, and logging | Format results, export data, and log execution details |
| 20 | Process management | Inspect, start, and stop processes, and understand the impact of these actions |
| 21 | Services, events, and system information | Inspect services, event logs, and basic system status |
| 22 | Environment variables and PowerShell profiles | Use environment variables and understand profiles and commands loaded at startup |
| 23 | Network diagnostics fundamentals | Check connectivity, name resolution, and network status with common commands |
| 24 | Web requests and REST APIs | Call APIs with `Invoke-RestMethod` and handle responses |
| 25 | Background jobs and workflows | Start and manage background jobs and retrieve their results |
| 26 | Remote management concepts | Learn about PowerShell Remoting, connection requirements, and security principles |
| 27 | Script security and execution policies | Understand execution policies, permissions, trusted sources, and sensitive data protection |
| 28 | Modules and code reuse | Import, explore, and create modules to organize reusable commands |
| 29 | Testing and code quality | Write basic tests, validate input, and check script quality |
| 30 | Capstone project | Build a file inventory or data reporting tool, with tests and usage instructions |

Start with Lesson 01. Add later lessons as folders and exercise files using the same numbering. Each topic can also be divided into several short exercises.

## Checking Paths with Test-Path

Use `Test-Path` to check whether a path exists. It returns `$true` when the path exists and `$false` when it does not. Use `-PathType Leaf` to check for a file or `-PathType Container` to check for a directory.

```powershell
# Check whether a path exists
Test-Path -Path .\README.md

# Check whether a path is a file or directory
Test-Path -Path .\README.md -PathType Leaf
Test-Path -Path .\01-Get-ChildItem -PathType Container
```

Run `Get-Help Test-Path -Examples` to see more examples.

## Suggested Lesson Format

Each lesson should include:

1. **Objectives**: List what learners should be able to do after the lesson.
2. **Concepts and examples**: Explain syntax and output with concise commands.
3. **Hands-on exercises**: Progress from modifying examples to completing a small task independently.
4. **Knowledge check**: Verify the result and explain what the commands do.
5. **Further challenge**: Add filtering, error scenarios, or other requirements.

## Recommended Study Approach

1. Read the lessons in order and run the examples line by line in a terminal.
2. Before running a command, understand what data it will read or modify.
3. Adjust parameters and observe the output instead of only copying and pasting.
4. After completing an exercise, try it again without looking at the example.
5. For an unfamiliar command, use `Get-Help <command-name> -Examples` to see examples. If local help is not installed, try `Get-Help <command-name> -Online`.

## Safety Notes

- Start with a practice directory and test data.
- Before deleting, overwriting, or making large-scale changes, verify the path and target. When needed, preview commands that support `-WhatIf`.
- Do not apply example commands directly to production environments or run commands as an administrator without understanding their effects.
- Script execution policies may restrict `.ps1` files. Check the current policy first; do not lower system security settings arbitrarily just to practice.

## Progress Tracker

- [ ] 01 — Listing and navigating items
- [ ] 02 — Command discovery and help
- [ ] 03 — Command syntax and naming conventions
- [ ] 04 — Paths and providers
- [ ] 05 — The pipeline and objects
- [ ] 06 — Selecting, filtering, and sorting
- [ ] 07 — Variables, types, and operators
- [ ] 08 — Strings and formatting
- [ ] 09 — Arrays and hash tables
- [ ] 10 — Conditional logic
- [ ] 11 — Loops and flow control
- [ ] 12 — Introduction to functions
- [ ] 13 — Function parameters and scope
- [ ] 14 — Working with files and directories
- [ ] 15 — Text files, encoding, and regular expressions
- [ ] 16 — Working with CSV data
- [ ] 17 — JSON and XML
- [ ] 18 — Error handling and debugging
- [ ] 19 — Output, reports, and logging
- [ ] 20 — Process management
- [ ] 21 — Services, events, and system information
- [ ] 22 — Environment variables and PowerShell profiles
- [ ] 23 — Network diagnostics fundamentals
- [ ] 24 — Web requests and REST APIs
- [ ] 25 — Background jobs and workflows
- [ ] 26 — Remote management concepts
- [ ] 27 — Script security and execution policies
- [ ] 28 — Modules and code reuse
- [ ] 29 — Testing and code quality
- [ ] 30 — Capstone project
