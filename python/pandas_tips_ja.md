## Series.applyのインデックス
* おそらく`Series.apply`の関数内でインデクスを取得する方法はない
* [`to_frame()`](#SeriesからDataFrameへの変換)してから`.name`でとる
```
series.to_frame().apply(lambda x: x.name, 1)
```

## SeriesからDataFrameへの変換
* `Series.to_frame()` 関数がある

## concat
* `pd.concat([a, b], axis=1)` で列結合(超基本だと思うが地味に使ってなかった)
* インデックスとかも合わせてくれるっぽいので要検証

## `pd.date_range`

* http://sinhrks.hatenablog.com/entry/2014/11/09/183603
* `pd.date_range("2017-10-01", freq="M", period=6)`で月末のリストになる