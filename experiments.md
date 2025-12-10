# NLP実験ログ

## 概要

| コンペ | ベストスコア | 状態 |
|--------|-------------|------|
| Dogs vs Cats | 0.11243 | ✅完了 |
| Disaster Tweets | 0.84063 | 🔄進行中（目標0.85） |
| Movie Reviews | 0.68771 | 🔄進行中（目標0.72） |
| Toxic Comment | 0.98565 | 🔄進行中（目標0.9886） |
| Quora Question Pairs | - | ⏸️スキップ |
| Google QUEST Q&A | 0.357 (CV) | 🔄進行中（後処理で改善予定） |
| TensorFlow QA | - | ⏳未着手 |
| NBME Patient Notes | - | ⏳未着手 |

---

## 習得済みテクニック

| 技術 | 学んだコンペ | 効果 |
|------|-------------|------|
| WeightedLayerPooling | Disaster Tweets | 最終4層の加重平均で精度向上 |
| LLRD（層ごと学習率減衰） | Disaster Tweets | 下位層は小さい学習率で安定 |
| 5-Fold CV + Ensemble | Disaster Tweets | 汎化性能向上、分散低減 |
| AMP混合精度訓練 | Disaster Tweets | メモリ半減、速度1.5倍 |
| Multi-Sample Dropout | Disaster Tweets | 複数Dropout平均で安定 |
| Label Smoothing | Disaster Tweets | 過信防止 |
| 埋め込み層凍結 | Disaster Tweets | 初期学習の安定化 |

---

## Disaster Tweets

### ベスト: 0.84063

| 実験 | モデル | 設定 | CV | LB | メモ |
|------|--------|------|----|----|------|
| baseline | DeBERTa-v3-base | lr=2e-5, epoch=3 | - | 0.834 | 初回提出 |
| +上級技術 | DeBERTa-v3-base | LLRD, WeightedLayerPooling, 5-Fold | 0.841 | 0.84063 | 現在のベスト |

### 上位Notebook分析で学んだこと
- 大きいモデル（large）＋シンプル設定が強い
- 手動ラベル修正で+0.005程度の効果あり
- 12-Fold×1エポック戦略も有効

---

## Movie Reviews

### ベスト: 0.68771

| 実験 | モデル | 設定 | CV | LB | メモ |
|------|--------|------|----|----|------|
| baseline | DeBERTa-v3-small | 20%データ, epoch=3 | 0.67 | 0.68771 | 軽量テスト |
| large_5fold | DeBERTa-v3-large | 100%データ, 5-Fold, epoch=5 | 0.713 | (未提出) | 18時間訓練→リセット消失 |

### 目標
- 公開Notebook最高: 0.717
- 目標: **0.72超え**
- 1位(0.765)と2位(0.760)は異常値（リーク疑い）、3位(0.709)が現実的な上限

---

## 次のアクション

1. Movie Reviews: DeBERTa-large 5-Fold再実行 → 0.72超え狙い
2. Disaster Tweets: 0.85達成のための追加改善
3. Toxic Comment: 次のコンペへ
