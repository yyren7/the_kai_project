---
sidebar_label: "2019年8月実施 線形代数"
tags:
  - Kyushu-University
---
# 九州大学 システム情報科学府 情報理工学専攻・電気電子工学専攻 2019年8月実施 線形代数

## **Author**
[Yu](https://blog.loveyou.moe/KU/%E4%B9%9D%E5%A4%A7%E6%83%85%E5%A0%B1%E7%90%86%E5%B7%A5%E5%AD%A6%E9%81%8E%E5%8E%BB%E5%95%8F%E3%81%AE%E8%A7%A3%E7%AD%94/), [蛋黄猫物理 (xhs: 94162357270)](https://www.xiaohongshu.com/user/profile/67173192000000001e009fa7?xsec_token=YBaJbvO4qazzvNUB-8gkqSwFa4usRBcKTQe93j6tfxtPw=)

## **Description**
数列 $a_0，a_1，a_2, \cdots$ は, $a_0 = 3，a_1 = 1，a_2 = 3$ および

$$
a_n = a_{n−1} + a_{n−2} + 2a_{n−3} \quad \quad (n = 3，4，5，\cdots)
$$

で定義される．

(1) $a_3，a_4，a_5$ を求めよ．

(2) 各 $n = 0，1，2，\cdots$ について次が成立つような行列 $T$ を答えよ．

$$
\begin{pmatrix}
a_{n+1}\\
a_{n+2}\\
a_{n+3}\\
\end{pmatrix} = T
\begin{pmatrix}
a_n\\
a_{n+1}\\
a_{n+2}\\
\end{pmatrix}
$$

(3) $T$ のすべての固有値とそれぞれに対応する固有ベクトルを求めよ．

(4) ベクトル $\begin{pmatrix} 3 \\1 \\3 \end{pmatrix}$を，前問で求めた固有ベクトルの線形結合として表せ．

(5) $a_n$ を求めよ．

## **Kai**
### (1)

$$
\begin{aligned}
a_3 &= a_2 + a_1 + 2a_0 = 3 + 1 + 2 \times 3 = 10\\
a_4 &= a_3 + a_2 + 2a_1 = 10 + 3 + 2 \times 1 = 15\\
a_5 &= a_4 + a_3 + 2a_2 = 15 + 10 + 2 \times 3 = 31 
\end{aligned}
$$

### (2)

$$
\begin{bmatrix}
a_{n + 1}\\
a_{n + 2}\\
a_{n + 3}\\
\end{bmatrix} = 
\begin{bmatrix}
a_{n + 1}\\
a_{n + 2}\\
a_{n + 2} + a_{n + 1} + 2a_{n}\\
\end{bmatrix} = T
\begin{bmatrix}
a_n\\
a_{n + 1}\\
a_{n + 2}\\
\end{bmatrix} \Rightarrow T = 
\begin{bmatrix}
0 & 1 & 0 \\
0 & 0 & 1 \\
2 & 1 & 1\\
\end{bmatrix}
$$

### (3)

$$
\begin{aligned}
&\because |A| = |\lambda E - T| = 
\begin{vmatrix}
\lambda & -1 & 0 \\
0 & \lambda & -1 \\
-2 & -1 & \lambda -1\\
\end{vmatrix} = (\lambda^2 + \lambda + 1)(\lambda - 2) = 0 \\
&\therefore \lambda_1 = 2 \quad \lambda_2 = \frac{-1 + \sqrt{3}i}{2} \quad \lambda_3 = \frac{-1 - \sqrt{3}i}{2}
\end{aligned}
$$

$\lambda_1 = 2$ のとき, $A_1x_1 = 0$ であり、$x_1 = \begin{bmatrix} \alpha_1\\ \alpha_2\\ \alpha_3\\ \end{bmatrix}$ とおくと,

$$
\begin{bmatrix}
2 & -1 & 0\\
0 & 2 & -1\\
-2 & -1 & 1\\
\end{bmatrix}
\begin{bmatrix}
\alpha_1\\
\alpha_2\\
\alpha_3\\
\end{bmatrix} = 0 \Rightarrow x_1 = 
\begin{bmatrix}
1 \\
2 \\
4 \\
\end{bmatrix}
$$

$\lambda_2 = \frac{-1 + \sqrt{3}i}{2}$ のとき, $A_2x_2 = 0$ であり、$x_2 = \begin{bmatrix} \beta_1\\ \beta_2\\ \beta_3\\ \end{bmatrix}$ とおくと,

$$
\begin{bmatrix}
\frac{-1 + \sqrt{3}i}{2} & -1 & 0 \\
0 & \frac{-1 + \sqrt{3}i}{2} & -1 \\
-2 & -1 & \frac{-3 + \sqrt{3}i}{2} \\
\end{bmatrix}
\begin{bmatrix}
\beta_1\\
\beta_2\\
\beta_3\\
\end{bmatrix} = 0 \Rightarrow x_2 =
\begin{bmatrix}
1 \\
\frac{-1 + \sqrt{3}i}{2} \\
\frac{-1 - \sqrt{3}i}{2} \\
\end{bmatrix}
$$

$\lambda_3 = \frac{-1 - \sqrt{3}i}{2}$ のとき, $A_3x_3 = 0$ であり、$x_3 = \begin{bmatrix} \gamma_1\\ \gamma_2\\ \gamma_3\\ \end{bmatrix}$ とおくと,

$$
\begin{bmatrix}
\frac{-1 - \sqrt{3}i}{2} & -1 & 0\\
0 & \frac{-1 - \sqrt{3}i}{2} & -1\\
-2 & -1 & \frac{-3 - \sqrt{3}i}{2}\\
\end{bmatrix}
\begin{bmatrix}
\gamma_1\\
\gamma_2\\
\gamma_3\\
\end{bmatrix} = 0 \Rightarrow x_3 = 
\begin{bmatrix}
1 \\
\frac{-1 - \sqrt{3}i}{2}\\
\frac{-1 + \sqrt{3}i}{2}\\
\end{bmatrix}
$$

### (4)

$$
\begin{bmatrix}
3 \\
1 \\
3 \\
\end{bmatrix} = 
\begin{bmatrix}
1 \\
2 \\
4 \\
\end{bmatrix} + 
\begin{bmatrix}
1 \\
\frac{-1 + \sqrt{3}i}{2} \\
\frac{-1 - \sqrt{3}i}{2} \\
\end{bmatrix} +
\begin{bmatrix}
1 \\
\frac{-1 - \sqrt{3}i}{2}\\
\frac{-1 + \sqrt{3}i}{2}\\
\end{bmatrix}
$$

### (5)

$$
\begin{aligned}
  \begin{bmatrix}
    a_n \\ a_{n-1} \\ a_{n-2}
  \end{bmatrix} &= T^{n-2} \cdot
  \begin{bmatrix}
    a_2 \\ a_1 \\ a_0
  \end{bmatrix} = AD^{n-2} A^{-1}A \cdot \begin{bmatrix}
    1 \\ 1 \\ 1
  \end{bmatrix} \\
  &= A \begin{bmatrix}
    2^{n-2} & 0 & 0 \\
    0 & (\frac{-1+\sqrt{3}i}{2})^{n-2} & 0 \\
    0 & 0 & (\frac{-1-\sqrt{3}i}{2})^{n-2}
  \end{bmatrix} \begin{bmatrix}
    1 \\ 1 \\ 1
  \end{bmatrix} \\
  &= \begin{bmatrix}
    1 & 1 & 1 \\
    2 & \frac{-1 + \sqrt{3}i}{2} &  \frac{-1 - \sqrt{3}i}{2} \\
    4 & \frac{-1 - \sqrt{3}i}{2} & \frac{-1 + \sqrt{3}i}{2}
  \end{bmatrix}
  \begin{bmatrix}
    2^{n-1} \\ (\frac{-1+\sqrt{3}i}{2})^{n-2} \\ (\frac{-1-\sqrt{3}i}{2})^{n-2}
  \end{bmatrix}
\end{aligned}
$$

従って、

$$
\begin{aligned}
a_n &= 2^{n-2} + \left(\frac{-1+\sqrt{3}i}{2}\right)^{n-2} + \left(\frac{-1-\sqrt{3}i}{2}\right)^{n-2} \\
&= 2^{n-2} + 2\cos \left(\frac{(n-2)\pi}{3} \right)
\end{aligned}
$$
