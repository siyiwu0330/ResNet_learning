# ResNet_learning

## ResNet浅谈
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
resnet18效果一般，下图是lr=0.0001跑100轮的效果

loss
---

![image](https://user-images.githubusercontent.com/40969794/125669324-29e21f26-dffd-462e-8f7f-2f1402f0b47b.png)

acc
---

Test Loss: 1.646891

Test Accuracy of     0: 33% (10/30)
Test Accuracy of     1: 36% (11/30)
Test Accuracy of     2: 56% (17/30)
Test Accuracy of     3: 33% (10/30)
Test Accuracy of     4: 36% (11/30)
Test Accuracy of     5: 76% (23/30)
Test Accuracy of     6: 33% (10/30)
Test Accuracy of     7: 73% (22/30)
Test Accuracy of     8: 23% ( 7/30)
Test Accuracy of     9: 36% (11/30)
Test Accuracy of    10: 46% (14/30)
Test Accuracy of    11: 50% (15/30)

Test Accuracy (Overall): 44% (161/360)




