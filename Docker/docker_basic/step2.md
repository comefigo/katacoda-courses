# コンテナイメージのタグ付け

1. タグ付けすることでバージョン管理できます<br/>
  `docker tag centos:6 my-centos:my-6`{{execute}} <br/>
    [説明]<br/>
    - `my-centos:my-6`のように任意のイメージ名とタグ名を付けることが可能<br/>

    - タグ付けすることで別バージョンのコンテナイメージとして扱うことができます

    [参照]<br/>
    - [docker tag](http://docs.docker.jp/engine/reference/commandline/tag.html)

2. タグしたイメージを確認します<br/>
  `docker image ls`{{execute}} <br/>