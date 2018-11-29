# 对曲线震荡现象的分析

这里采用的模型是有信息上传率的模型，并且K不为0。因为感染率曲线震荡的现象在所有模型中都会出现。

## 1. 参数过多

并且参数只作用于疾病传播模型的感染率和康复率上，尤其是感染率。当前$\sigma_S=0.3$, $\sigma_I=0.6$, 导致感染率衰减因子最低可以达到0.18。而康复率最高可以增大$\sigma_R=1.5$倍。 于是最终作用于疾病传播阈值上的衰减因子最高达到0.12。

在上层的信息传播作用下很容易使得疾病有效传播率骤减，之后感染率降低使得衰减因子失效，疾病有效传播率回弹。

衰减参数导致的传播模型有很大的惯性，只是不知道这种惯性为什么可以在每个时间都能造成如此大的影响。针对这个过程，调节疾病感染率会产生一些作用。

针对这一猜测，可以存取感染率和康复率变化曲线，和基线对照。


1. 对于WS-BA网络(BA用于传播疾病)

	设定 $\sigma_{S}=0.3$, $\sigma_{I}=0.6$, $\sigma_{F}=0.8$, $\sigma_{R}=1.3$, $\lambda=0.6$, $\delta=0.15$, $\mu=0.1$ 和 $K=0.3$。

	* $\beta=0.2$
	![beta=0.2](D:\Projects\Network\Epidemic-Information_spreading\Matlab\figures\model2\WS_BA_beta_0.2.png)
	* $\beta=0.35$
	![beta=0.35](D:\Projects\Network\Epidemic-Information_spreading\Matlab\figures\model2\WS_BA_beta_0.35.png)
	* $\beta=0.4$
	![beta=0.4](D:\Projects\Network\Epidemic-Information_spreading\Matlab\figures\model2\WS_BA_beta_0.4.png)
	* $\beta=0.45$
	![beta=0.45](D:\Projects\Network\Epidemic-Information_spreading\Matlab\figures\model2\WS_BA_beta_0.45.png)
	* $\beta=0.5$
	![beta=0.5](D:\Projects\Network\Epidemic-Information_spreading\Matlab\figures\model2\WS_BA_beta_0.5.png)
	* $\beta=0.6$
	![beta=0.6](D:\Projects\Network\Epidemic-Information_spreading\Matlab\figures\model2\WS_BA_beta_0.6.png)
	* $\beta=0.8$
	![beta=0.8](D:\Projects\Network\Epidemic-Information_spreading\Matlab\figures\model2\WS_BA_beta_0.8.png)
	* $\beta=0.9$
	![beta=0.9](D:\Projects\Network\Epidemic-Information_spreading\Matlab\figures\model2\WS_BA_beta_0.9.png)

## 2. 蒙塔卡罗模拟次数依然不够多

原论文做了10000次独立实现，所得的曲线没有震动。我在实现的时候最多做了100次仿真，并不清楚是不是这个原因。

## 3. 网络本身参数

我所进行实验选取的网络是程序生成的网络，并且生成参数并没有可以选择，很可能导致网络平均度等指标有异于实际网络。

以之前生成的ER网络来说，当时随手选了0.2的连边率，导致生成的网络平均度为400，而原论文采用的ER网络平均度为15。在进行实验时0.2尚未连边概率使得网络振动尤其大，减小平均度后虽然震荡大大减缓，但是这一现象依然存在且不可忽视。