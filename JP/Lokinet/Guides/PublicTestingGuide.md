title: Lokiドキュメンテーション | Lokinetのパブリックテストガイド
description: このガイドではお使いのパソコン内のLokinet起動時の案内をいたします。そしてソフトウェアのパフォーマンスの点検、また修正及び改良が必要な箇所を検出するために対処可能なタスクの例もご紹介いたします。

# Lokinetのパブリックテストガイド

Lokinetアルファ版のパブリックテスト段階に関心を持ってくれてありがとうございます。何カ月もかかってこの段階にまで到達しました。この新型オニオンルーターを試験実行してくださる方々に感謝したいと思います。

このガイドではお使いのパソコン内のLokinet起動時の案内をいたします。そしてソフトウェアのパフォーマンスの点検、また修正及び改良が必要な箇所を検出するために対処可能なタスクの例もご紹介いたします。Lokinetを稼働させるマシンが増えれば増えるほど、またLokinet上のトラフィックが増えれば増えるほど開発はより良いものとなるでしょう。

Lokiのソフトウェアは全てのOSで起動できます。Linux版（.debパッケージの形で）、Windows版の32ビットまたは64ビット、そしてOSX版のバイナリファイルが[lokinet.org](https://lokinet.org/) で入手可能です。

## 目次

- [Lokinetの概観](#Overview)
- [ヘルプを受ける方法、バグ報告のガイドライン](#getting-help-and-reporting-bugs-guidelines)
  - [ヘルプを受ける方法](#getting-help)
  - [バグ報告のガイドライン](#reporting-bugs)
- [ユーザガイド](#user-guide)
  - ステップ 1 [Lokinetをインストールする](#1-lokinet-installation)
  - ステップ 2 [SNAppへのアクセス](#2-accessing-snapps)
  - ステップ 3 [LokinetのIRCチャットへの参加](#3-joining-a-lokinet-irc-chat)
  - ステップ 4 [SNAppをホストする](#4-hosting-a-snapp)

## ヘルプを受ける方法、バグ報告のガイドライン

パブリックテストの目的のはできる限り多くのフィードバックを集めることです。テスターそしてLokinet開発チームの仕事をしやすくするため、以下のガイドラインに従うよう求めていきたいと思います。

### ヘルプを受ける方法

もし、このガイドに不明な点ががある場合、または自身で特定できない問題に直面した場合、まずは[ディスコードの#lokinet-helpチャンネル](https://discord.gg/67GXfD6) でお尋ね下さい。あるいは、[Telegram](https://t.me/LokiCommunity)、[Twitter](https://twitter.com/loki_project), それとも[Reddit](https://www.reddit.com/r/LokiProject/) でも問い合わせることができます。（訳注：残念ながら、サポートチャンネルは英語のみです。日本語のサポートはできかねます。申し訳ございません。）

### バグ報告

以上のチャンネルからサポートを受けても、なお課題を解決できない場合、[Loki-networkのリポジトリー](https://github.com/loki-project/loki-network/issues) でissueを作成して下さい。

issueを作成するには、以下のテンプレートを使って下さい：[Github issueテンプレートの例](../../../Contributing/Issue_Template/)。（訳注：リポジトリーは英語のみですので、こちらでも日本語のサポートはできかねます。）

## ユーザガイド

Lokinetをインストールするから[SNApp](../../Lokinet/SNApps.md) をホストするまでのセットアップガイドが用意されています。

次の順序でガイドに従うようおすすめします：

### 1. Lokinetをインストールする

このガイドで、パソコンにLokinetを起動できるように準備します。自分のシステムによれば、以下のガイドから選んで下さい：

##### Linuxでインストール

ガイドをアクセスするには[ここ](../Guides/lokinet-linux-guide.md) にクリックして下さい。

このガイドでは、以下の点を説明します：

- 非ルートユーザの作成、そしてそのユーザに管理者権限を与える。

- パッケージリストをアップデートし、必要なアップデートをインストールする。

- Lokinetのインストール。

##### Windowsでインストール

ガイドをアクセスするには[ここ](../Guides/lokinet-windows-guide.md) にクリックして下さい。

このガイドでは、以下の点が説明されます：

- 非ルートユーザの作成。

- 最新Windowsインストーラーのダウンロード。

- Lokinetランチャーのインストール。

- DNSサーバーの設定

ガイドに従って、遭遇した問題を[discord](https://discord.gg/67GXfD6) の#lokinet-helpチャンネルでモデレーターに報告して下さい。ビルド問題に遭遇した場合、特にご自身で解決できた際は、報告願います。

##### Mac OSXインストール

ガイドをアクセスするには[ここ](../Guides/lokinet-mac-guide.md) にクリックして下さい。

このガイドでは、以下の点が説明します：

- 最新Mac OSXインストーラーのダウンロード。

- Lokinetランチャーのインストール。

- DNSサーバーの設定

ガイドに従って、遭遇した問題を[discord](https://discord.gg/67GXfD6) の#lokinet-helpチャンネルでモデレーターに報告して下さい。ビルド問題に遭遇した場合、特にご自身で解決できた際は、報告願います。


### 2. SNAppへのアクセス

このガイドはSNAppへアクセスする方法を解説いたします。ガイドをアクセスするには[ここ](../Guides/AccessingSNApps.md) にクリックして下さい。

このガイドでは、以下の点が説明します：

- 初めてLokinetを初期化する。

- `./lokinet`を実行する。

- 初めてSNAppをアクセスする。

ガイドに従って、遭遇した問題を[discord](https://discord.gg/67GXfD6) の#lokinet-helpチャンネルでモデレーターに報告して下さい。問題に遭遇した場合、特にご自身で解決できた際は、[Loki-networkのリポジトリー](https://github.com/loki-project/loki-network/issues) に報告願います。

### 3. LokinetのIRCチャットに参加する
このガイドはLokinetのIRCチャットに参加する方法を教えます。ガイドをアクセスするには[ここ](../Guides/LokinetIRC.md) にクリックして下さい

別法として、好みのIRCクライアントをダウンロードして、「./lokinet」を実行しながらサーバーアドレスを「http://dw68y1xhptqbhcm5s8aaaip6dbopykagig5q5u1za4c7pzxto77y.loki 」に設定し、ポート番号を「6667」に設定して「#lokinet」チャンネルに加わって下さい。

### 4. SNAppをホストする

このガイドはSNAppホストする方法を教えます。ガイドをアクセスするには[ここ](../Guides/HostingSNApps.md) にクリックして下さい。

このガイドでは、以下の点を説明します：

- Lokinet公開鍵を見つける。

- 「lokinet.ini」ファイルを編集して永続的なSNAppを有効にする。

- SNAppコードのためのディレクトリーを作成する。

- 「Hello lokinet」が入ってる「index.html」ファイルを作成して、ネットワークに見せる。

- SNAppディレクトリーをLokinetへ送信して、ブラウザでアクセスする。

ガイドに従って、遭遇した問題を[discord](https://discord.gg/67GXfD6) の#lokinet-helpチャンネルでモデレーターに報告して下さい。問題に遭遇する場合、特にご自身で解決できた際は、[Loki-networkのリポジトリー](https://github.com/loki-project/loki-network/issues) に報告願います。
