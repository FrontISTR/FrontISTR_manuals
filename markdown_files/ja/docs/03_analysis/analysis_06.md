# ユーザーサブルーチン

ユーザーがFrontISTRの機能をプログラミングにより拡張するためのインターフェースを提供すする。これらのインターフェースは、基本的にサブルーチンヘッダを含むFORTRANサブルーチンで、入出力変数の記述とこれらの変数のための宣言文である。ルーチンの主要部は、ユーザーによって書かなければならない。

FrontISTRは以下のユーザサブルーチンインターフェースを提供している。

## ユーザー定義材料の入力

ユーザー定義材料を使用する場合、最大100のユーザー定義材料定数が使用可能である。材料定数の入力は以下のように、制御データファイル内の１行10数値、最大10行まで入力可能である。

*2行目～最大10行目*

v1, v2, v3, v4, v5, v6, v7, v8, v9, v10

　......

## 弾塑性変形に関わるサブルーチン（uyield.f90）

弾塑性剛性マトリクスおよび応力のreturn
mappingを計算するためのサブルーチンを提供している。ユーザー定義降伏関数を利用する場合、まず入力ファイルに!PLASTIC,
TYPE=USERを設定して必要な材料定数を入力し、次にサブルーチンuElastoPlasticMatrixおよびuBackwardEulerを作成する必要がある。

（１）弾塑性剛性マトリクスの計算サブルーチン

subroutine uElastoPlasticMatrix( matl, stress, istat, fstat, D )

REAL(KIND=kreal), INTENT(IN) :: matl(:)

REAL(KIND=kreal), INTENT(IN) :: stress(6)

INTEGER, INTENT(IN) :: istat

REAL(KIND=kreal), INTENT(IN) :: fstat(:)

REAL(KIND=kreal), INTENT(OUT) :: D(:,:)

matl:　材料定数を保存する配列（最大100）

stress: 2nd Piola-Kirchhoff応力

istat: 降伏状態(0: 未降伏；　1: 降伏した)

fstat: 状態変数.　fstat(1)=塑性ひずみ、fstat(2:7)= back
stress(移動または複合硬化時)

D: 弾塑性マトリクス

（２）応力のReturn mapping計算サブルーチン

subroutine uBackwardEuler ( matl, stress, istat, fstat )

REAL(KIND=kreal), INTENT(IN) :: matl(:)

REAL(KIND=kreal), INTENT(INOUT) :: stress(6)

INTEGER, INTENT(INOUT) :: istat

REAL(KIND=kreal), INTENT(IN) :: fstat(:)

matl: 材料定数を保存する配列（最大100）

stress: trial stress弾性変形を仮定し得られた2nd Piola-Kirchhoff応力

istat: 降伏状態(0: 未降伏；　1: 降伏した)

fstat: 状態変数.　fstat(1)=塑性ひずみ、fstat(2:7)= back
stress(移動または複合硬化時)

## 弾性変形に関わるサブルーチン（uelastic.f90）

弾性および超弾性問題の弾性剛性マトリクスおよび応力の更新計算をするためのサブルーチンを提供している。ユーザー弾性または超弾性構成式を利用する場合、まず入力ファイルに!ELASTIC,
TYPE=USERまたは!HYPERELASTIC,
TYPE=USERを設定して必要な材料定数を入力し、次にサブルーチンuElasticMatrixおよびuElasticUpdateを作成する必要がある。

（１）弾性剛性マトリクスの計算サブルーチン

subroutine uElasticMatrix( matl, strain, D )

REAL(KIND=kreal), INTENT(IN) :: matl(:)

REAL(KIND=kreal), INTENT(IN) :: strain(6)

REAL(KIND=kreal), INTENT(OUT) :: D(6,6)

matl: 材料定数を保存する配列（最大100）

strain: Green-Lagrangeひずみ

D: 弾性マトリクス

（２）応力の計算サブルーチン

subroutine uElasticUpdate ( matl, strain, stress )

REAL(KIND=kreal), INTENT(IN) :: matl(:)

REAL(KIND=kreal), INTENT(IN) :: strain(6)

REAL(KIND=kreal), INTENT(OUT) :: stress(6)

matl: 材料定数を保存する配列（最大100）

strain: Green-Lagrangeひずみ

stress: 応力

## ユーザー定義材料に関わるサブルーチン（umat.f）

弾性、超弾性、弾塑性材に拘らず一般的な材料の変形解析のインターフェースを提供する。

（１）剛性マトリクスの計算サブルーチン

subroutine uMatlMatrix( mname, matl, ftn, stress, fstat, D, temperature,
dtime )

CHARACTER(len=\*), INTENT(IN) :: mname

REAL(KIND=kreal), INTENT(IN) 　 :: matl(:)

REAL(KIND=kreal), INTENT(IN) 　:: ftn(3,3)

REAL(KIND=kreal), INTENT(IN) 　 :: stress(6)

REAL(KIND=kreal), INTENT(IN) 　:: fstat(:)

REAL(KIND=kreal), INTENT(OUT)　:: D(:,:)

REAL(KIND=kreal), optional 　　 :: temperature

REAL(KIND=kreal), optional :: dtime

mname: 材料名

matl: 材料定数を保存する配列（最大100）

ftn: 変形勾配テンソル

stress: 2nd Piola-Kirchhoff応力

fstat: 状態変数

D: 構成式

temperature: 温度

dtime: 時間増分

（２）ひずみおよび応力の更新計算サブルーチン

subroutine uUpdate( mname, matl, ftn, strain, stress, fstat,
temperature, dtime )

character(len=\*), intent(in) :: mname

real(KIND=kreal), intent(in) :: matl

real(kind=kreal), intent(in) 　 :: ftn(3,3)

real(kind=kreal), intent(inout) :: strain(6)

real(kind=kreal), intent(inout) :: stress(6)

real(kind=kreal), intent(inout) :: fstat(:)

real(KIND=kreal), optional :: temperature

real(KIND=kreal), optional :: dtime

mname: 材料名

matl: 材料定数を保存する配列（最大100）

ftn: 変形勾配テンソル

strain: ひずみ

stress: 2nd Piola-Kirchhoff応力

fstat: 状態変数

temperature: 温度

dtime: 時間増分

## ユーザー定義外部荷重の処理サブルーチン（uload.f）

ユーザー定義外部荷重を処理するインターフェースを提供する。

ユーザー定義外部荷重を利用するため、まず外部荷重を定義するための数値構造tULoadを定義し、入力ファイルの!ULOADを利用してその定義を読み込む。その後、以下のインターフェースを利用して、外部荷重を組み込む。

（１）外部荷重の読み込みサブルーチン

integer function ureadload( fname )

character(len=\*), intent(in) :: fname

fname: 外部ファイル名。このファイルからユーザー定義外部荷重を読み込む。

（２）外部荷重を全体荷重ベクトルへ組み込むサブルーチン

subroutine uloading( cstep, factor, exForce )

integer, INTENT(IN) :: cstep

　　REAL(KIND=kreal), INTENT(IN) :: factor

REAL(KIND=kreal), INTENT(INOUT) :: exForce(:)

cstep: 現時点の解析ステップ数

factor: 現ステップの荷重係数

exForce: 全体荷重ベクトル

（３）残差応力の計算サブルーチン

subroutine uResidual( cstep, factor, residual )

integer, INTENT(IN) :: cstep

REAL(KIND=kreal), INTENT(IN) :: factor

REAL(KIND=kreal), INTENT(INOUT) :: residual(:)

cstep: 現時点の解析ステップ数

factor: 現ステップの荷重係数

residual: 全体残差力ベクトル