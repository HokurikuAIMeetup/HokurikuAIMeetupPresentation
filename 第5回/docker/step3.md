# Dockerのコマンド解説*1

## 1. `docker pull`
- dockerレジストリからdockerイメージを取得する。  
`docker pull nginx`{{execute T1}}  
- ホストにあるdockerイメージの一覧を表示する。  
`docker image`{{execute T1}}

## 2. `docker run`
- dockerイメージをもとにコンテナを起動する。 
- docker runの構文  
    `docker run [OPTIONS] IMAGE [COMMAND] [ARG...]`
- コマンド例1
nginxというイメージをもとにコンテナを作成する  
`docker run --name example1 --publish 80:80 -d nginx`{{execute T1}}
- オプションの説明
  - --name <コンテナの名前> わかりやすいようにコンテナに名前をつける。
  - --publish <ホスト側ポート>:<コンテナ側ポート> コンテナのportをホストマシンに公開する。
  - --detach デタッチモードで起動できる。コンテナをバックグラウンドで実行できる。
  
起動中のコンテナを一覧にして表示する
`docker ps`{{execute T1}}  
コマンド例2
対話モードでdockerを起動する。  
`docker run --name example2 -it --volume /:/ python:3.8 bash`{{execute T1}}
- オプションの説明
  - --volume <ホスト側ディレクトリ>:<コンテナ側ディレクトリ>
   ホストのディレクトリをコンテナと強雨うする
  - -it オプションの`--interactive`と`--tty`をくみあわせたもの。
    コンテナを対話モードで実行することができる。
- Ctrl+Dで対話モードを終了する。
3. コンテナの起動,停止
   - `docker start <コンテナ名>`　コンテナを起動する   
  `docker start example1`{{execute T1}}
  - `docker stop <コンテナ名>` コンテナを停止する。  
  `docker stop example1`{{execute T1}}
4. コンテナの削除  
   - `docker rm <コンテナ名>`  
  `docker rm example1`{{execute T1}}



## 参考
*1 https://knowledge.sakura.ad.jp/14427/