# 02 — 命令探索與說明

本單元介紹如何探索 PowerShell 命令、查看語法與參數，以及在執行命令前閱讀本機或線上說明。

## 學習目標

- 依名稱、動詞、名詞或模組尋找命令。
- 閱讀命令的語法、參數、範例與詳細說明。
- 分辨 Cmdlet、函式、別名及外部應用程式。
- 使用具名及位置參數，並遵循 PowerShell 命令慣例。

## 尋找命令

使用 `Get-Command` 探索目前工作階段中可用的命令：

```powershell
# 尋找名稱包含 Process 的命令
Get-Command -Name *Process*

# 尋找使用 Get 動詞的命令
Get-Command -Verb Get

# 只列出 Cmdlet
Get-Command -CommandType Cmdlet

# 尋找指定模組中的命令
Get-Command -Module Microsoft.PowerShell.Management
```

`CommandType` 欄位表示命令的實作類型，常見類型包含 `Cmdlet`、`Function`、`Alias` 與 `Application`。

## 閱讀命令說明

使用 `Get-Help` 了解命令的用途與可用參數：

```powershell
# 顯示說明摘要
Get-Help Get-Process

# 顯示可執行的範例
Get-Help Get-Process -Examples

# 顯示詳細說明及參數描述
Get-Help Get-Process -Detailed

# 顯示完整說明
Get-Help Get-Process -Full

# 在可連線時開啟線上文件
Get-Help Get-Process -Online
```

範例適合作為起點，但套用前仍應閱讀參數描述，並確認命令會產生的影響。

## 查看語法與參數

查看命令可接受的語法形式：

```powershell
Get-Command Get-Process -Syntax
```

查看單一參數：

```powershell
Get-Help Get-Process -Parameter Name
```

方括號中的內容（例如 `[<CommonParameter>]`）為選用項目。參數集則用來表示可以一起使用的參數組合。

## 具名與位置參數

具名參數會明確表示參數用途：

```powershell
Get-Process -Name pwsh
```

若參數支援位置值，也可以省略參數名稱：

```powershell
Get-Process pwsh
```

學習命令或撰寫可重用腳本時，建議優先使用具名參數，因為內容更清楚，也不會依賴參數位置。

## 命令慣例

PowerShell Cmdlet 名稱遵循 `Verb-Noun` 慣例：

- `Get`：取得資訊。
- `Set`：變更值。
- `New`：建立項目。
- `Remove`：刪除項目。

```powershell
# 查看核准使用的動詞
Get-Verb

# 以物件方式顯示命令資訊
Get-Command -Name Get-ChildItem | Select-Object Name, CommandType, Source
```

`Get-Command` 與 `Get-Help` 只會顯示命令資訊，不會執行被查詢命令所描述的操作。

## 練習

1. 尋找名稱包含 `Item` 的所有可用命令。
2. 使用 `Get-Command` 確認 `Get-Help` 是 Cmdlet 還是函式。
3. 顯示 `Get-ChildItem` 的範例。
4. 查看 `Get-ChildItem` 的語法，並說明具名參數與位置參數的差異。
5. 尋找使用 `Test` 動詞的命令，挑選一個並使用 `Get-Help` 查看說明。

若說明內容尚未安裝，請在環境及網路政策允許時執行 `Update-Help`。更新說明可能需要提高權限。
