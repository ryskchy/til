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