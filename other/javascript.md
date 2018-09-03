# JavaScript

## import

- ECMAScript6 から import と export が実装される(詳細未調査)
- html の`<script>` タグで呼び出すときは`<body>`の最後にするとレンダリング後にダウンロードされるから推奨される
- 依存関係の親から順にか呼び出す
  - global な名前空間に入るため

## number

- javascript の数値はすべて浮動小数点数
- parseInt()しても number のまま
- 整数部分は 53 ビットなので long より狭い

## オブジェクトのメンバ名（連想配列のキー）

- 下記のようにすると、キーは文字列の'1,1'になる
  - for .. of でループするときに注意

'''
var a = {};
a[[1, 1]] = 10;
'''

## nodist

- windows で複数バージョン使用は nodist を使う
  - powershell でしか動かない？

## npm install のオプション

- `--save`: `package.json` に記録される
  - `--save-dev`: devDependencies に記載され、開発環境をつくったときだけインストールされる
- `-g`: グローバル環境にインストールされる
