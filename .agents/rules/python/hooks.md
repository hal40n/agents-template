---
paths:
  - "**/*.py"
  - "**/*.pyi"
---

# Pythonフック

> このファイルは [common/hooks.md](../common/hooks.md) をPython固有の内容で拡張したものです。

## PostToolUse フック

`~/.claude/settings.json` で設定する：

- **black / ruff**：`.py` ファイルの編集後に自動フォーマットを実行する
- **mypy / pyright**：`.py` ファイルの編集後に型チェックを実行する

## 警告

- 編集したファイルに `print()` 文があれば警告する（代わりに `logging` モジュールを使うこと）
