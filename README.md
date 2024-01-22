# 連合学習を用いた歩行時間予測モデルの評価

## 歩行時間予測モデル
- 説明変数：歩道の幅 [m], 通常時の歩行速度 [m/s], 混雑度  
  width, speed, crowd_level_2, crowd_level_3, crowd_level_4, crowd_level_5
- 目的変数：1mあたりの歩行時間の実測値と理論値との誤差 [s/m]  
$\frac{1}{\text{distance}} \left( \text{time} - \frac{\text{distance}}{\text{speed}} \right) = \frac{\text{time}}{\text{distance}} - \frac{1}{\text{speed}}$

## 連合学習の評価結果
1m歩いた時の平均時間誤差 (MAE) [s/m]

- ランダムに分割

| クライアント数 | 収束ラウンド数 | 全体 | 混雑度1 | 混雑度2 |  混雑度3 |  混雑度4 |  混雑度5 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 10 | 2 | 0.06191 | 0.03721 | 0.03657 | 0.05074 | 0.07378 | 0.11339 |
| 50 | 3 | 0.06202 | 0.03674 | 0.03618 | 0.04965 | 0.07596 | 0.11379 |
| 100 | 5 | 0.06236 | 0.03771 | 0.03695 | 0.05077 | 0.07371 | 0.11478 |
| 500 | 30 | 0.06248 | 0.03759 | 0.03683 | 0.05112 | 0.07384 | 0.11517 |
| 1000 | 100 | 0.06253 | 0.03801 | 0.03723 | 0.05101 | 0.07386 | 0.11464 |

<br>

- 歩行速度別に分割

| クライアント数 | 収束ラウンド数 | 全体 | 混雑度1 | 混雑度2 |  混雑度3 |  混雑度4 |  混雑度5 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 10 | 10 | 0.06257 | 0.03794 | 0.03723 | 0.04992 | 0.07491 | 0.11505 |
| 50 | 15 | 0.06276 | 0.03883 | 0.03785 | 0.05069 | 0.07396 | 0.11456 |
| 100 | 20 | 0.06282 | 0.03900 | 0.03810 | 0.05099 | 0.07374 | 0.11436 |
| 500 | 30 | 0.06283 | 0.03824 | 0.03741 | 0.05124 | 0.07485 | 0.11456 |
| 1000 | 75 | 0.06281 | 0.03806 | 0.03721 | 0.05113 | 0.07485 | 0.11497 |

## 実装
- 言語：
  <img src="https://img.shields.io/badge/-Python-3776AB.svg?logo=python&style=plastic">
- 連合学習フレームワーク：
  <img src="https://flower.dev/_next/image/?url=%2F_next%2Fstatic%2Fmedia%2Fflower_white_border.c2012e70.png&w=640&q=75" width="18px" alt="Flower Website">
  <img src="https://img.shields.io/badge/-Flower-F2B705.svg?logo=&style=plastic">
- 統合開発環境：
  <img src="https://img.shields.io/badge/-Colab-F9AB00.svg?logo=google%20colab&style=plastic">

## 各ファイルの説明
- federated_learning.ipynb：連合学習で構築した歩行時間予測モデルを評価
- linear_regression.ipynb：2つの歩行時間予測モデルを評価
- multi_agent_simulation.ipynb：歩行者マルチエージェントシミュレーションから学習データセットを作成
- dataset.csv：multi_agent_simulation.ipynbで作成したデータセット
