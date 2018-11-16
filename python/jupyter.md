# jupyter

## リモートアクセス可能なように動かす(最新版)

- `jupyter notebook --generate-config`とし、コンフィグファイルの `c.NotebookApp.ip`を修正すればとりあえずアクセスは出来るようになる(要ファイアウォール設定)
  - ~/.jupyter/jupyter_notebook_config.py が作成される
- 起動時に `jupyter notebook --ip="*"` としてもいい
- パスワードはランダムに設定されて、サーバーコンソールに暗号化されたトークンがログとして流れる
- サーバで自動的に開くブラウザでは URL に?token=hogehoge とついていて、この url なら自動的にログインできる
- 今まで ipython を開いてやっていたパスワードの暗号化処理は `jupyter notebook password`コマンドで実行できる(~/.jupyter/jupyter_notebook_config.json 内に記載される)
- 起動引数で token を渡せる `jupyter notebook --NotebookApp.token='xxx'`

## conda で作ったカーネルを切り替える

- 環境一覧を取得

```bash
conda info -e
```

- 対象環境を activate

```bash
activate <envname> # (envnameはcondaで作った環境名)
```

- 次を実行

```bash
ipython kernel install --user --name=<envname> --display-name=<DisplayName>
```

- 追加後

![キャプチャ](キャプチャ.png)
画像は DisplayName が Anaconda2.7 のケース

- Pipenv 等で作った環境でも同様にシェルが使える状態にすれば可能

## Magic Function の作り方

- `IPython.core.magic` から `register_cell_magic, register_line_cell_magic, register_line_magic`あたりをインポートして関数をデコレートするか、
- `IPython.core.magic` から `magics_class` をインポートしてクラスをデコレートし、 `cell_magic, line_cell_magic, line_magic`あたりをインポートしてメソッドをデコレートする
- クラスをデコレートすると Magic Function の実行をまたいで状態を保持できる
- `IPython.core.magic_arguments` の`argument, magic_arguments, parse_argstring` あたりで引数をパースできる（詳細未確認）
- コードを実行する場合は`IPython.core.interactiveshell.InteractiveShell` オブジェクトを受け取り、`run_cell, safe_execfile` 等する

## 標準入出力

- `sys.stdin.readline` は常に空文字を返す
  - 書き換えても`input`はキャプチャできない
- `sys.stdout`は書き換えればキャプチャできる
  - `sys.__stdout__` はコンソール側の出力なので、戻すためには別変数に保持する必要がある
