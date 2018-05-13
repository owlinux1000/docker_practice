# 目標：sinatraが動くだけの環境を立てる

## 0. コピー用のディレクトリとその中身の作成

```
$ mkdir app
$ emacs app/main.rb
```


## 1. Dockefileの作成

今回は、sinatraを動かすためにまず ```gem install sinatra``` をする必要がある。  

```
FROM ruby:2.5.0
COPY ./app /app
WORKDIR /app
RUN gem install sinatra
CMD ["ruby", "main.rb", "-o", "0.0.0.0"] # 普通に起動するとlocalhostになる
```

## 2. Dockerイメージの作成

```
$ docker build -t sinatra .
```

## 3. 起動

ホスト4567:コンテナ4567をつなげて、起動

```
$ docker run -d -p 4567:4567 sinatra
```

## 4. テスト

```
$ curl localhost:4567/
Hello World from Sinatra in Docker
```
