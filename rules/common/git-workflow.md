# Gitワークフロー

## コミットメッセージの形式

```text
<type>: <description>

<任意の本文>
```

タイプ一覧：`feat`・`fix`・`refactor`・`docs`・`test`・`chore`・`perf`・`ci`

## プルリクエストのワークフロー

PRを作成する際は：

1. 最新のコミットだけでなく、コミット履歴全体を分析する
2. `git diff [base-branch]...HEAD` ですべての変更内容を確認する
3. 包括的なPRサマリーを作成する
4. TODOチェックリスト形式でテスト計画を記載する
5. 新しいブランチの場合は `-u` フラグでプッシュする

> Git操作の前段にあたる開発プロセス（計画・TDD・コードレビュー）については
> [development-workflow.md](./development-workflow.md) を参照すること。
