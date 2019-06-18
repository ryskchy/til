# その他 OSS ライブラリの tips

## shapely

- 多角形の面積計算や bool 処理ができる
- `shapely.geometry.Polygon`オブジェクト
- `contains`,`crosses`, `overwraps`,`intersects`,`touches`があるので使い分けに注意
- `contains`:
  - `other`の点が全て内部にある
- `crosses`:
  - interor 同士が重なるが、`contains`でない
- `intersect`:
  - お互いの外周含めて重なりがある

## freezegun

- `datetime.now` の時刻を置き換えられる

```python
@freezegun.freeze_time('2015-10-21')
def main():
    print(datetime.now())
```

- 参考: <http://blog.amedama.jp/entry/2016/12/06/220000>

## Matplotlib で色を順番に選ぶ

- `cmap =plt.rcParams['axes.prop_cycle']`

## Windows で OpenAI Gym

- `pip install -U git+https://github.com/Kojoley/atari-py.git`
- <http://daruma3940.hatenablog.com/entry/2017/08/13/030344>
