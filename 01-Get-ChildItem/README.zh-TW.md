# 01 — 列出與瀏覽項目

本單元介紹如何使用 `Get-ChildItem` 查看資料夾中的檔案與子資料夾，並練習指定路徑、篩選結果及顯示隱藏項目。

## 學習目標

- 列出目前位置或指定位置中的項目。
- 使用常見參數調整列出結果。
- 看懂命令輸出的檔案與資料夾資訊。

## 命令範例

```powershell
# 列出目前位置的項目
Get-ChildItem

# 列出指定資料夾的項目
Get-ChildItem -Path .

# 只列出副檔名為 .txt 的檔案
Get-ChildItem -Filter *.txt

# 包含隱藏項目
Get-ChildItem -Force

# 列出目前位置及其子資料夾中的項目
Get-ChildItem -Recurse
```

`Get-ChildItem` 的輸出是 PowerShell 物件，包含名稱、路徑、項目類型與時間等資訊。可使用 `Get-Help Get-ChildItem -Examples` 查看更多範例。

## 練習

1. 列出目前位置的項目，辨認檔案與資料夾。
2. 指定一個練習資料夾，列出其中的項目。
3. 使用 `-Filter` 找出特定副檔名的檔案。
4. 比較一般列出結果與加入 `-Force` 後的結果。

本單元的範例只用於列出項目。使用 `-Recurse` 前，請確認指定的路徑與範圍。
