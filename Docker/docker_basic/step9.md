# Pythonプログラムを実行します

このステップではコンテナの利用シーンをわかりやすくするために、<br/>
`1 + 1`を求めるPythonのプログラムを実装する例で説明します<br/>

従来の方法では、お使いのPCにPythonをインストールし、プログラムを書き、実行するという流れになると思います<br/>
コンテナに置き換えると以下のような手順になります<br/>

1. Pythonのコンテナを起動します<br/>
  `docker container run -it --name my-calc python:slim bash`{{execute T1}} <br/>

2. Terminal 2を開き、サンプルプログラムをコンテナ内の`/root/`にコピーします<br/>
  `docker container cp /my-calc.py my-calc:/`{{execute T2}} <br/>

    **[説明]**<br/>
      - ホストのファイルをコンテナにコピー。あるいはコンテナのファイルをホストにコピー

    **[参照]**<br/>
      - [docker cotainer cp](https://docs.docker.com/engine/reference/commandline/container_cp/)

3. Terminal 1でサンプルプログラムを実行します<br/>
  `./my-calc.py`{{execute T1}} <br/>

    [実行結果]<br/>

    ```shell
    2
    ```