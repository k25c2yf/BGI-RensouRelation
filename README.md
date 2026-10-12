# 戀想關係 開源中文補丁（UTF-8 / BGI）

《恋想リレーション》（戀想關係／恋想关系）BGI 引擎中文補丁，由 **開源漢化組** 製作。

- 繁體：BIG5 流程
- 簡體：GBK 流程

> **本倉庫不提供編譯好的執行檔**，只提供自行編譯用的材料與遊戲攻略。

---

## 年齡分級

本作為 **18+** 成人遊戲。未滿十八歲（或未達你所在地區法定成年年齡）請勿下載、安裝或遊玩。

---

## 自行編譯／重新打包

### 環境

- Windows
- [Python 3](https://www.python.org/downloads/)（安裝時勾選 Add Python to PATH）
- 7-Zip（解分卷壓縮 `.7z.001`）
- [Enigma Virtual Box](https://enigmaprotector.com/en/aboutvb.html)（倉庫內 `Enigma Virtual Box/enigmavb.exe`）
- 自行持有的正版《恋想リレーション》

下載整個倉庫（Code → Download ZIP，或 `git clone`）後，在倉庫**根目錄**操作。

### 主要路徑

| 路徑 | 用途 |
|---|---|
| `source/` | 原版腳本 |
| `big5/` | 繁中劇本 txt（含 `Custom_tc.txt`、`SetupForEtc_tc.txt`） |
| `jp/jpname/` | 各章原日文人名表（對應 `●編號●`） |
| `big5pic.7z.001`～`.004` | 繁中圖片分卷 |
| `gbkpic.7z.001`～`.004` | 簡中圖片分卷 |
| `font/` | 字型（`HuiFont29.ttf`、`PixlMpls12.ttf`） |
| `sysprg/sysprg_big5/` | 繁中系統 `_bp` |
| `sysprg/sysprg_GBK/` | 簡中系統 `_bp` |
| `rensou_UTF8_FIX.exe` | 已改 UTF-8 的主程式（Enigma 輸入檔） |
| `outputbig5.bat` / `outputgbk.bat` | 編譯腳本 |
| `繁體中文轉簡體中文.py` | 繁→簡劇本轉換 |

### `jp/jpname`：人名必須保留日文

`jp/jpname/` 對應劇本裡 `●編號●` 的**原日文說話人名**。引擎靠日文原名對人名圖片，改成中文會對不到圖。請勿把這裡改成中文。

### 不可修改的地方

- 主程式內的 `RensouRelation` 字串是啟動判定與檔案檢查條件，**絕對不可修改**。
- 選項關鍵字（`Custom_tc.txt`）要與劇本中登錄的關鍵字文字完全相同，否則隱藏選項無法觸發。

### 1. 解圖片分卷

用 7-Zip 對 `big5pic.7z.001`、`gbkpic.7z.001` 解壓（會自動接續其他分卷），解成**資料夾**。

### 2. 繁體：編譯

```bat
outputbig5.bat
```

成功後產生 `outputbig5/`（過程用 `temp/`）。

### 3. 繁體：Enigma Virtual Box 打包

1. 主程式 **Input File**：`rensou_UTF8_FIX.exe`
2. Files 加入：
   - `big5pic/`（`big5pic.7z.001` 解壓出來的繁中圖片）
   - `font/`
   - `outputbig5/`
   - `sysprg/sysprg_big5/`
3. 輸出檔名例：`RensouRelation-BIG5.exe`
4. Process。

`_bp` 檔名要與原版一致，不要多包一層資料夾。

### 4. 簡體：轉換並編譯

```bat
outputgbk.bat
```

`outputgbk.bat` 會先執行 `繁體中文轉簡體中文.py`（讀 `./big5`，寫 `./gbk`），再編譯到 `outputgbk/`。

### 5. 簡體：Enigma Virtual Box 打包

1. 主程式同樣用 `rensou_UTF8_FIX.exe`
2. Files 加入：
   - `font/`
   - `gbkpic/`（`gbkpic.7z.001` 解壓出來的簡中圖片）
   - `outputgbk/`
   - `sysprg/sysprg_GBK/`
3. 輸出檔名例：`RensouRelation-GBK.exe`

---

## 中文化範圍

- 劇本繁／簡中文化（控制符、ruby 保留）
- 選項與關鍵字（`Custom`）、時間線流程圖文字（`SetupForEtc`）
- 系統 `_bp` 文字、視窗標題、backlog 選項顯示修正
- BMP 圖片（UI、關鍵字卡、阿茲轉場圖等）與字型

---

## 攻略

倉庫附《戀想關係 全收集攻略》（繁／簡，docx／pdf），包含四位女主角路線、關鍵字取得位置、特典 H 與 CG 全收集方法。

小提示：關鍵字是在劇情中以登錄方式取得；四條線全通後，開新遊戲進入 `_01` 開頭才會解鎖特典 H 的「叮」「嘛」。

---

## 注意與免責

- 遊戲著作權歸原製作公司及相關權利人。本專案只提供粉絲翻譯與技術適配，與官方無關。
- 補丁免費、僅供個人學習與研究，禁止販售。
- 解包、改檔、使用封裝工具的風險由使用者自行承擔。
- 文本含機器翻譯後人工修潤，歡迎開 Issue／PR。

---

## 回報問題

請開 Issue 並附上：BIG5 或 GBK、章節與對話 ID（如 `●018672●`）、截圖。
