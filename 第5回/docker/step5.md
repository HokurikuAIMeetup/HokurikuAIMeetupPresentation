# Dockerを機械学習で使う
Dockerを用いてjupyter notebookを起動する。*1    
`docker run -p 80:8888 --rm -it tensorflow/tensorflow:1.15.4-jupyter`{{execute T1}}  
tokenはコマンドラインの下のほうに書いてある。

dockerでkaggleのノートブックの環境も使うことができる。  
`docker run --rm -it gcr.io/kaggle-images/python /bin/bash
`{{execute T1}}
## 参考
*1 https://hub.docker.com/r/tensorflow/tensorflow/