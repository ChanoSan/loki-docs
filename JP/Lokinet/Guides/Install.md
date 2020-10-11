title: Lokiドキュメンテーション | LokinetのLinuxインストールガイド
description: このガイドは、Linuxでソースコードからバイナリをビルドする方法を説明します。すでにビルドされたバイナリの場合、lokinet.orgにアクセスしてリリースファイルをダウンロードして下さい。

# Linuxの初期設定

Linuxでのlokinetのインストールは簡単です。

## debianベースのディストリビューションで

debianリポジトリを追加する：

```bash
sudo apt update 
sudo apt install curl 
curl -s https://deb.loki.network/public.gpg | sudo apt-key add -
echo "deb https://deb.loki.network $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/loki.list
apt update
```

...そしてlokinetをインストールする：

```bash
sudo apt install lokinet
```

完了しました。DNSはセットアップされており、いつでも起動する準備が整っています。

## Linuxミント

ミントは初心者にやさしいディストリビューションですが、開発者達はなぜかこれを独特な存在にしたかったみたいで、特殊な命名規則を用いてしまっています。ともかく、ミントの場合は余分な手順と労力が必要です。

[このテーブル](https://linuxmint.com/download_all.php) を参照して、`/etc/apt/sources.list.d/loki.list`にあるミントのリリース名をUbuntuリリース名に置換して下さい。

## 他のディストリビューション

ソースからビルドする。

要件：

* c++17 compiler
* cmake
* git
* pkg-config
* setcap
* sqlite3
* libunbound
* libuv 1.x
* zmq
* libsodium >= 1.0.18 

...そしてリポジトリをクローンしてビルドする：


```bash
git clone --recursive https://github.com/loki-project/loki-network
mkdir loki-network/build
cd loki-network/build
cmake ..
make -j$(nproc)
sudo make install # このステップは任意ではありません
```

### Lokinetをブートストラップ

lokinetをブートストラップするのに、普通のユーザとして以下のコマンドを１回実行する：

```bash
lokinet -g
lokinet-bootstrap
```

そしてlokinetをフォアグラウンドへ普通のユーザーとして実行する：

```bash
lokinet
```

### DNS設定

debianパッケージを利用する場合、以下のステップは不必要です。

#### systemd-resolved

systemd-resolvedを利用する場合、`contrib/systemd-resolved/lokinet.conf`を`/etc/systemd/resolve.d.conf/10-lokinet.conf`へコピーして、`sudo systemctl restart systemd-resolved`を実行してsystemd-resolvedを再起動する。

#### resolvconf

systemd-resolvedを利用しない場合、resolveconfを利用する。

以下のコマンドを実行する：

```
sudo nano /etc/resolvconf/resolv.conf.d/head
```

以下の行をファイルの最後に追加する：

```
nameserver 127.3.2.1
```

追加が完了したら、CTRL-xを押す。
エンターを押して変更を確認する。

以下のコマンドを実行して/etc/resolv.confファイルをアップデートする：

```
sudo resolvconf -u
```
### 完了

おめでとうございます。ガイドをクリアしました。ここから[Lokinetパブリックテストのガイド](../PublicTestingGuide/#2-accessing-snapps)へ戻りましょう。
