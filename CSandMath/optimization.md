# Optimization 全般

## 凸性の種類

### 関数の凸性

- convex (凸):
  - 関数$f:\mathbb{R}^n\to\mathbb{R}$が凸
  - $\Leftrightarrow$ $\forall \bm{x},\bm{y}\in\mathbb{R}^n$について$f(\alpha \bm{x}+(1-\alpha)\bm{y}\geq \alpha f(\bm{x})+(1-\alpha)f(\bm{y}),\quad \forall \alpha \in (0,1)$
- strict convex (狭義凸):
  - 上記不等式が strict に成立
- proper convex (真凸):
  - 凸関数$f:\mathbb{R}^n\to\mathbb{R}\cup\{+\infty\}$について、$\text{dom} f\neq \emptyset$
    - $\text{dom} f=\{\bm{x}\in\mathbb{R}^n|f(\bm{x})<-\infty\}$
- strong convex (強凸):
  - $f$が →$m$-strong convex ($m>0$)$\Leftrightarrow$ $(\nabla f(\bm{x})-\nabla f(\bm{y}))^\top(\bm{x}-\bm{y})\geq m\|\bm{x}-\bm{y}\|^2$

## 非凸区分線形関数の混合整数計画表現

- パフォーマンス参考 <https://www.google.co.jp/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwj2yfKK2-rWAhVMTbwKHejHAsUQFggnMAA&url=http%3A%2F%2Fwww.logopt.com%2Fmikiokubo%2Fpresen%2FGurobi-Ex1-2013-5.ppt&usg=AOvVaw36gm_aiUNrYCg9h6pV9wNY>
- TODO 対数集約型凸結合のライブラリ化を試みる

## ASP (Answer Set Programming)

- <https://github.com/potassco/clingo>
- <https://www.cs.uni-potsdam.de/~torsten/ijcai13tutorial/asp.pdf>

## 単体法と内点法の解の違い

- 単体法は実行可能基底解をたどるため、得られる最適解は頂点（L0 ノルム最小な最適解）
- 内点法は中心パスをたどるため、普通に実行しても基底解には収束しない
- Gurobi では`Params.Method`を`Barrier`にしていても`Crossover` (内点法で得られた最適解を基底解に変換する処理)がデフォルトで ON になっているため、ソルバーから返ってくる解は基底解
- `Params.Crossover=0` とすれば Crossover が働かず、基底でない解が得られる
