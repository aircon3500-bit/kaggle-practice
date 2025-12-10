# NBME - Score Clinical Patient Notes

## タスク概要
- 医療患者ノートからの臨床概念スパン抽出（Token Classification）
- 評価指標: Micro F1（文字レベル）

## 実験ログ

### 2024/12/10 - ベースライン実験
**モデル**: microsoft/deberta-v3-base  
**環境**: Google Colab Pro+ (A100)

| Epoch | Train Loss | Valid Loss |
|-------|------------|------------|
| 1     | 0.0111     | 0.0066     |
| 2     | 0.0054     | **0.0059** |
| 3     | 0.0038     | 0.0061     |
| 4     | 0.0026     | 0.0063     |
| 5     | 0.0020     | 0.0067     |

**発見**:
- Epoch 2でValid Loss最小 → Early Stopping推奨
- CV評価にバグあり（offset_mapping問題）→ 要修正

## TODO
- [ ] Y.Nakamaベースライン使用
- [ ] CV評価（F1スコア）を正しく実装
- [ ] 後処理追加（4位のコード参考）
- [ ] Pseudo Labeling実装

## 参考リンク
- [1位解法](https://www.kaggle.com/competitions/nbme-score-clinical-patient-notes/discussion/323095)
- [4位解法（後処理コード）](https://www.kaggle.com/competitions/nbme-score-clinical-patient-notes/discussion/323085)
- [Y.Nakama Baseline](https://www.kaggle.com/code/yasufuminakama/nbme-deberta-base-baseline-train)
