# Windows tips

## メモリ診断 (20170915)

### 概要

- Windows でメモリ関連のハードウェア異常が見受けられるときに使える、Windows メモリ診断と言うものがある。
- メモリを 1 枚刺しにしたり、刺すソケットを変えたりしながら試せば原因を特定できるかも
- 診断としては貧弱らしく、見過ごされるエラーもあるが、これでハードウェア異常が見つかればほぼ故障らしい

### 実行方法

- 検索窓にメモリ診断と打ち込んで再起動して待つ
- 結果はスタートボタン右クリック → イベントビュアー →Windows ログ → システム で見られる。
- XML がコピーできるが、読み方は知らない

## ショートカット

- Win + S
  - Cortana 起動（検索窓起動）。Mac の Splotlight 感覚で意外と使える

## 登録されている拡張子は表示しないの無効化するコマンド

- `reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v "HideFileExt" /t REG_DWORD /d "0" /f`

## どのポートでどのアプリケーションが使われているか調べる

- `netstat -nao`

## VPN 接続をコマンド上で管理する

- powershell に `Add-VPNConnection`, `Set-VPNConnection`がある
- ユーザ名、パスワードの変更はできない

## シンボリックリンク

- `mklink <destination> <origin>`
- ディレクトリなら-D をつける

## リモートデスクトップにローカルアカウントでログイン

- 最近の windows はログイン時に Microsoft Account でログインさせようとする
- ユーザー名を `マシン名\ユーザー名` とするか、`\ユーザー名`とすればローカルアカウントとして認識されるよう
