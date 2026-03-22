# AiToEarn Project Rules

## 1. Web 前端 (Next.js)
- **技术栈**：Next.js, Tailwind v4, shadcn/ui, Zustand。
- **目录**：组件须用独立文件夹（含 `index.tsx`，大驼峰）。API 方法与类型强制分离。
- **状态 (Zustand)**：页面级共享用局部 Store。获取多个属性**必须**用 `useShallow`。
- **样式**：禁硬编码颜色（如 `#000`），用 `bg-(--primary-color)`。整体简约留白，多用中性灰。
- **特有工具**：
  - OSS：`getOssUrl` / `getOssProxyPath`
  - 货币：`appCurrencySymbol` + `appCurrency`
  - SEO：`getMetadata`
  - 接口：必须判断 `code === 0`。

## 2. 后端 (NestJS)
- **架构**：Controller (路由/转换) -> Service (业务/权限) -> Repository (纯数据)。
- **命名**：文件用 `kebab-case`。类 `PascalCase`，变量 `camelCase`，常量 `UPPER_SNAKE_CASE`。
- **Repository**：必须用标准动词前缀：`get/list/create/update/delete/count`。分页必带 `WithPagination` 后缀。禁业务动词。
- **DTO/VO**：
  - DTO：Zod -> `createZodDto`。禁实体做入参。分页用 `PaginationDtoSchema`。
  - VO：只暴露外部字段，用 `createPaginationVo` 封装。禁直接返回实体。
- **文档**：必须用 `@ApiTags`、`@ApiDoc` 及 Zod `.describe()`。

## 3. 全局规范
- **不可变性**：禁止 Mutation，永远返回新对象。
- **文件拆分**：200-400 行最佳，超 800 行必拆。
- **安全与错误**：Zod 校验一切输入；完善的 `try/catch` 处理。