# Quora Question Pairs

文ペア類似度判定（重複質問検出）

## Status
ベースライン実行中...

## Results
| Version | Score | Model | Notes |
|---------|-------|-------|-------|
| v1 | - | DeBERTa-v3-base | 実行中 |

## 技術メモ
- クラス不均衡補正（train 37% → test 17%）
- データ拡張（Q1,Q2入れ替え）
- pos_weight=0.474
