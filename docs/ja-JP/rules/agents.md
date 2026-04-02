# Agent オーケストレーション

## 利用可能な Agent

リポジトリの Codex サブエージェント設定で提供:

| Agent | 目的 | 使用タイミング |
|-------|---------|-------------|
| planner | 実装計画 | 複雑な機能、リファクタリング |
| architect | システム設計 | アーキテクチャの意思決定 |
| tdd-guide | テスト駆動開発 | 新機能、バグ修正 |
| code-reviewer | コードレビュー | コード記述後 |
| security-reviewer | セキュリティ分析 | コミット前 |
| build-error-resolver | ビルドエラー修正 | ビルド失敗時 |
| e2e-runner | E2Eテスト | 重要なユーザーフロー |
| refactor-cleaner | デッドコードクリーンアップ | コードメンテナンス |
| go-reviewer | Go コードレビュー | Go プロジェクト |
| go-build-resolver | Go ビルドエラー修正 | Go ビルド失敗時 |
| database-reviewer | データベースレビュー | スキーマ設計、SQL、移行 |
| python-reviewer | Python コードレビュー | Python プロジェクト |
| typescript-reviewer | TypeScript コードレビュー | TypeScript / JavaScript プロジェクト |
| gan-planner | フロントエンド原型計画 | GAN 原型の設計 |
| gan-generator | フロントエンド原型生成 | 原型の高速生成 |
| gan-evaluator | フロントエンド原型評価 | 生成結果のレビュー |

## Agent の即座の使用

ユーザープロンプト不要:
1. 複雑な機能リクエスト - **planner** agent を使用
2. コード作成/変更直後 - **code-reviewer** agent を使用
3. バグ修正または新機能 - **tdd-guide** agent を使用
4. アーキテクチャの意思決定 - **architect** agent を使用

## 並列タスク実行

独立した操作には常に並列 Task 実行を使用してください:

```markdown
# 良い例: 並列実行
3つの agent を並列起動:
1. Agent 1: 認証モジュールのセキュリティ分析
2. Agent 2: キャッシュシステムのパフォーマンスレビュー
3. Agent 3: ユーティリティの型チェック

# 悪い例: 不要な逐次実行
最初に agent 1、次に agent 2、そして agent 3
```

## 多角的分析

複雑な問題には、役割分担したサブ agent を使用:
- 事実レビュー担当
- シニアエンジニア
- セキュリティエキスパート
- 一貫性レビュー担当
- 冗長性チェック担当
