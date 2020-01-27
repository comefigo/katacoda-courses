# Docker基礎

このシナリオではDockerの基礎的なコマンドを実行して、Dockerを理解する内容になっています。<br/>
Dockerコマンドは旧式と新式の二種類ありますが、新式で扱います。<br/>
- [docker container / image コマンド新旧比較](https://qiita.com/zembutsu/items/6e1ad18f0d548ce6c266)
- [Docker engine command reference](https://docs.docker.com/engine/reference/commandline/docker/)

# 前提知識

以下の前提知識（箇条書き）があると理解しやすいと思います。

- Linuxの基礎
    - パッケージマネージャー(yum、apt-get)
    - ディストリビューション(CentOS、Ubuntu、Fedora、Redhat)
    - ls、curl、cp、mv、cron
- VMareなどの仮想マシン
- APPサーバ、Webサーバ、DBサーバの多層構造
- ネットワーク（ブリッジ、NAT）
