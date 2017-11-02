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

## ??演算子
* `Hoge a = hoge?? new Hoge();`
* `Hoge a = hoge == null ? new Hoge() : hoge;` と同等

## Nullabe構造体のValueプロパティ
* `(bool?)`などのnull許容型にある.Valueプロパティは、.HasValueがtrueの時 (=null以外のものが入っている時)はnull非許容の値を返すが、nullのときは例外になるので安全ではない

## Nullable boolのif分岐(WPFのDialogResult等)
* StackOverflowでは `if(value == true)`が人気。個人的にはかなり違和感がある
* 他に `if(value.HasValue && value.Value)`, `if(value ?? false)`など