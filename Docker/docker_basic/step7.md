# 稼働中のコンテナに接続

1. コンテナに接続します<br/>
  `docker container run -d --name my-ping centos:7 ping localhost`{{execute T1}} <br/>

    **[説明]**<br/>
      - `-d`はコンテナをバックグラウンドで稼働させる

2. Terminal 2を開き、稼働中のコンテナに（別プロセス）接続<br/>
  `docker container exec -it my-ping bash`{{execute T2}} <br/>

    **[説明]**<br/>
      - `exec`はコンテナ内でコマンドを発行する<br/>
        メインのプロセス(`ping`)とは別のプロセスを実行できる
      - `bash`を起動してコンテナを操作する<br/>

    **[参照]**<br/>
    - [docker container exec](https://docs.docker.com/engine/reference/commandline/container_exec/)

3. Terminal 2でコンテナ内のプロセスを確認します<br/>
  `ps aux`{{execute T2}} <br/>

    **[説明]**<br/>
      - `ping`のプロセスが実行中であることが確認できる

4. Terminal 2で稼働中のコンテナからログアウトします<br/>
  `exit`{{execute T2}} <br/>

5. Terminal 2で実行中のプロセスに接続<br/>
  `docker container attach my-ping`{{execute T2}} <br/>

    **[説明]**<br/>
      - `ping`コマンドの実行ログが確認できる
      - ホストに抜ける場合は、「Ctrl」+「P」または「Ctrl」+「Q」<br/>
        ※「Ctrl」+「C」で実行中のコンテナが終了しますので、ご注意ください！


