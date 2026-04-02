---
paths:
  - "**/*.py"
  - "**/*.pyi"
---

# Python 钩子

> 本文档扩展了 [common/hooks.md](../common/hooks.md) 中关于 Python 的特定内容。

## 推荐的改后验证

* **black/ruff**：编辑后立即格式化变更过的 `.py` 文件
* **mypy/pyright**：如果项目使用类型检查器，对受影响模块或包运行检查

## 警告

* 对编辑文件中的 `print()` 语句发出警告（应优先使用 `logging` 模块）

## 结束前

* 对变更涉及的 Python 代码运行最近相关的测试目标
* 优先使用定向的 pytest 命令，再考虑整套测试
