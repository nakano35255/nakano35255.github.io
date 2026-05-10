---
layout: page
title: 数値計算コード
permalink: /codes/
order: 6
---

研究で用いている数値計算コードや、公開している研究用ソフトウェアをまとめています。

## spectral-noisy-coupled-burgers-1d

[spectral-noisy-coupled-burgers-1d](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d) は、1次元多成分ノイズあり結合 Burgers 方程式を解くための C++ ソルバーです。

対象としている方程式は、次の形で書ける保存型の確率偏微分方程式です。

$$
\partial_t \phi^\alpha
+ \sum_\beta A_{\alpha\beta}\partial_x\phi^\beta
- \sum_\beta D_{\alpha\beta}\partial_x^2\phi^\beta
+ \sum_{\beta,\gamma}H^\alpha_{\beta\gamma}\partial_x(\phi^\beta\phi^\gamma)
=
\sum_\beta B_{\alpha\beta}\partial_x\xi^\beta .
$$

Fourier スペクトル法を用いて空間微分を高精度に評価し、非線形項は 3/2 padding による擬スペクトル法で計算しています。KPZ 普遍性クラスを調べるための様々な観測量に対応しており、新しい観測量の追加も容易に行えるように設計されています。

本コードの特徴は、LAMMPS 風の `input.script` によってシミュレーション設定を柔軟に制御できる点です。
これにより、さまざまな 1 次元多成分揺らぐ流体方程式を、同じ枠組みで簡単に計算できます。また、Fourier スペクトル法を用いることで、空間微分を高精度に評価できます。

コード内の examples では、以下のような検証計算を行えます。

* fluctuating advection-diffusion equation の有限サイズ厳密解との比較
* 1成分 noisy Burgers equation において、height fluctuation が KPZ 普遍クラスの GOE Tracy-Widom 型分布へ近づくことのデモンストレーション解析（Oliveira, Ferreira, Alves, [Phys. Rev. E 85, 010601 (2012)](https://doi.org/10.1103/PhysRevE.85.010601) など）
* 2成分 coupled Burgers equation において、height fluctuation が KPZ 方程式の厳密解とどのように関連するかの最新研究の再現（De Nardis, Gopalakrishnan, Vasseur, [Phys. Rev. Lett. 131, 197102 (2023)](https://doi.org/10.1103/PhysRevLett.131.197102) など）

**リンク**

* GitHub repository: [spectral-noisy-coupled-burgers-1d](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d)
* Documentation: [README](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d/blob/main/README.md), [WIKI](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d/blob/main/WIKI.md)
* Examples: [examples directory](https://github.com/nakano35255/spectral-noisy-coupled-burgers-1d/tree/main/examples)


## spectral-scalar-fluctuating-hydrodynamics-1d

1成分に制限する代わりに、より複雑な揺らぐ流体方程式を解くための数値計算コードを公開予定です。

対象としている方程式は、次の形で書ける1成分密度場 $\rho(x,t)$ の保存則型確率偏微分方程式です。

$$
\frac{\partial \rho(x,t)}{\partial t}
=
\frac{\partial}{\partial x}
\left[
D(\rho)\frac{\partial \rho}{\partial x}
\right]
-
\frac{\partial}{\partial x}
\left[
M(\rho)\frac{\partial^3 \rho}{\partial x^3}
\right]
-
\frac{\partial}{\partial x}
\left[
v(x)A(\rho)
\right]
+
\frac{\partial}{\partial x}
\left[
\sqrt{2\sigma(\rho)}\,\xi(x,t)
\right].
$$
