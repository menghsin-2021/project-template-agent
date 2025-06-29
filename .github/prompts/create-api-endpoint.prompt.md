---
mode: agent
tools: [create_file, insert_edit_into_file, run_in_terminal, file_search, read_file]
description: "自動建立完整的 API 端點，包含控制器、路由、型別定義和測試"
---

# 建立完整的 RESTful API 端點

請自動建立一個完整的 RESTful API 端點，包含所有必要的檔案和設定。

## 端點規格

### 基本資訊
- **資源名稱**：{RESOURCE_NAME} (例如：users, products, orders)
- **路由前綴**：`/api/{resource}`
- **支援方法**：GET, POST, PUT, DELETE

### 檔案結構
請建立以下檔案結構：
```
src/
├── controllers/{Resource}Controller.ts
├── services/{Resource}Service.ts
├── models/{Resource}.ts
├── routes/{resource}.ts
├── types/{Resource}Types.ts
├── middleware/{resource}Validation.ts
└── tests/{resource}.test.ts
```

## 自動化任務

### 1. 型別定義 ({Resource}Types.ts)
```typescript
export interface {Resource} {
  id: string;
  // 根據資源特性定義屬性
  createdAt: Date;
  updatedAt: Date;
}

export interface Create{Resource}Request {
  // 建立請求的屬性
}

export interface Update{Resource}Request {
  // 更新請求的屬性
}

export interface {Resource}Response {
  // API 回應的屬性
}
```

### 2. 資料模型 ({Resource}.ts)
```typescript
import { {Resource} } from '../types/{Resource}Types';

export class {Resource}Model {
  // 資料庫操作方法
  static async findAll(): Promise<{Resource}[]>
  static async findById(id: string): Promise<{Resource} | null>
  static async create(data: Create{Resource}Request): Promise<{Resource}>
  static async update(id: string, data: Update{Resource}Request): Promise<{Resource}>
  static async delete(id: string): Promise<boolean>
}
```

### 3. 服務層 ({Resource}Service.ts)
```typescript
import { {Resource}Model } from '../models/{Resource}';
import { Create{Resource}Request, Update{Resource}Request } from '../types/{Resource}Types';

export class {Resource}Service {
  async getAll{Resource}s() {
    // 商業邏輯
  }

  async get{Resource}ById(id: string) {
    // 商業邏輯
  }

  async create{Resource}(data: Create{Resource}Request) {
    // 商業邏輯
  }

  async update{Resource}(id: string, data: Update{Resource}Request) {
    // 商業邏輯
  }

  async delete{Resource}(id: string) {
    // 商業邏輯
  }
}
```

### 4. 控制器 ({Resource}Controller.ts)
```typescript
import { Request, Response } from 'express';
import { {Resource}Service } from '../services/{Resource}Service';

export class {Resource}Controller {
  constructor(private {resource}Service: {Resource}Service) {}

  // GET /api/{resource}
  async getAll(req: Request, res: Response) {
    // 控制器邏輯
  }

  // GET /api/{resource}/:id
  async getById(req: Request, res: Response) {
    // 控制器邏輯
  }

  // POST /api/{resource}
  async create(req: Request, res: Response) {
    // 控制器邏輯
  }

  // PUT /api/{resource}/:id
  async update(req: Request, res: Response) {
    // 控制器邏輯
  }

  // DELETE /api/{resource}/:id
  async delete(req: Request, res: Response) {
    // 控制器邏輯
  }
}
```

### 5. 路由設定 ({resource}.ts)
```typescript
import { Router } from 'express';
import { {Resource}Controller } from '../controllers/{Resource}Controller';
import { validate{Resource} } from '../middleware/{resource}Validation';

const router = Router();
const {resource}Controller = new {Resource}Controller();

router.get('/', {resource}Controller.getAll);
router.get('/:id', {resource}Controller.getById);
router.post('/', validate{Resource}, {resource}Controller.create);
router.put('/:id', validate{Resource}, {resource}Controller.update);
router.delete('/:id', {resource}Controller.delete);

export default router;
```

### 6. 驗證中間件 ({resource}Validation.ts)
```typescript
import { Request, Response, NextFunction } from 'express';
import Joi from 'joi';

const create{Resource}Schema = Joi.object({
  // 驗證規則
});

const update{Resource}Schema = Joi.object({
  // 驗證規則
});

export const validate{Resource} = (req: Request, res: Response, next: NextFunction) => {
  // 驗證邏輯
};
```

### 7. 測試檔案 ({resource}.test.ts)
```typescript
import request from 'supertest';
import app from '../app';

describe('{Resource} API', () => {
  describe('GET /api/{resource}', () => {
    // 測試案例
  });

  describe('POST /api/{resource}', () => {
    // 測試案例
  });

  // 其他測試案例
});
```

## 執行步驟

1. **分析現有專案結構**
2. **建立型別定義檔案**
3. **建立資料模型**
4. **實作服務層邏輯**
5. **建立控制器**
6. **設定路由**
7. **加入驗證中間件**
8. **撰寫測試檔案**
9. **更新主路由檔案**
10. **執行測試驗證**

## 需要的資訊

請在執行前確認：
- 資源名稱（單數形式，如：user, product）
- 資源的主要屬性
- 特殊的商業邏輯需求
- 驗證規則
- 是否需要認證/授權
