# ResNet_learning

## ResNet浅尝辄止
网络层数过多导致了以下两个主要问题：

1. 梯度消失和梯度爆炸
2. 网络退化

ResNet通过在原有函数上增加一个传递自身信息的x以求解决上述两个问题

F(x) = x + F(x)

F(x) 是使用两层神经网络对目标函数进行拟合的函数， 残差网络的主要贡献就是在这之上增加了一个x

其具体结构如图：

![image](https://user-images.githubusercontent.com/40969794/125481285-410923e3-3a30-43ee-b2d5-988a9ee497e9.png)

ResNet理论上的功能：
1. 通过x来将前层的信息无损的传递到下层，功能类似LSTM记忆门效果
2. 通过x来保证每次反向传播都有一个1，以此来避免梯度的消失

因为有x的存在，且因为拟合函数 F(x) 相比于趋近 x 而言更容易趋近于0，因此残差网络能有效的“屏蔽”掉一些无用的网络层，将信息流无损的向下传递（对网络进行剪枝）
  
为了避免参数过多和适应小样本数据的训练ResNet还在原本的基础上设计了进阶版的层数更多的网络，他们的具体结构如下：
  
![image](https://user-images.githubusercontent.com/40969794/125482497-4f748f11-30ba-4fa0-b801-62ba7a645388.png)


## resnet18
resnet18效果一般，下图分别是是lr=0.0001和lr=0.001时跑100轮的效果，虽然训练损失还没有完全收敛，但是从验证损失可以看到模型已经考试出现过拟合的现象,此处采用的是直接将resnet最后一层的fc层输出改为12的方法，效果不是很理想


loss
---

![image](https://user-images.githubusercontent.com/40969794/125670226-59acd1d4-fe1b-41f9-884b-b5caf79282e1.png)
![image](https://user-images.githubusercontent.com/40969794/125735039-8751aa14-648f-45cb-a337-8a8c6f375e87.png)


acc
---

![image](https://user-images.githubusercontent.com/40969794/125669715-390e1ba6-9623-4ffe-ad81-2db0d8f405ff.png)
![image](https://user-images.githubusercontent.com/40969794/125735053-2f845057-2d69-4615-8893-f1804bf3ca59.png)





