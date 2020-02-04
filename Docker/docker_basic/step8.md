# コンテナのログを確認

1. pingし続けるコンテナを起動します<br/>
  `docker container run -d --name my-ping2 centos:7 ping localhost`{{execute T1}} <br/>

2. 実行中のコンテナの実行ログを確認します<br/>
  `docker container logs my-ping2`{{execute T1}} <br/>

    **[説明]**<br/>
      - `logs`で実行中の`my-ping2`コンテナの標準出力を確認できます
      - もっともよく使うコマンドのうちの一つ！

    **[参照]**<br/>
      - [docker container logs](https://docs.docker.com/engine/reference/commandline/container_logs/)