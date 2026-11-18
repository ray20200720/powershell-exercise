# 01 — Listing and Navigating Items

This lesson introduces `Get-ChildItem` for viewing files and subdirectories. You will practice specifying paths, filtering results, and displaying hidden items.

## Learning Objectives

- List items in the current location or a specified location.
- Adjust the results with common parameters.
- Understand the file and directory information returned by the command.

## Command Examples

```powershell
# List items in the current location
Get-ChildItem

# List items in a specified directory
Get-ChildItem -Path .

# List only files with the .txt extension
Get-ChildItem -Filter *.txt

# Include hidden items
Get-ChildItem -Force

# List items in the current location and its subdirectories
Get-ChildItem -Recurse
```

`Get-ChildItem` returns PowerShell objects that include information such as the name, path, item type, and timestamps. Run `Get-Help Get-ChildItem -Examples` to see more examples.

## Paging Through Results

When there are many items, pipe the results to `Out-Host -Paging` to view them page by page:

```powershell
Get-ChildItem | Out-Host -Paging
```

To view a fixed number of 20 items per page, use `Select-Object` to skip earlier items:

```powershell
# Page 1
Get-ChildItem | Select-Object -First 20

# Page 2
Get-ChildItem | Select-Object -Skip 20 -First 20
```

## Exercises

1. List the items in the current location and identify the files and directories.
2. Specify a practice directory and list its items.
3. Use `-Filter` to find files with a particular extension.
4. Compare the regular results with the results returned when using `-Force`.

The examples in this lesson only list items. Before using `-Recurse`, verify the specified path and scope.
