## dllを別フォルダにまとめる
* app.config内、`<probing privatePath="lib" />`と足すとlib内に入れても読み取られる

```
<runtime>
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
 <probing privatePath="lib" />
</assemblyBinding>
</runtime>
```

## デスクトップアプリ上のブラウザコントロール
* WPFの`System.Windows.Controls.WebBrowser` はデフォルトではIE7互換
    * IE11互換にするには(実行側で?)レジストリ書き換えが必要
* フォームのwebコントロールもおそらく同じ
* CefSharpというのを使うとChromiumが埋め込めるかも？