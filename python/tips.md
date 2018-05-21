# Python tips

## import

* 上位フォルダ同じ名前のモジュールがあるとそっちが優先的に読み込まれることがある
* `from . import hoge` で回避可能
* 実態未解明

## ディレクトリ作成

* `os.mkdir` は途中のパスが存在するとエラーになるが、`os.makedirs`は再帰的にディレクトリを作る。
* また、 `exist_ok=True` とすると、対象ディレクトリが存在してもエラーにならない

## ディクショナリの結合

* `dict1.update(dict2)` ディクショナリを結合できる
  * キーが同じならおそらく後者になる
* `dict1.update(key=value)` でも可

## 数字フォーマット

* `"{:02d}".format(1)`で`"01"`
* 何回調べても忘れる(C#も)

## setの扱いについて

* `a.intersection(b)`でも`set.intersection(a,b)`いける
* `set.union(a,b,c,d,...)`ができる
  * `set.union(*[1,2,3,4])`もok
* `set.isdisjoint`がintersectionが無いかどうか
* `a.difference(b)`は $$\forall x \in a and x \not\in b$$

|演算子|関数|意味|
|--:|:--|:--|
|`s <= t`|`s.issubset(t)`|sの要素すべてがtにあればTrue|
|`s >= t`|`s.isuperset(t)`|tの要素すべてがsにあればTrue||
|`s | t`|`s.union(t)`|和集合|
|`s & t`|`s.intersection(t)`|共通部分|
|`s - t`|`s.difference(t)`|sの要素のうちtに含まれないもの|
|`s ^ t`|`s.union(t)`|どちらか一方にだけあるもの|

## ディレクトリのコピー、削除

* ディレクトリの再帰的コピー

```python
import distutils.dir_util
distutils.dir_util.copy_tree("source_path", "dit_path")
```

* ディレクトリの削除（中身がある）

```python
shutil.rmtree("hoge")
```

## ファイルを再帰的に探索

```python
def find_all_files(directory):
  for root, dirs, files in os.walk(directory):
    yield root
    for file in files:
      yield os.path.join(root, file)

for file in find_all_files('/tmp/test'):
  print file
```

## SimpleHTTPServer on python3

* `pyhon -m http.server [ポート番号]`

## 複数文字のreplace

```python
table = str.maketrans({
  '、': ',',
  '。': '.',
  '・': '',
})
result = text.translate(table)
```

* `maketrans` は `str.maketrans('abcd', 'ABCD')` とも書ける(第三引数で削除)

## dataset.freeze

* dbのデータをcsvやjsonで出力するメソッド
* datafreeze という独立したモジュールになった(201709くらい？)

## ディクショナリの初期化

* `d = {"a:"b", "c":"d"}` は
* `d = dict(a="b", c="d")` と書ける

## '''hogehoge''' の改行を改行しない

```python
'''hogehoge\
piyopiyo'''
```

で`'hogehogepiyopiyo'`と同じ扱い

## dictionaryを