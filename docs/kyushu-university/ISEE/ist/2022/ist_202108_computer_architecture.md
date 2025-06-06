---
sidebar_label: "2021年8月実施 計算機アーキテクチャ"
tags:
  - Kyushu-University
---
# 九州大学 システム情報科学府 情報理工学専攻 2021年8月実施 計算機アーキテクチャ


## **Author**
[Yu](https://blog.loveyou.moe/KU/%E4%B9%9D%E5%A4%A7%E6%83%85%E5%A0%B1%E7%90%86%E5%B7%A5%E5%AD%A6%E9%81%8E%E5%8E%BB%E5%95%8F%E3%81%AE%E8%A7%A3%E7%AD%94/)

## **Description**
### 【問 1】
下図の論理回路の出力 $X, Y$ および内部回路 $G_1, G_2$ の論理関数が以下の様な真理値表で表されるとき、部分回路 $F$ の論理関数 $F(a, b, c, d)$ の最簡積和形を示せ。
ただし、論理関数の最簡積和形とは、その論理関数を表す積和形論理式のうち、積項数が最小のものを指す。
積項数が等しい積和形論理式が複数ある場合には、そのなかでリテラル数が最小のものを指す。

<figure style="text-align:center;">
  <img src="https://raw.githubusercontent.com/Myyura/the_kai_project_assets/main/kakomonn/kyushu_university/ISEE/ist_2022_computer_architecture_p1.png" width="400" alt=""/>
</figure>

<figure style="text-align:center;">
  <img src="https://raw.githubusercontent.com/Myyura/the_kai_project_assets/main/kakomonn/kyushu_university/ISEE/ist_2022_computer_architecture_p2.png" width="600" alt=""/>
</figure>

### 【問 2】
5つのステージからなるパイプライン型データパスを有するインオーダ・マイクロプロセッサについて考える。
実装されたパイプラインステージは、IF（命令取得）、ID（命令デコード）、EX（実行）、MEM（メモリアクセス）、ならびに、WB（ライトバック）である。
加算命令の実行における各ステージの処理内容は以下の表に従う。
ここで、各パイプラインステージの実行は常に $1$ クロックサイクルで完了できると仮定する。
また、WBステージでレジスタに書き込まれた値は、同一クロックサイクルにて、後続命令のIDステージで読み出し可能である。
さらに、全てのRAW（Read-After-Write）ハザードはパイプラインストールにより解決する。以下の各問に答えよ。

#### <center> パイプライン式データパスの動作
|ステージ|加算命令（add $x, $y, $z）実行における各ステージの処理内容|
|-|-|
|IF|メモリより実行すべき命令を取得し、次命令取得のためにプログラム・カウンタを更新|
|ID|命令の解読。レジスタファイルからレジスタ $y ならびに $z を読み出し。|
|EX|レジスタファイルから読み出した $y と $z の内容を加算。|
|MEM|特に無し（加算結果をWBステージへ転送）。|
|WB|加算結果をレジスタファイル内のレジスタ $x に書き込み。|

(1) 以下に示すアセンブリプログラムについて考える。各行において `#` 記号から右はコメントである。プログラム中に存在するフロー依存関係について、どの命令が、どの命令のどのレジスタに関して依存しているかをすべて列挙せよ。

```text
add $1 ,$3, $5   # <1>
add $9 ,$2, $3   # <2>
add $6 ,$3, $3   # <3>
add $3 ,$4, $3   # <4>
add $4 ,$7, $1   # <5>
add $5 ,$7, $4   # <6>
add $9 ,$3, $6   # <7>
add $2 ,$7, $6   # <8>
```

(2) 命令発行幅は $1$ と仮定する。このアセンブリプログラムの実行に要するクロックサイクル数を答えよ。

(3) 命令パイプラインの命令発行幅を $2$ へ増加し、インオーダ・スーパスカラ方式へと拡張する（依存関係のない命令を最大で $2$ 個同時に実行できる）。拡張後の命令パイプラインにて、このアセンブリプログラムの実行に要するクロックサイクル数を答えよ。

(4) 上記 (3) の拡張によりクロック周波数が $5\%$ 低下した。この拡張による性能向上率を答えよ。

### 【問 3】
キャッシュメモリにおける「初期参照ミス」「競合性ミス」「容量性ミス」とは何かそれぞれ説明せよ。


## **Kai** 
### 【問 1】
|a|b|c|d|f|
|-|-|-|-|-|
|0|0|0|0|x|
|0|0|0|1|0|
|0|0|1|0|x|
|0|0|1|1|x|
|0|1|0|0|x|
|0|1|0|1|1|
|0|1|1|0|1|
|0|1|1|1|x|
|1|0|0|0|1|
|1|0|0|1|0|
|1|0|1|0|x|
|1|0|1|1|x|
|1|1|0|0|0|
|1|1|0|1|0|
|1|1|1|0|0|
|1|1|1|1|1|

<figure style="text-align:center;">
  <img src="https://raw.githubusercontent.com/Myyura/the_kai_project_assets/main/kakomonn/kyushu_university/ISEE/ist_2022_computer_architecture_p3.png" width="500" alt=""/>
</figure>

$$
F = \overline{a}b + cd + \overline{b}\overline{d}
$$

### 【問 2】
#### (1)

$$
1 \Rightarrow 5(\$1),3 \Rightarrow 7(\$6),3 \Rightarrow 8(\$6),4 \Rightarrow 7(\$3),5 \Rightarrow 6(\$4)
$$

#### (2)
14

#### (3)
12

#### (4)
1.11

### 【問 3】
初期参照ミス:キャッシュラインを最初にアクセスするときに起こるミス

競合性ミス:同じインデクスをもつ異なるキャッシュラインにアクセスすることで起こるミス

容量性ミス:キャッシュしたいライン数がキャッシュ容量を上回ることで起こるミス