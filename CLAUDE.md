# Claude × Obsidian 連携ルール

あなたは私のアシスタントです。
このリポジトリ（`drjack500-maker/obsidian-vault`）は私の Obsidian Vault です。
Vault を「外部脳」として扱い、セッションを跨いで知識を引き継いでください。

## 0. Vault へのアクセス方法

- Vault は GitHub リポジトリ。PC の Obsidian とは Git プラグインで同期している（[[obsidian-github-sync]]）
- このリポジトリで開いたセッション: リポジトリ内のファイルをそのまま読み書きする
- 別リポジトリのセッション: `drjack500-maker/obsidian-vault` をセッションに追加してクローンし、そこで読み書きする
- セッション開始時に `git pull` して最新にする
- 書き込んだら、その場で `main` に commit & push する（PC 側が自動で pull する）

## 1. 初期セットアップ（2026-10-03 実施済み）

ユーザーから「初期セットアップして」と言われたら、Vault 配下に以下のフォルダ構造を作成する:

```
Vaultのルート/
├── Knowledge/      # 技術的な知見・解決したバグ・新しい発見
│   └── mistakes.md # AIのミス記録
├── Decisions/      # 判断・選択・方針決定の記録
├── Projects/       # 進行中のプロジェクトの状態
└── Preferences/    # 自分の好み・作業スタイル
```

空フォルダには `.gitkeep` を置いて残す。

作成後、ユーザーに以下を伝える:

- どのフォルダを作ったか
- 各フォルダに何を書き込むのか
- 最初に書いておくと良いもの（例: 自己紹介を `Preferences/profile.md` に書く）

このセクションは初回セットアップ時のみ実行し、通常の会話では参照しなくてよい。

## 2. 読み取り（セッション開始時に必ず実行）

新しい会話の最初のメッセージで、以下を実行:

1. 行動ルール（`Knowledge/mistakes.md`）とユーザープロファイル（`Preferences/` 配下）を最初に読み込む
2. ユーザーの質問に関連するキーワードで Vault を検索する
3. ヒットしたノートを読む
4. 読み取った内容を踏まえて回答する

スキップしてよい場合: 明らかに Vault と無関係な単発質問（例:「今何時?」「1+1は?」）

## 3. 書き込み（該当したら、その場で Vault に書き込む）

「後で書く」はしない。会話の流れの中で都度書き込む。

- **Knowledge/**
  - バグや問題が解決した（原因と解決策をペアで）
  - ライブラリ・API・ツールの新しい発見
  - 環境構築・設定でハマって解決した
  - 「次回同じ作業で知っておきたかった」と思ったこと
- **Decisions/**
  - 複数の選択肢から 1 つを選んだ判断（A vs B、なぜ A か）
  - 設計・方針の決定
- **Projects/**
  - プロジェクトの状態・バージョン・概要が変わった
- **Preferences/**
  - ユーザーの好み・作業スタイルを新たに発見した

## 4. 書き込みフォーマット

ノートには必ず YAML フロントマターを付与:

```markdown
---
date: YYYY-MM-DD
tags: [relevant, tags]
project: project-name
related: ["[[Other Note]]"]
---

# タイトル

本文。関連ノートには [[wiki link]] でリンクする。
```

フロントマター内の wiki link は引用符で囲む（囲まないと Obsidian がリンクとして認識しない）。

## 5. ファイル命名規則

- Knowledge: `topic-subtopic.md`（例: `nextjs-auth-cookie.md`）
- Decisions: `YYYY-MM-DD-topic.md`（例: `2026-05-16-database-choice.md`）
- Preferences: `category.md`（例: `coding-style.md`）
- Projects: `project-name.md`

## 6. mistakes.md への追記ルール

セッション中にユーザーから訂正を受け、かつ以下 3 条件をすべて満たすときのみ `Knowledge/mistakes.md` に追記:

1. ユーザーからの明示的な訂正である（自分の気づきではない）
2. 繰り返し起こり得るパターンである（一度きりの偶発ではない）
3. 具体的な「する/しない」で書ける

形式:

```
YYYY-MM-DD: [一言で何を間違えたか]
NG Action: 実際にやってしまった間違い
Correct Action: 次回からの正しい対応
Trigger: このルールが適用される状況
```

## 7. 報告

Vault を読み書きしたら、何をしたか明示的にユーザーに伝える:

- 「Obsidian: Knowledge/xxx.md を読みました」
- 「Obsidian: Knowledge/xxx.md に書き込みました」

サイレントで読み書きしない。透明性を保つ。

## 8. 作業スタイル

- シンプルで読みやすいものを優先する
- 不要な装飾・冗長な説明は省く
- 既存のパターン・命名規則に合わせる
- デプロイや動作確認は自分で完結させ、ユーザーに頼まない
