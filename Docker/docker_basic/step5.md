# コンテナの原則

**1コンテナ1プロセス**

# コンテナ操作

1. コンテナの情報を確認します<br/>
  `docker container inspect <コンテナ名 | コンテナID>` {{copy}} <br/>

    [説明]<br/>
      - コンテナ情報（IP、マウント先、ホスト名）がjson形式で表示される

    [参照]<br/>
    - [docker container inspect](https://docs.docker.com/engine/reference/commandline/container_inspect/)


2. 停止中のコンテナを起動します<br/>
  `docker container start <コンテナ名 | コンテナID>` {{copy}} <br/>

    [説明]<br/>
      - 再度同じコマンドが実行される

    [参照]<br/>
    - [docker container start](https://docs.docker.com/engine/reference/commandline/container_start/)

3. コンテナを削除します<br/>
  `docker container rm <コンテナ名 | コンテナID>` {{copy}} <br/>

    [説明]<br/>
      - 再度同じコマンドが実行される
      - `-f`を追加することで起動中のコンテナを強制削除できます

    [参照]<br/>
    - [docker container rm](https://docs.docker.com/engine/reference/commandline/container_rm/)