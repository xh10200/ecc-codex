---
paths:
  - "**/*.ts"
  - "**/*.tsx"
  - "**/*.js"
  - "**/*.jsx"
---

# TypeScript/JavaScript 钩子

> 此文件扩展了 [common/hooks.md](../common/hooks.md)，并添加了 TypeScript/JavaScript 特有的内容。

## 推荐的改后验证

* **Prettier**：编辑后立即格式化变更过的 JS/TS 文件
* **TypeScript 检查**：对变更文件所属的配置运行 `tsc`
* **console.log 警告**：标记编辑文件中的 `console.log`，除非它是明确保留的临时调试代码

## 结束前

* 为变更代码运行最近相关的测试命令
* 审计已修改文件中的 `console.log` 或其他调试残留
