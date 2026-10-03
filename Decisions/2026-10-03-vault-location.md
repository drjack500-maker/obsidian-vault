---
date: 2026-10-03
tags: [obsidian, claude, setup]
project: obsidian-vault
related: ["[[obsidian-github-sync]]"]
---

# Vault の置き場所: GitHub リポジトリ

## 状況

Claude Code のクラウドセッションから PC 上の Obsidian Vault を読み書きしたい。
クラウドのコンテナからは PC のファイルに直接届かず、Obsidian 用の MCP コネクタも未接続。

## 選択肢

- A. GitHub の新規 private リポジトリ（Obsidian の Git プラグインで同期）
- B. Google Drive（Drive デスクトップで同期したフォルダを Obsidian で開く）
- C. 作業中のリポジトリ（myproject）内に `vault/` を作る
- D. リモートから使える Obsidian MCP コネクタを接続する

## 決定: A

- どのセッションからでも git で確実に読み書きできる
- 変更履歴が残り、Claude の書き込みを後から確認・取り消しできる
- B は検索や一括の読み書きが不安定
- C はプロジェクトのコードと個人の知識が混ざり、他プロジェクトから使いにくい
- D はローカルの Obsidian をクラウドに公開する必要があり手間が大きい
