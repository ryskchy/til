## ボタンの形を変える
* ボタンのTempleteプロパティで色々書ける
* Te,pleteBindingバインディング拡張で、テンプレート適用先のプロパティ値を参照できる

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