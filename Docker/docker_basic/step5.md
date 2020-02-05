# コンテナの原則

**1コンテナ1プロセス**

# コンテナ操作

1. コンテナの情報を確認します<br/>
  `docker container inspect my-hello`{{execute T1}} <br/>

    **[説明]**<br/>
      - コンテナ情報（IP、マウント先、ホスト名）がjson形式で表示される
      - コンテナ名の代わりにコンテナIDを指定してもOK。他のコンテナのIDと被りがなければ一桁から指定できます<br/>

    **[参照]**<br/>
    - [docker container inspect](https://docs.docker.com/engine/reference/commandline/container_inspect/)


2. 停止中のコンテナを起動します<br/>
  `docker container start my-hello`{{execute T1}} <br/>

    **[説明]**<br/>
      - 再度同じコマンド(`hello world`)が実行される<br/>

    **[参照]**<br/>
    - [docker container start](https://docs.docker.com/engine/reference/commandline/container_start/)

3. コンテナを削除します<br/>
  `docker container rm my-hello2`{{execute T1}} <br/>

    **[説明]**<br/>
      - 停止中のコンテナが削除されます
      - `-f`を追加することで起動中のコンテナを強制削除できます<br/>

    **[参照]**<br/>
    - [docker container rm](https://docs.docker.com/engine/reference/commandline/container_rm/)