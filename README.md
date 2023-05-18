# Overview
ICR, kaggle competition
初めてのKaggleコンペティション！Kaggle日記。もし書き方が分からなくなったら[こちらを参照](https://zenn.dev/fkubota/articles/3d8afb0e919b555ef068)

実際の書き方は[こんな感じ](https://github.com/Yuki-Tanaka-33937424/kaggle-Shopee-Price-Match-Guarantee)

**コンペの概要**
このコンペティションの目的は、ある人が3つの病状のいずれかを持っているかどうかを予測することです。あなたは、その人が3つの医学的状態のいずれか1つ以上を持っているか（クラス1）、または3つの医学的状態のいずれも持っていないか（クラス0）を予測するように求められています。あなたは、健康特性の測定値に基づいて訓練されたモデルを作成することになります。 誰かがこれらの病状にあるかどうかを判断するには、患者から情報を収集するための長い、侵入的なプロセスが必要です。予測モデルを使えば、病状に関連する主要な特徴を収集し、その特徴を符号化することで、このプロセスを短縮し、患者の情報を非公開にすることができます。 あなたの研究は、研究者が特定の特性の測定値と潜在的な患者の状態との間の関係を発見するのに役立ちます。

年齢は単なる数字だと言われますが、加齢に伴ってさまざまな健康上の問題が生じます。 心臓病や認知症から難聴や関節炎に至るまで、老化は多くの病気や合併症の危険因子です。 バイオインフォマティクスの成長分野には、生物学的老化を遅らせたり逆転させたり、加齢に伴う重大な病気を予防したりする介入に関する研究が含まれています。 データ サイエンスは、たとえサンプル数が少なくても、多様なデータを使用して問題を解決する新しい方法を開発する上で役割を果たす可能性があります。

現在、病状を予測するために XGBoost やランダム フォレストなどのモデルが使用されていますが、モデルのパフォーマンスは十分ではありません。 人命がかかっている重大な問題に対処する場合、モデルはさまざまなケース間で確実かつ一貫して正しい予測を行う必要があります。

2015 年に設立されたコンテスト主催者の InVitro Cell Research, LLC (ICR) は、再生および予防の個別化医療に焦点を当てた私募企業です。 ニューヨーク市大都市圏にある同社のオフィスと研究室には、最先端の研究スペースが備わっています。 InVitro Cell Research の科学者は、老化した人々を迅速に修復する方法を研究するという使命を指導し、定義することで、InVitro Cell Research を際立たせています。

このコンテストでは、健康特性データの測定に取り組み、バイオインフォマティクスにおける重要な問題を解決します。 既存の方法を改善することを目的として、最小限のトレーニングに基づいて、人が 3 つの病状のいずれかに罹患しているかどうかを予測するモデルを作成します。

成長を続けるバイオインフォマティクス分野の発展を支援し、多様なデータを使用して複雑な問題を解決する新しい方法を探索することができます。

# Data 日本語訳
train.csv - トレーニングセット。

Id 各オブザベーションの一意な識別子。

AB-GL 56個の匿名化された健康特性。EJはカテゴリーであるが、それ以外はすべて数値である。

クラス バイナリターゲット：1は、被験者が3つの条件のうちの1つと診断されたことを示し、0は、診断されていないことを示す。

test.csv - テストセット。目標は、このセットの被験者が2つのクラスのそれぞれに属する確率を予測することである。

greeks.csv - 補助的なメタデータで、トレーニングセットでのみ利用可能です。

Alpha 年齢に関連する状態がある場合、その種類を特定する。

A 年齢に関連した状態はない。クラス0に対応する。

B, D, G 3つの加齢に関連した状態。クラス 1 に対応する。

Beta, Gamma, Delta 3つの実験特性を示す。

Epsilon この被験者のデータが収集された日付。なお、テストセットのデータはすべてトレーニングセットが収集された後に収集されたものである。

sample_submission.csv - 正しい形式のサンプル提出ファイル。詳細は、「評価」ページを参照してください。

# Log
## 20230517
* この日に参加した。初めての参加でちょっと緊張。
* テーブルデータが扱えそうだったので、参加した。
* 概要は、おそらく、病気に罹患しているか、していないかを分類する。

## 20230518
* 今日はデータを探索した。散策してくれていたやつがあったので、それを参照した。こちら[[ICR IARC, 2023] EDA and Submission](https://www.kaggle.com/code/sergiosaharovskiy/icr-iarc-2023-eda-and-submission)
* わかったこと
*   XGBのモデルが使われていて、どんな感じのモデルを作ると一番いいかが実験されていた。トレーニングサマリーの部分。
*   データが左寄りに分布していることと右にめちゃくちゃ広い
*   値も結構、小さいのから大きいのまでそろっている
*   大体、数値のデータ。
*    (クラス 1 に対する特徴の分布は非常に平坦であるか、密であるかのいずれか)
*    テストデータは使い物にならなさそう
*    あとディスカッションでも見たが一日一回に提出が制限されているらしい
* あと、今日は「Kaggleで勝つデータ分析の技術」という本を読んだ
*   評価指標と目的関数を合わせることや考慮することでいいモデルが作成できる。
*   基本的に評価指標と目的関数は合わせよう
*   アンサンブルという手法がある。面白そう。
