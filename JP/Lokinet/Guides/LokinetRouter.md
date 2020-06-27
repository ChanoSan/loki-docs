title: Lokiドキュメンテーション | Lokinet ルーターガイド | Linux
description: このガイドでは、Lokinetルーターを動かす方法を順番にわかりやすく説明していきます。Lokinetとは、シビル攻撃に対する耐性をもった新しいオニオンルーターです。


# Lokinet ルーターガイド
著者: Jason (jagerman), Johnathan (SonOfOtis)

出典: [https://deb.imaginary.stream/](https://deb.imaginary.stream/)

### はじめに

このドキュメントではLokinetルーターの設定と使い方を正確に説明しています。開発者ではない初心者の方でも、問題なくできるでしょう。

もしあなたがサーバーやCLIに慣れているなら、[上級設定ガイド](#express-setup-guide)へスキップしてください。 

もちろん、どのOSについても、これに基づいてLokiソフトウェアを稼働させることができます。

## Linuxへの初期設定

###1. 非ルートユーザーを作る
公開サーバーではソフトウェアをルートユーザーで動かさないのが最善策です。
全てルートユーザーで動かすことは可能ですが、非ルートユーザーを作ることが強く推奨されます。
あなたのサーバーで次のコマンドを実行してください:


```
adduser <username>
```

あなたが使用したい名前で `<username>` を置き換えてください。 このユーザーガイドでは、ユーザー名を `lokinetRouter` として説明します。

```
adduser lokinetRouter
```

新しいユーザーのパスワードを聞かれるので、ルートユーザーとは異なるセキュアなパスワードを入力してください。

パスワードが設定されると、ユーザーの設定についていくつかの入力を求められる場合がありますが、サービスノードの動作には重要でないので、それぞれEnterキーを押すだけで大丈夫です。

それが終われば、新しいアカウントに権限を付与するために次の２つのコマンドを実行してください。

```
usermod -aG sudo lokinetRelay
```

```
sudo su - lokinetRelay
```

###2. サーバーの設定

パッケージリストをアップデートし、依存するパッケージの最新バージョンを取得しアップデートします。

以下のコマンドを実行してください。

```
sudo apt-get update
```

パッケージリストがダウンロードされたことが通知されます。次のコマンドを実行し、すべてのパッケージの新しいバージョンをインストールしてください。

```
sudo apt-get upgrade
```

ディスクスペースの使用について認証を聞かれれば、'y'を入力し認証してください。

> Note: If you are prompted at any time that a version of any file is available then click the up and down arrows until you are hovering over install the package maintainer’s version and click enter.

もし、コンピュータに curl がインストールされていなければ、後で使うのでインストールしておきます:

```
sudo apt install curl
```

###3. Lokinetルーターのインストール
これはのステップは、リポジトリを設定したい場合に一度だけ行うものです。一度設定すれば、自動的にリポジトリがアップデートされます。

Lokiを `apt` のリポジトリに追加するには、以下のコマンドを実行します:

以下のコマンドは、署名に使用されている Jagermans さんの公開鍵をインストールするものです。

```
curl -s https://deb.imaginary.stream/public.gpg | sudo apt-key add -
```

次のコマンドで、 `apt` のパッケージリストに追加します。:

```
echo "deb https://deb.imaginary.stream $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/imaginary.stream.list
```

これで、パッケージのリポジトリは以下のコマンドと連動します:

```
sudo apt update
```

Lokinetルーターを新たにインストールする:

```
sudo apt install lokinet-router
```

これでLokinetのリレーとしてサーバーが動きます。

## Lokinetルーターを動かす・止める

Lokinetルーターを手動で動かすには、次のように入力してください:

```
sudo systemctl start lokinet-router
```

手動で止めるには次のように入力してください:

```
sudo systemctl stop lokinet-router
```

---

## 上級設定ガイド

```
adduser lokinetRouter
```

```
usermod -aG sudo lokinetRelay
```

```
sudo su - lokinetRelay
```

```
sudo apt install curl
```

```
curl -s https://deb.imaginary.stream/public.gpg | sudo apt-key add -
```

```
echo "deb https://deb.imaginary.stream $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/imaginary.stream.list
```

```
sudo apt update
```

```
sudo apt install lokinet-router
```