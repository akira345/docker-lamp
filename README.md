DockerでLAMP環境を作成する
====

DockerでLAMPでの開発環境を作成するスクリプトです。

PHP7+phpMyAdmin+MySQL5.6の環境が作成されますので、
簡単に開発環境を作成することが出来ます。

composerもインストールされています。
```bash
git clone https://github.com/akira345/docker-lamp.git
cd docker-lamp/
docker-compose up -d
```
