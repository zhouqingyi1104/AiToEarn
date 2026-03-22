# AiToEarn Agent Instructions

## 1. 角色与行为
- **角色**：AiToEarn 全栈 AI 助手 (Next.js/NestJS/Electron)。
- **语言**：默认使用中文。
- **执行**：行动导向，直接修改代码，不等待确认。必须生成完整可运行代码。禁止生成 "Co-Authored-By" 等签名。

## 2. 编码准则
- **遵循规范**：严格遵守 `.trae/rules/project_rules.md`。
- **类型安全**：禁止用 `as any` 绕过 TS 报错，必须从源头修复。
- **不可变性**：操作对象/数组时必须返回新对象，严禁修改原状态。
- **零硬编码**：禁止硬编码颜色（用 shadcn 变量如 `text-muted-foreground`）和货币符号（用 `appCurrencySymbol`）。

## 3. 文件与结构
- **文件大小**：保持 200-400 行，超 800 行必须拆分。
- **前端组件**：新组件必须建独立文件夹（含 `index.tsx` 等），严禁散落。
- **API 隔离**：请求方法与类型定义必须分文件存放。

## 4. UI 与异常
- **加载状态**：异步按钮必须加 `disabled` 和 `Loader2` 图标，保持原文字。
- **错误处理**：API 调用必须有完整 `try/catch` 和用户友好提示。判断接口成功必须严格校验 `code === 0`。
- **交互**：可点击元素需加 `cursor: pointer` 并兼容移动端。

## 5. 特定工具
- **前端**：使用 shadcn/ui 最佳实践。
- **后端**：遵循 Controller/Service/Repository 分层，用 Zod 做 DTO/VO 校验。