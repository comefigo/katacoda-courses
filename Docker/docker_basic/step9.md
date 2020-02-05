# Pythonプログラムを実行します

このステップではコンテナの利用シーンをわかりやすくするために、<br/>
`3.14 * x`を求めるPythonのプログラムを実装する例で説明します<br/>

従来の方法では、お使いのPCにPythonをインストールし、プログラムを書き、実行するという流れになると思います<br/>
コンテナに置き換えると以下のような手順になります<br/>

1. Pythonのコンテナを起動します<br/>
  `docker container run -it --name my-calc python:3-slim bash`{{execute T1}} <br/>

2. Terminal 2を開き、サンプルプログラムをmy-calcコンテナの`/`にコピーします<br/>
  `docker container cp ./my-calc.py my-calc:/`{{execute T2}} <br/>

    **[説明]**<br/>
      - ホストのファイルをコンテナにコピー。あるいはコンテナのファイルをホストにコピー
      - 別のシナリオで予めコードをコンテナイメージに取り込んだ例を紹介します<br/>

    **[参照]**<br/>
      - [docker cotainer cp](https://docs.docker.com/engine/reference/commandline/container_cp/)

3. Terminal 1でサンプルプログラムに引数5（任意の数字）を渡し実行します<br/>
  `./my-calc.py 5`{{execute T1}} <br/>

    **[実行結果]**<br/>

    ```shell
    15.700000000000001
    ```

    **[説明]**<br/>
      - Pythonの実行環境をコンテナにカプセル化し、実行したいプロセス(my-calc.py)をコンテナ内で実行する

4. まとめ<br/>
  このようにコンテナはプロセスを実行できるカプセル化された環境であることがわかると思います<br/>
  また、実行環境をコンテナ化したことにより、ホストの環境を汚すことなくプロセスを実行できます<br/>
  起動するコンテナのバージョンを変更することで容易に動作確認ができます

5. Python2.7で再実行します<br/>
  `exit`{{execute T1}} <br/>
  `docker container run -it --name my-calc2 python:2-slim bash`{{execute T1}} <br/>

6. Terminal 2で、サンプルプログラムをmy-calc2コンテナの`/`にコピーします<br/>
  `docker container cp ./my-calc.py my-calc2:/`{{execute T2}} <br/>

7. Terminal 1でサンプルプログラムに引数2（任意の数字）を渡し実行します<br/>
  `./my-calc.py 5`{{execute T1}} <br/>

    **[実行結果]**<br/>

    ```shell
    15.700000000000001
    ```

    **[説明]**<br/>
      - pythonのバージョンが異なるが、実行結果が同じとわかる
      - このようにバージョン違い環境も容易に再現できる