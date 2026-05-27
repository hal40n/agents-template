---
paths:
  - "**/*.py"
  - "**/*.pyi"
---

# Pythonセキュリティ

> このファイルは [common/security.md](../common/security.md) をPython固有の内容で拡張したものです。

## シークレット管理

```python
import os
from dotenv import load_dotenv

load_dotenv()

api_key = os.environ["OPENAI_API_KEY"]  # 未設定の場合は KeyError を発生させる
```

## セキュリティスキャン

**bandit** を使って静的セキュリティ解析を実行する：

```bash
bandit -r src/
```

## 参照

Django固有のセキュリティガイドラインはスキル `django-security` を参照すること（該当する場合）。
