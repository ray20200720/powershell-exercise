# 03 — Command Syntax and Naming Conventions

This lesson introduces PowerShell's `Verb-Noun` naming convention, aliases, positional parameters, and common parameters. You will learn how to read command syntax and choose clear, predictable commands.

## Learning Objectives

- Recognize the `Verb-Noun` structure used by PowerShell cmdlets.
- Find the full command name behind an alias.
- Use named and positional parameters.
- Identify common parameters available to many cmdlets.

## Verb-Noun Naming

PowerShell cmdlets usually use an approved verb followed by a noun:

```powershell
Get-Process
New-Item
Copy-Item
Remove-Item
```

The verb describes the action, while the noun identifies the target. Use `Get-Verb` to inspect approved verbs:

```powershell
Get-Verb

# Show verbs in a specific group
Get-Verb | Where-Object Group -eq Common
```

Use clear, descriptive names when creating functions so their purpose is consistent with standard PowerShell commands.

## Aliases

An alias is a short alternative name for a command:

```powershell
# gci is an alias for Get-ChildItem
Get-Alias -Name gci

# Expand an alias from a command session
Get-Alias -Name gci, gal, gps
```

Aliases can save typing during interactive use, but full command names are easier to understand in scripts and shared documents:

```powershell
# Concise interactive form
gci

# Clearer form for scripts
Get-ChildItem
```

Use `Get-Alias` to search for aliases:

```powershell
Get-Alias -Definition Get-ChildItem
```

## Named and Positional Parameters

A named parameter includes its name and value:

```powershell
Get-ChildItem -Path . -Filter *.txt
```

A positional parameter can be supplied without its name:

```powershell
Get-ChildItem . -Filter *.txt
```

Use `Get-Command -Syntax` to inspect where parameters can appear:

```powershell
Get-Command Get-ChildItem -Syntax
```

Prefer named parameters in scripts because they make the command's intent explicit and remain easier to read as the command's parameter definitions change.

## Common Parameters

Many PowerShell cmdlets support the same common parameters:

```powershell
# Preview supported changes instead of performing them
Remove-Item -Path .\practice.txt -WhatIf

# Ask for confirmation
Remove-Item -Path .\practice.txt -Confirm

# Display detailed progress messages
Get-ChildItem -Path . -Verbose

# Suppress recovery from non-terminating errors
Get-ChildItem -Path . -ErrorAction SilentlyContinue
```

Other common parameters include `-Debug`, `-WarningAction`, and `-OutVariable`. Whether a common parameter changes the command's behavior depends on the parameter and cmdlet.

## Exercises

1. Use `Get-Verb` to find five approved verbs and describe the action each suggests.
2. Use `Get-Alias -Name gcm, gci, gps` and write the full name of each command.
3. Run `Get-ChildItem -Path .` and then rewrite it using the path as a positional value.
4. Display the syntax for `Copy-Item` and identify its positional parameters.
5. Run a command that supports `-WhatIf` and preview the action before allowing it to run.

Do not run commands that modify or delete files until you have confirmed the path and scope. Use `-WhatIf` when a cmdlet supports it.
