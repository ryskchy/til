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