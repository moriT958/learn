# データ構造とアルゴリズム

データ構造とアルゴリズムのメモ

## ヒープと優先度付きキュー

ヒープとは？

- max-ヒープとは
  - maxヒープ条件を満たす完全２分木のことである
  - maxヒープ条件: 親ノードが常に子ノードより大きい
  - ノード数 = ヒープサイズ (ヒープを実装する配列の長さ)

優先度付きキューとは？

- 優先度を持つキュー
  - 優先度が高い順にデータが取り出される
  - ヒープによって実現する

応用例

- 優先度キュー（OS, タスク管理）
- K 番目に大きい数を求める(サイズKのminヒープ)
- リアルタイムデータ（ストリーム処理）
- 最短経路探索（ダイクストラ法）
