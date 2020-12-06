## Docker Compose とは？*1
Docker Composeとは複数コンテナのDockerアプリケーションを実行定義するツールである。

## 実際に使ってみよう！
wordpressの実行を例に説明する。  
docker-compose.yml
```
version: '3'
services:

  wordpress:
    image: wordpress
    container_name: some-wordpress
    restart: always
    ports:
      - 80:80
    environment:
      WORDPRESS_DB_PASSWORD: my-secret-pw

  mysql:
    image: mysql:5.7
    container_name: some-mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
```

コンテナをバックグラウンドで起動する  
`docker-compose up -d`{{execute T1}}  
コマンドライン上で実行されていることの確認    
`docker-compose ps`{{execute T1}}  
Docker composeを停止する
`docker-compose stop`{{execute T1}}  

## 参考
*1 https://knowledge.sakura.ad.jp/21387/