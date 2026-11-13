# CodeCraft

**CodeCraft** 是面向 Claude Code 與 Codex 的通用「程式實作與驗證」Skill，以**最小變更、遵循既有設計、實際驗證**為原則，適用於功能開發、Bug 修正與使用者明確要求的重構。

## 核心能力

- 遵循 KISS、YAGNI，不為假設中的未來需求過度設計，也不從假設情境推演第二層、第三層需求。
- 優先沿用現有程式架構、API、套件與術語，不順便重構無關程式。
- 收錄個人編碼偏好（單數命名、`itor`、bool 判斷寫法、Go 檔名與回傳值等），並附範例。
- 執行與本次變更相關的測試、lint、build，明確回報真正執行的檢查結果。
- 保護既有工作樹與其他任務的暫存資料；未授權不進行 Git 歷史或遠端變更。

## Repository 結構

```text
CodeCraft/
├── README.md
├── CHANGELOG.md
└── skills/
    └── code-craft/
        └── SKILL.md
```

所有規則集中在單一 `SKILL.md`（約 1,000 tokens）。語言規則目前篇幅很小，拆成獨立檔案省下的 Token 有限，反而多一次讀檔，也可能被模型漏讀；日後某語言規則明顯變長時，再拆到 `references/`。

## 安裝

將 `skills/code-craft/` **整個資料夾**複製到所使用工具的 Skill 目錄：

| 工具 | 個人 Skill 目錄 | 專案 Skill 目錄 |
| --- | --- | --- |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` |
| Codex | `~/.agents/skills/` | `.agents/skills/` |

安裝完成後，目錄應是 `~/.claude/skills/code-craft/SKILL.md` 或 `~/.agents/skills/code-craft/SKILL.md`。路徑與載入方式請以使用中的工具版本為準。

### 回覆語言建議

Skill 只有在觸發後才會生效，因此「以繁體中文回覆」在未觸發 Skill 的對話中不會套用。若希望每次對話都使用繁體中文，建議另外寫進 `~/.claude/CLAUDE.md`（Claude Code）或 `AGENTS.md`（Codex）。

## 使用範例

- 「依現有設計實作 Go 的登入功能，完成後執行相關測試。」
- 「修正這個 C# 錯誤，僅修改必要程式，回報驗證結果。」
- 「在不變更既有 API 的前提下重構這段程式。」

## 與其他 Skill 的分工

- **SpecKeeper：** 負責確認設計規格、決策狀態與權威來源。
- **CodeCraft：** 依確認的規格實作程式，並執行相關驗證。
- **RepoFlow：** 負責 Commit、分支、PR 等版本控制流程。
- **CodeReview：** 負責由獨立審查者進行程式碼審查。

CodeCraft 可以獨立安裝，不強制依賴其他 Skill。專案有更明確的規則時，以專案規範為準。

## 維護

- 目前版本：`v0.2.0`，尚未經 Claude Code 或 Codex 實際功能測試。
- 發布新版本前，建議測試：單數命名與 `itor` 是否確實套用、lint 衝突處理、最小修改、驗證失敗處理、分析模式不改檔、Git 操作授權。
- 未預先加入 `LICENSE`；公開授權方式由 Repository 擁有人決定。
