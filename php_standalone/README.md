# 目標：PHPだけの環境を立てる

## 0. 同期用ディレクトリとその中身の作成

```
$ mkdir app
$ echo "<?php phpinfo(); ?>" > app/index.php
```

## 1. Dockerfileの作成

普通のphpのほうはphp-cliなので注意

```
FROM php:7.1-apache
```

2. Dockerfileにもとづいてイメージを持ってくる

```
$ docker build -t php_standalone .
```

3. デーモンで、ホスト80とコンテナ80をつなげて、ホストのappディレクトリとコンテナの/var/www/htmlをつなげる

```
$ docker run -d -p 80:80 -v (pwd)/app:/var/www/html php_standalone
```

4. アクセス

アクセスするといつものページが見れる

