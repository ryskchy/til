## githubへのローカルブランチの新規push

* `git push -u origin new_branch`
* `-u` をつけると自動的に追跡ブランチになる

## remoteブランチの削除
* ローカルブランチを消してから `git push origin :branchname`

## ブランチのrename
* `git branch -m <old> <new>`
* かれんとなら `git branch -n <new>`でいい