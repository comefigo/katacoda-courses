# コンテナイメージを取得

1. CentOS 6のイメージを取得します<br/>
  `docker pull centos:6`{{execute}} <br/>

    [説明]<br/>
    - pull･･･コンテナイメージの[リポジトリ](https://hub.docker.com/_/centos?tab=description)（デフォルトは[Docker hub](https://hub.docker.com/search?q=&type=image)）からイメージを取得。プライベートなリポジトリも構築可能
    - centos･･･イメージの名前
    - 6･･･タグ名。指定しない場合は`latest`（最新版）として扱われます
    - イメージの実態は**アプリケーションが実行できるためのファイル群**(OS関連、ランタイム、ミドルウェアなど)

    [参照]<br/>
      - [docker pull](http://docs.docker.jp/engine/reference/commandline/pull.html)

2. 取得したイメージを確認します<br/>
  `docker image ls`{{execute}} <br/>

    [実行結果]<br/>

    ```shell
    REPOSITORY      TAG         IMAGE ID            CREATED             SIZE
    centos          6           d0957ffdf8a2        10 months ago       194MB
    ```

    [説明]<br/>
    - REPOSITORY･･･イメージ名<br/>
      個人のイメージは「ユーザ名/イメージ名:タグ名」を付けるのが慣例
    - TAG･･･タグ名
    - IMAGE ID･･･イメージID
    - SIZE･･･イメージサイズ

    [ポイント]<br/>
      - **アプリケーションを動作させるための最低限のファイル群しかない**ため、サイズが小さい<br/>
      　※通常の[CentOS 6のISOイメージサイズ](http://isoredirect.centos.org/centos/6/isos/x86_64/)は3.7GB～

    [参照]<br/>
      - [docker image](https://docs.docker.com/engine/reference/commandline/image/)(英語)

3. より詳細のイメージの情報を表示します<br/>
  `docker inspect centos:6`{{execute}}

    [実行結果]<br/>
    ```json
    [
    {
        "Id": "sha256:d0957ffdf8a2ea8c8925903862b65a1b6850dbb019f88d45e927d3d5a3fa0c31",
        "RepoTags": [
            "centos:6"
        ],
        "RepoDigests": [
            "centos@sha256:dec8f471302de43f4cfcf82f56d99a5227b5ea1aa6d02fa56344986e1f4610e7"
        ],
        "Parent": "",
        "Comment": "",
        "Created": "2019-03-14T21:20:11.486358099Z",
        "Container": "d519f3e5c41d16388d3fba0dac626427b21deb98cce150dee80c180b9baf9435",
        "ContainerConfig": {
            "Hostname": "d519f3e5c41d",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/sh",
                "-c",
                "#(nop) ",
                "CMD [\"/bin/bash\"]"
            ],
            "ArgsEscaped": true,
            "Image": "sha256:143abcd43bce45f4fd9ba51c7361051d7ea9e9e1eadb66e5c94a9c1b7754524f",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.label-schema.build-date": "20181006",
                "org.label-schema.license": "GPLv2",
                "org.label-schema.name": "CentOS Base Image",
                "org.label-schema.schema-version": "1.0",
                "org.label-schema.vendor": "CentOS"
            }
        },
        "DockerVersion": "18.06.1-ce",
        "Author": "https://github.com/CentOS/sig-cloud-instance-images",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/bash"
            ],
            "ArgsEscaped": true,
            "Image": "sha256:143abcd43bce45f4fd9ba51c7361051d7ea9e9e1eadb66e5c94a9c1b7754524f",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.label-schema.build-date": "20181006",
                "org.label-schema.license": "GPLv2",
                "org.label-schema.name": "CentOS Base Image",
                "org.label-schema.schema-version": "1.0",
                "org.label-schema.vendor": "CentOS"
            }
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 193898046,
        "VirtualSize": 193898046,
        "GraphDriver": {
            "Data": {
                "RootDir": "/var/lib/docker/overlay/8dbe20bfb1b46bad6495f0fde28921ea3003e02da49b9454746291efe6a3a88c/root"
            },
            "Name": "overlay"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:af6bf1987c2eb07d73f33836b0d8fd825d7c785273526b077e46780e8b4b2ae9"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
    ]
    ```

    [説明]<br/>
    - `docker inspect <リソース名 もしくは リソースID>`で指定したリソース(イメージ、コンテナ、ネットワーク)の詳細情報を確認することができます
    - リソースの情報は**json形式**で表示されます

    [参照]<br/>
    - [docker inspect](http://docs.docker.jp/engine/reference/commandline/inspect.html)