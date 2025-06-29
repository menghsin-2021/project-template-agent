# 建立 Prompt 和 Instruction 檔案指引

## 概述

本專案支援兩種類型的定義檔案格式，提供更大的靈活性和組織性：
- `.github/prompts/*.prompt.md` - 提示訊息檔案
- `.github/instructions/*.instructions.md` - 指令說明檔案

## 📝 .prompt.md 檔案格式

### 用途
`.prompt.md` 檔案用於撰寫提示訊息或引導用戶完成特定的開發任務。

### 檔案結構
```markdown
---
mode: ask|edit|agent
tools: [tool1, tool2, tool3]  # 僅在 mode: agent 時需要
description: "提示描述"
---

# 提示標題

## 提示內容
詳細的提示訊息內容...

## 預期輸出
說明預期的輸出格式或結果...
```

### 模式說明

#### 1. ask 模式
```markdown
---
mode: ask
description: "詢問用戶特定資訊的提示"
---

# 詢問專案設定

請提供以下專案設定資訊：
- 專案名稱
- 專案描述
- 技術堆疊選擇
```

#### 2. edit 模式
```markdown
---
mode: edit
description: "引導程式碼編輯的提示"
---

# 建立 React 元件

請建立一個新的 React 函式元件，包含：
- TypeScript 型別定義
- Props 介面
- 錯誤處理
- 樣式設定
```

#### 3. agent 模式
```markdown
---
mode: agent
tools: [create_file, insert_edit_into_file, run_in_terminal]
description: "自動化執行複雜任務的代理提示"
---

# 建立完整的 API 端點

請自動建立一個完整的 RESTful API 端點，包含：
- 控制器檔案
- 路由設定
- 型別定義
- 測試檔案
- 文件更新
```

### 可用工具列表
當 `mode: agent` 時，可以在 `tools` 中指定以下工具：

#### 檔案操作工具
- `create_file` - 建立新檔案
- `read_file` - 讀取檔案內容
- `insert_edit_into_file` - 編輯檔案
- `replace_string_in_file` - 替換檔案內容
- `list_dir` - 列出目錄內容

#### 搜尋工具
- `file_search` - 搜尋檔案
- `grep_search` - 文字搜尋
- `semantic_search` - 語意搜尋

#### 執行工具
- `run_in_terminal` - 執行終端命令
- `run_vs_code_task` - 執行 VS Code 任務

#### Git 工具
- `get_changed_files` - 取得變更檔案

## 📋 .instructions.md 檔案格式

### 用途
`.instructions.md` 檔案提供具體的上下文資訊，包含詳細的背景知識、精確的範例，幫助 LLM 更好地理解專案結構。

### 檔案結構
```markdown
# 指令標題

## 背景知識
詳細的背景資訊和上下文...

## 程式碼範例
```typescript
// 具體的程式碼範例
interface Example {
  // 詳細註解
}
```

## 最佳實踐
- 實踐建議 1
- 實踐建議 2

## 常見問題
### Q: 問題描述
A: 解答說明

## 相關檔案
- `src/components/` - 元件目錄
- `src/types/` - 型別定義
```

### 範例：API 開發指引
```markdown
# API 開發指引

## 背景知識
本專案使用 Express.js + TypeScript 開發 RESTful API，採用分層架構：
- Controller 層：處理 HTTP 請求
- Service 層：商業邏輯
- Repository 層：資料存取

## 程式碼範例

### 控制器範例
```typescript
import { Request, Response } from 'express';
import { UserService } from '../services/UserService';

export class UserController {
  constructor(private userService: UserService) {}

  async getUser(req: Request, res: Response) {
    try {
      const userId = req.params.id;
      const user = await this.userService.findById(userId);
      res.json(user);
    } catch (error) {
      res.status(500).json({ error: error.message });
    }
  }
}
```

## 最佳實踐
- 使用 TypeScript 型別安全
- 實作錯誤處理中間件
- 加入 API 文件（Swagger）
- 撰寫單元測試
```

## 📁 檔案組織規則

### Prompts 目錄結構
```
.github/prompts/
├── create-env.prompt.md          # 環境設定提示
├── setup-project.prompt.md       # 專案設定提示
├── create-api.prompt.md           # API 建立提示
├── deploy-app.prompt.md           # 部署應用提示
└── debug-issues.prompt.md         # 除錯提示
```

### Instructions 目錄結構
```
.github/instructions/
├── commit-guidelines.instructions.md      # Git 提交規範
├── feature-spec-template.instructions.md  # 功能規格模板
├── git-workflow-complete.instructions.md  # Git 工作流程
├── api-development.instructions.md        # API 開發指引
├── testing-guidelines.instructions.md     # 測試指引
└── deployment-process.instructions.md     # 部署流程
```

## 🚀 建立新檔案的步驟

### 建立 Prompt 檔案
1. 確定提示的目的和模式
2. 在 `.github/prompts/` 目錄中建立新檔案
3. 使用 `{purpose}.prompt.md` 命名格式
4. 填寫 frontmatter 和內容
5. 測試提示是否有效

### 建立 Instruction 檔案
1. 識別需要說明的概念或流程
2. 在 `.github/instructions/` 目錄中建立新檔案
3. 使用 `{concept}.instructions.md` 命名格式
4. 提供詳細的背景知識和範例
5. 包含最佳實踐和常見問題

## 💡 使用建議

### 何時使用 .prompt.md
- 需要引導用戶完成特定任務
- 自動化執行複雜的開發工作
- 標準化開發流程
- 減少重複性工作

### 何時使用 .instructions.md
- 提供複雜概念的詳細說明
- 建立開發標準和規範
- 分享最佳實踐和經驗
- 幫助新團隊成員理解專案

## 🔄 維護和更新

1. **定期檢視**：每月檢查檔案是否需要更新
2. **版本控制**：使用 Git 追蹤變更
3. **測試驗證**：確保提示和指令仍然有效
4. **收集回饋**：從團隊成員收集使用心得
5. **持續改善**：根據實際使用情況調整內容

## 📖 參考資源

- [AI Prompt 設計最佳實踐](https://example.com/prompt-design)
- [技術文件撰寫指引](https://example.com/tech-writing)
- [專案模板使用說明](../README.md)
