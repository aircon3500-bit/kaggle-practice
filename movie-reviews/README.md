# Movie Reviews

Sentiment Analysis on Movie Reviews - 5クラス感情分類

## Results

| Version | Score | Model | Notes |
|---------|-------|-------|-------|
| v1 | 0.68771 | DeBERTa-v3-small | 20%データ, 3エポック |
| v2 | (未提出) | DeBERTa-v3-large | 5-Fold CV, 18時間訓練→リセット消失 |

## Target

- 公開最高: 0.717
- 目標: **0.72超え**
- 1位(0.765)は異常値、3位(0.709)が現実的上限

## Tech Stack

- PyTorch
- transformers (DeBERTa-v3)
- 5-Fold CV
- Colab Pro+ (A100)

## Lessons Learned

- 5クラス分類はNeutralが50%以上で不均衡
- largeモデルは時間かかる（A100で約18時間）
- チェックポイント保存必須
