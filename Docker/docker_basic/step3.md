# コンテナイメージの削除

1. コンテナイメージを削除します<br/>
  `docker image rm my-centos:my-6`{{execute T1}} <br/>

    **[説明]**<br/>
    - `my-centos:my-6`は前述に付けた`任意のイメージ名:タグ名`
    - イメージIDのみの指定でもOK。<br/>
      他のイメージIDと被りがなければ、イメージIDの先頭1桁～指定でもOK
    - 複数イメージを削除したい場合は、半角空白でイメージ名もしくはイメージIDを区切る<br/>

    **[参照]**<br/>
      - [docker image rm](https://docs.docker.com/engine/reference/commandline/image_rm/)

2. イメージを確認します<br/>
  `docker image ls`{{execute T1}} <br/>

    **[説明]**<br/>
    - 元のイメージが削除されていないことが確認できます
    - 元のイメージ(`centos:6`)を削除した場合は、任意のイメージ(my-centos)が残ります