# 集成学习
 集成学习是通过训练弱干个弱学习器，并通过一定的结合策略，从而形成一个强学习器。
##  Bagging算法
Bagging算法可与其他分类、回归算法结合，提高其准确率、稳定性的同时，通过降低结果的方差，避免过拟合的发生。
## 算法步骤
给定一个大小为n的训练集D，Bagging算法从中均匀、有放回地（即使用自助抽样法）选出m个大小为的子集n'，作为新的训练集。在这m个训练集上使用分类、回归等算法，则可得到m个模型，再通过取平均值、取多数票等方法，即可得到Bagging的结果。

## Boosting算法
GBDT (Gradient Boosting Decision Tree) 是机器学习中一个长盛不衰的模型，其主要思想是利用弱分类器（决策树）迭代训练以得到最优模型，该模型具有训练效果好、不易过拟合等优点。GBDT 在工业界应用广泛，通常被用于点击率预测，搜索排序等任务。

提升方法（Boosting），是一种可以用来减小监督式学习中偏差的机器学习算法。弱学习者一般是指一个分类器，它的结果只比随机分类好一点点；强学习者指分类器的结果非常接近真值。

## 算法步骤
大多数提升算法包括由迭代使用弱学习分类器组成，并将其结果加入一个最终的成强学习分类器。每一轮的训练集不变，只是训练集中每个样例在分类器中的权重发生变化。而权值是根据上一轮的分类结果进行调整。

Boosting方式每次使用的是全部的样本，每轮训练改变样本的权重。下一轮训练的目标是找到一个函数f 来拟合上一轮的残差。当残差足够小或者达到设置的最大迭代次数则停止。Boosting会减小在上一轮训练正确的样本的权重，增大错误样本的权重。（对的残差小，错的残差大。

### Boosting常见算法
#### LightGBM
优点：

- 更快的训练速度
- 更低的内存消耗
- 更好的准确率
- 分布式支持，可以快速处理海量数据

LightGBM 还具有支持高效并行的优点。LightGBM 原生支持并行学习，目前支持特征并行和数据并行的两种。

- 特征并行的主要思想是在不同机器在不同的特征集合上分别寻找最优的分割点，然后在机器间同步最优的分割点。
- 数据并行则是让不同的机器先在本地构造直方图，然后进行全局的合并，最后在合并的直方图上面寻找最优分割点。

#### XGBoost
#### CatBoost

![](
  ./img/boosting.png)

 ## 资料
 https://towardsdatascience.com/catboost-vs-light-gbm-vs-xgboost-5f93620723db

 https://blog.csdn.net/weixin_39807102/article/details/81912566
 
  