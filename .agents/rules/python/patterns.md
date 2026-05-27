---
paths:
  - "**/*.py"
  - "**/*.pyi"
---

# Pythonパターン

> このファイルは [common/patterns.md](../common/patterns.md) をPython固有の内容で拡張したものです。

## Protocol（ダックタイピング）

```python
from typing import Protocol

class Repository(Protocol):
    def find_by_id(self, id: str) -> dict | None: ...
    def save(self, entity: dict) -> dict: ...
```

## DataclassをDTOとして使う

```python
from dataclasses import dataclass

@dataclass
class CreateUserRequest:
    name: str
    email: str
    age: int | None = None
```

## コンテキストマネージャとジェネレーター

- リソース管理には `with` 文（コンテキストマネージャ）を使う
- 遅延評価とメモリ効率の高いイテレーションにはジェネレーターを使う

## 参照

デコレーター・並行処理・パッケージ構成などの包括的なパターンはスキル `python-patterns` を参照すること。
