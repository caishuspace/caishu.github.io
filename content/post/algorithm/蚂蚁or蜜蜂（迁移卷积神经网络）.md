---
title: "蚂蚁or蜜蜂（迁移卷积神经网络）"
description: "蚂蚁or蜜蜂（迁移卷积神经网络）"
keywords: "蚂蚁or蜜蜂（迁移卷积神经网络）"

date: 2021-02-19T17:25:19+08:00
lastmod: 2021-02-19T17:25:19+08:00

categories:
  - 算法刷题
tags:
  - Code
  - pytorch
  - 深度学习
# categories:技术积累、论文阅读、问题解决、算法刷题、其他等四个条目，其余放在tags里面。

# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
#link:
# 图片链接，用在open graph和twitter卡片上
# Image source link that will use in open graph and twitter card
#imgs:
# 在首页展开内容
# Expand content on the home page
#expand: true
# 外部链接地址，访问时直接跳转
# It's means that will redirecting to external links
#extlink:
# 在当前页面开启或关闭评论功能
# Switch to enabled or disabled comment plugins in this post
#comment:
#  enable: false
# 开启文章目录功能
# Enable table of content
#toc: false
# 绝对访问路径
# Absolute link for visit
#url: "蚂蚁or蜜蜂（迁移卷积神经网络）.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

蚂蚁or蜜蜂（迁移卷积神经网络）

<!--more-->
## 迁移大型卷积神经网络实验 
- 使用数据集hymenoptera 
- 下载地址 [hymenoptera传送门](https://download.pytorch.org/tutorial/hymenoptera_data.zip "hymenoptera传送门") 
- 运行环境： 
`system='Linux', node='0c6f88beb51d', release='4.19.112+', version='#1 SMP Thu Jul 23 08:00:38 PDT 2020', machine='x86_64', processor='x86_64'` 

- 代码  
```python 
import torch 

import torch.nn as nn 
import torch.optim as optim 
from torch.autograd import Variableimport torch.nn.functional as F 
import numpy as npimport torchvision 
from torchvision import datasets,models,transforms 
import matplotlib.pyplot as plt 
import time 
import copy 
import os
data_dir = '/content/drive/MyDrive/pytorch_learning/hymenoptera_data' # 数据存储总路径 
image_size = 224  #图像大小为224*224像素 
# 加载过程对图像进行如下操作 
# 1.随机从原始图像中切下来一块224*224大小的区域 
# 2.随机水平翻转图像# 3.将图像的色彩数值标准化
train_dataset = datasets.ImageFolder(os.path.join(data_dir, 'train'), 
transforms.Compose([ 
  transforms.RandomResizedCrop(image_size), 
  transforms.RandomHorizontalFlip(),                    
  transforms.ToTensor(),                    
  transforms.Normalize([0.485,0.456,0.406],[0.229,0.224,0.225])                    
  ]),                    
  ) 
  # 加载校验数据集 
val_dataset = datasets.ImageFolder(os.path.join(data_dir, 'train'),                                     
  transforms.Compose([                                         
  transforms.Resize(256),                                         
  transforms.CenterCrop(image_size),                                        
  transforms.ToTensor(),                                         
  transforms.Normalize([0.485,0.456,0.406],[0.229,0.224,0.225])                                     
  ]),                                    
  )
  # 创建相应数据加载器
  # 读取数据中分类类别数
num_classes = len(train_dataset.classes)
# 模型迁移
net = models.resnet18(pretrained=True)
for param in net.parameters():    
    param.requires_grad = False# 预训练方式迁移num_ftrs = net.fc.in_features # ResNet18最后全连接层的输入神经元个数
    net.fc = nn.Linear(num_ftrs, 2) # 拿掉ResNet18的最后两层全连接层，替换成输出单元为2的全连接层criterion = nn.CrossEntropyLoss()
    optimizer = optim.SGD(net.parameters(),lr=0.0001,momentum=0.9)
    use_cuda = torch.cuda.is_available()  # 判断是否可以使用GPU进行加速
    dtype = torch.cuda.FloatTensor if use_cuda else torch.FloatTensor
    itype = torch.cuda.FloatTensor if use_cuda else torch.FloatTensor
    net = net.cuda() if use_cuda else net
def rightness(predictions, labels):    
    pred = torch.max(predictions.data, 1)[1] # 对于任意一行（一个样本）的输出值的第1个维度，求最大，得到每一行的最大元素的下标    
    rights = pred.eq(labels.data.view_as(pred)).sum() #将下标与labels中包含的类别进行比较，并累计得到比较正确的数量    
return rights, len(labels) #返回正确的数量和这一次一共比较了多少元素
if __name__=="__main__":
            
    train_loader = torch.utils.data.DataLoader(train_dataset,batch_size=4,shuffle=True,num_workers=4)    
    val_loader = torch.utils.data.DataLoader(val_dataset,batch_size=4,shuffle=True,num_workers=4)    
    print(use_cuda)    
    record = [] # 记录准确率等数值的容器    
    num_epochs =20    
    net.train(True)    
for epoch in range(num_epochs):        
    train_rights = []        
    train_losses = []        
    for batch_idx, (data,target) in enumerate(train_loader):            
        data, target = Variable(data), Variable(target)            
        if use_cuda:                
          data, target = data.cuda(),target.cuda()            
        output = net(data) # 完成一次预测            
        loss= criterion(output,target)            
        loss =loss.cpu() if use_cuda else loss            
        optimizer.zero_grad() # 清空梯度            
        loss.backward()            
        optimizer.step()            
        right = rightness(output,target)            
        train_rights.append(right)            
        train_losses.append(loss.data.numpy())            
        if batch_idx %100 == 0:                
          print('MyEpoch [{}/{}], Step [{}/{}], Loss: {:.4f}'.format(epoch + 1, num_epochs, batch_idx, len(train_loader), loss.item()))                
          print('时间戳', time.strftime("%Y-%m-%d %H:%M:%S"))
```

## 环境对比
#### colab 平台
- 配置 ：system='Linu', node='0c6f88beb51', release='4.19.112+', version='#1 SMP Thu Jul 23 08:00:38 PDT 2020', machine='x86_64', processor='x86_64'
GPU显存:15843721216字节
![xPGEjS.png](https://s1.ax1x.com/2022/09/20/xPGEjS.png)
#### 本地机器CPU
- 配置：system='Windows', node='DESKTOP-7845150', release='10', version='10.0.19041', machine='AMD64', processor='AMD64 Family 21 Model 101 Stepping 1, AuthenticAMD'
![xPGtHJ.png](https://s1.ax1x.com/2022/09/20/xPGtHJ.png)
## 后记
- GPU在科学计算上，真的不知道甩了CPU几条街啊。果然好设备才是生产力发展的要素。今天实验了好几个平台，百度AI只能用自己的框架，取消了对pytorch等深度学习 框架的支持，另外的，也都是比较“便宜”吧，白薅羊毛的平台，也都是有诸多限制，综合比较而言，这个calob还是不错的。
