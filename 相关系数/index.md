# 

#相关系数

`cor(x,use=c("all.obs","everything","complete.obs","pairwise.complete.obs"),method=c("pearson", "kendall", "spearman"))`
`cor.test(x, y, method=c("pearson", "kendall", "spearman"),alternative = c("two.sided", "less", "greater"))`

统计分析中常见的变量类型有连续型数值变量，无序分类变量、有序分类变量。

连续型数值变量：如销售额、气温、工资收入、考试成绩；

无序分类变量：如性别男和女，血型种类；

有序分类变量：如学历水平小学、初中、高中、大学、研究生；

##Pearson相关系数

作用：是衡量线性关联性的程度

定义：两个连续变量(X,Y)的pearson相关性系数(Px,y)等于它们之间的协方差cov(X,Y)除以它们各自标准差的乘积(σX,σY)

使用前提：

1. 实验数据通常假设是成对的来自于正态分布的总体。由于我们在求皮尔森相关性系数以后，通常还会用t检验之类的方法来进行皮尔森相关性系数检验，而 t检验是基于数据呈正态分布的假设的。  
2. 实验数据之间的差距不能太大，或者说皮尔森相关性系数受异常值的影响比较大  
3. 两个数据序列的数据要一一对应，等间距等比例。数据序列通常来自对同一组样本的多次测量或不同视角的测量。

>**example:**

> Pearson's product-moment correlation

>data:  data[, 2] and data[, 3]

>t = 13.681, df = 448, p-value < 2.2e-16

>alternative hypothesis: true correlation is not equal to 0

>95 percent confidence interval:

 >0.4741850 0.6049145

>sample estimates:

>cor  

>0.5428297 


在上面的结果中：

*	t是t检验统计值（t = 13.681）
*	df是自由度（df = 448）
*	p值是t检验的显着性水平（p-value < 2.2e-16）
*	95CI是是相关系数在95％时的置信区间（[4741850,0.6049145）  
*	cor是相关系数（0.543）


##spearman相关系数

作用：非参数相关系数，不是衡量线性相关的，而是衡量秩序的相关性的

定义：可以理解成就是一种顺序或者排序，根据原始数据的排序位置进行求解，即依据两列成对等级的各对等级数之差来进行计算。这种表征形式就没有了求皮尔森相关性系数时那些限制

使用前提：

1. 不服从双变量正态分布的资料；  
2. 总体分布类型未知；  
3. 两个数据序列的数据一一对应，等间距等比例。数据序列通常来自对同一组样本的多次测量或不同视角的测量。

##kendall相关系数

作用：计算有序类别的相关系数

定义：n个同类的统计对象按特定属性排序，其他属性通常是乱序的。同序对和异序对之差与总对数（n*(n-1)/2)的比值定义为Kendall系数。

使用前提：

1. 两个分类变量均为有序分类  
2. 当既不满足正态分布，也不是等间距的定距数据


##总结

Pearson,Spearman和Kendall作用：


1. Pearson积差相关系数衡量了两个定量变量之间的线性相关程度  

2. Spearman等级相关系数则衡量分级定序变量之间的相关程度  

3. Kenddall’s Tau相关系数也是一种非参数的等级相关度量


Pearson,Spearman和Kendall的区别：

*	对于一般情况默认数据服从正太分布的或两个连续变量间呈现线性相关时，使用Pearson积差相关系数

*	Spearman相关系数对原始变量的分布不作要求，属于非参数统计方法，相对于Pearson相关使用范围要广些，对于服从Pearson相关系数的数据也可以计算Spearman相关系数，但是效果要低一些（因为Spearman忽略了原始变量的值的大小，只看重此值在整个变量数据的名次位置）

*	当资料不服从双变量正态分布或总体分布型未知或原始数据时用等级表示时，宜用Spearman或Kendall相关


##补充

> 来自两个变量（x，y）中每个变量的数据是否服从正态分布

1. 使用Shapiro-Wilk正态性检验 –> R函数：shapiro.test（）  
2. 画qqplot —> R函数：ggpubr :: ggqqplot（）  
3. 画概率密度图 –> lines(density(data$wes_TMB),col="blue",lwd=2)
