title:Lokiドキュメンテーション | Lokinet概要 | オニオンルーター
description:Lokinetはブロックチェーンにより執行されそしてインセンティブ化される独自のオニオンルーターです。Lokinetでは、IPアドレスや正体をさらけ出さずに匿名でインターネットにアクセスでき、プライベートなサイトを訪れる、もしくは作成できます。

# Lokinet概要

Lokinet上の[サービスノード](../ServiceNodes/SNOverview.md)は[低遅延のオニオンルーティングプロトコル](../Lokinet/LLARP.md)を運用し、Lokinetという完全に分散されるオーバーレイネットワークを形成します。オニオンルーティングプロトコルは、ユーザを分散的ネットワークを介してトンネルや経路を形成することを可能にし、複数のノードを経由させてデータパケットのソースや行き先を隠ぺいします。

Lokinetは信頼されている権威者に頼らずに、ブロックチェーンからステートを完全に得ます。ユーザは個々の[サービスノード](../ServiceNodes/SNOverview.md)と接続でき、データパケットを転送するための双方向経路を形成できます。ネットワーク内部にホストされる様々な[SNApp](../Lokinet/SNApps.md)というサービスへもアクセスできます。ユーザは[サービスノード](../ServiceNodes/SNOverview.md)の[出口機能](/ServiceNodes/ServiceNodeFunctions/#exit-nodes)を利用して、IPアドレスを公開せずに外部インターネットを閲覧できます。

## ガイドと情報資源

| **ガイド/情報資源**                                                             | **説明**                                                                                            |
|-------------------------------------------------------------------------        |---------------------------------------------------------------------------------------------        |
| [Lokinetパブリックテストのガイド](../Lokinet/Guides/PublicTestingGuide.md)      | Lokinetパブリックテストの完全ガイド。                                                               |
| [Linuxセットアップガイド](../Lokinet/Guides/lokinet-linux-guide.md)                                | Linux用Lokinetの準備。　                                                                         |
| [Windowsセットアップガイド](../Lokinet/Guides/lokinet-windows-guide.md)| Windows用Lokinetの準備。 |
| [macOSセットアップガイド](../Lokinet/Guides/lokinet-mac-guide.md)| macOS用Lokinetの準備。|
| [Linux - 自分でコンパイルする](../Lokinet/Guides/Install.md)| Lokinetをソースコードから自分でコンパイルする方法。|
| [SNAppへのアクセス](../Lokinet/Guides/AccessingSNApps.md)                       | SNAppにアクセスする方法。                                                                          |
| [LokinetでIRCの使い方](../Lokinet/Guides/LokinetIRC.md)                  　     | Lokinetを介してIRCチャットと接続する方法。                                                         |
| [SNAppをホストする](../Lokinet/Guides/HostingSNApps.md)                         | 自分のSNApp/秘匿サービスをホストする方法。                                                         |
| [LLARPのGithub](https://github.com/loki-project/loki-network)                   | LLARP (低遅延の匿名ルーティングプロトコル)、レイヤ３オニオンルーティングプロトコル。               |
| [Lokinetルーター/リレーを立ち上げる方法](../Lokinet/Guides/TestNetRelay.md)       | テストネットワーク上にリレーをホストする方法。                                                     |
| [Lokinet設定ファイル](../Lokinet/Guides/LokinetConfig.md)                       | このガイドは設定ファイル、そのセクション、キー、そして値を説明します。                             |
