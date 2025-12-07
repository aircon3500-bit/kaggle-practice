# Toxic Comment Classification

マルチラベル分類 - 有害コメントの6種類を判定

## Task

| 項目 | 内容 |
|------|------|
| タスク | マルチラベル分類（1コメント→複数ラベル可） |
| ラベル | toxic, severe_toxic, obscene, threat, insult, identity_hate |
| 評価指標 | 列ごとのROC-AUC平均 |
| データ | Wikipedia コメント 159,571件 |

## Target: 0.9886

## 新しく学ぶこと

- マルチラベル分類の実装
- BCEWithLogitsLoss（各ラベル独立した2値分類）
- Sigmoid出力（Softmaxではない）

## Results

| Version | Score | Model | Notes |
|---------|-------|-------|-------|
| - | - | - | 実装予定 |

## 上位Notebook分析

- 0.986台: BiGRU-LSTM + Dual Embedding + 10シード平均
- 0.987台: 13〜18モデルの大規模アンサンブル
- 共通点: 多様なモデルの組み合わせが鍵
