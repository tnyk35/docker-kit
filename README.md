# dockerでLAMP環境作ってみた

## lampディレクトリ

### 構成
- CentOS 7.4
- Apache 2.4.6
- PHP 7.2.1
- MySQL 5.7.20

### ファイル構造
- mysql/my.cnf MYSQLの設定ファイル
- webroot/　サーバーのルートディレクトリになる。ここにファイルを置けば表示できる
- Dockerfile　省略
- docker-compose.yml　省略
- httpd.conf Apacheの設定　/etc/httpd/conf/httpd.confの末尾に追加される

### 手順

1.Docker for MAC（Windows）を入れる

ここからDL
https://store.docker.com/editions/community/docker-ce-desktop-mac

または

```
# homebrewで管理したい場合
brew cask install docker
```

2.cloneしてdocker-composeを実行

```
git clone 
cd docker/lamp/
docker-compose up（もしくは、docker-compose up -d）
```

- 起動が終わったら、http://localhost:10080/ にアクセスすればphpinfoの画面が出てくる
- http://localhost:10080/db.php にアクセスすればDBの設定情報がみれる

ちなみに
- 止めたいときは
```
docker-composer down
```

- 消したいときは
```
docker-composer rm
```

- 直接サーバーにアクセスしたいときは
```
docker exec -it lamp_web_1 bash
```

### DB接続情報

- id root
- pw root
- port 13306

```
mysql -u root -p -h 127.0.0.1 --port 13306
```

でアクセス出来る。

※多分ローカルにmysqlはいってないとコマンドが実行できないはず