## Setup

### Setup

プロジェクトフォルダ作成

```
docker-compose run --rm app django-admin startproject config .
```

### dbの値変更

```
[settings.py]

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'root',
        'PASSWORD': 'password',
        'HOST': 'db',
        'PORT': 5432,
    }
}
```

### 起動

```
docker-compose up
```

### migrate

```
docker-compose exec app bash
python manage.py migrate
```

## 参考記事

- 参考

https://self-methods.com/django-docker-easy/

プロジェクト作成 は下記だとDockerfileのある箇所における

```
docker-compose run --rm app django-admin startproject config .
```

マイグレーションコマンド
```
python manage.py migrate
```

- db参考
https://inglow.jp/techblog/docker-django/


- DBの設定ファイル
settings.py

■エラー集

- mysql 5.7が M1では利用できない対応

https://gihyo.jp/dev/serial/01/mysql-road-construction-news/0167

- エラー: no matching manifest for linux/arm64/v8 in the manifest list entries
https://zenn.dev/marumarumeruru/articles/55173a98863d4e


- ドキュメント <=  うまくいかない
https://docs.docker.jp/compose/django.html


- django-web-1  | django.db.utils.OperationalError: (1044, "Access denied for user 'django'@'%' to database 'django'")

volumeが悪さしている？


- Djungo ドキュメント

https://docs.djangoproject.com/ja/4.1/intro/tutorial01/


startproject は rails newと同じ
```
 django-admin startproject mysite
```



- PYTHONUNBUFFERED
  - 非空なら標準出力・標準エラーのストリームのバッファリングを行わない
- requirements.txt
  - bundle installの Gemfileのようなもの
  - 中に Djungoを入れている

- ファイルの関係
  - Dockerfileに pythonを入れる && ライブリインストールコマンド
  - requirements.txt: Djungoなどの情報を設置

- docker-compose up
  - build と run でコンテナを作成


- プロジェクト作成

```
docker-compose run web django-admin.py startproject composeexample .
```
