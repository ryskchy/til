# Misc

## ボイラープレート

- 定型文、おまじない

## リファクタリング

- まずは Duplication を解消ことを優先する
  - 修正も duplicate することになる

## SSH 公開鍵

- `~/.ssh/config` に

```text
Host github github.com
  HostName github.com
  IdentityFile ~/.ssh/<秘密鍵名>
  User git
```

と書けば ssh の鍵を指定できる

## Slack bot

- 書き込むだけの slack bot は incomming webhook で十分
