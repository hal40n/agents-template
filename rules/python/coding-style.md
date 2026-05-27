---
paths:
  - "**/*.py"
  - "**/*.pyi"
---

# Pythonコーディングスタイル

> このファイルは [common/coding-style.md](../common/coding-style.md) をPython固有の内容で拡張したものです。

## 標準

- **PEP 8** の規約に従う
- すべての関数シグネチャに**型アノテーション**を付ける

## イミュータビリティ

不変なデータ構造を優先する：

```python
from dataclasses import dataclass

@dataclass(frozen=True)
class User:
    name: str
    email: str

from typing import NamedTuple

class Point(NamedTuple):
    x: float
    y: float
```

## フォーマット

- **black** — コードフォーマット
- **isort** — インポートの並び替え
- **ruff** — リント

## 参照

包括的なPythonのイディオムとパターンはスキル `python-patterns` を参照すること。
