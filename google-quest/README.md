# Google QUEST Q&A Labeling

質問・回答ペアの品質を30指標で予測（マルチ出力回帰）

## Status
🔄 分析完了、ベースライン実装待ち

## タスク概要
- 入力：question_title + question_body + answer
- 出力：30個の連続値（0〜1）
- 評価：Spearman相関係数の平均

## 上位解法分析

| 順位 | 主な技術 |
|------|----------|
| 1位 | StackExchange事前学習、疑似ラベル、ビニング後処理 |
| 2位 | Binary Encoded Targets、Q/A分離、閾値クリッピング |
| 3位 | Min-Max Scaling、Optunaブレンド |
| 4位 | 3つのBERT、max_voters後処理 |

## 重要な知見
- **後処理が超重要**：Spearmanは順位を見る → 離散化で+0.02〜0.04
- **Q/A分離**：質問系21列と回答系9列を別モデルで予測
- **WeightedLayerPooling**：複数層の加重平均が有効

## 実装予定
- [ ] ベースライン（DeBERTa-v3-base、後処理なし）
- [ ] 後処理追加（ビニング）
- [ ] 改善（WeightedLayerPooling、Multi-Sample Dropout）

## Results

| Version | CV Score | Model | Notes |
|---------|----------|-------|-------|
| v1 (Baseline) | 0.357 | DeBERTa-v3-base | 5-Fold, 後処理なし |

## ベースライン設定

| 項目 | 値 |
|------|-----|
| モデル | DeBERTa-v3-base |
| max_len | 512 |
| batch_size | 8 |
| epochs | 5 |
| n_folds | 5 |
| lr | 2e-5 |

## 次のステップ

- [ ] 後処理（ビニング）追加 → +0.02〜0.04見込み
- [ ] WeightedLayerPooling
- [ ] Q/A分離モデル
