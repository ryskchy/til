## import
* ECMAScript6からimportとexportが実装される(詳細未調査)
* htmlの`<script>` タグで呼び出すときは`<body>`の最後にするとレンダリング後にダウンロードされるから推奨される
* 依存関係の親から順にか呼び出す
    * globalな名前空間に入るため

## number
* javascriptの数値はすべて浮動小数点数
* parseInt()してもnumberのまま
* 整数部分は53ビットなのでlongより狭い