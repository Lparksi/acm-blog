---
{"dg-publish":true,"permalink":"//2025/2-2/f/"}
---

#数论/位运算/多种位运算复和

 
---
# 题目
$\hspace{15pt}$对于给定的区间 $l$ 到 $r$，从中选取两个整数 $x$ 和 $y$，使得下式成立：

  
$x + y = (x \operatorname{or} y) + (x \operatorname{and} y) + (x \operatorname{xor} y)$  
  

$\hspace{15pt}$求解有多少对不同的满足条件的 $x, y$。  
  
$\hspace{15pt}$在本题中，$\operatorname{or}$ 代表按位或运算、$\operatorname{and}$ 代表按位与运算、$\operatorname{xor}$ 代表按位异或运算。如果您需要更多位运算相关的知识，可以参考 [**OI-Wiki的相关章节**](https://oi-wiki.org/math/bit/#%E4%B8%8E%E6%88%96%E5%BC%82%E6%88%96)。

---
# 输入&输出
$\hspace{15pt}$每个测试文件均包含多组测试数据。第一行输入一个整数 $T\left(1\leqq T\leqq 2 \times 10^5\right)$ 代表数据组数，每组测试数据描述如下：  
  
$\hspace{15pt}$在一行上输入两个整数 $l, r\left(0\leqq l\leqq r\leqq 10^{18}\right)$ 代表求解的区间。
$\hspace{15pt}$对于每一组测试数据，在一行上输出一个整数，代表满足条件的不同的 $x, y$ 的对数。

---
# 样例

## 输入
```
2
0 0
1 3
```
## 输出
```
1
3
```
## 说明
  
$\hspace{15pt}$对于第一组测试数据，$x$ 和 $y$ 仅能取到 $0$；而 $0 \operatorname{or} 0 = 0$、$0 \operatorname{and} 0 = 0$、$0 \operatorname{xor} 0 = 0$，所以满足条件。

---
# 思路

通过 [[知识库/数论/位运算#多种类型位运算的技巧\|结论]] 将问题转化。

$(x \operatorname{and} y) + (x \operatorname{or} y) = x + y$ 
现在只需要找到  $x \operatorname{xor} y = 0$ 的所有 $x$和$y$ 显然仅当$x=y$时成立，于是问题变为找到区间内有多少个唯一元素，即区间长度

---
# 做法
输出 $r-l+1$即可。

---

# 代码

```cpp

```
---
# 反思

---
