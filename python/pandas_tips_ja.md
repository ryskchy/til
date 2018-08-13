# Pandas

## Series.applyのインデックス

* おそらく`Series.apply`の関数内でインデクスを取得する方法はない
* [`to_frame()`](#SeriesからDataFrameへの変換)してから`.name`でとる

```python
series.to_frame().apply(lambda x:x.name, 1)
```

## SeriesからDataFrameへの変換

* `Series.to_frame()` 関数がある

## concat

* `pd.concat([a, b], axis=1)` で列結合(超基本だと思うが地味に使ってなかった)
* インデックスとかも合わせてくれるっぽいので要検証

## `pd.date_range`

* <http://sinhrks.hatenablog.com/entry/2014/11/09/183603>
* `pd.date_range("2017-10-01", freq="M", period=6)`で月末のリストになる
  * `freq="M"` ならなんでもいい

## `stack` と`unstack`

* `DataFrame`をstackすると行と列がindexとなった`Series`ができる
  * columns がMultiIndexの時は`DataFrame.stack(level=1)`や`DataFrame.stack(level=[0,1])`で展開するインデックスを選べる。複数可。
* 逆にMultiIndexな`Series`を`unstack`するとテーブルになる