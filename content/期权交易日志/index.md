+++
title = "期权交易日志-1"
description = "挨打……"
date = 2024-4-12
updated = 2024-4-12
draft = false

[taxonomies]
tags = ["交易","期权","加密货币"]

[extra]
math = true
math_auto_render = true
keywords = "交易"
toc = true
+++

# 近期的一次交易教训

最近一直在玩加密的期权，由于资金小，只能做买方……

买方很蛋疼的一点就是胜率很低，期权的本质是在交易波动率，卖方天然的就有溢价，所以当买方进场就得交1-2个点的入场费。

## 当前的策略

1. 买隔两个月的稍微实值一到两个档的期权（theta损耗小），一个月内换仓或者平仓。
2. 在区间内进行delta对冲（+-10%），赚点gamma收益减少theta损失，并赌行情突破区间，突破后择时止盈。
3. 盈利内容包含：delta对冲的gamma收益，行情突破的收益(delta与vega)。

## 存在的问题

1. 这个策略非常依赖择时进入和退出（买方好像都这样……）
2. delta对冲时需要考虑波动率偏斜、对冲标的物本身的变化（永续的费率，交割的升贴水）

## 交易复盘

交易所是某安，标的是eth，购入的日期为24-4-1，行权日期为24-5-31

当时的波动率偏斜很离谱，市场处于牛市前期，所以斜率非常陡，


# 图片

{{ img(src="./img/huashou1.jpg" alt="Ferris is Happy" h=300 w=300) }}

<!-- ![画手](./img/huashou1.jpg) -->


# 代码

```rust
fn main() {
    println!("Hello, world!");
}
```

# 表格

| 1 | 2 | 3 |
| - | - | - |
| 4 | 5 | 6 |
| 7 | 8 | 9 |

# 公式

$$
f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi
$$

# 链接

[百度](https://www.baidu.com)
