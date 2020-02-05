# コンテナイメージの取得

1. CentOS 6のイメージを取得します<br/>
  `docker image pull centos:6`{{execute T1}} <br/>

    **[説明]**<br/>
      - pull･･･コンテナイメージの[リポジトリ](https://hub.docker.com/_/centos?tab=description)（デフォルトは[Docker hub](https://hub.docker.com/search?q=&type=image)）からイメージを取得。プライベートなリポジトリも構築可能
      - centos･･･イメージの名前
      - 6･･･タグ名。指定しない場合は`latest`（最新版）として扱われます
      - イメージの実態は**アプリケーションが実行できるためのファイル群**(OS関連、ランタイム、ミドルウェアなど)
      - ローカルにコンテナイメージがなければ、リポジトリからコンテナイメージを取得

    **[参照]**<br/>
      - [docker image pull](https://docs.docker.com/engine/reference/commandline/image_pull/)

2. 取得したイメージを確認します<br/>
  `docker image ls`{{execute T1}} <br/>

    **[実行結果]**<br/>

    ```shell
    REPOSITORY      TAG         IMAGE ID            CREATED             SIZE
    centos          6           d0957ffdf8a2        10 months ago       194MB
    ```

    **[説明]**<br/>
      - REPOSITORY･･･イメージ名<br/>
        個人のイメージは「ユーザ名/イメージ名:タグ名」を付けるのが慣例
      - TAG･･･タグ名
      - IMAGE ID･･･イメージID
      - SIZE･･･イメージサイズ<br/>

    **[ポイント]**<br/>
      - **アプリケーションを動作させるための最低限のファイル群しかない**ため、サイズが小さい<br/>
        ※このイメージはCentOSとして認識できるシステム用のファイル群＋ユーティリティ(shell)などが必要最小限のもの<br/>通常の[CentOS 6のISOイメージサイズ](http://isoredirect.centos.org/centos/6/isos/x86_64/)は3.7GB～<br/>

    **[参照]**<br/>
      - [docker image ls](https://docs.docker.com/engine/reference/commandline/image_ls/)

3. より詳細のイメージの情報を表示します<br/>
  `docker image inspect centos:6`{{execute T1}}

    **[説明]**<br/>
      - `docker image inspect イメージID`で指定したイメージの詳細情報を確認することができます
      - リソースの情報は**json形式**で表示されます

    **[参照]**<br/>
      - [docker image inspect](https://docs.docker.com/engine/reference/commandline/image_inspect/)
