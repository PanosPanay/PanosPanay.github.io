---
title: deeplearning.ai_C2W1_practical_aspects_of_deep_learning
date: 2020-03-07 20:05:48
tags:
- deeplearning
- 吴恩达
- 深度学习
categories:
- 深度学习
---

# C2W1 深度学习的实践层面

# 吴恩达深度学习C2W1 深度学习的实践层面

- 如何配置训练集、验证集、测试集
- 如何分析偏差、方差，如何处理高偏差or高方差or高偏差和高方差共存的问题
- 如何在神经网络中应用不同形式的正则化（正则化解决高方差过拟合问题）
  - L2正则化
  - dropout
  - 其他正则化（数据扩增、early stopping）
- 加快神经网络训练速度的技巧（归一化输入）
- 梯度检验（调试后向传播是否正确）



## 编程作业

### 1、初始化参数

1. 不同的初始化方法可能导致性能最终不同

2. 随机初始化有助于打破对称，使得不同隐藏层的单元可以学习到不同的参数。

3. 初始化时，初始值不宜过大。

4. **He初始化搭配ReLU激活函数**常常可以得到不错的效果。

   ```python
   # GRADED FUNCTION: initialize_parameters_he
   
   def initialize_parameters_he(layers_dims):
       """
       Arguments:
       layer_dims -- python array (list) containing the size of each layer.
       
       Returns:
       parameters -- python dictionary containing your parameters "W1", "b1", ..., "WL", "bL":
       """
       
       np.random.seed(3)
       parameters = {}
       L = len(layers_dims) - 1 # integer representing the number of layers
        
       for l in range(1, L + 1):
           ### START CODE HERE ### (≈ 2 lines of code)
           parameters['W' + str(l)] = np.random.randn(layers_dims[l], layers_dims[l - 1]) * np.sqrt(2 / layers_dims[l - 1])
           parameters['b' + str(l)] = np.zeros((layers_dims[l], 1))
           ### END CODE HERE ###
           
       return parameters
   ```

   

### 2、正则化

解决过拟合（高方差）

- L2正则化（“权重衰减”：权重被改变到较小的值）

  - compute_cost_with_regularization(A3, Y, parameters, lambd)

    计算代价函数时增加正则化项

  - backward_propagation_with_regularization(X, Y, cache, lambd)

    权重矩阵的梯度计算要加上正则化项的导数

  若 λ 过大，可能导致高偏差

- dropout正则化

  - `forward_propagation_with_dropout` instead of `forward_propagation`.
  - `backward_propagation_with_dropout` instead of `backward_propagation`.

  正则化只用于训练，不要在测试中使用

### 3、梯度校验



