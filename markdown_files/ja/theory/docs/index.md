<!-- 表記は FrontISTR ver. 0.0 で統一します -->
# FrontISTR 理論マニュアル

本ソフトウェアは文部科学省次世代ＩＴ基盤構築のための研究開発「イノベーション基盤シミュレーションソフトウェアの研究開発」プロジェクトによる成果をシーズとして，継続的に開発されている並列有限要素解析プログラムです。
本ソフトウェアを無償または営利目的でご使用になる場合、「MITライセンス」をご了承頂くことが前提となります。

<img src="./image/FrontISTR_logo.png" width="350px">

| 項目 | 説明 |
|:---------:|:---------|
| ソフトウェア名称 | FrontISTR |
| バージョン | 5.0 |
| ライセンス形態 | MIT License |
| 問い合わせ先 | FrontISTR研究会<br> 〒277-8563 千葉県柏市柏の葉5-1-5<br> 東京大学大学院新領域創成科学研究科 奥田研究室（気付）<br> E-mail：fstr_seminar@multi.k.u-tokyo.ac.jp |

## マニュアルリスト

  - [FrontISTR ver. 5.0 ユーザーマニュアル]()
  - [FrontISTR ver. 5.0 インストールマニュアル]()
  - [FrontISTR ver. 5.0 理論マニュアル]()
  - [FrontISTR ver. 5.0 解析マニュアル]()
  - [FrontISTR ver. 5.0 チュートリアルマニュアル]()

<!-- ここまでテンプレート -->
---

本マニュアルでは、大規模並列FEM非線形構造解析プログラムFrontISTRで用いられる、有限要素法（Finite Element Method）による解析手法について説明します。

固体の応力解析手法については、まず微小変形線形弾性静解析手法について示し、引き続き大変形問題を扱う際に必要となる幾何学的非線形解析手法、弾塑性解析手法について示します。
さらにFEMによる応力解析の結果を利用して得られる破壊力学パラメータを評価する方法についてまとめたものを示します。
次に、固有値解析および熱伝導解析手法について示します。

## 本マニュアルの記載内容

- 静的解析
    - [微小変形線形弾性静解析](./02_theory/theory_01)
    - [非線形静解析手法](./02_theory/theory_02)
- 動的解析
    - [動的解析手法](./02_theory/theory_03)
    - [固有値解析](./02_theory/theory_05)
    - [周波数応答解析](./02_theory/theory_06)
- [熱伝導解析](./02_theory/theory_04)
- [参考文献](./02_theory/theory_07)
