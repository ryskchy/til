## リモートアクセス可能なように動かす(最新版)
* `jupyter notebook --generate-config`するだけでとりあえずアクセスは出来るようになる(要ファイアウォール設定)
  * ~/.jupyter/jupyter_notebook_config.pyが作成される
* パスワードはランダムに設定されて、サーバーコンソールに暗号化されたトークンがログとして流れる
* サーバで自動的に開くブラウザではURLに?token=hogehogeとついていて、このurlなら自動的にログインできる
* 今までipythonを開いてやっていたパスワードの暗号化処理は `jupyter notebook password`コマンドで実行できる(~/.jupyter/jupyter_notebook_config.json内に記載される)
* 起動引数でtokenを渡せる `jupyter notebook --NotebookApp.token='xxx'`

## condaで作ったカーネルを切り替える

* 環境一覧を取得
`conda info -e`
* 対象環境をactivate
`activate py2` (py2はAnaconda2.7をインストールした環境)
* `ipython kernel install --user --name=py2 --display-name=Anaconda2.7` を実行
* 追加後

![キャプチャ](キャプチャ.png)