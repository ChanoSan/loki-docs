title: Lokiドキュメンテーション | LokinetにSNApp、秘匿サービスとも呼ばれる、をホストする方法
description: SNAppの機能は現在栄えているTorのいわゆる「秘匿サービス」と似てます。SNAppはlokinet外にホストされているコンテンツへのアクセスするより高い匿名性で、lokinet内に交信する機能をユーザに与えます。

# SNAppをホストする方法
## 1. lokinetアドレスを準備する方法

望ましい結果により、一時的なSNApp、またはloki公開鍵を永続的に利用するSNAppが運営可能です。

### 1.1 一時的なSNApp
一時的なSNAppは永続的な公開鍵の使用を必要としない秘匿サービスです。

つまり、SNAppをホスティングするサーバーが再起動されたら、他者と共有の公開鍵はもはや使うことができません。

このようなSNAppにはさらなるセットアップの必要がありません。一時的なSNAppをホストしたい場合は、[ステップ2](#2-finding-your-snapps-lokinet-address)へ飛んで下さい。

### 1.2 永続的なSNApp
「lokinet.ini」ファイルを開いて、SNApp鍵ファイルを保存される場所へのパスを追加する。

DebパッケージからLokinetをビルドした場合、以下のコマンドで「lokinet.ini」ファイルを見つけられます：
```
sudo nano /etc/loki/lokinet.ini
```
もしくは、ソースからビルドした場合は「lokinet.ini」ファイルは以下のファルダーに見つけれます：
```
~/.lokinet/lokinet.ini
```

[network]部までスクロールダウンして、以下の行を追加する：

```
keyfile=/var/lib/lokinet/snappkey.private 
```

<user>をパソコンのhostnameに置き換えれば、代わりにSNApp秘密鍵のパスを好きな場所に設定できます。

次にlokinetを再起動したら、以前に設定したディレクトリに「snappkey.private」は生成されます。
```
sudo systemctl restart lokinet
```

## 2. SNAppのlokinetアドレスを見つける

ホスト検索ツールを利用して現在のSNAppアドレスを見つけることができます：

```
nslookup -type=cname localhost.loki 127.0.0.1 
```

Linuxでは、「host」コマンドも使えます。クエリーに行うlokiアドレスは同じですが、他のインストールされているリゾルバーとのコンフリクトをよけるためリゾルバーは「127.3.2.1」というアドレスを利用します。

```
host -t cname localhost.loki 127.3.2.1
```

## 3. SNAppを作る
ターミナルにこのコマンドを実行して、homeフォルダーに新しいディレクトリを作成する：

```
mkdir ~/snapp/
```
その新しいフォルダーに、indexファイルを作成する：

```
touch ~/snapp/index.html
```

このファイルはSNAppにホストされるコンテンツを含みます。新しいindex.htmlファイルをアクセスするために、以下のコマンドを実行します：

```
vi ~/snapp/index.html
```

index.htmlファイルにテキストを入力するのに、「a」を押す。

「Hello Lokinet」を入力して、ESCキーを押す。

ESCキーは押されたら、コマンド入力モードに戻ります。

次は「:w」を入力して、エンターキーを押してファイルに書き込む。

そして「:q」を入力して、エンターキーを押してエディターを閉じる。「~/snapp/」の前のディレクトリに戻ることができるでしょう。

## 4. SNAppを公開する

これで、以下のコマンドをSNAppのフォルダーから実行してindex.htmlファイルをLokinetに公開する：

```
sudo python3 -m http.server --bind <ip> <port>
```

この例では、pubkeyは「lokitun0」に設定され、アドレスは「172.16.10.1」になります。<port>番号は任意で設定可能です。それ故に、この例の実行するコマンドは：
```
sudo python3 -m http.server --bind 172.16.10.1 80
``` 
この前に保存した.lokiアドレスを訪れると、「Hello Lokinet」というメッセージは表示されるでしょう。

Lokinet IRCで、他のユーザーは作ったSNAppをアクセスできるかどうかを試してみましょう。

### 完了

おめでとうございます。ガイドをクリアしました。ここから[Lokinetパブリックテストのガイド](../PublicTestingGuide/)へ戻りましょう。
