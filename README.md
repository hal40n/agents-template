# 開発プロジェクト向け Claude Code テンプレート

開発プロジェクトで利用する agents / skills / rules を一元管理するテンプレート。
**「`agents-template/`（実体）+ `.claude/`（シンボリックリンクのみ）」** の二層構造を採用し、複数プロジェクト間でマスターを共有しつつ、Claude Code には標準の `.claude/` 経由で読み込ませる。

---

## ディレクトリ構成

```PlainText
~/Products/
│
├── agents-template/           ← 実体（マスター。編集はここで行う）
│   ├── CLAUDE.md
│   ├── 50_security.md
│   ├── README.md
│   ├── agents/                ← 開発系エージェント定義
│   │   ├── code-reviewer.md
│   │   ├── tdd-guide.md
│   │   ├── security-reviewer.md
│   │   ├── python-reviewer.md
│   │   └── refactor-cleaner.md
│   ├── skills/                ← 開発系スキル
│   │   ├── coding-standards/
│   │   ├── tdd-workflow/
│   │   ├── security-review/
│   │   ├── e2e-testing/
│   │   └── write-readme/
│   └── rules/                 ← コーディング規約
│       ├── common/
│       └── python/
│
└── .claude/                   ← シンボリックリンクのみ（Claude Code が読む場所）
    ├── CLAUDE.md       → ../agents-template/CLAUDE.md
    ├── 50_security.md  → ../agents-template/50_security.md
    ├── agents/         → ../agents-template/agents
    ├── skills/         → ../agents-template/skills
    └── rules/          → ../agents-template/rules
```

`~/Products/` 直下で Claude Code を実行すると、`.claude/` 経由で `agents-template/` の中身が読まれる。

---

## 設計方針

| 役割 | 場所 |
| --- | --- |
| **実体ファイル** | `agents-template/` 配下 |
| **Claude Code への入口** | `.claude/` 配下（シンボリックリンクのみ） |

- 編集はすべて `agents-template/` 側で行う
- `.claude/` は触らない（ただのリンク群）
- Git で版管理する場合は `agents-template/` をコミット対象に、`.claude/` は `.gitignore` でもよい

---

## 個別プロジェクトから利用する

`~/Products/<project>/` 配下で Claude Code を実行する場合、その階層に独自の `.claude/` を作って `agents-template/` を参照する。

```bash
cd ~/Products/<your-project>
mkdir -p .claude
cd .claude

ln -sfn ../../agents-template/agents agents
ln -sfn ../../agents-template/skills skills
ln -sfn ../../agents-template/rules rules
ln -sfn ../../agents-template/CLAUDE.md CLAUDE.md
ln -sfn ../../agents-template/50_security.md 50_security.md
```

> プロジェクト固有の `.claude/` を別に置きたい場合は、必要なリンクだけを上記から選ぶ。逆にプロジェクト固有のスキルを足したいときは、リンクを実体コピーに切り替えてから追記する。

---

## マスターを更新する

```bash
cd ~/Products/agents-template
# agents/ skills/ rules/ を編集
git diff
```

実体を編集すれば、シンボリックリンクで参照している全プロジェクトに即座に反映される。

---

## 含まれているエージェント

| エージェント | 目的 |
| --- | --- |
| `code-reviewer` | コード品質・セキュリティ・保守性のレビュー |
| `tdd-guide` | TDDサイクル（RED→GREEN→REFACTOR）の進行 |
| `security-reviewer` | 認証・入力検証・シークレット等の脆弱性検出 |
| `python-reviewer` | Python固有の品質・スタイルレビュー |
| `refactor-cleaner` | デッドコード・未使用インポート等のクリーンアップ |

## 含まれているスキル

| スキル | 目的 |
| --- | --- |
| `coding-standards` | コーディング規約のベースライン |
| `tdd-workflow` | TDDワークフロー（カバレッジ80%以上） |
| `security-review` | セキュリティ機能実装時のチェックリスト |
| `e2e-testing` | Playwright E2Eテスト・Page Object Model・CI連携 |
| `write-readme` | README.md執筆ワークフロー（汎用） |

## 含まれているルール

`rules/common/`：
- agent-orchestration.md / code-review.md / coding-style.md / development-workflow.md
- git-workflow.md / hooks.md / patterns.md / performance.md / security.md / testing.md

`rules/python/`：
- coding-style.md / hooks.md / patterns.md / security.md / testing.md
