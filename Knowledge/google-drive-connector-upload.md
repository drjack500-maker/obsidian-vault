---
date: 2026-10-25
tags: [google-drive, claude, connector, upload]
project: general
related: ["[[snore-reset-56]]"]
---

# Claude の Google Drive コネクタで動画を置けない

## ハマったこと

- Google Drive コネクタの `create_file` は、ファイルの中身を文字列（テキストか base64）として渡す方式
- 数MBの動画（例: 5.3MB の MP4）は文字列が長すぎて Claude から渡せない。テキスト（.md / .srt）やフォルダ作成はできる

## 対処

- 動画は GitHub（public の `myproject`）と Obsidian Vault の `Attachments/` に置く
- Drive には README・字幕・ダウンロード用リンクを置き、動画本体はユーザーがフォルダへドラッグする
