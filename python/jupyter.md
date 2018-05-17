# jupyter

## リモートアクセス可能なように動かす(最新版)

* `jupyter notebook --generate-config`するだけでとりあえずアクセスは出来るようになる(要ファイアウォール設定)
  * ~/.jupyter/jupyter_notebook_config.pyが作成される
* パスワードはランダムに設定されて、サーバーコンソールに暗号化されたトークンがログとして流れる
* サーバで自動的に開くブラウザではURLに?token=hogehogeとついていて、このurlなら自動的にログインできる
* 今までipythonを開いてやっていたパスワードの暗号化処理は `jupyter notebook password`コマンドで実行できる(~/.jupyter/jupyter_notebook_config.json内に記載される)
* 起動引数でtokenを渡せる `jupyter notebook --NotebookApp.token='xxx'`

## condaで作ったカーネルを切り替える

* 環境一覧を取得

```bash
conda info -e
```

* 対象環境をactivate

```bash
activate <envname> # (envnameはcondaで作った環境名)
```

* 次を実行

```bash
ipython kernel install --user --name=<envname> --display-name=<DisplayName>
```

* 追加後

![キャプチャ](キャプチャ.png)

画像はDisplayNameがAnaconda2.7のケース