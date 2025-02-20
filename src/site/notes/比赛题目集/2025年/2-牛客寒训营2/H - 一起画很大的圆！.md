---
{"dg-publish":true,"permalink":"//2025/2-2/h/"}
---


#数学/圆/三点确定最大圆
 
---
# 题目
$\hspace{15pt}$牛可乐正在研究==二维平面==。现在，他已经划定了一个矩形区域，左侧边界为 $x=a$，右侧边界为 $x=b$，下侧边界为 $y=c$，上侧边界为 $y=d$，他想要在四条直线所围成的矩形的**边界上**找到三个不同的整数点 $A,B,C$，使得过这三个点画出的圆半径最大。  
$\hspace{15pt}$请你帮助他实现！  

---
# 输入&输出
$\hspace{15pt}$每个测试文件均包含多组测试数据。第一行输入一个整数 $T\left(1\leqq T\leqq 100\right)$ 代表数据组数，每组测试数据描述如下：  
  
$\hspace{15pt}$在一行上输入四个整数 $a,b,c,d \left( -10^6 \leqq a,b,c,d \leqq 10^6;\ a < b;\ c < d \right)$ 代表牛可乐选定的区域左、右、下、上边界。

$\hspace{15pt}$对于每一组测试数据，输出三行。每行输出两个整数，代表你所选定点的横纵坐标。你需要确保这三个点位于区域边界上，且过三点能作出一个合法的圆（互不相同、不共线）。  
  
$\hspace{15pt}$如果存在多个解决方案，您可以输出任意一个，系统会自动判定是否正确。注意，自测运行功能可能因此返回错误结果，请自行检查答案正确性。

---
# 样例

## 输入
```
2
-1 1 1 2
0 1 0 1
```
## 输出
```
-1 1
0 2
1 2
0 0
0 1
1 1
```
## 说明
	对于第一组测试数据，一共可以作出如下图所示的四个合法圆，我们可以证明，实线的圆是其中最大的。

[[_attachments/f0473ffc1ea8ad0484a0a696a4b0a1a0_MD5.jpeg|]]
![_attachments/f0473ffc1ea8ad0484a0a696a4b0a1a0_MD5.jpeg](/img/user/_attachments/f0473ffc1ea8ad0484a0a696a4b0a1a0_MD5.jpeg)

---
# 思路

要使得到的圆尽可能大，需要 ==**这三个点尽可能在一条直线上**==（接近）
<svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
  <!-- 分散的三个点形成小圆 -->
  <circle cx="50" cy="150" r="3" fill="red"/>
  <circle cx="150" cy="150" r="3" fill="red"/>
  <circle cx="100" cy="50" r="3" fill="red"/>
  <circle cx="100" cy="112.5" r="62.5" stroke="blue" fill="none"/>
  <polyline points="50,150 150,150 100,50" fill="none" stroke="#999" stroke-dasharray="4"/>
  
  <!-- 接近共线的三个点形成大圆 -->
  <circle cx="50" cy="30" r="3" fill="green"/>
  <circle cx="150" cy="30" r="3" fill="green"/>
  <circle cx="100" cy="33" r="3" fill="green"/>
  <circle cx="100" cy="-1160" r="1190" stroke="orange" fill="none" stroke-width="0.5"/>
  <polyline points="50,30 150,30 100,33" fill="none" stroke="#999" stroke-dasharray="4"/>

  <!-- 标注说明 -->
  <text x="10" y="20" font-size="12">三点分散时</text>
  <text x="100" y="130" font-size="10" fill="blue">半径62.5</text>
  <text x="10" y="40" font-size="12">三点接近共线时</text>
  <text x="100" y="-1100" font-size="10" fill="orange" transform="scale(1,-1)">半径≈1190</text>
</svg>
- 长边上取两点，短边上取离长边最近的点
考虑一下三种情况
1. 正方形
![](https://img0.parksi.top/ShareX/2025/01/%25iS3IcRnELi.webp)
2. 竖边长的长方形
![](https://img0.parksi.top/ShareX/2025/01/%25QLAwGL888p.webp)
3. 横边长的长方形
![](https://img0.parksi.top/ShareX/2025/01/%25w8YZBXHTwV.webp)

---
# 做法
综上：
- 若竖直边界 >= 水平边界 取 左下角点 + 左下角点向上平移 1 + 左上角点向右平移 1
- 若竖直边界 < 水平边界 取 左上角点 + 左上角点向右平移 1 + 右上角点向下平移 1

即 **长边上选一个端点 + 一个离该端点最近的点，短边上选取一个点，且尽可能的靠近长边**

---

# 代码

```cpp
#include<bits/stdc++.h>
#define endl '\n'
typedef long long ll;
using namespace std;
// 赛后
void solve() {
	ll a,b,c,d;
	cin >> a>>b>>c>>d;
	if(b-a<d-c) { // 竖直边界大
		cout<<a<<" "<<c<<endl; //左下角点
		cout<<a<<" "<<c+1<<endl; //左下角点向上平移1
		cout<<a+1<<" "<<d<<endl; //左上角点向右平移1
		return;
	} else { // 竖直边界小
		cout<<a<<" "<<d<<endl; //左上角点
		cout<<a+1<<" "<<d<<endl;//左上角点向右平移1
		cout<<b<<" "<<d-1<<endl;//右上角点向下平移1
	}
	
	
}

int main() {
	ios::sync_with_stdio(0);
	cin.tie(0), cout.tie(0);

	int t=1;
	cin >> t;
	while(t--) solve();
	return 0;
}
```
---
# 反思

---
要发散思维