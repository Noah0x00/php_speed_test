# phpでpreloadのスピード計測
## 概要
dockerを使用して、PHPのフレームワークLaravelの初期画面で速度計測を行います

## 環境
- nginx(docker imageのnginx:latest)
- PHP7.2.12
- PHP7.4.3
- Laravel Framework 7.2.0

## 使用方法
### コンテナの起動

```
cd ./docker
docker-compose -f ./docker-compose-phpv[使用したいバージョン].yml up -d
```
- docker-compose-phpv7.2.12.yml
  - PHP7.2.12(opcacheあり)
- docker-compose-phpv7.4.3.yml
  - PHP7.4.3(opcacheあり)
- docker-compose-phpv7.4.3_preload.yml
  - PHP7.4.3(opcache、preloadあり)

### URL
- http://localhost:8080/
  - Laravelのデフォルトページ
- http://localhost:8080/phpinfo
  - phpinfo
- http://localhost:8080/included_files
  - includeされてるファイル一覧

## その他
- preloadされてるファイル
  - Laravelのデフォルトページでincludeされてるファイル一覧をopcache_compile_fileしただけの簡単なものです
- preloadするファイルを変更したい
  - docker/phpv[変更したいバージョン]/preload_laravel.phpを変更
- 別のPHPのバージョンを試したい
  - docker/phpv[バージョン]を使用したいバージョンに合わせてコピー
    - docker/phpv[バージョン]/DockerfileのFROMを変更使用したいバージョンに変更
    - docker/phpv[バージョン]/php.iniはバージョンに合わせて修正
  - docker/docker-compose-phpv[バージョン].ymlを使用したいバージョンに合わせてコピー
    - docker/docker-compose-phpv[バージョン].ymlのappの項目を変更
