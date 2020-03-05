---
title: tensorflow
date: 2020-03-05 14:33:12
tags:
- tensorflow
- 深度学习
categories:
- 深度学习
---

# TensorFlow

## 1、GPU版TensorFlow安装

参考：https://tf.wiki/zh/basic/installation.html

1. 安装NVIDIA 驱动程序

   访问NVDIA官网下载：https://www.nvidia.com/Download/index.aspx?lang=en-us
   
   可在cmd中输入`nvidia-smi -L`查看显卡型号，下载相应版本的驱动程序，安装后重启电脑。
   
2. 建立conda虚拟环境并进入

   打开Anaconda Prompt，输入：（python版本号填写自己的python环境版本）

   ```shell
   conda create --name tf2 python=3.7      # “tf2”是你建立的conda虚拟环境的名字
   conda activate tf2                      # 进入名为“tf2”的conda虚拟环境
   ```

   进入虚拟环境后命令行最左边或显示虚拟环境名称(tf2):

   ![image-20200305145416211](tensorflow/image-20200305145416211.png)

   （注：其他关于虚拟环境的操作如下：

   ```shell
   conda create --name [env-name]      # 建立名为[env-name]的Conda虚拟环境
   conda activate [env-name]           # 进入名为[env-name]的Conda虚拟环境
   conda deactivate                    # 退出当前的Conda虚拟环境
   conda env remove --name [env-name]  # 删除名为[env-name]的Conda虚拟环境
   conda env list                      # 列出所有Conda虚拟环境
   ```

3. 安装 CUDA Toolkit 和 cuDNN。

   ```shell
   # 注：以下两行命令中的版本号严格按照https://www.tensorflow.org/install/gpu#software_requirements 安装，
   # 对于 TensorFlow 2.1，可使用
   conda install cudatoolkit=10.1
   conda install cudnn=7.6.5
   ```

4. 安装gpu版tensorflow

   ```shell
   # pip install tensorflow-gpu # 会自动安装对应版本的 CUDA Toolkit 和 cuDNN
   pip install tensorflow	
   # 从 TensorFlow 2.1 开始，pip 包 tensorflow 即同时包含 GPU 支持
   ```

   注：从 TensorFlow 2.1 开始，pip 包 `tensorflow` 即同时包含 GPU 支持，无需通过特定的 pip 包 `tensorflow-gpu` 安装 GPU 版本。如果对 pip 包的大小敏感，可使用 `tensorflow-cpu` 包安装仅支持 CPU 的 TensorFlow 版本。

   也可以使用 `conda install tensorflow` 来安装 TensorFlow，不过 conda 源的版本往往更新较慢，难以第一时间获得最新的 TensorFlow 版本.

   安装完后，可以通过命令`pip list`查看安装的包列表

5. 检测是否正确安装

   （如果你在 Windows 下安装了 TensorFlow 2.1 正式版，可能会在导入 TensorFlow 时出现 [DLL 载入错误](https://github.com/tensorflow/tensorflow/issues/35749) 。此时安装 [Microsoft Visual C++ Redistributable for Visual Studio 2015, 2017 and 2019](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 即可正常使用。）

   在虚拟环境中输入`python`，进入python环境，输入：

   ```python
   import tensorflow as tf
   ```

   如果报错：

   ```
   ImportError: DLL load failed: 找不到指定的模块。
   
   Failed to load the native TensorFlow runtime.
   ```

   进入https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads安装Visual Studio 2015, 2017 and 2019即可。

6. 第一个程序

   在虚拟环境中输入`python`，进入python环境，输入：

   ```python
   import tensorflow as tf
   
   A = tf.constant([[1, 2], [3, 4]])	
   # 运行这一行若报错cudaGetDevice() failed. Status: CUDA driver version is insufficient for CUDA runtime version
   # 跳转到第1步，安装一下NVIDIA 驱动程序即可
   
   B = tf.constant([[5, 6], [7, 8]])
   C = tf.matmul(A, B)
   
   print(C)
   ```

   输出如下结果表明安装成功

   ```python
   tf.Tensor(
   [[19 22]
   [43 50]], shape=(2, 2), dtype=int32)
   ```

7. 

