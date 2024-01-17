---
layout:     post
title:     科学数据处理笔记
subtitle:   ~懒惰的智慧~
date:       2020-04-13
author:     Glider
header-img: img/废弃窑洞.jpg
catalog: true
tags:
    - matplotlib
    - numpy
    - python
    - blog
---
# 前言

数据处理这块有时需要直观的查看, 便于分析代码的正确性与数据的结构.
之前写了很多关于matplotlib的代码, 可惜一直没有进行笔记的整理. 今天心血来潮, 记录一下以前踩过的坑与脚本备份

## 矩阵进行图像显示(包括了矩阵翻转, 热力图显示)

```
import numpy as np
import matplotlib.pylab as plt

a = np.random.randint(0,2,(10,10))
b = np.flip(a,0)

fig, ax = plt.subplots(2,1)
ax0 = ax[0].imshow(a,cmap = 'binary')  #binary是1黑0白,  gray是相反的
ax1 = ax[1].imshow(b,cmap = 'binary')
fig.colorbar(ax0,ax = [ax[0],ax[1]])
plt.show()
```

## 矩阵进行升采样(扩展)

```
def change_pix(matrix,dpi = (100,100)):
    new_im = Image.fromarray(matrix)
    new_im = new_im.resize(size=dpi, resample=Image.BOX)
    matrix_changed = np.asarray(new_im)
    return matrix_changed

```

# 矩阵数据统计直方图

```
a = np.random.randn(10000)

plt.hist(a, bins=500, edgecolor='None', facecolor='black')
plt.show()
```

# 结语

以后会在这里更新.
