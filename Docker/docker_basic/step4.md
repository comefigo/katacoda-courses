# コンテナの起動

1. 起動中のコンテナを確認します<br/>
  `docker container ls`{{execute T1}} <br/>

    **[説明]**<br/>
    - 稼働中のコンテナの一覧を表示します
    - 起動しているコンテナは一つもないことが確認できます<br/>

    **[参照]**<br/>
    - [docker container ls](https://docs.docker.com/engine/reference/commandline/container_ls/)

2. 停止中のコンテナも含めて確認します<br/>
  `docker container ls -a`{{execute T1}} <br/>

    **[実行結果]**<br/>

    ```shell
    CONTAINER ID   IMAGE     COMMAND       CREATED       STATUS       PORTS    NAMES
    ```

    **[説明]**<br/>
    - `-a`を付加することで停止中のコンテナも表示します
    - 起動や停止しているコンテナは一つもないことが確認できます

3. コンテナを起動します<br/>
  `docker container run -i --name my-hello centos:6 echo 'hello world' `{{execute T1}} <br/>

    ****[実行結果]****<br/>

    ```shell
    hello world
    ```

    **[説明]**<br/>
    - `run`･･･指定したイメージからコンテナを生成します
    - `-i`･･･実行結果を出力します
    - `イメージ名:タグ名`ではなく、イメージIDを指定することも可能です
    - `echo 'hello world'`は**[ベースイメージ(centos:6)で指定されたコマンド](https://github.com/CentOS/sig-cloud-instance-images/blob/23b05f6a35520ebf338e4df918e4952830da068b/docker/Dockerfile#L11)を上書きすることができる**
    - `--name`･･･コンテナ名を命名して起動。未指定の場合は、適当な名前が割り当てられます<br/>

    **[参照]**<br/>
      - [docker container run](https://docs.docker.com/engine/reference/commandline/container_run/)

4. 起動中のコンテナを確認します<br/>
  `docker container ls`{{execute T1}} <br/>

    **[説明]**<br/>
    - 起動しているコンテナは一つもないことが確認できます

5. 停止中のコンテナも含めて確認します<br/>
  `docker container ls -a`{{execute T1}} <br/>

    **[実行結果]**<br/>

    ```shell
    CONTAINER ID   IMAGE        COMMAND                CREATED          STATUS                     PORTS    NAMES
    aab56677fc9e   centos:6     "echo 'hello world'"   3 seconds ago    Exited (0) 2 seconds ago            my-hello
    ```

    **[説明]**<br/>
    - 停止しているコンテナが一つあります
    - CONTAINER ID･･･コンテナ生成された際に自動で割り振られる**一意のID**
    - IMAGE･･･コンテナの起動元のイメージID
    - COMMAND･･･コンテナ生成時に実行されるコマンド(`hello world`を表示するコマンド)
    - PORTS･･･通信を許可しているポート
    - NAMES･･･コンテナ名

6. コンテナを起動してもすぐに停止する理由は？

    実行したプロセス(`hello world`の表示)がすぐ終了したから、コンテナも停止した<br/>
    通常のOSにおいては実行したプロセスが完了しても、待機プロセスがバックグラウンドで常駐しているため、OSが自動停止しない<br/>
    コンテナは**バックグラウンドなプロセスではなく、フォアグラウンドなプロセスがない限り、終了します**

7. 再度コンテナを起動します<br/>
  `docker container run -i --name my-hello2 centos:6 echo 'hello katacoda' `{{execute T1}} <br/>

    **[実行結果]**<br/>

    ```shell
    hello katacoda
    ```

8. 再度、停止中のコンテナも含めて確認します<br/>
  `docker container ls -a`{{execute T1}} <br/>

    **[実行結果]**<br/>

    ```shell
    CONTAINER ID   IMAGE        COMMAND                   CREATED          STATUS                     PORTS    NAMES
    aab56677fc9e   centos:6     "echo 'hello world'"      3 seconds ago    Exited (0) 2 seconds ago            my-hello
    7821f714f10b   centos:6     "echo 'hello katacoda'"   3 seconds ago    Exited (0) 2 seconds ago            my-hello2
    ```

    **[説明]**<br/>
    - 停止しているコンテナが2つになりました
    - コンテナIDはそれぞれ異なるIDになっています<br/>
      つまり、2つのコンテナはそれぞれ別ものとして扱われます(※図1)

    [図1]