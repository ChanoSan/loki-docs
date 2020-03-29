title: Lokiドキュメント | セッション | オープングループセットアップガイド
description: セッションで永続的な履歴のチャットルームをホストするためのexpressでREST API。自分のサーバー上にホストされるので、これらのチャンネルの容量に制限がありません。

# セッションのオープングループセットアップ

セッションで永続的な履歴のチャットルームをホストするためのexpressでREST API。自分のサーバー上にホストされるので、これらのチャンネルの容量に制限はありません。公共チャンネルですから、ここで個人情報を投稿しないようにご留意願います。

ADNスタンダードなREST APIを提供するプラットフォームサーバーそしてセッション専用の動作（暗号キー登録とチャンネル管理の機能）のためのサーバーの2つのデーモンによって実行されています。

# 要求
- 公開のIPアドレスでホストすること
- 公開のIPアドレスと繋がっているDNSホスト名
- Eメールアドレス（Let's Encryptには必要です）
- 少なくとも4GBの空き容量そして512mbのRAM容量（それより少ない容量では実行できるかもしれませんが、保証できません）

# インストール

## 1. dockerをインストール（debian)
debianではない場合のインストールガイドはここ：http://docs.docker.jp/engine/installation/toc.html

さらなるトラブルシューティング対応方法の場合はここ：　http://docs.docker.jp/engine/installation/linux/docker-ce/debian.html　あるいは　http://docs.docker.jp/engine/installation/linux/docker-ce/ubuntu.html

### すでにインストールされているdockerがある場合、アンインストールしましょう
`sudo apt-get remove docker docker-engine docker.io`

### 公式dockerリポジトリーをインストールする
- `sudo apt-get update`
- `sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common`

#### Debianの場合
- `curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -`
- `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"`

#### Ubuntuの場合
- `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
- `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`

### dockerをインストールしてテストする
- `apt-get update`
- `sudo apt-get install docker-ce`
- To check to make sure it's all working: `docker run hello-world`

## 2. docker-composeをインストールする

### docker-composeのスクリプトを作成する
`curl -L "https://github.com/docker/compose/releases/download/1.25.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

### 実行可能なファイルかどうかを確かめる
`chmod u+x /usr/local/bin/docker-compose`

## 3. SOGSをインストールする
- `git clone https://github.com/loki-project/session-open-group-server.git`

### SOGS git submodulesをインストールする
- `cd session-open-group-server`
- `git submodule init`
- `git submodule update`

### acme.jsonの許可は正しく設定されることをチェック
`chmod 600 docker/acme.json`

### 設定をセットアップする
- `cp loki_template.ini loki.ini`

### 公開鍵（PUBKEY）を入手する
- 「PUBKEY」を自分の公開鍵に取り換えて、以下の行を実行する：`echo "PUBKEY=true" >> loki.ini`

### 実行する
「your@email.tld」を自分のメール、そして「yourssl.domain.tld」をホスト名に取り換えて下さい。Let's EncryptによるSSL証明書に必要ですので、プログラムは自動的に登録しようとします。

`EMAIL=your@email.tld DOMAIN=yourssl.domain.tld docker-compose up -d`

# アップグレードする方法
- 以下を「loki-messenger-public-server」ディレクトリから実行して下さい。
- dockerを停止するのに：`EMAIL=your@email.tld DOMAIN=yourssl.domain.tld docker-compose down`
- 最新のソースと設定ファイルを入手する場合：`git pull`
- submoduleの更新を入手する場合：`git submodule init`
- プラットフォーム/nodepomfの更新を入手する場合：`git submodule update`
- ローカルdockerイメージをアップデートする場合：`EMAIL=your@email.tld DOMAIN=yourssl.domain.tld docker-compose build`
- サーバーを再起動するのに：`EMAIL=your@email.tld DOMAIN=yourssl.domain.tld docker-compose up -d`

## サポートが必要の場合

このガイドには分からないことがある場合、それとも自分で特定できない課題にぶつかる場合、まずは[ディスコードの#lokinet-helpチャンネル](https://discord.gg/67GXfD6) で尋ねて下さい。あるいは、[Telegram](https://t.me/LokiCommunity)、[Twitter](https://twitter.com/loki_project), それとも[Reddit](https://www.reddit.com/r/LokiProject/) でも問い合わせることができます。（訳注：残念ながら、サポートチャンネルは英語のみです。日本語のサポートはできません。申し訳ございません。）

## バグ報告

以上のチャンネルからサポートをもらってもまだ課題を解決できない場合、[セッションパブリックサーバーのリポジトリー](https://github.com/loki-project/loki-messenger-public-server/issues) でissueを作成して下さい。

issueを作成するには、以下のテンプレートを使って下さい：[Github issueテンプレートの例](../../../Contributing/Issue_Template/)。（訳注：リポジトリーは英語のみですので、ここでも日本語のサポートはできません。）
