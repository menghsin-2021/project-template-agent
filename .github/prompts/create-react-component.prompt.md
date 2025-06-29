---
mode: edit
description: "指導建立 React 元件的提示"
---

# 建立 React TypeScript 元件

請建立一個新的 React 函式元件，遵循以下規範：

## 元件結構要求

### 1. 檔案組織
```
src/components/{ComponentName}/
├── index.ts                 # 匯出檔案
├── {ComponentName}.tsx      # 主元件檔案
├── {ComponentName}.test.tsx # 測試檔案
├── {ComponentName}.stories.tsx # Storybook 檔案（如果使用）
└── styles.module.css       # 樣式檔案
```

### 2. TypeScript 型別定義
- 定義明確的 Props 介面
- 使用適當的 React 型別（如 ReactNode, MouseEvent 等）
- 加入 JSDoc 註解說明

### 3. 元件實作
- 使用 React.memo 進行效能最佳化（如需要）
- 實作 forwardRef（如需要）
- 加入適當的錯誤邊界處理
- 包含 loading 和 error 狀態處理

### 4. 樣式設定
- 使用 CSS Modules 或 styled-components
- 支援 responsive 設計
- 遵循設計系統規範

### 5. 測試
- 單元測試覆蓋主要功能
- 測試 props 傳遞
- 測試事件處理
- 測試條件渲染

## 範例結構

```typescript
// ComponentName.tsx
import React, { forwardRef } from 'react';
import styles from './styles.module.css';

/**
 * ComponentName 元件的 Props 定義
 */
export interface ComponentNameProps {
  /** 元件標題 */
  title: string;
  /** 是否顯示載入狀態 */
  loading?: boolean;
  /** 點擊事件處理器 */
  onClick?: (event: React.MouseEvent<HTMLElement>) => void;
  /** 自訂 CSS 類名 */
  className?: string;
  /** 子元件 */
  children?: React.ReactNode;
}

/**
 * ComponentName 元件
 *
 * @param props - 元件屬性
 * @returns React 元件
 */
export const ComponentName = forwardRef<HTMLDivElement, ComponentNameProps>(
  ({ title, loading = false, onClick, className, children, ...props }, ref) => {
    // 元件邏輯實作

    if (loading) {
      return <div className={styles.loading}>載入中...</div>;
    }

    return (
      <div
        ref={ref}
        className={`${styles.container} ${className || ''}`}
        onClick={onClick}
        {...props}
      >
        <h2 className={styles.title}>{title}</h2>
        {children}
      </div>
    );
  }
);

ComponentName.displayName = 'ComponentName';
```

## 建立步驟

1. **確定元件名稱和用途**
2. **定義 Props 介面**
3. **實作主元件邏輯**
4. **加入樣式設定**
5. **撰寫測試檔案**
6. **建立 Storybook 檔案**（如適用）
7. **更新匯出檔案**

## 注意事項

- 元件名稱使用 PascalCase
- 檔案名稱保持一致
- 遵循專案的程式碼風格
- 加入適當的錯誤處理
- 考慮無障礙設計 (a11y)
- 確保元件可重用性
