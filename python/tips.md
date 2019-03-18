# Python tips

## import

- 上位フォルダ同じ名前のモジュールがあるとそっちが優先的に読み込まれることがある
- `from . import hoge` で回避可能
- 実態未解明

## ディレクトリ作成

- `os.mkdir` は途中のパスが存在するとエラーになるが、`os.makedirs`は再帰的にディレクトリを作る。
- また、 `exist_ok=True` とすると、対象ディレクトリが存在してもエラーにならない

## ディクショナリの結合

- `dict1.update(dict2)` ディクショナリを結合できる
  - キーが同じならおそらく後者になる
- `dict1.update(key=value)` でも可

## 数字フォーマット

- `"{:02d}".format(1)`で`"01"`
- 何回調べても忘れる(C#も)

## set の扱いについて

- `a.intersection(b)`でも`set.intersection(a,b)`いける
- `set.union(a,b,c,d,...)`ができる
  - `set.union(*[1,2,3,4])`も ok
- `set.isdisjoint`が intersection が無いかどうか
- `a.difference(b)`は $$\forall x \in a and x \not\in b$$

|   演算子 | 関数                | 意味                              |
| -------: | :------------------ | :-------------------------------- |
| `s <= t` | `s.issubset(t)`     | s の要素すべてが t にあれば True  |
| `s >= t` | `s.isuperset(t)`    | t の要素すべてが s にあれば True  |  |
|  `s | t` | `s.union(t)`        | 和集合                            |
|  `s & t` | `s.intersection(t)` | 共通部分                          |
|  `s - t` | `s.difference(t)`   | s の要素のうち t に含まれないもの |
|  `s ^ t` | `s.union(t)`        | どちらか一方にだけあるもの        |

## ディレクトリのコピー、削除

- ディレクトリの再帰的コピー

```python
import distutils.dir_util
distutils.dir_util.copy_tree("source_path", "dit_path")
```

- ディレクトリの削除（中身がある）

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
  print(file)
```

## SimpleHTTPServer on python3

- `pyhon -m http.server [ポート番号]`

## 複数文字の replace

```python
table = str.maketrans({
  '、': ',',
  '。': '.',
  '・': '',
})
result = text.translate(table)
```

- `maketrans` は `str.maketrans('abcd', 'ABCD')` とも書ける(第三引数で削除)

## dataset.freeze

- db のデータを csv や json で出力するメソッド
- datafreeze という独立したモジュールになった(201709 くらい？)

## ディクショナリの初期化

- `d = {"a:"b", "c":"d"}` は
- `d = dict(a="b", c="d")` と書ける

## '''hogehoge''' の改行を改行しない

```python
'''hogehoge\
piyopiyo'''
```

で`'hogehogepiyopiyo'`と同じ扱い

## unittest.mock

- `mock.patch` で適用範囲を限定して名前空間を置き換えられる
- `from hoge import piyo` と `import hoge` の `hoge.piyo` は別々に置き換えられる
- 参考: <http://blog.amedama.jp/entry/2016/12/06/220000>

## freezegun

- `datetime.now` の時刻を置き換えられる

```python
@freezegun.freeze_time('2015-10-21')
def main():
    print(datetime.now())
```

- 参考: <http://note.crohaco.net/2015/python-mock/>

## logging

- `FATAL` は `CRITICAL`、`WARN`は`WARNING`に置き換える
- `logging.handlers.HTTPHandler` はヘッダに`"Content-type": application/x-www-form-urlencoded"` をセットする
  - slack の incomming webhook 等ではエラーになる?

## クロージャの変数参照

```python
def add(x,y):
    return x + y

functions = [lambda z: add(z, y) for y in range(10)]
```

とすると、`functions` の中身のラムダ式はグローバル変数`y`と引数`z`の足し算を返す関数になるだけ。

無理やり作るなら

```python
functions = [(lambda yy: (lambda z: add(z, yy)))(y) for y in range(10)]
```

とすれば、外側のラムダ式を実行する際に y の値が参照されるので、y の値を固定できる。

ちゃんとするならオブジェクトを作ったほうがいい

```python
def add(x,y):
    return x + y

class adder(object):

    def __init__(self, y):
        self.y = y

    def add(self, x):
        return add(x, self.y)

functions = [adder(y).add for y in range(10)]
```

## os.walk

- root, directories, files を返すジェネレータ
- 指定したフォルダから階層順、名前順に一覧を返す

## open

- いつの間にか`codecs.open` しなくても`open(fname,encoding="utf-8")` とできるようになってた（いつから？）

## Windows で OpenAI Gym

- `pip install -U git+https://github.com/Kojoley/atari-py.git`
- <http://daruma3940.hatenablog.com/entry/2017/08/13/030344>

## Macでimportした時にCompilation failedになる時

- `import theano`などで起きる
  - `stdio.h`がないと言われる
- xcodeの仕様変更で`/local/include`に何も入っていないのが原因
- `/Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg` をインストールすればok

## Matplotlib で色を順番に選ぶ

- `cmap =plt.rcParams['axes.prop_cycle']`