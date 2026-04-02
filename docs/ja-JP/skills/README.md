# スキル

スキルは Codex が文脈に応じて読み込む知識モジュールです。ローカルでの設計、実装、テスト、検証、レビューの閉ループを支えるために使います。

## 現在の保留カテゴリ

### 言語・実装パターン
- `coding-standards/` - 共通のコーディング基準
- `frontend-patterns/` - React / Next.js パターン
- `golang-patterns/` - Go 設計パターン
- `python-patterns/` - Python 設計パターン
- `bun-runtime/` - Bun ランタイム運用
- `nextjs-turbopack/` - Next.js / Turbopack 運用

### テスト・検証
- `e2e-testing/` - E2E テスト
- `eval-harness/` - 評価ハーネス
- `golang-testing/` - Go テスト戦略
- `python-testing/` - Python テスト戦略
- `tdd-workflow/` - テスト駆動開発ワークフロー
- `verification-loop/` - 検証ループ

### API・セキュリティ
- `api-design/` - API 設計
- `security-review/` - セキュリティレビュー

### データベース・ワークフロー補助
- `postgres-patterns/` - PostgreSQL パターン

## スキル構造

各スキルは専用ディレクトリに `SKILL.md` を持ちます。

```text
skills/
├── coding-standards/
│   └── SKILL.md
├── golang-patterns/
│   └── SKILL.md
├── python-testing/
│   └── SKILL.md
...
```

## スキルの使い方

Codex はタスク内容に応じて関連するスキルを読み込みます。例：

- Go の実装やレビュー → `golang-patterns` と `golang-testing`
- Python の変更 → `python-patterns` と `python-testing`
- API 設計やエンドポイント整理 → `api-design`
- テスト主導で進める変更 → `tdd-workflow`

**覚えておいてください**：スキルは実装を助ける実務資料です。ルールと組み合わせて使うことで、一貫した品質を保てます。
