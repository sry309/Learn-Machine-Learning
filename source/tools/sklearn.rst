sklearn
============================================================

简介
------------------------------------------------------------
scikit-learn是Python重要的机器学习库，简称sklearn，支持包括分类、回归、降维和聚类四大机器学习算法。还包含了特征提取、数据处理和模型评估三大模块。

sklearn是Scipy的扩展，建立在NumPy和matplotlib库的基础上。利用这几大模块的优势，可以大大提高机器学习的效率。

sklearn拥有着完善的文档，上手容易，具有着丰富的API，在学术界颇受欢迎。sklearn已经封装了大量的机器学习算法，包括LIBSVM和LIBINEAR。同时sklearn内置了大量数据集，节省了获取和整理数据集的时间。


数据集模块
------------------------------------------------------------
sklearn中包含了大量的优质的数据集，可供练习使用。可 ``from sklearn import datasets`` 使用。

数据预处理模块
------------------------------------------------------------
preprocessing模块，可 ``from sklearn import preprocessing`` 使用。

数据归一化
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
为了使得训练数据的标准化规则与测试数据的标准化规则同步，preprocessing中提供了很多Scaler

::

    data = [[0, 0], [0, 0], [1, 1], [1, 1]]
    # 1. 基于mean和std的标准化
    scaler = preprocessing.StandardScaler().fit(train_data)
    scaler.transform(train_data)
    scaler.transform(test_data)

    # 2. 将每个特征值归一化到一个固定范围
    scaler = preprocessing.MinMaxScaler(feature_range=(0, 1)).fit(train_data)
    scaler.transform(train_data)
    scaler.transform(test_data)
    #feature_range: 定义归一化范围

正则化
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
当你想要计算两个样本的相似度时必不可少的一个操作，就是正则化。其思想是：首先求出样本的p-范数，然后该样本的所有元素都要除以该范数，这样最终使得每个样本的范数都为1。

::

    >>> X = [[ 1., -1.,  2.],
    ...      [ 2.,  0.,  0.],
    ...      [ 0.,  1., -1.]]
    >>> X_normalized = preprocessing.normalize(X, norm='l2')

    >>> X_normalized                                      
    array([[ 0.40..., -0.40...,  0.81...],
           [ 1.  ...,  0.  ...,  0.  ...],
           [ 0.  ...,  0.70..., -0.70...]])

one-hot编码
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
one-hot编码是一种对离散特征值的编码方式，在LR模型中常用到，用于给线性模型增加非线性能力。

::

    data = [[0, 0, 3], [1, 1, 0], [0, 2, 1], [1, 0, 2]]
    encoder = preprocessing.OneHotEncoder().fit(data)
    enc.transform(data).toarray()
