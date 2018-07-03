# Git

## githubへのローカルブランチの新規push

* `git push -u origin new_branch`
* `-u` をつけると自動的に追跡ブランチになる

## remoteブランチの削除

* ローカルブランチを消してから `git push origin :branchname`

## ブランチのrename

* `git branch -m <old> <new>`
* カレントなら `git branch -n <new>`でいい

## [github]プルリクエストのマージの際のsquash

* Confirm meregeのボタンの横からsquashができる
  * コミットをまとめる

## リモート側の変更(ブランチの削除など)がローカルに反映されないときの対応

* `git remote show origin` でリモートとの対応関係が表示される
  * 動悸されているものはtracked, リモートで消えているものはstale
* `git remote purune origin` で一気に消せる

## リモートブランチをローカルにチェックアウト

* `git checkout -b <localbranchname> origin/remotebranchname`
* 勝手にsetupstreamされる

## 部分的にpush

* `git subtree push --prefix=<prefix> <remote> <branch>`

## コミットの取り消し

* `git reset --soft HEAD^`
* `--soft` をつけるとワーキングディレクトリはそのまま、`--hard` はワーキングディレクトリも戻す
* 何もつけないとindexも戻す（addも戻す）

## addの取り消し

* `git reset HEAD <filename>`

## `HEAD`, `~` `^`,

* `HEAD`: 今のブランチの先頭コミット
* `~`: n世代前のコミットを指定
  * `~2`: 2世代前のコミット
* `^`: 親コミット
  * `^^`: 1番目の親の1番目の親
  * `^2`: 2番目の親