## ボイラープレート

* 定型文、おまじない

## リファクタリング

* まずはDuplicationを解消ことを優先する
  * 修正もduplicateすることになる

## SSH公開鍵

* `~/.ssh/config` に

```text
Host github github.com
  HostName github.com
  IdentityFile ~/.ssh/<秘密鍵名>
  User git
```

と書けばsshの鍵を指定できる