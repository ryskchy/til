## Series.applyのインデックス
* おそらく`Series.apply`の関数内でインデクスを取得する方法はない
* [`to_frame()`](#SeriesからDataFrameへの変換)してから`.name`でとる
```
series.to_frame().apply(lambda x:x.name, 1)
```

## SeriesからDataFrameへの変換
* `Series.to_frame()` 関数がある