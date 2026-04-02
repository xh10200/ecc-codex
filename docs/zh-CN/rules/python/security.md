---
paths:
  - "**/*.py"
  - "**/*.pyi"
---

# Python 安全

> 本文档基于 [通用安全指南](../common/security.md) 扩展，补充了 Python 相关的内容。

## 密钥管理

```python
import os
from dotenv import load_dotenv

load_dotenv()

api_key = os.environ["OPENAI_API_KEY"]  # Raises KeyError if missing
```

## 安全扫描

* 使用 **bandit** 进行静态安全分析：
  ```bash
  bandit -r src/
  ```

## 参考

查看技能：`security-review` 以获取通用安全检查清单；如果项目涉及 Web 接口，再结合具体框架的官方安全文档使用。
