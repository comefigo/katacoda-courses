# Webサーバを実行してみよう

　前述では実行したい処理(Pythonの計算処理)を必要なタイミングでコンテナで実行して、結果を得ていましたが、Webアプリケーションのように常時待機するような場合はどうなるのかを見ていきましょう<br/>

※下記ではWebアプリケーションではなく、Webサーバを例にしています<br/>

1. Webサーバのコンテナを起動します<br/>
  `docker container run -d --name my-httpd -v ${PWD}/htdocs:/usr/local/apache2/htdocs -p 80:80 httpd:2-alpine`{{execute T1}} <br/>

    **[説明]**<br/>
      - `-v`はホストの`htdocs`（必ず絶対パス）をコンテナの`/usr/local/apache2/htdocs`にマウントする<br/>
        前述ではファイルをコンテナにコピーしていましたが、フォルダを直接マウントすることで、<br/>
        **ホストのデータとコンテナのデータが共有フォルダのように同じものを参照**することができます<br/>
        また、コンテナ内で生成されたデータはコンテナを削除することで消えるが、このようにホストにデータを保存することで**データの永続化**もできます
      - `${PWD}`はコマンドの実行時のパスを取得する環境変数。Windowsは`%cd%`
      - `httpd`はApacheサーバのコンテナイメージ
      - `-p 80:80`はホストの80番ポートとコンテナの80番ポートをマッピングする<br/>
        コンテナへのネットワーク接続はホストのネットワークインターフェースを経由して通信されるため、<br/>
        このように外部からコンテナに通信する必要がある時は明示的にポートのマッピング(ポートフォワーディング)を宣言する必要がある<br/>

    **[参照]**<br/>
      - [httpd(docker hub)](https://hub.docker.com/_/httpd)

2. Webコンテンツを確認します<br/>
  https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/

3. コンテンツを編集してみます<br/>
  `echo -e "<h3>change test page!!</h3>" >> ${PWD}/htdocs/index.html`{execute T1}} <br/>

4. 編集した内容を確認してみしょう<br/>
  https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/

5. まとめ<br/>
    マウントすることでコンテナとホスト間でデータが共有され、このWebサーバの例のようにデザインを確認しながらhtmlファイルを編集するのも簡単にできます<br/>
    繰り返しますが、コンテナは**プロセスが稼働するための環境**でしかない。この例のようにWebページを表示するための環境(Webサーバ)でしかない