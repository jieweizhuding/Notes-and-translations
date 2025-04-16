## 对数据进行预处理
$$
X_{m*n},x_i=(x_{i1},x_{i2}...x_{in})_{1*n},X=(x_1,x_2,...x_m)^T_{m*1}
$$
$$
\hat{X}=mean(X)=\frac{1}{M}\sum_{i=1}^{M} x_i=\frac{1}{M}(lX),l=(1,1,...,1)_{1*m} 
$$
$$
S(X)=covariance(X)=\frac{1}{M}\sum_{i=1}^{i=M}(x_i- \hat{X})^T(x_i-\hat{X})=\frac{1}{M}(X^T-\hat{X}^Tl)(X^T-\hat{X}^Tl)^T=\frac{1}{M}(X^T-\frac{1}{M}X^Tl^Tl)(X^T-\frac{1}{M}X^Tl^Tl)^T=\frac{1}{M}(X^T(I_M-\frac{1}{M}l^Tl))(X^T(I_M-\frac{1}{M}l^Tl))^T=\frac{1}{M}X^THH^TX
$$
$$
H=I_M-\frac{1}{M}l^Tl
$$
其中的代换对于新手来说并不容易，特别是求和转化为矩阵，但也有一些简单的方法
$$
\hat{X}_{1*n}=>l_{1*m}X_{m*n}
$$
$$
S(X)_{n*n}=(X^T_{n*m}-\hat{X}^T_{n*1}l_{1*m})_{n*m}(X^T_{n*m}-\hat{X}^T_{n*1}l_{1*m})^T_{m*n}
$$
接下来考察H,容易证明
$$
H=(I_M-\frac{1}{M}l^Tl)=H^T
$$
$$
H^n=H
$$
则
$$
S(X)=\frac{1}{M}X^THH^TX=\frac{1}{M}X^THX
$$

## PCA
PCA的原则有两点：最大投影方差，最小重构代价；但他们本质是等价的，因此，这里我们使用其中容易的一点进行证明：
<b>最大投影方差</b>
假设我们找到了一组标准正交基u，对其中的第i个分析(注意数据在使用前需要标准化)
$$
J=\frac{1}{M}\sum((x_i-\hat{X})u)^T((x_i-\hat{X})u)=u^T\frac{1}{M}\sum_{i=1}^{i=M}(x_i- \hat{X})^T(x_i-\hat{X}) u=u^TSu
$$
接下来由拉格朗日数乘法
$$
\begin{cases}
J=u^TSu\\u^Tu=1
\end{cases}
$$
$$
L=u^TSu+\lambda(1-u^Tu)
$$
$$
\frac{dL}{du}=2Su-2\lambda u=0
$$
$$
Su=\lambda u
$$
可知u是S的特征向量，lambda是S的特征值。

