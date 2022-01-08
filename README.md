# Russkij 音導俄拼
![Image](https://github.com/K-PK66/Images/blob/main/Screen%20Recording%202022-01-07%20at%2022.11.58.gif)

Russkij (Русский) 是基於Rime中州韻輸入法引擎的俄文輸入方案，**支持自動聯想功能**。本輸入法旨在幫助更多俄語初學者或對俄語輸入鍵位不熟悉的用户，因而沒有採用俄文鍵盤格式或macOS自帶音標型俄語輸入方案，而是採用了基於GOST 1971和英國標準兩者進行結合並改良的新方案（關於各字母的輸入鍵法，請看dict文件。dict文件還在開發狀態，詞庫尚不完全）。

## 下載與安裝
下載、安裝Rime輸入法引擎，請點擊[這裏](rime.im)。

下載本輸入方案，請點擊[這裏](https://github.com/K-PK66/Rime-Russkij/releases)對應的最新版本下載（不要點擊本界面code模块直接下載，否則會有其他無關內容）。

只需要將這裏所有yaml文件拽入設定文件夾，之後在default.custom.yaml中“schema_list:”一欄添加如下代碼後重新部署即可使用：

```
- schema: russkij
```

若您沒有建立過default.custom.yaml文件，請新建之，並直接複製下方代碼後粘貼其中，隨後重新部署即可使用。

```
# default.custom.yaml
# encoding: utf-8

patch:
  switcher:
    caption: 〔方案選單〕
    hotkeys:
    - Control+grave

  # 候选词 5 个
  menu:
    page_size: 5

  schema_list:
    - schema: luna_pinyin_simp	# 朙月拼音·简化字，可以按 ctrl+` 选择临时启用正體中文
    - schema: luna_pinyin_fluency  # 语句流
    - schema: double_pinyin_flypy  # 小鶴雙拼
    - schema: wubi_pinyin          # 五笔拼音混合輸入
    - schema: wubi86               # 五笔86
    - schema: luna_pinyin_tw       # 朙月拼音·臺灣正體，可以按 ctrl+` 選擇臨時啓用简体中文
    - schema: russkij              # 音導俄拼

  ascii_composer:
    good_old_caps_lock: true
    switch_key:
      Control_L: noop
      Control_R: noop
      Caps_Lock: commit_code
      Eisu_toggle: clear
      Shift_L: commit_code
      Shift_R: commit_code

  # 默认标点符号
  # (如果不灵，则 把 luna_pinyin_simp.custom.yaml 里的 punctuator 部分注释掉 )
  punctuator:
    half_shape:
    # 列出和 英文标点 不同的 标点 (即打中文时需要 "特别改" 的标点)
    # 常用标点: 冒号 分号 顿号 名字分词号 逗号 句号 问号 感叹号 钱号 破折号 省略号
    # 成对标点: 双引号 单引号 书名号 括号

      # 常用标点
      ':' : '：'
      ';' : '；'
      '\' : '、'
      '/' : '/'
      '|' : '·'
      ',' : '，'
      '.' : '。'
      '?' : '？'
      '!' : '！'
      '$' : '￥'
      '_' : '——'
      '^' : '……'

      # 成对标点
      '''' : { pair: [ '‘', '’' ] }
      '"' : { pair: [ '“', '”' ] }
      '<' : '《'
      '>' : '》'
      '[' : '【'
      ']' : '】'
      #'(' : '（'
      #')' : '）'

#     其他标点样式参考。用它们替换上面的配置即可
#     更多参见 ori_default.yaml
#     '<' : [ 《, 〈, «, ‹ ]
#     '>' : [ 》, 〉, », › ]
#     '''' : { pair: [ '‘', '’' ] }
#     '"' : { pair: [ '“', '”' ] }
#     '/': ['/', '÷']
#     '\' : [ 、, '\', ＼ ]
#     '|' : [ ·, '|', ｜, '§', '¦' ]
#     '~' : [ '~', ～ ]
#     '%' : [ '%', ％, '°', '℃' ]
#     '$' : [ ￥, '$', '€', '£', '¥', '¢', '¤' ]
#     '*' : [ '*', ＊, ·, ・, ×, ※, ❂ ]
#     '[' : [ 「, 【, 〔, ［ ]
#     ']' : [ 」, 】, 〕,  ］ ]
#     '{' : [ 『, 〖, ｛ ]
#     '}' : [ 』, 〗, ｝ ]

  key_binder:
    bindings:
      #
      # 快捷键，更多参见 ori_default.yaml
      #
      - { when: always, accept: Shift+space, toggle: full_shape } # Shift+space 切换全角/半角
      - { when: has_menu, accept: minus, send: Page_Up }
      - { when: has_menu, accept: equal, send: Page_Down }
      #
      # paging
      #
      - { when: has_menu, accept: comma, send: Page_Up }
      - { when: has_menu, accept: period, send: Page_Down }
      #
      # more technical binding
      #
      # Emacs style
      # - { when: composing, accept: Control+p, send: Up }
      # - { when: composing, accept: Control+n, send: Down }
      # - { when: composing, accept: Control+b, send: Left }
      # - { when: composing, accept: Control+f, send: Right }
      # - { when: composing, accept: Control+a, send: Home }
      # - { when: composing, accept: Control+e, send: End }
      # - { when: composing, accept: Control+d, send: Delete }
      # - { when: composing, accept: Control+k, send: Shift+Delete }
      # - { when: composing, accept: Control+h, send: BackSpace }
      # - { when: composing, accept: Control+g, send: Escape }
      # - { when: composing, accept: Control+bracketleft, send: Escape }
      # - { when: composing, accept: Alt+v, send: Page_Up }
      # - { when: composing, accept: Control+v, send: Page_Down }
      # paging keys
      # - { when: composing, accept: ISO_Left_Tab, send: Page_Up }
      # - { when: composing, accept: Shift+Tab, send: Page_Up }
      # - { when: composing, accept: Tab, send: Page_Down }
      # - { when: has_menu, accept: minus, send: Page_Up }
      # - { when: has_menu, accept: equal, send: Page_Down }
      # - { when: paging, accept: comma, send: Page_Up }
      # - { when: has_menu, accept: period, send: Page_Down }
      # hotkey switch
      - { when: always, accept: Control+Shift+1, select: .next }
      - { when: always, accept: Control+Shift+2, toggle: ascii_mode }
      - { when: always, accept: Control+Shift+3, toggle: full_shape }
      - { when: always, accept: Control+Shift+4, toggle: simplification }
      - { when: always, accept: Control+Shift+5, toggle: extended_charset }
      - { when: always, accept: Control+Shift+exclam, select: .next }
      - { when: always, accept: Control+Shift+at, toggle: ascii_mode }
      - { when: always, accept: Control+Shift+numbersign, toggle: full_shape }
      - { when: always, accept: Control+Shift+dollar, toggle: simplification }
      - { when: always, accept: Control+Shift+percent, toggle: extended_charset }
      - { when: always, accept: Shift+space, toggle: full_shape }
      - { when: always, accept: Control+period, toggle: ascii_punct }
style:
    horizontal: true
    color_scheme: luna

```
## 使用
在按照dict文件中描述的各字母輸入方式鍵入一些字母后，輸入法將匹配以您剛鍵入的字母序列開頭的若干詞彙，並依序排在選項卡中（這一字母序列未必是該詞語的全拼，但必須從該詞語開頭起進行鍵入）。只需根據這些給出的詞彙中您所需要的左側的序號進行數字鍵入，即可將該詞彙回敲至待輸入區域。這一定程度上可以減少敲擊鍵盤耗費的時間，提升鍵入效率。若您在第一頁選項卡中沒有看到您想要的詞彙，出於達成節省時間之效的考慮，建議進一步敲擊以提供更多詞彙字母序列信息，而不是繼續翻至下一頁查找。

本輸入法目前有一定模糊音識別功能，但仍不是很健全。目前，本輸入法支持ph到f(Ф)與c到ts(Ц)的轉換。此外，目前該輸入法僅支持逐單詞回敲；換言之，一個含有n個詞語的句子需要重複操作n次“輸入—空格/編號回敲-空格分隔”的操作。

## 版本記錄
### v 2022.1.1
初代，創建該輸入法，並滿足字母表順序ай-及其以前的詞庫聯想輸出。（2022年1月7日）
### v 2022.1.1000
輸入法自動聯想詞庫條目滿千紀念版本。（2022年1月8日）下載[點此>>](https://github.com/K-PK66/Rime-Russkij/releases/tag/RusskijUpdate1000)
