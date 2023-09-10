- （主观概率）
  collapsed:: true
	- 传统意义上的概率是对*多次重复*的随机事件的发生的可能性的分析，
	- 现实生活中，很多事件并不能完全的重复出现，如某一年的经济情况，或某一天的天气情况等，
	- 因此人们提出了主观概率的概念，指人们根据经验对随机事件的概率的主观评判，
- Bayes公式
	- 定义
	  collapsed:: true
		- $P(B_{j}|A) = \dfrac{P{(AB_{j})}}{P(A)} = \dfrac{P(B_{j})P(A|B_{j})}{\sum\limits_{i = 1}^{n}P(B_{i})P(A|B_{i})}$
	- 含义
	  collapsed:: true
		- $P(B_{j})$为已知信息，被称为*先验概率*；即没有额外信息的情况下，人们对事件B_{j}的概率的估计，
		- $P(A|B_{j})$为经过实验得到的数据信息；即在已知信息的基础上，事件A发生的概率，
		- $P(B_{j}|A)$为经过计算得到的结果，被称为*后验概率*；即综合实验数据得到的信息，对事件B_{j}的概率的“修正”，
- 先验分布（prior）
	- 先验分布的求解
		- 主观概率
		- 先验超参数法
		  collapsed:: true
			- 一般称参数先验分布族中的参数为“超参数”，
			- 超参数的求解方式较为多样，可以由样本直接估计得到，也可由样本的分位数信息估计得到，
		- 无信息先验分布
		  collapsed:: true
			- 若难以找到先验分布的信息，则一种给出先验分布的方法为“无信息”先验，
			- 均匀分布
			  collapsed:: true
				- 离散均匀分布
				- 有限区间均匀分布
				- 无限区间均匀分布
				  collapsed:: true
					- 理论上，无限区间不存在均匀分布；但大部分参数的可能取值都为无限区间，
					- 此处定义了广义先验密度，即只要保证\pi(\theta) \ge 0和由此算得的后验密度\pi(\theta| x)满足pdf的条件，则$\int \pi(\theta) d\theta$可以不为1，
					- 因此，无限区间的均匀分布一般定义为\pi(\theta) \equiv 1，
			- @一般情形
			  collapsed:: true
				- Jeffreys无信息先验
				  collapsed:: true
					- 使用样本分布族的Fisher信息量的平方根作为无信息先验密度，
		- 共轭先验分布族
		  collapsed:: true
			- 若先验分布\pi(\theta) 与算得的后验分布\pi(\theta|x) 为同一分布族，则称该分布族为共轭先验分布族，
			- 如Poisson分布的共轭先验分布族为伽马分布，
			- （先验分布与样本的分布可能不是同一分布族），
- 后验分布（posterior）
	- 定义
		- 称给定样本X = x后，参数\theta的条件分布\pi(\theta | x)为\theta的后验分布，
		- 即$\pi(\theta| x) = \dfrac{f(x, \theta)}{m(x)} = \dfrac{f(x|\theta)\pi(\theta)}{\int f(x|\theta)\pi(\theta)d \theta}$，
		- 其中f(x, \theta)为x和\theta的联合分布；由条件分布定义，可以拆分为f(x|\theta)\pi(\theta)，或\pi(\theta|x)m(x)，
		- 因此联合分布可以由先验分布\pi(\theta)和样本的分布f(x|\theta)（即给定\theta后x的分布）算得，
		- m(x)为x的边缘分布，可通过对联合分布f(x, \theta)中的\theta进行积分算得，
	- 简化计算
	  collapsed:: true
		- 若先验分布为共轭先验分布族，
		- 由后验分布的计算公式$\pi(\theta| x) = \dfrac{f(x|\theta)\pi(\theta)}{m(x)}$可以看出，\pi(\theta | x)只与f(x|\theta)\pi(\theta)相差一个与x有关，但与\theta无关的项，
		- 因此，只需要算出f(x|\theta)\pi(\theta)，再根据其形式和参数分布族的正则性，添加正则因子即可，
		- 即无需通过积分求解m(x)的具体分布，
- 经验贝叶斯方法（empirical）
  collapsed:: true
	- 利用历史样本，对先验分布进行一定的估计，
- Bayes统计推断
	- 概述
	  collapsed:: true
		- 综合了样本数据的后验分布\pi(\theta | x)是Bayes统计推断的核心，
		- 在样本数据较少时，传统的统计推断方式得到的结论一般较为极端（0或1）；而综合了先验信息的Bayes推断则会显得更加“合理”，
	- 点估计
		- 估计值
		  collapsed:: true
			- 一般思路为用后验分布\pi(\theta| x)的数字特征来估计参数，
			- 众数：即使后验分布函数\pi(\theta| x)达到极值的自变量\theta的取值，
			  collapsed:: true
				- 有时称为广义MLE——部分情况下，先验分布为U(0, 1)时的后验众数估计与传统的MLE的取值相同，
			- 中位数：即使后验分布函数\Pi(\theta| x) = 1/2的自变量\theta的取值，
			- 期望：即$E_{\pi}(\theta) = \int_{S_{\theta}}\theta \cdot \pi(\theta| x)d\theta$，
			- 若后验分布\pi(\theta| x)恰好为对称分布，则上述三个数字特征相同，
	- 区间估计
	  collapsed:: true
		- 估计值
		  collapsed:: true
			- 称使P(a \le \theta \le b|x) \ge 1 - \alpha的区间[a, b]为\theta的Bayes区间估计；一般称为“可信区间”，
			- a，b仍为样本X的函数，即估计量\theta(X)，
			- 由于\theta的后验分布已知， 因此一般直接根据\theta的点估计和后验分布\pi(\theta| x)直接求解后验区间，
	- 假设检验
	  collapsed:: true
		- 由于后验分布\pi(\theta| x)已知，因此Bayes假设检验的基本方式就是直接计算H_{0}和H_{1}的后验概率，
		- 即$\alpha_{0} = P(\theta \in \Theta_{0} | x)，\alpha_{1} = P(\theta \in \Theta_{1} | x)$；
		- 再对比\alpha_{0}和\alpha_{1}，拒绝域为{$\frac{\alpha_{0}}{\alpha_{1}} \le 1$}，
		- Bayes假设检验更易于处理多重假设的情况（即并检验，交检验），只要分别计算每个\Theta_{i}，并取最大（最小）的一个\alpha_{i}作为H_{0}的水平即可，
	- 观察值估计
	  collapsed:: true
		- 设随机变量Z为与参数\theta有关，且（条件）分布已知 g(z|\theta)的随机变量，
		- 类似容忍区间，在得到参数\theta的估计后，希望进一步根据\theta求解具体的随机变量Z的可能取值，
		- 依然可以从条件分布的角度分析，
		- 先求得X = x的条件下Z，\theta的联合分布$f(Z, \theta | x) = g(z|\theta)\pi(\theta| x)$；
		- 再对参数\theta积分，即可得到X = x的条件下Z的边缘分布，即$p(Z | x) = \int_{S_{\theta}}f(Z, \theta | x)  d\theta$，
		- 然后就可以根据p(Z | x) 来对Z的取值进行推断，
- [[统计决策理论]]
-
- [[概率论]]
- [[数理统计]]