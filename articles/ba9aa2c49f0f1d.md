---
title: "Laravel 8以降のファイルストレージで動的にS3のバケットを変更する方法"
emoji: "🪣"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["laravel", "s3"]
published: true
---

表題の件で、あまり情報がなく微妙にハマったので自分なりの解決策を残しておきます。

## 環境
PHP 8.1.18
Laravel 9.19

## 解決策

```php
$s3_bucket_name = 'S3_BUCKET_NAME';

$disk = Storage::build([
    ...config('filesystems.disks.s3'),
    'bucket' => $s3_bucket_name,
]);
```

`Storage::build` というメソッドを利用して、オンデマンドでディスクを作成しています。
ここでは、PHP8.1で追加された[文字列キー配列のアンパック](https://www.php.net/releases/8.1/ja.php#array_unpacking_support_for_string_keyed_arrays)を用いて既存のS3情報を展開した上で、バケット名のみを上書きしています。
もちろん、すべての情報をべた書きして作成することも可能です。
なお、[公式ドキュメント](https://laravel.com/docs/8.x/filesystem#on-demand-disks)によると、Laravel 8 から `Storage::build` が追加されたようです。
