# コンテナイメージを取得

1. CentOS 6のイメージを取得します<br/>
  `docker pull centos:6`{{execute}} <br/>

    [説明]<br/>
    - pull･･･コンテナイメージの[リポジトリ](https://hub.docker.com/_/centos?tab=description)（デフォルトは[Docker hub](https://hub.docker.com/search?q=&type=image)）からイメージを取得。プライベートなリポジトリも構築可能
    - centos･･･イメージの名前
    - 6･･･タグ名。指定しない場合は`latest`（最新版）として扱われます
    - イメージの実態は**アプリケーションが実行できるためのファイル群**(OS関連、ランタイム、ミドルウェアなど)

2. 取得したイメージを確認します<br/>
  `docker image ls`{{execute}} <br/>

  [説明]<br/>
  - REPOSITORY･･･イメージ名<br/>
    個人のイメージは「ユーザ名/イメージ名:タグ名」を付けるのが慣例
  - TAG･･･タグ名
  - IMAGE ID･･･イメージID
  - SIZE･･･イメージサイズ

  [ポイント]<br/>
    - **アプリケーションを動作させるための最低限のファイル群しかない**ため、サイズが小さい<br/>
    　※通常の[CentOS 6のISOイメージサイズ](http://isoredirect.centos.org/centos/6/isos/x86_64/)は3.7GB～