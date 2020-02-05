# ホストとコンテナの関係

1. コンテナに接続します<br/>
  `docker container run -it centos:6 bash`{{execute T1}} <br/>

    **[説明]**<br/>
      - コンテナの生成と同時にbashが実行されます
      - `-it`はログインする際に必須のパラメータになります
      - `[root@コンテナID /]#` になったらログイン完了です

2. 新しいTerminal 2を起動し、起動中のコンテナを確かめてみよう<br/>
  `docker container ls`{{execute T2}} <br/>

    **[説明]**<br/>
      - 1つのコンテナが起動中であると確認できます
      - 前述で立ち上げたコンテナがログイン状態のため、起動したままになっています

## コンテナとホストは異なるOSとして認識される

1. Terminal 1でコンテナのOSのバージョンを確認します<br/>
  `cat /etc/redhat-release`{{execute T1}} <br/>

    **[実行結果]**<br/>
      ```
      CentOS release 6.10 (Final)
      ```

    **[説明]**<br/>
      - CentOSとして認識されています

2. Terminal 2でホストのOSのバージョンを確認します<br/>
  `cat /etc/os-release`{{execute T2}} <br/>

    **[実行結果]**<br/>
      ```
      NAME="Ubuntu"
      VERSION="19.04 (Disco Dingo)"
      ID=ubuntu
      ID_LIKE=debian
      PRETTY_NAME="Ubuntu 19.04"
      VERSION_ID="19.04"
      HOME_URL="https://www.ubuntu.com/"
      SUPPORT_URL="https://help.ubuntu.com/"
      BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
      PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
      VERSION_CODENAME=disco
      UBUNTU_CODENAME=disco
      ```

    **[説明]**<br/>
      - Ubuntuである
      - コンテナとホストは**異なるOSとして認識されています**

## コンテナのプロセスはホストで動く

1. Terminal 1(コンテナ)でsleepプロセスを実行します<br/>
  `sleep 10000`{{execute T1}} <br/>

    **[説明]**<br/>
      - 10000間待機する

2. Terminal 2で実行中のプロセスを確認します<br/>
  `ps -aux`{{execute T2}} <br/>

    **[説明]**<br/>
      - `sleep`を実行しているプロセスを確認します
      - ホストからはコンテナのプロセスを確認できます
      - コンテナ同士のプロセスは名前空間が異なるため、お互いにアクセスすることはできない
      - コンテナからホストのプロセスは見えない

3. Terminal 1(コンテナ)のsleepを「Ctrl」＋「C」で停止させます


## コンテナはホストのカーネルと共有する

※コンテナランタイム(kata containers)を変えることでカーネル分離型のコンテナを作ることもできる。それによりセキュリティの強度を高めることができる

1. Terminal 1(コンテナ)でカーネルを確認します<br/>
  `uname -a`{{execute T1}} <br/>

2. Terminal 2でカーネルを確認します<br/>
  `uname -a`{{execute T2}} <br/>

    **[説明]**<br/>
      - カーネルが同じである
      - コンテナのセキュリティに脆弱性があるとホストも感染しやすくなる

3. Terminal 1でコンテナを終了します<br/>
  `exit`{{execute T1}} <br/>