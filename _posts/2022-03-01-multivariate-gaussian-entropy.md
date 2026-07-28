---
layout: single
title: "【数学】多元高斯分布的熵"
date: 2022-03-01 21:18:25
author_profile: true
---

作者: 引线小白-本文永久链接：http://www.limoncc.com/概率论/2017-01-10-多元高斯分布的熵/
知识共享许可协议: 本博客采用署名-非商业-禁止演绎4.0国际许可证

## 一、若干引理
### 1、引理1.0
#### 1、连续随机向量函数
考虑一般情况，我们有随机向量 $\displaystyle \bm{x}\sim f(\bm{x})$。现在有函数 $\displaystyle \bm{y}=\bm{g}(\bm{x}):\mathbb{R}^k\mapsto\mathbb{R}^d$。即有：
$$\begin{aligned}
\bm{y}=\bm{g}(\bm{x})
\end{aligned}$$
若上述方程有唯一解：
$$\begin{aligned}
\bm{x}=\bm{h}(\bm{y})
\end{aligned}$$
则称函数 $\displaystyle \bm{x}=\bm{h}(\bm{y})$是 $\displaystyle \bm{y}=\bm{g}(\bm{x})$的反函数。同时我们有雅可比行列式：
$$\begin{aligned}
\bm{J}=\mathrm{det}\left[\frac{\partial \bm{x}}{\partial \bm{y}^\text{T}}\right]
\end{aligned}$$

#### 2、变量代换引理
【定理1.0】
对于连续随机向量 $\displaystyle \bm{x}\sim f(\bm{x})$，函数 $\displaystyle \bm{y}=\bm{g}(\bm{x})$满足下列条件：
1、 $\displaystyle \bm{y}=\bm{g}(\bm{x})$有唯一反函数 $\displaystyle \bm{x}=\bm{h}(\bm{y})$
2、 $\displaystyle \bm{y}=\bm{g}(\bm{x})$和 $\displaystyle \bm{x}=\bm{h}(\bm{y})$连续
3、 $\displaystyle \bm{J}=\mathrm{det}\left[\frac{\partial \bm{x}}{\partial \bm{y}^\text{T}}\right]$存在而且连续
那么
$$\begin{aligned}
f(\bm{y})=\left\{\begin{array}{l}f_\bm{x}\left[\bm{h}\left(\bm{y}\right)\right]\times\left|\,\bm{J}\right|&\text{ 若 }\bm{y}\in G \\\ 0 &\text{ 若 }\bm{y}\notin G \end{array}\right.
\end{aligned}$$
其中 $\displaystyle G=\{\bm{y}\mid \bm{y}=\bm{g(\bm{x})},\,\bm{x}\in \mathbb{R}^k\}$。 $\displaystyle \left|\,\bm{J}\right|$是雅可比行列式的绝对值，请勿与行列式符号混淆

证明：

为了区分随机变量与随机变量实例，我们定义 $\displaystyle \bm{\xi}$是随机向量，而 $\displaystyle \bm{x}$是随机向量$\displaystyle \bm{\xi}$的实例；$\displaystyle \bm{\eta}$是随机向量，而 $\displaystyle \bm{y}$是随机向量$\displaystyle \bm{\eta}$的实例
当 $\displaystyle \bm{y}\notin G$时， 显然有 $\displaystyle f_\bm{\eta}(\bm{y})=0$。
当 $\displaystyle \bm{y}\in G$时，有：
$$\begin{aligned}
F_ \bm{\eta}(\bm{y})=P(\bm{\eta}\leqslant \bm{y})=\int_A f_ \bm{\xi}(\bm{x})\mathrm{d}\bm{x}
\end{aligned}$$
其中： $\displaystyle A=\bigcap_{j=1}^{d}\{\bm{x}\mid g_j(\bm{x})\leqslant y_j\}$，在上式中换元： $\displaystyle \bm{x}=\bm{h}(\bm{y})$得：
$$\begin{aligned}
F_ \bm{\eta}(\bm{y})=\int_C\mathbb{I}_G(\bm{y})\times f_ \bm{\xi}\left[\bm{h}(\bm{y})\right]\cdot\left|\bm{J}\right|\mathrm{d}\bm{y}
\end{aligned}$$
其中 $\displaystyle C=\prod_{j=1}^{d}(-\infty,y_j]$， $\displaystyle \mathbb{I}_G(\bm{y})$是 $\displaystyle G$的示性函数。由此当 $\displaystyle \bm{y}\in G$时：
$$\begin{aligned}
f_ \bm{\eta}(\bm{y})=f_\bm{\xi}\left[\bm{h}\left(\bm{y}\right)\right]\times\left|\,\bm{J}\right|
\end{aligned}$$
证毕。
其中证明中最关键的地方在于： $\displaystyle A\to C$的转变中，函数增减涉及积分方向的问题。这一问题的清晰说明较为繁琐，可以参考《数学分析原理》229页定理10.9以及微分形式的积分。

### 2、引理2.0
定义方阵的幂(可以是分数) $\displaystyle \bm{A}^n=\bm{U}\bm{\Lambda}^n\bm{U}^\text{T}$。其中 $\displaystyle \bm{A}=\bm{U}\bm{\Lambda}\bm{U}^\text{T}$是约当分解或者叫谱分解，简单说就是对角化。

1、马哈拉诺比斯变换引理
我们有任意高斯分布 $\displaystyle \bm{x}\sim\mathcal{N}\left(\bm{\mu},\bm{\varSigma}\right)$。我们称 $\displaystyle \bm{y}=\bm{\varSigma}^{-\frac{1}{2}}\left[\bm{x}-\bm{\mu}\right]$为马哈拉诺比斯变换。其中
$$\begin{aligned}
\bm{y}\sim\mathcal{N}\left(\bm{0},\bm{I}_k\right)
\end{aligned}$$
也就是说 $\displaystyle y_i$是标准高斯分布 $\displaystyle \mathcal{N}\left(0,1\right)$。

证明：
知道：
$$\begin{aligned}
p(\bm{x})=(2\pi)^{-\frac{k}{2}}\left|\bm{\varSigma}\right|^{-\frac{1}{2}}\exp\left[-\frac{1}{2}(\bm{x}-\bm{\mu})^\mathrm{T}\bm{\varSigma}^{-1}(\bm{x}-\bm{\mu}) \right]
\end{aligned}$$
同时有： $\displaystyle \bm{x}=\bm{\varSigma}^{\frac{1}{2}}\bm{y}+\bm{\mu}$。 $\displaystyle \bm{J}=\mathrm{det}\left[\frac{\partial \bm{x}}{\partial \bm{y}^\text{T}}\right]=\left|\bm{\varSigma}\right|^{\frac{1}{2}}$
有变量代换定理有：
$$\begin{aligned}
p(\bm{y})=(2\pi)^{-\frac{k}{2}}\exp \left[-\frac{1}{2}\bm{y}^\text{T}\bm{y}\right]
\end{aligned}$$
证毕。
当然我们也可以通过特征函数的方法对马哈拉诺比斯变换引理加以证明。

## 二、熵
对于连续随机变量有： $\displaystyle \mathrm{H}[\bm{x}]
=\mathrm{E}[\mathrm{I}(\bm{x})]
=-\int p(\bm{x})\ln p(\bm{x})\mathrm{d}\bm{x}$
下面我们推导多元高斯分布的熵：
$$\begin{aligned}
\mathrm{H}[\bm{x}]
&=-\int p(\bm{x})\ln p(\bm{x})\mathrm{d}\bm{x}\\
&=-\int p(\bm{x})\ln \left[(2\pi)^{-\frac{k}{2}}\left|\bm{\varSigma}\right|^{-\frac{1}{2}}\exp\left[-\frac{1}{2}(\bm{x}-\bm{\mu})^\mathrm{T}\bm{\varSigma}^{-1}(\bm{x}-\bm{\mu}) \right]\right]\mathrm{d}\bm{x}\\
&=-\int p(\bm{x}) \left[\ln \left((2\pi)^{-\frac{k}{2}}\left|\bm{\varSigma}\right|^{-\frac{1}{2}}\right)-\frac{1}{2}(\bm{x}-\bm{\mu})^\mathrm{T}\bm{\varSigma}^{-1}(\bm{x}-\bm{\mu}) \right]\mathrm{d}\bm{x}\\
&=\ln \left((2\pi)^{\frac{k}{2}}\left|\bm{\varSigma}\right|^{\frac{1}{2}}\right)+\frac{1}{2}\int p(\bm{x}) \left[(\bm{x}-\bm{\mu})^\mathrm{T}\bm{\varSigma}^{-1}(\bm{x}-\bm{\mu}) \right]\mathrm{d}\bm{x}\\
&=\ln \left((2\pi)^{\frac{k}{2}}\left|\bm{\varSigma}\right|^{\frac{1}{2}}\right)+\frac{1}{2}\int p(\bm{y})\times\bm{y}^\text{T}\bm{y}\mathrm{d}\bm{y}\\
&=\ln \left((2\pi)^{\frac{k}{2}}\left|\bm{\varSigma}\right|^{\frac{1}{2}}\right)+\frac{1}{2}\sum_{i=1}^k\mathrm{E}[y_i^2]\\
&=\ln \left((2\pi)^{\frac{k}{2}}\left|\bm{\varSigma}\right|^{\frac{1}{2}}\right)+\frac{k}{2}\\
&=\ln \left[(2\pi\mathrm{e})^{\frac{k}{2}}\left|\bm{\varSigma}\right|^{\frac{1}{2}}\right]\\
&=\frac{k}{2}\left(\ln2\pi+1\right)+\frac{1}{2}\ln\left|\bm{\varSigma}\right|
\end{aligned}$$

注意：推导中我们使用了马哈拉诺比斯变换引理。

## 三、评述
1、在求解多元高斯分布的熵中，我们使用了变量代换，同时引用了马哈拉诺比斯变换引理。
2、深层次的原理涉及到微分形式的积分。同时我们也可以浅层次的理解：使用特征函数导出马哈拉诺比斯变换引理
3、好了我们不应止步，我们征途是星辰大海。


---

>**:four_leaf_clover:碎碎念:four_leaf_clover:**
>Hello米娜桑，这里是英国留学中的杨丝儿。我的博客的关键词集中在算法、机器人、人工智能、数学等等，点个关注吧，持续高质量输出中。
>**:cherry_blossom:唠嗑QQ群**：[兔叽的魔术工房](https://jq.qq.com/?_wv=1027&k=EaGddTQg) (942848525)
>**:star:B站账号**：[杨丝儿今天也在科学修仙](https://space.bilibili.com/98639326)（UP主跨站求个关注）
