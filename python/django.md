# django

## アプリケーションを作るときのお約束

```
django-admin startproject <project_name>
cd <project_name>
python managee.py startapp <app_name>
```

## URLからパラメータを取り出す

* `<project>/<project>/url.py` でurlパターンを指定
  * django.urls.pathとdjango.conf.urls.urlで微妙に挙動が違う?
* 呼び出し先の関数で第一引数(request)の`request.GET` にdjango.http.QueryDict型で保持
  * valueがリストになっていることに注意