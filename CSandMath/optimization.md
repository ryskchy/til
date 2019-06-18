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
