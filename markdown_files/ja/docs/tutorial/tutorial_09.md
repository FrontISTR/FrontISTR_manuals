## 接触解析（その１）

本解析の実施には、`tutorial/09_contact_hertz` のデータを用います。

### 解析対象

解析はHerz接触問題で、解析対象の形状を図4.9.1に、メッシュデータを図4.9.2に示します。メッシュには六面体1次要素を用い、メッシュ規模は要素数168、節点数408です。

図4.9.1　解析対象の形状　　　　　　図4.9.2　解析対象のメッシュデータ

<div style="text-align: center;">
<img src="./media/tutorial09_01.png" width="350px"><br>
図4.9.1　解析対象の形状
</div>

<div style="text-align: center;">
<img src="./media/tutorial09_02.png" width="350px"><br>
図4.9.2　解析対象のメッシュデータ
</div>

### 解析内容

円板の1/4モデルの上面に圧縮方向の強制変位を与える接触解析を拡張ラグランジュ乗数法で実施します。解析制御データを以下に示します。

### 解析結果

5サブステップ目の解析結果について、y方向変位のコンターを付加した変形図をREVOCAP\_PrePostで作成して図4.9.3に示します。また、解析結果の数値データとして、解析結果ログファイルの一部を以下に示します。

<div style="text-align: center;">
<img src="./media/tutorial09_03.png" width="350px"><br>
図4.9.3　変形およびy方向変位の解析結果
</div>
