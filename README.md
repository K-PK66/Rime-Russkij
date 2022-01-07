# Russkij 音導俄拼
![Image](https://github.com/K-PK66/Rime-Russkij/blob/main/Images/Display.gif)

基於Rime中州韻輸入法引擎的俄文輸入方案，**支持自動聯想功能**。本輸入法旨在幫助更多俄語初學者或對俄語輸入鍵位不熟悉的人，因而沒有採用俄文鍵盤格式或macOS自帶音標型俄語輸入方案，而是採用了基於GOST 1971和英國標準兩者進行結合並改良的新方案（關於各字母的輸入鍵法，請看dict文件。dict文件還在開發狀態，詞庫尚不完全）。

## 下載、安裝、使用
下載、安裝Rime輸入法引擎，請點擊[這裏](rime.im)。

下載本輸入方案，請點擊[這裏](https://github.com/K-PK66/Rime-Russkij/archive/refs/heads/main.zip)。

只需要將這裏所有yaml文件拽入設定文件夾，之後在default.custom.yaml中“schema_list:”一欄添加如下代碼後重新部署即可使用：

```
- schema: russkij
```

## 版本記錄
### v 2022.1.1
創建該輸入法，並滿足字母表順序ай-及其以前的詞庫聯想輸出。（2022年1月7日）
