# コンテナの起動

1. 起動中のコンテナを確認します<br/>
  `docker container ls`{{execute}} <br/>

    [説明]<br/>
    - 稼働中のコンテナの一覧を表示します
    - 起動しているコンテナは一つもないことが確認できます

    [参照]<br/>
      - [docker container ls](https://docs.docker.com/engine/reference/commandline/container_ls/)

2. 停止中のコンテナも含めて確認します<br/>
  `docker container ls -a`{{execute}} <br/>

    [説明]<br/>
    - `-a`を付加することで停止中のコンテナも表示します
    - 起動や停止しているコンテナは一つもないことが確認できます

3. コンテナを起動します<br/>
  `docker container run -i centos:6 echo 'hello world' `{{execute}} <br/>

    [実行結果]<br/>

    ```shell
    hello world
    ```

    [説明]<br/>
    - `run`･･･指定したイメージからコンテナを生成します
    - `-i`･･･実行結果を出力します
    - `イメージ名:タグ名`ではなく、イメージIDを指定することも可能です

    [参照]<br/>
      - [docker container run](https://docs.docker.com/engine/reference/commandline/container_run/)

4. 起動中のコンテナを確認します<br/>
  `docker container ls`{{execute}} <br/>

    [説明]<br/>
    - 起動しているコンテナは一つもないことが確認できます

5. 停止中のコンテナも含めて確認します<br/>
  `docker container ls -a`{{execute}} <br/>

    [実行結果]<br/>

    ```shell
    CONTAINER ID   IMAGE        COMMAND                CREATED          STATUS                     PORTS    NAMES
    aab56677fc9e   centos:6     "echo 'hello world'"   3 seconds ago    Exited (0) 2 seconds ago            mystifying_diffi
    ```


    [説明]<br/>
    - 停止しているコンテナが一つあります
    - CONTAINER ID･･･コンテナ生成された際に自動で割り振られる**一意のID**
    - IMAGE･･･コンテナの起動元のイメージID
    - COMMAND･･･コンテナ生成時に実行されるコマンド(`hello world`を表示するコマンド)
    - PORTS･･･通信を許可しているポート
    - NAMES･･･コンテナ名。指定がなければ適当な名前が割り振られる

6. コンテナを起動してもすぐに停止する理由は？

    A: 実行したプロセス(`hello world`の表示)がすぐ終了したから、コンテナも停止した<br/>
    　通常のOSにおいては実行したプロセスが完了しても、待機プロセスがバックグラウンドで常駐しているため、OSが自動停止しない<br/>
    　コンテナは**バックグラウンドなプロセスではなく、フォアグラウンドなプロセスがない限り、終了します**