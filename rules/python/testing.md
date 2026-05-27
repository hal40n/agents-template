---
paths:
  - "**/*.py"
  - "**/*.pyi"
---

# Pythonテスト

> このファイルは [common/testing.md](../common/testing.md) をPython固有の内容で拡張したものです。

## フレームワーク

テストフレームワークには **pytest** を使う。

## カバレッジ

```bash
pytest --cov=src --cov-report=term-missing
```

## テストの整理

`pytest.mark` でテストをカテゴリ分けする：

```python
import pytest

@pytest.mark.unit
def test_calculate_total():
    ...

@pytest.mark.integration
def test_database_connection():
    ...
```

## 参照

pytestの詳細なパターンとフィクスチャはスキル `python-testing` を参照すること。
