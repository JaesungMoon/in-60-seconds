# 今日の成果

---

## Who am I?

@devj

ネイティブエンジニアですが、
クラウドプラットフォームのインフラチームに所属しています。
普段はメインにiOS/Android/Unity/Windows用のSDKの開発と
自社環境にDockerで構成されているゲームサーバの軽いモニタリングをしています。

---
## 今日のやりたかったこと

AWS初期設定
AWS環境にChefを使ってDockerでHAProxyを使ったLB(夢)
 - application-staging
 - application-prod
 - haproxy-lb

---

## 実際にやったこと

 - AWS 初期設定
 - EC2で作業
 - EC2でChef
 - EC2でdocker-compose
 - EC2でdockerだけ

---

## AWS 初期設定

 - IAMユーザー設定
   - ルートユーザー設定
 - セキュリティ設定
   - ユーザー生成
   - ユーザーグループ生成
 - 料金関連設定
   - 料金警告通知など

---

## EC2で作業

 - インスタンス生成
 - キーペアをダウンロード＞忘れた
 - キーペアダウンロードは一度のみだったので再度インスタンス作成＋キーペアのダウンロード
 - SSH接続成功

---

## EC2でChef - 1

Chef構成

 - Chef Server
   - Nodeの管理、Cookbook, Recipe情報などの構成管理を行う
   - Workstation
 - Knifeコマンドで、CookbookやRecipeを操作したり、Chef Serverに支持をしたりする環境
 - Node
   - Chef Serverが管理するマシン
   - Chef Serverで管理しているCookbookやRecipe情報をNode上のChef Clientが取得して、そのタスクを実行します。

---

## EC2でChef - 2

**Chef ServerインストールからWorkstationの設定まで**
```
$ chef-server-ctl reconfigure
```

CommandFailed: Expected process to exit with [0], but received '1'

原因メモリ不足

---

## EC2でChef - 3

結論: microではメモリが足りないのでChef Serverインストールができない
次になにやる？

 - Chef Solo
 - Amazon ECS: amazon + docker
 - Amazon EKS: amazon + kubernetes
 - GKE

---


## EC2 Docker-Compose

docker インストール
```
$ sudo /bin/bash
$ yum update
$ yum install -y docker
# docker 起動
$ service docker start # < 失敗する?
```

---

## docker-compose インストール

```
$ curl -L "https://github.com/docker/compose/releases/download/1.9.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
-> 権限で怒られたのでrootで実行
$ sudo chmod +x /usr/local/bin/docker-compose
-> rootで実行失敗したのでec2-userで実行
$ docker-compose --version
```

---

## WordPressを立ち上げる

[ここ](https://qiita.com/yumatsud/items/33bc22f7d8f640a286f4)を参考にもくもく

Docker Composerを使って複数のコンテナを一元管理
構成
 - WordPressイメージを利用
 - MySQLイメージを利用
 - データ保存先は保存用のコンテナを準備
[プログラマのためのDocker教科書](https://www.amazon.co.jp/Docker/dp/479814102X/ref=tmm_other_meta_binding_swatch_0?_encoding=UTF8&qid=1483682891&sr=8-1-fkmr0)が参考リンクらしい

---

## WordPressを立ち上げる - 結果

docker imageのダウンロードとコンテナ起動は成功したが、

Error establishing a database connection
エラーになりました。

---

## dockerだけでwebpage


dockerだけでwebpageを出す

