## dllを別フォルダにまとめる
* app.config内、`<probing privatePath="lib" />`と足すとlib内に入れても読み取られる

```
<runtime>
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
 <probing privatePath="lib" />
</assemblyBinding>
</runtime>
```

### ビルド後イベントでlibにdllを移動する
```
cd $(TargetDir)
mkdir lib
move /Y *.dll lib
move /Y *.pdb lib
move /Y *.config lib
move /Y *.xml lib
move /Y lib\$(TargetName).* .
```
* exeからロードする場合はexeも移す

## デスクトップアプリ上のブラウザコントロール
* WPFの`System.Windows.Controls.WebBrowser` はデフォルトではIE7互換
    * IE11互換にするには(実行側で?)レジストリ書き換えが必要
* フォームのwebコントロールもおそらく同じ
* CefSharpというのを使うとChromiumが埋め込めるかも？

## VisualStudioのビルドイベント内でビルド先を取得する
* `$(TargetDir)` でビルド先ディレクトリ、`$(TargetName)`でビルドするアセンブリ名
    * 実行ファイルなら`$(TargetName)`.exe

## VisualStudioのプロジェクトビルドイベントを構成別にする
* csprojでは構成別にビルドイベントを指定できない(!!)みたいなので、 $(ConfigulationName) を使ってif文で分ける
```
if $(ConfigurationName) ==  Release (
echo Release
)
else (
echo "not Release"
)
```
