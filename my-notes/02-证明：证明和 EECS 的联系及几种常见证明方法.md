---
date: 2025-09-16
tags: [离散数学, 学习笔记]
author: Zeeh-Lin
---

# 02-证明: 证明和 EECS 的联系及几种常见证明方法

## *Proofs* 和 EECS 的关系

>Proofs are very powerful and are in some ways like computer programs. Indeed, there is a deep historic link between these two concepts that we will touch upon in this course — the invention of computers is intimately tied to the exploration of the idea of a mathematical proof about a century ago.  

note02 中给出两个例子，用来说明“what types of ‘computer science-related’ statements might we want to prove?  ”。

1. Does program P halt on every input? 
2. Does program P correctly compute the function f (x), i.e. does it output f (x) on input x, for every x?   

“证明”的力量在于：我们可以用“有限”的事实，证明一个具有“无穷”多种情况的真实性。在数字电路或程序设计中，我们同样关心：一个电路或程序是否在任意情况下都成立。



## 直接证明法

> **Direct Proof**
> Goal: To prove P =>Q
> Approach: Assume P
>
> ...
>
> Therefore Q




## 逆否证明法

>**Proof by Contraposition** 
>
>Goal: To prove P => Q. 
>
>Approach: Assume ~Q. 
>
>... 
>
>Therefore ~P 
>
>Conclusion: ~Q => ~P, which is equivalent to P => Q.

用逆否证明法可以证明**鸽巢理论**：令n、k为正整数。把n个鸽子蛋放进k个鸽子巢里。如果n>k， 那么至少有一个鸽子巢装了多个鸽子蛋。

当物体在盒子中的排列方式很复杂时，这个理论可能并不显而易见。下面给出一个例子：人类头发数量的平均值大约是100000根，因此假设一个人头发不超过500000根。旧金山的人口超过800000。根据鸽巢理论（人口数是鸽子蛋，头发数量是鸽子巢），旧金山至少有两个人拥有相同的头发数量。

在这个例子中，“旧金山至少有两个人拥有相同的头发数量” 这个结论的得出，并不依赖于头发的具体分布方式。



##  反证法

反证法，亦称归谬法。典型流程如下：

> **Proof by Contradiction**
> Goal: To prove P.
> Approach: Assume $\neg P$
>
> ​			...
> ​			R
>
> ​			...
>
> ​			$\neg R$
> Conclusion: $\neg P \implies \neg R \and R$, which is a contradiction. Thus, P.

反证法成立的原因如下：
$$
\neg P \implies \neg R \and R \equiv False\\
\text{the contrapositive of this statement is:} \quad True \implies P
$$
接下来给出了两个使用反证法的例子：

1. 证明：有无穷多个素数
2. 证明：$\sqrt{2}$是无理数

证明过程使用了两个引理，证明过程略。

值得注意的是，**为什么上面两个例子可以使用反证法？**原因是，它们都试图证明一些事情**不存在**。

例如：第一个例子在证明，**不存在**一个最大的素数。第二个例子在证明，**不存在**两个整数a和b，使得$\sqrt{2} = \frac{a}{b}$。

通常情况下，直接证明这类命题很复杂，而采用反证法可以简化这个过程。



## 分类证明法

给出一个例子来说明分类证明法，并引出**非结构性证明**。



## 证明中的常见错误

### 循环证明：不要用结论反推结论

例如：P is "-2 = 2".	P => (4=4) => True

上面这个证明， 我们证明了P=>True，但这不等于P本身是True。根据蕴含的定义，当P为False时，P=>True这个命题永远为真。

### 变量为0

典型的例子是：

假设x=y， x(x-y) = (x+y)(x-y)。不能得到x=x+y，因为x-y为0，等式两边不能同时除0。

### 当心负数和不等式

错误示范：$-2 \leq 1, \text{两边平方}, 4 \leq 1$

值得注意的是：$a\leq b \not\Rightarrow |a|\leq |b|$



## 再论 *Proofs* 和 EECS 的关系

我们有时引入**引理**，来将一个大的证明分解成几个小的**引理**。这个理念可以在程序中得到体现：将一个大的程序分解成几个小的子程序。同时，尽量保证各个引理（子程序）具有通用性，这样他可以被复用。这和verilog语言中`module`的理念相通，把一个大的电路分解成数个电路模块分别设计，这是一种常见的工作流程。
