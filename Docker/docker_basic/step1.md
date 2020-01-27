# コンテナイメージを取得

1. CentOS 6のイメージを取得します<br/>
  `docker pull centos:6`{{execute HOST1}} <br/>

    [説明]<br/>
    - pull･･･コンテナイメージの[リポジトリ](https://hub.docker.com/_/centos?tab=description)（デフォルトは[Docker hub](https://hub.docker.com/search?q=&type=image)）からイメージを取得。プライベートなリポジトリも構築可能
    - centos･･･イメージの名前
    - 6･･･タグ名。指定しない場合は`latest`（最新版）として扱われます
    - イメージの実態は**アプリケーションが実行できるためのファイル群**(OS関連、ランタイム、ミドルウェアなど)