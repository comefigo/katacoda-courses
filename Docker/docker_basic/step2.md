# コンテナイメージのタグ付け

1. タグ付けすることでバージョン管理できます<br/>
  `docker image tag centos:6 my-centos:my-6`{{execute T1}} <br/>

    **[説明]**<br/>
    - `my-centos:my-6`のように任意のイメージ名とタグ名を付けることが可能
    - タグ付けすることで別バージョンのコンテナイメージとして扱うことができます

    **[参照]**<br/>
    - [docker image tag](https://docs.docker.com/engine/reference/commandline/image_tag/)

2. タグしたイメージを確認します<br/>
  `docker image ls`{{execute T1}} <br/>

    **[実行結果]**<br/>
    ```
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    centos              6                   d0957ffdf8a2        10 months ago       194MB
    my-centos           my-6                d0957ffdf8a2        10 months ago       194MB
    ```

    **[説明]**<br/>
    - IMAGE ID･･･元のイメージ（`centos:6`）のIDとまったく同じ<br/>
      二つのイメージは別ものとして扱えるが、**実体は同じもの**<br/>
      gitのブランチのようなイメージ<br/>
      ゆえに、依存関係もあります