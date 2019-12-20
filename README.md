<<<<<<< HEAD
# Angfa Callcenter/Manage System 詳細設計資料  
## 関連資料

| 資料 | 認証情報（ID/Password） |
| --- | --- |
| [コールセンター・管理システム詳細設計（本資料）](http://d20ywh3pjw8uqh.cloudfront.net/index.html) | rvp-angfa / scalpd |
| [中継API Swagger UI](http://3.114.104.100/) | david / david123 |
| [データモデル by Prisma](https://cm1.backlog.jp/file/MP_ANGFA_DAVID/70_%E4%B8%AD%E7%B6%99%E3%82%B5%E3%83%BC%E3%83%90/01_%E4%BD%9C%E6%A5%AD%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB/01_%E3%83%87%E3%83%BC%E3%82%BF%E3%83%A2%E3%83%87%E3%83%AB/) | - |
| [データモデル by Prisma @ Google Drive](https://drive.google.com/drive/u/1/search?q=sku_code_alt%20parent:1pVZoaDTTwNHZZb7eTyLu7mExTuVjBAKk) | - |

## 更新方法
### ローカルで更新
新しいページを追加する場合  
* `SUMMARY.md` に新しいページの目次を作成する  
* `gitbook init` を実行  
* 実行後に追加するページのファイルが作成されているので、 `contents/template.md` の内容をそのページにコピーする  
* 内容を編集後、 `gitbook serve` で表示に問題ないことが確認する  
* `gitbook build` で静的ファイルを生成する  

既存ページを編集する場合
* 上記手順の4つ目から実行  

### Githubへpush
直接masterへpushでOK  

```
$ git push origin master
```

### S3へアップロード
aws-cli（推奨）かAWSのS3画面からアップロードする  

```
$ aws s3 cp _book/ s3://angfa-revamp-docs/ --recursive
```

## その他
### デプロイ方法メモ
以下を参考に設定  
* S3/CloudFront: [\[CloudFront \+ S3\]特定バケットに特定ディストリビューションのみからアクセスできるよう設定する ｜ Developers\.IO](https://dev.classmethod.jp/cloud/aws/cloudfront-s3-origin-access-identity/)  
* Basic認証: [簡単だった！CloudFront \+ S3 に BASIC認証を入れる方法 \| カフーブログ](https://kahoo.blog/howto-basic-auth-on-cloudfront-s3/)  
=======
# pullreq
>>>>>>> origin/master
