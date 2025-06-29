# 開發指令索引

這個資料夾包含所有專案開發相關的指令和工作流程文件。

## 📁 檔案結構

### 📋 Instructions 檔案 (*.instructions.md)

#### Git 工作流程
- `git-workflow-complete.instructions.md` - 完整的 Git 工作流程指南
- `commit-guidelines.instructions.md` - Commit 訊息規範

#### 功能開發規格
- `feature-spec-template.instructions.md` - 功能規格文件模板
- `prompt-and-instruction-creation.instructions.md` - Prompt 和 Instruction 建立指引

### 📝 Prompts 檔案 (*.prompt.md)
位於 `.github/prompts/` 目錄中的提示訊息檔案：
- `create-env.prompt.md` - 環境設定提示

## 📝 檔案命名規則

### Instructions 檔案
- 格式：`{concept}.instructions.md`
- 用途：提供詳細的背景知識、上下文和最佳實踐
- 位置：`.github/instructions/`

### Prompts 檔案
- 格式：`{purpose}.prompt.md`
- 用途：引導用戶完成特定任務或自動化開發工作
- 位置：`.github/prompts/`

## 📋 使用方式

### Instructions 檔案使用
1. **新功能開發**：先閱讀 `git-workflow-complete.instructions.md`
2. **建立規格文件**：使用 `feature-spec-template.instructions.md` 模板
3. **提交程式碼**：遵循 `commit-guidelines.instructions.md` 規範
4. **建立新提示**：參考 `prompt-and-instruction-creation.instructions.md`

### Prompts 檔案使用
1. **環境設定**：使用 `create-env.prompt.md` 引導設定
2. **自動化任務**：建立對應的 agent 模式 prompt
3. **用戶引導**：建立 ask 模式 prompt 收集資訊

## 🔄 更新規則

- 所有新的開發指令使用 `*.instructions.md` 格式
- 所有提示訊息使用 `*.prompt.md` 格式並放在 `.github/prompts/` 目錄
- 檔案命名使用小寫字母和連字符
- 每個文件都應包含明確的使用指南和範例
- Instructions 檔案應提供詳細的背景知識和上下文
- Prompts 檔案應包含適當的 frontmatter 設定

---

## 📖 了解更多

- 詳細的 Prompt 和 Instruction 建立指引：`prompt-and-instruction-creation.instructions.md`
- Git 工作流程：`git-workflow-complete.instructions.md`
- 功能規格模板：`feature-spec-template.instructions.md`

當你需要特定的開發指引時，請參考對應的 instructions 檔案或建立新的指令文件。
