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
 - staging-application
 - prod-application
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

### EC2でChef

Chef構成

### Chef Server
 - Nodeの管理、Cookbook, Recipe情報などの構成管理を行う
### Workstation
 - Knifeコマンドで、CookbookやRecipeを操作したり、Chef Serverに支持をしたりする環境
### Node
 - Chef Serverが管理するマシン
 - Chef Serverで管理しているCookbookやRecipe情報をNode上のChef Clientが取得して、そのタスクを実行します。

---

@snapend

@snap[east span-50]
![](assets/img/presentation.png)
@snapend

@snap[south span-100 text-white]
Snap Layouts let you create custom slide designs directly within your markdown.
@snapend

---?color=linear-gradient(90deg, #5384AD 65%, white 35%)
@title[Add A Little Imagination]

@snap[north-west h4-white]
#### And start presenting...
@snapend

@snap[west span-55]
@ul[spaced text-white]
- You will be amazed
- What you can achieve
- *With a little imagination...*
- And **GitPitch Markdown**
@ulend
@snapend

@snap[east span-45]
@img[shadow](assets/img/conference.png)
@snapend

---?image=assets/img/presenter.jpg

@snap[north span-100 h2-white]
## Now It's Your Turn
@snapend

@snap[south span-100 text-06]
[Click here to jump straight into the interactive feature guides in the GitPitch Docs @fa[external-link]](https://gitpitch.com/docs/getting-started/tutorial/)
@snapend
