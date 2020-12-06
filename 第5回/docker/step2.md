# Dockerの仕組み

## コンテナと仮想マシン*1
仮想環境の作成には仮想マシンを用いる方法とコンテナを用いる方法の2種類がある。
- 仮想マシン
  - ホストマシン上でHypervisorを利用しゲストOSを動かす。
- コンテナ
  - コンテナを用いるとホストマシンのカーネルを利用してプロセスをユーザから隔離することであたかも別のOSが動いているかのようにする。

![](https://i.imgur.com/XqDGSm9.png)

## コンテナとイメージ*
- コンテナはLinuxのプロセスの一つである。
- コンテナがプロセスであることの確認  
  `ps aux`でLinuxで動作しているすべてのプロセルをリストアップし、`grep nginx`でnginxというプロスを検索する。  
`ps aux | grep nginx`{{execute T1}}

## Dockerイメージとは？*3 
- Dockerイメージはコンテナを作るのに必要なパッケージのようなもの
- Dockerイメージを用いてコンテナを作成する。
  ![](https://i.imgur.com/BiC28jo.png)

## DockerイメージはDockerfileから作られる*4
- Dockerイメージは層状になっている。
- DockerfileとはDockerイメージを作るための複数の複数のコマンドを記述したもの
- このコマンド一つ一つがレイヤーとなる。
  ![](https://i.imgur.com/i836jDP.png)
## Dockerfileを使ってイメージを作ってみる

Dockerfile
```
FROM python:3.8
COPY app.py / 
CMD python app.py
```

app.py
```
print("Hello Docker")
```

ビルドする。
`docker build -t hello .`{{execute T1}}


## Dockerの構成*2
- DockerはDockerクライアント、Dockerホスト、レジストリの三つで構成されている。
- 下記の図のようにクライアントとホスト、ホストとレジストリが相互にやり取りを行う。
![](https://i.imgur.com/ojrgfOM.png)


## ホスト
- Docker daemonによって構成されている。
- Docker daemonはimage、container、networkのようなDocker Objectを管理する。
![](https://i.imgur.com/Raby2Cy.png)

## クライアント
- dockerコマンドのことである。
- `docker run`、`docker pull`、`docker build` のようなコマンドを用いてDocker deamonとやりとりをすることができる。

## レジストリ
- docker imageを保管する場所
- 代表的なものに[Docker Hub](https://hub.docker.com/)がある。
- これを用いるとdocker imageを保存、取得を行うことができる。

まとめるとこのようになる。  
![](https://docs.docker.com/engine/images/architecture.svg)
## 参考
*1 https://knowledge.sakura.ad.jp/13265/  
*2 https://docs.docker.com/get-started/overview/  
*3 https://qiita.com/zembutsu/items/24558f9d0d254e33088f  
*4 https://docs.docker.com/storage/storagedriver/  