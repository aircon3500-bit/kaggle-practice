# Disaster Tweets

NLP text classification - 災害ツイート判定（2クラス分類）

## Results

| Version | Score | Model | Notes |
|---------|-------|-------|-------|
| v1 | 0.834 | DeBERTa-v3-base | ベースライン |
| v2 | 0.84063 | DeBERTa-v3-base | +LLRD, WeightedLayerPooling, 5-Fold |

**Best Score: 0.84063**

## Target: 0.85

## 上位Notebook分析から学んだこと

| Notebook | Score | 学び |
|----------|-------|------|
| Ryan Barreto | 0.84707 | WeightedLayerPooling, LLRD |
| 12-Fold戦略 | 0.84615 | 多Fold×少エポックが有効 |
| 1-Epoch Large | 0.84829 | 大モデル+シンプル設定が強い |
| Multi-Dropout | 0.84921 | 複数Dropout平均で安定 |

## 習得テクニック

- WeightedLayerPooling（最終4層の加重平均）
- LLRD（層ごと学習率減衰）
- 5-Fold CV + Ensemble
- AMP混合精度訓練
- Multi-Sample Dropout
- Label Smoothing
- 埋め込み層凍結

## Tech Stack

- PyTorch
- transformers (DeBERTa-v3)
- Kaggle Notebooks (GPU T4 x2)
