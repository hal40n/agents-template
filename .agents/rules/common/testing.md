# テスト要件

## 最低テストカバレッジ：80%

必須のテスト種別（すべて必要）：

1. **ユニットテスト** — 個々の関数・ユーティリティ・コンポーネント
2. **インテグレーションテスト** — APIエンドポイント・DB操作
3. **E2Eテスト** — 重要なユーザーフロー（言語ごとにフレームワークを選択）

## テスト駆動開発（TDD）

必須ワークフロー：

1. テストを先に書く（RED）
2. テストを実行して失敗することを確認する
3. 最小限の実装を書く（GREEN）
4. テストを実行して通過することを確認する
5. リファクタリングする（IMPROVE）
6. カバレッジが80%以上であることを確認する

## テスト失敗のトラブルシューティング

1. **`tdd-guide`** エージェントを使う
2. テストの独立性を確認する
3. モックが正しいか検証する
4. テストではなく実装を修正する（テスト自体が間違っている場合を除く）

## テスト構造（AAAパターン）

テストは Arrange-Act-Assert の構造を優先する：

```typescript
test('類似度を正しく計算する', () => {
  // Arrange（準備）
  const vector1 = [1, 0, 0]
  const vector2 = [0, 1, 0]

  // Act（実行）
  const similarity = calculateCosineSimilarity(vector1, vector2)

  // Assert（検証）
  expect(similarity).toBe(0)
})
```

Pythonの場合：

```python
def test_calculates_similarity_correctly():
    # Arrange
    vector1 = [1, 0, 0]
    vector2 = [0, 1, 0]

    # Act
    similarity = calculate_cosine_similarity(vector1, vector2)

    # Assert
    assert similarity == 0
```

## テスト名の付け方

テスト対象の振る舞いを説明する説明的な名前を使う：

```typescript
test('クエリに一致するマーケットがない場合は空の配列を返す', () => {})
test('APIキーが未設定の場合はエラーをスローする', () => {})
test('Redisが利用できない場合は部分一致検索にフォールバックする', () => {})
```
