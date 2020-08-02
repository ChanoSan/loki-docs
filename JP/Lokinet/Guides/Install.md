title: Lokiドキュメンテーション | LokinetのLinuxインストールガイド
description: このガイドは、Linuxでソースコードからバイナリをビルドする方法を説明します。すでにビルドされたバイナリの場合、lokinet.orgにアクセスしてリリースファイルをダウンロードして下さい。

# LokiNETインストールガイド - Linux

このガイドは、Linuxでソースコードからバイナリをビルドする方法を説明します。すでにビルドされたバイナリの場合、[lokinet.org](https://lokinet.org/) を訪れてリリースファイルをダウンロードして下さい。

コンパイルするには、利用するプラットフォーム版のLokinetの[最新リリース](https://github.com/loki-project/loki-network/releases) をダウンロードして下さい。

コンパイルエラーに遭遇したら、[ここ](../../../Contributing/Issue_Template/) からのテンプレートを使って、[ここ](https://github.com/loki-project/loki-network/issues) に報告して下さい。

## Linuxで最初のセットアップ

### 1. 非ルートユーザの作成

公開サーバーの運営には、ルートユーザとしてソフトウェアを実行しないということが最善の措置です。サーバーに、以下のコマンドで、非ルートユーザを作成します。

```
sudo adduser <username>
```

'<username>'を好みの名前に置き換えて下さい。このガイドのため、ユーザ名を仮に「lokitestnet」にします。

同じユーザー名を使うのだとしたら、コマンドを実行してください。：

```
sudo adduser lokitestnet
```

コマンドが実行されたら、ターミナルは作成されたユーザの新しいパスワードを入力するように求めてきます。ルートユーザと異なるパスワードを使って下さい。

パスワードが設定されたら、ターミナルは新しいアカウントに関する詳細を入力するように求めてきます。とはいえ、Lokinetにアクセスするには関係ありませんので、エンターキーを押して各プロンプトを飛ばすこともできます。

それらが完了したら、以下の2つのコマンドを実行してアカウントに管理者権限を与え、使い始めます。

```
sudo usermod -aG sudo lokitestnet
su - lokitestnet
```

### 2. パソコン準備
先ずはパッケージリストをアップデートします。以下のコマンドはリポジトリーからパッケージリストをダウンロードし、最新バージョンやその依存関係についての情報をアップデートします。全てのリポジトリーとPPAはそのようにアップデートされます。

以下のコマンドを実行します：

```
sudo apt-get update
```

様々なパッケージリストがダウンロードされたことに気付くでしょう。ダウンロードが完了したら、以下のコマンドでシステムに現在インストールされるパッケージのアップデートをフェッチしてください。

```
sudo apt-get upgrade
```

ディスク領域使用を許可するよう求められます。許可するのためには、「y」を入力してエンター・キーを押します。

>注意：利用可能なバージョンのダウンロードを求められたなら、パッケージメンテナのバージョンを選択できるまで上下の矢印キーを押し、エンター・キーを押します。

### 3. 依存関係
ビルドするための依存関係をインストールする必要があります。以下のコマンドを入力してLokinetが要する依存関係を全てインストールします。

```
sudo apt install build-essential cmake libcap-dev wget git resolvconf curl libuv1-dev libsodium-dev libcurl4-openssl-dev
```


依存関係がインストールされたら、loki-networkのリポジトリをクローンします：
```
git clone https://github.com/loki-project/loki-network
cd loki-network
```
### 4. 正常な運転のためにビルドする場合
正常な運転のためにビルドするには、以下の2つのコマンドを実行します：

```
make
sudo make install
```

### 5. DNSの設定
次に、resolv.confファイルを編集してDNSリゾルバを追加する必要があります。

以下のコマンドを実行します。

```
sudo nano /etc/resolvconf/resolv.conf.d/head
```

以下のファイルの最後に追加します：

```
nameserver 127.3.2.1
```

追加されたら、コントロールキーを押しながらXキーを押します。
ファイル変更を確認するため、エンターキーを押します。

次は、以下のコマンドで/etc/resolv.confファイルをアップデートする必要があります：

```
sudo resolvconf -u
```

---

### 任意：　debianパッケージをビルドする方法

debianパッケージが欲しい場合、必要となるdebianメンテナーのパッケージをインストールします...

    $ sudo apt install debuild

...そして以下のコマンドでビルドします

    $ debuild -us -b
---
### 完了

おめでとうございます。ガイドをクリアしました。ここから[Lokinetパブリックテストのガイド](../PublicTestingGuide/#2-accessing-snapps)へ戻りましょう。
