title: Lokiドキュメンテーション | Lokinet Linux GUIインストールガイド | オニオンルーティング
description: このガイドはLokinet（シビル攻撃に対する抵抗力を持つ新たなオニオンルーター）をLinuxで作動させる方法についての手順説明書です。

# Lokinet GUIインストールガイド - Linux
著者: Jason (jagerman), Johnathan (SonOfOtis)

ソース： [https://deb.imaginary.stream/](https://deb.imaginary.stream/)

WindowsまたはMacでLokinet GUIをダウンロードするためには、[lokinet.org](https://lokinet.org) あるいは [loki.network](https://loki.network) を開いて、ダウンロードボタンをクリックする。


## Linuxで最初のセットアップ

### 1. パソコンの準備
パッケージリストをアップデートしましょう。以下のコマンドはリポジトリーからパッケージリストをダウンロードし、最新バージョン及び依存関係についての情報をアップデートします。このコマンドで全てのリポジトリーやPPAはアップデートされます。

以下のコマンドを実行してください

```
sudo apt-get update
```

様々なパッケージリストがダウンロードされたことに気付くでしょう。これが完了したら、以下のコマンドでシステムにインストールされるパッケージの最新バージョンをインストールしてください。

```
sudo apt-get upgrade
```

ディスク領域の使用の許可が必要です。「y」の後にエンターキーを入力して許可してください。

> 注意：利用可能なバージョンのダウンロードを求められたなら、パッケージメンテナのバージョンを選択できるまで上下の矢印キーを押してから、エンター・キーを押してください。

後で「curl」を使いますので、まだインストールされていない場合は以下のコマンドでインストールしましょう：

```
sudo apt install curl
```

### 2. インストール方法

このステップは最初にリポジトリーを設定する時のみ必要です。それ以降、システムアップデートをする時には、リポジトリーは自動的にアップデートされます。

Lokiの'apt'リポジトリーを追加するために、以下のコマンドを実行してください：

このコマンドで、バイナリ実行ファイルを署名したJagermanさんの公開キーをインストールしてください。

```
curl -s https://deb.imaginary.stream/public.gpg | sudo apt-key add -
```

次のコマンドは'apt'がパッケージを見つけれるようにします：

```
echo "deb https://deb.imaginary.stream $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/imaginary.stream.list
```

そしてパッケージリポジトリーをリシンク（エラーのチェックを行い、データーが破損している場合、元の状態に修復）します：

```
sudo apt update
```

次はlokinetをインストールします：

```
sudo apt install lokinet-gui
```

おめでとうございます！　Lokinetがインストールされ、バックグラウンドに実行されています。

GUIクライアントへアクセスするには、lokinet-guiアプリを開くだけです。

## LokinetをON/OFFにする方法

ただ、lokinet-guiクライアントを開いて、パワーボタンをクリックするだけです。

![lokinet-gui](../../docs/assets/lokinetGui.PNG)


## プライベートのままでLokinetを閲覧しましょう
ブラウザーを開いて、「Lokinet Wiki」SNAppを開いてください：

- Lokinet Wiki [http://dw68y1xhptqbhcm5s8aaaip6dbopykagig5q5u1za4c7pzxto77y.loki/wiki/](http://dw68y1xhptqbhcm5s8aaaip6dbopykagig5q5u1za4c7pzxto77y.loki/wiki/)

おめでとう！　Lokinetを閲覧できるようになりました。

---
## トラブルシューティング

### DNSの設定

.lokiアドレスの変換には問題がある場合、resolv.confファイルを編集してDNSリゾルバを追加する必要があります。

#### メソッド１

以下のコマンドを実行します：
```
apt install resolvconf
```

そしてlokinetを再起動します：

```
systemctl restart lokinet
```

#### メソッド2
メソッド１が上手く行かない場合、手でネームサーバーを入力し、追加する必要があります。

以下のコマンドを実行します：

```
sudo nano /etc/resolvconf/resolv.conf.d/head
```

以下をファイルの最後に追加します：

```
nameserver 127.3.2.1
```

追加されたら、コントロールキーを押しながらXキーを押します。 
ファイル変更を確認するため、エンターキーを押します。

次は、以下のコマンドで/etc/resolv.confファイルをアップデートする必要があります：

```
sudo resolvconf -u
```

そしてlokinetを再起動します：

```
systemctl restart lokinet
```

--- 

## 完了

おめでとうございます！　ガイドをクリアしました。ここから[秘匿サービスやLokinet SNAppsにアクセスする方法](AccessingSNApps.md)へ移りましょう。
