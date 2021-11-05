# Use_AWS_ECS
AWS ECSを使ってみる

## 手順

### Dockerイメージの準備

```
$ docker run hello-world
```

```
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete 
Digest: sha256:37a0b92b08d4919615c3ee023f7ddb068d12b8387475d64c622ac30f45c29c51
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```

### AWS ECS

#### タスク

1. ECSで検索
2. タスク定義
3. FARGATEを選択して、次のステップをクリック
4. 必須項目の入力
    1. タスク名（任意）
    2. タスクメモリ
    3. タスクCPU
4. コンテナの追加
    1. コンテナ名
    2. イメージ
        - イメージはDockerHubのイメージ名を設定。今回は「hello-world」

#### クラスター

1. クラスターをクリック
2. クラスターの作成
3. ネットワーキングのみを選択して、次のステップをクリック
4. 必須項目の入力
    1. クラスター名
5. 次へ押下

#### クラスターへタスクをデプロイする

1. クラスター -> 作成したクラスターをクリック
2. サービスタブ -> デプロイ押下
3. デプロイ設定
    - アプリケーションタイプ : タスク
    - ファミリー : タスク作成で作成したやつ

### 実行

（デプロイすると実行される？）  
ログに```docker run hello-world```したときと同じメッセージが出力される。

## 参考

- [ECSタスクでHello Worldしてみた:DevelopersIO](https://dev.classmethod.jp/articles/ecs-hello-world-task/)