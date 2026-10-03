---
date: 2026-10-03
tags: [obsidian, git, github, claude, setup]
project: obsidian-vault
related: ["[[2026-10-03-vault-location]]"]
---

# Obsidian Vault を GitHub 経由で Claude と共有する

## ハマったこと

- Claude Code のクラウドセッションからは PC 上の Obsidian に直接アクセスできない（Obsidian の MCP もない）
- Claude からの GitHub リポジトリ新規作成は `403 Resource not accessible by integration` で失敗する
  - 原因: Claude GitHub App にリポジトリ作成の権限がない
  - 解決: リポジトリは GitHub 上で自分で作り、Claude GitHub App のアクセス対象に追加する

## PC 側の同期手順

1. GitHub Desktop などで `drjack500-maker/obsidian-vault` を PC にクローンする
2. Obsidian で「フォルダを保管庫として開く」→ クローンしたフォルダを選ぶ
3. 設定 → コミュニティプラグイン → 「Git」をインストールして有効化
4. Git プラグインの設定
   - 起動時に pull する: ON
   - 自動 commit-and-sync の間隔: 5 分程度

## Claude 側

- 書き込んだら `main` に即 commit & push する
- PC 側は起動時と定期同期で pull するので、Claude の書き込みが Obsidian に反映される
- `.obsidian/workspace.json` などは `.gitignore` で除外し、同期の競合を防ぐ
