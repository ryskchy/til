## ボタンの形を変える
* ボタンのTempleteプロパティで色々書ける
* TempleteBindingバインディング拡張で、テンプレート適用先のプロパティ値を参照できる
* ContentPresenterをつけないともとのContentが反映されない
    * TargetTypeをつけていないときも反映されない

## GroupBoxのヘッダをラジオボタンに
* 普通に
```
<GroupBox Name="gbHogehoge">
                    <GroupBox.Header>
                        <RadioButton
                            Name="rbHoge"
                            Content="Line" />
                    </GroupBox.Header>
```
でできる

## Radiobuttonのグルーピング
* 同じ親コンテナに配置するか、GroupNameプロパティで指定する

## コントロール同士のバインディング
```
<CheckoBox Name="cb">
<Button IsEnabled={Binding ElementName=cb, Path=IsChecked}>
```

## Mahapps.MetroのRangeSlider
* Minimum, Maximumは選択できる範囲、選択している小さい側はLowerValue, 大きい方はUpperValue
* MinimumRangeがUpperとLowerの差

## Window in Window
* XamlでGridなどの子要素としてWindowは入れられない
* ドラッグではみ出してもいいなら
```
var child = new ChildWindow()
child.Owner = this //ユーザーコントロールから呼ぶ場合はWindow.GetWindow(this)
child.WindowStartupLocation = WindowStartupLocation.CenterOwner;
```
で相対位置が親ウインドウの真ん中に表示される
* UserControlにすれば子要素にできる
    * IsVisibleChangedにイベントハンドラを足して閉じたときの処理を書く
* Windowを継承しても、幾つかのメンバを変更すれば子要素にできるようだが未検証 (20171026)

## [XAML]MarginとPadding
* marginはコントロールの外側、他コントロールとの余白
* paddingはコントロールの内側、コンテンツとの余白
* cssとだいたい同じ

## [XAML] XAML内で文字列の書式指定
* `<TextBlock Text="{Binding hoge, StringFormat=Format{0}hoge}">`
* ただしバインディングする対象が先頭の場合は
    * `<TextBlock Text="{Binding hoge, StringFormat={}{0}hoge}">`
    とする必要がある

## 日付の書式
* "d" でToShortDateStringと同じ"{0:d}"

## SaveFileDialog
* `Microsoft.Win32.SaveFileDialog` を使うときに`SaveFileDialog.Initial`