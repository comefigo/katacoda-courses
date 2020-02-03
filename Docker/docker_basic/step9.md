# Pythonプログラムを実行します

このステップではコンテナの利用シーンをわかりやすくするために、<br/>
`1 + 1`を求めるPythonのプログラムを実装する例で説明します<br/>

従来の方法では、お使いのPCにPythonをインストールし、プログラムを書き、実行するという流れになると思います<br/>
コンテナに置き換えると以下のような手順になります<br/>

1. Pythonのコンテナを起動します<br/>
  `docker container run -it --name my-calc python:slim bash`{{execute HOST0}} <br/>

2. Terminal 2からサンプルプログラムをコンテナ内にコピーします<br/>
  `docker container cp /my-calc.py my-calc:/`{{execute HOST1}} <br/>

3. Terminal 1でサンプルプログラムを実行します<br/>
  `./my-calc.py`{{execute HOST0}} <br/>