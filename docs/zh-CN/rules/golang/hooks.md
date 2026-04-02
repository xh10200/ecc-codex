---
paths:
  - "**/*.go"
  - "**/go.mod"
  - "**/go.sum"
---

# Go 钩子

> 本文件通过 Go 特定内容扩展了 [common/hooks.md](../common/hooks.md)。

## 推荐的改后验证

* **gofmt/goimports**：编辑后立即格式化变更过的 `.go` 文件
* **go vet**：对受影响的包或模块运行静态分析
* **staticcheck**：条件允许时，对修改过的包运行扩展静态检查

## 结束前

* 为受影响的包重新运行最小相关的 `go test`
* 如果改动了 `go.mod` 或 `go.sum`，在模块级确认依赖和构建健康状态
