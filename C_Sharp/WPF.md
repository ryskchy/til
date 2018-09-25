## ボタンの形を変える

- ボタンの Templete プロパティで色々書ける
- TempleteBinding バインディング拡張で、テンプレート適用先のプロパティ値を参照できる
- ContentPresenter をつけないともとの Content が反映されない
  - TargetType をつけていないときも反映されない

## GroupBox のヘッダをラジオボタンに

- 普通に

```xml
<GroupBox Name="gbHogehoge">
          <GroupBox.Header>
            <RadioButton
              Name="rbHoge"
              Content="Line" />
          </GroupBox.Header>
```

でできる

## Radiobutton のグルーピング

- 同じ親コンテナに配置するか、GroupName プロパティで指定する

## コントロール同士のバインディング

```xaml
<CheckoBox Name="cb">
<Button IsEnabled={Binding ElementName=cb, Path=IsChecked}>
```

## Mahapps.Metro の RangeSlider

- Minimum, Maximum は選択できる範囲、選択している小さい側は LowerValue, 大きい方は UpperValue
- MinimumRange が Upper と Lower の差

## Window in Window

- Xaml で Grid などの子要素として Window は入れられない
- ドラッグではみ出してもいいなら

```
var child = new ChildWindow()
child.Owner = this //ユーザーコントロールから呼ぶ場合はWindow.GetWindow(this)
child.WindowStartupLocation = WindowStartupLocation.CenterOwner;
```

で相対位置が親ウインドウの真ん中に表示される

- UserControl にすれば子要素にできる
  - IsVisibleChanged にイベントハンドラを足して閉じたときの処理を書く
- Window を継承しても、幾つかのメンバを変更すれば子要素にできるようだが未検証 (20171026)

## [XAML]Margin と Padding

- margin はコントロールの外側、他コントロールとの余白
- padding はコントロールの内側、コンテンツとの余白
- css とだいたい同じ

## [XAML] XAML 内で文字列の書式指定

- `<TextBlock Text="{Binding hoge, StringFormat=Format{0}hoge}">`
- ただしバインディングする対象が先頭の場合は
  - `<TextBlock Text="{Binding hoge, StringFormat={}{0}hoge}">`
    とする必要がある

## 日付の書式

- "d" で ToShortDateString と同じ"{0:d}"

## SaveFileDialog

- `Microsoft.Win32.SaveFileDialog` を使うときに`SaveFileDialog.Initial`
