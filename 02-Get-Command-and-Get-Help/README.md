# 02 — Command Discovery and Help

This lesson explains how to discover PowerShell commands, inspect their syntax and parameters, and read local or online help before running them.

## Learning Objectives

- Find commands by name, verb, noun, or module.
- Read a command's syntax, parameters, examples, and detailed description.
- Distinguish cmdlets, functions, aliases, and external applications.
- Use named and positional parameters while following PowerShell command conventions.

## Finding Commands

Use `Get-Command` to discover commands available in the current session:

```powershell
# Find commands whose names contain "Process"
Get-Command -Name *Process*

# Find commands with the Get verb
Get-Command -Verb Get

# Find only cmdlets
Get-Command -CommandType Cmdlet

# Find commands from a particular module
Get-Command -Module Microsoft.PowerShell.Management
```

The `CommandType` column identifies how a command is implemented. Common types include `Cmdlet`, `Function`, `Alias`, and `Application`.

## Reading Command Help

Use `Get-Help` to learn what a command does and which parameters it accepts:

```powershell
# Display the help summary
Get-Help Get-Process

# Show runnable examples
Get-Help Get-Process -Examples

# Show detailed help, including parameter descriptions
Get-Help Get-Process -Detailed

# Show all available help
Get-Help Get-Process -Full

# Open the online documentation when an internet connection is available
Get-Help Get-Process -Online
```

The examples are a useful starting point, but always read the parameter descriptions and confirm the command's effects before adapting them.

## Viewing Syntax and Parameters

Inspect the command's accepted forms with its syntax:

```powershell
Get-Command Get-Process -Syntax
```

Inspect one parameter:

```powershell
Get-Help Get-Process -Parameter Name
```

Parameters in square brackets, such as `[<CommonParameter>]`, are optional. Parameter sets group combinations of parameters that can be used together.

## Named and Positional Parameters

A named parameter makes its purpose explicit:

```powershell
Get-Process -Name pwsh
```

If a parameter supports a positional value, its parameter name can be omitted:

```powershell
Get-Process pwsh
```

Prefer named parameters when learning commands or writing reusable scripts because they are clearer and less dependent on parameter position.

## Command Conventions

PowerShell cmdlet names follow the `Verb-Noun` convention:

- `Get` retrieves information.
- `Set` changes a value.
- `New` creates an item.
- `Remove` deletes an item.

```powershell
# Inspect approved verbs
Get-Verb

# Display command information as objects
Get-Command -Name Get-ChildItem | Select-Object Name, CommandType, Source
```

`Get-Command` and `Get-Help` only display information about commands; they do not perform the action described by the command being inspected.

## Exercises

1. Find all available commands whose names contain `Item`.
2. Use `Get-Command` to identify whether `Get-Help` is a cmdlet or function.
3. Display the examples for `Get-ChildItem`.
4. Inspect the syntax of `Get-ChildItem` and explain the difference between named and positional parameters.
5. Find commands that use the `Test` verb and choose one to inspect with `Get-Help`.

If help content is missing, run `Update-Help` only when your environment and network policy allow it. Updating help may require elevated permissions.
