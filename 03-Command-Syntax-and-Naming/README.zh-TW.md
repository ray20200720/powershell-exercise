# 03 — 命令語法與命名慣例

本單元介紹 PowerShell 的 `Verb-Noun` 命名方式、別名、位置參數與常見參數。完成後，將能閱讀命令語法並選擇清楚、可預期的命令寫法。

## 學習目標

- 認識 PowerShell Cmdlet 常用的 `Verb-Noun` 命名結構。
- 查出別名對應的完整命令名稱。
- 使用具名參數與位置參數。
- 辨認多數 Cmdlet 可使用的常見參數。

## Verb-Noun 命名

PowerShell Cmdlet 通常由核准的動詞與名詞組成：

```powershell
Get-Process
New-Item
Copy-Item
Remove-Item
```

動詞描述操作，名詞則指出操作目標。可使用 `Get-Verb` 查看核准使用的動詞：

```powershell
Get-Verb

# 顯示指定分類的動詞
Get-Verb | Where-Object Group -eq Common
```

建立函式時，使用清楚且具描述性的名稱，讓用途與標準 PowerShell 命令一致。

## 別名

別名是命令的簡短替代名稱：

```powershell
# gci 是 Get-ChildItem 的別名
Get-Alias -Name gci

# 一次查詢多個別名
Get-Alias -Name gci, gal, gps
```

互動操作時，別名可以減少輸入；但在腳本及共用文件中，完整命令名稱通常更容易理解：

```powershell
# 適合互動操作的簡短寫法
gci

# 適合腳本的清楚寫法
Get-ChildItem
```

也可以使用 `Get-Alias` 搜尋指定命令有哪些別名：

```powershell
Get-Alias -Definition Get-ChildItem
```

## 具名與位置參數

具名參數會同時提供參數名稱與值：

```powershell
Get-ChildItem -Path . -Filter *.txt
```

位置參數可省略參數名稱，直接提供值：

```powershell
Get-ChildItem . -Filter *.txt
```

可使用 `Get-Command -Syntax` 查看參數可出現的位置：

```powershell
Get-Command Get-ChildItem -Syntax
```

在腳本中建議優先使用具名參數。即使命令的參數定義變更，也能維持較清楚、較易閱讀的操作意圖。

## 常見參數

許多 PowerShell Cmdlet 支援相同的常見參數：

```powershell
# 預覽支援的變更，但不實際執行
Remove-Item -Path .\practice.txt -WhatIf

# 執行前要求確認
Remove-Item -Path .\practice.txt -Confirm

# 顯示詳細執行訊息
Get-ChildItem -Path . -Verbose

# 不顯示可繼續執行的錯誤
Get-ChildItem -Path . -ErrorAction SilentlyContinue
```

其他常見參數還包含 `-Debug`、`-WarningAction` 與 `-OutVariable`。實際效果會依參數及 Cmdlet 而有所不同。

## 練習

1. 使用 `Get-Verb` 找出五個核准使用的動詞，並說明各動詞代表的操作。
2. 使用 `Get-Alias -Name gcm, gci, gps`，寫出每個別名對應的完整命令。
3. 執行 `Get-ChildItem -Path .`，再改成只使用位置值傳入路徑。
4. 顯示 `Copy-Item` 的語法，找出可用的位置參數。
5. 執行支援 `-WhatIf` 的命令，先預覽操作，而不要實際執行。

確認路徑與範圍前，請勿執行會修改或刪除檔案的命令。Cmdlet 支援 `-WhatIf` 時，應先使用它預覽。
