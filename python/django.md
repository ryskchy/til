# django

## アプリケーションを作るときのお約束

```sh
django-admin startproject <project_name>
cd <project_name>
python managee.py startapp <app_name>
```

## URLからパラメータを取り出す

* `<project>/<project>/url.py` でurlパターンを指定
  * django.urls.pathとdjango.conf.urls.urlで微妙に挙動が違う?
* 呼び出し先の関数で第一引数(request)の`request.GET` にdjango.http.QueryDict型で保持
  * valueがリストになっていることに注意

## URLのマッピング

* `<project>/url.py` 内の `url_patterns` にdjango.urls.path などで指定
* django.urls.pathは第一引数がroute, 第二引数がview
* django.urls.includeで他のファイルのURLパターンをインクル0度する


## モデルの変更

1. `<application>/models.py`を変更する
2. `python manage.py makemigrations`
3. `python manage.py migrate`

* `migrate` は`sqlmigrate <appname> <migration No>`で実行するSQLを事前に見られる
* `python manage.py check`で事前確認