# LinQ

## LinQ to Entity で、評価されてないメンバの評価をしようとするとエラーになる

- `hoge.Where(x => x.Values.FirstOrDefault(y =>y != null)).Tolist()` みたいな
  - `hoge.ToList().Where(x => x.Values.FirstOrDefault(y =>y != null)).Tolist()` とすればできなくもないが遅い（Values の要素数が多い時）
