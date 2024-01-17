+++
title = "文章模板"
description = "copy工程师"
date = 1970-01-01
updated = 1970-01-01
draft = false

[taxonomies]
tags = ["博客"]

[extra]
math = true
math_auto_render = true
keywords = "博客"
toc = true
+++


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
|---|---|---|
| 4 | 5 | 6 |
| 7 | 8 | 9 |

# 公式

$$
f(x) = \int_{-\infty}^\infty\hat f(\xi)\,e^{2 \pi i \xi x}\,d\xi
$$

# 链接

[百度](https://www.baidu.com)