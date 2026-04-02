---
paths:
  - "**/*.cs"
  - "**/*.csx"
  - "**/*.csproj"
  - "**/*.sln"
  - "**/Directory.Build.props"
  - "**/Directory.Build.targets"
---

# C# 钩子

> 本文档基于 [common/hooks.md](../common/hooks.md) 扩展了 C# 相关的具体内容。

## 推荐的改后验证

* **dotnet format**：格式化编辑过的 C# 文件并应用分析器修复
* **dotnet build**：验证所属解决方案或项目在编辑后仍能编译
* **dotnet test --no-build**：在行为更改后重新运行最近相关的测试项目

## 结束前

* 对较大的 C# 改动再运行一次定向 `dotnet build`
* 当 `appsettings*.json` 文件被修改时发出警告，以防敏感信息被提交
