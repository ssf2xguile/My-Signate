# 概要

これはA.M.RがSIGNATEコンペに参加するためのリポジトリである。


# 環境構築

Dockerをベースに環境構築を行う。jupyter notebookのdockerイメージを利用するためDockerfileは必要としない。
1. Dockerイメージをpullする ※初回のみ
```
docker pull continuumio/anaconda3:latest
```
2. Dockerコンテナを立ち上げる(Windowsの場合)
```
docker run -v %cd%:/signate -p 8889:8888 --rm -it continuumio/anaconda3:latest
```
Mac or Linuxの場合
```
docker run -v $(pwd):/signate -p 8889:8888 --rm -it continuumio/anaconda3:latest
```
3. コンテナ内でjupyter notebookを起動する
```
jupyter notebook --ip 0.0.0.0 --allow-root --no-browser --NotebookApp.disable_check_xsrf=True --NotebookApp.token='' --NotebookApp.password='' /signate
```
4. ブラウザでjupyter notebookにアクセスする
`http://localhost:8889`を開く

[参考][Dockerコンテナを利用したPython,Jupyterの環境構築とVScodeとのリモート接続](https://qiita.com/sumiyoshi01/items/06d5277692f0444473b9)

## ディレクトリ構造

```
signate
├─data_in	# 入力データを保管するフォルダ
├─data_out	# 出力データを保管するフォルダ
├─model		# プログラムにより作成した機械学習モデルを保管するフォルダ
└─src		# ソースコードを保管するフォルダ
```
