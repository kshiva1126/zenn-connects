---
title: ".gitignoreを使わずに追跡対象から除外する"
emoji: "⛳"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["git"]
published: true
---

備忘録としてまとめておきます。

## 方法

.git/info/exclude に除外したいファイルを記載します。
```
echo "local-file.txt" >> ./.git/info/exclude
```

## 最後に
ドキュメントに当たるのはやっぱり大事
