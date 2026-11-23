# Codebase Graph Lite

一個純 Markdown 的 Codex 技能，用來在改程式前看清楚入口、呼叫關係和影響範圍。Codex 用現有的工具讀檔與搜尋，再畫 Mermaid 圖，並附上證據所在的檔案和行號。

全程無需 Python、Node.js 或額外套件。技能沒有 hook，原本的讀檔和搜尋方式照常運作。

## 安裝

把 [`codebase-graph-lite` 技能資料夾](.agents/skills/codebase-graph-lite/) 複製到下列任一位置。

| 範圍 | 技能檔案的位置 |
| --- | --- |
| 只在某個專案使用 | `<專案根目錄>/.agents/skills/codebase-graph-lite/SKILL.md` |
| 在本機各個專案使用 | `~/.agents/skills/codebase-graph-lite/SKILL.md`，Windows 對應 `%USERPROFILE%\.agents\skills\codebase-graph-lite\SKILL.md` |

[Codex 技能安裝與載入位置](https://developers.openai.com/codex/skills)

## 用法

在 Codex 對話中選擇 `$codebase-graph-lite`，然後描述你想查的路徑。例如：

> $codebase-graph-lite 先畫出匯入憑證從 CLI 和 HTTP API 到 Application use case 的呼叫路徑。標出 DI 綁定在哪裡，以及這次改用例會影響哪些入口。

圖上的實線代表能從原始碼或設定確認的關係。虛線代表依目前證據推測、仍有條件待確認的關係。你也可以請 Codex 把圖和證據存成專案內的 Markdown，日後再查時會先核對目前的程式碼。
