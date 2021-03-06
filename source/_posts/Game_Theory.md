title: Game Theory(from Coursera)'s Summary
tags:
  - Mathematics
  - Coursera
date: 2014-12-08 20:38:43
catagories:
---
最近没事又跑到C站补了博弈论的公开课。其实讲得很少也很浅。不过这类内功修炼下还是有点感觉的，时不时会在论文中突然就出现个纳什均衡帕累托最优什么的呢。

##Concepts
**Strategy**: 某个Player可以做的选择
**Action**: 所有Player作出的Strategy的某个交集
**Best Response**: 这名玩家在当前情况下得益最高的选择(可能有等值的好几个)
**Nash Equilibrium**: 没有玩家愿意偏离的策略集(注意是情况已经出现，对方策略必定已知。当前情况下全是Best Response，没有明显更好的选择了)
**Strictly Dominant Strategy**: 这个选择比其他选择在每一种情况下值都更优。被dominate的策略是可以直接扔掉不要的
**Weakly Dominant Strategy**: 相比上面可以是某个更优其他同等。扔掉被它dominate的可能会连带扔走其中一个纳什均衡哦，虽然肯定不是最后一个)
**Pareto Optimality**: 没有其他策略Pareto Dominate(某些得益更高，其他得益也至少相等)的策略

<!--more-->

##Normal-Form Games
最简单的用表格表示的博弈
**Pure Strategy**
不带概率，选定某个策略
**Mixed Strategy**
Mixed Strategy就是在自己手上的几个Pure Strategy中叠加上概率分布。通过计算期望判断优劣。
这种情况下，一种纳什均衡，就要使得别人在自己的概率下没法区别他的策略。比如横向的策略乘以竖向的概率(该格子出现概率)，各行之间相等。
Mixed Strategy均衡并不包含Pure Strategy，因为Pure Strategy均衡的策略至少对于某个人来说明显更好，而不仅仅是相等。
Mixed Strategy中也有Strictly Dominant Strategy，比如两种策略中无论怎样的概率分布都比第三种策略的收益好。

##Extensive-Form Games
为了区分先后顺序，画成树状。
**Perfect information Extensive-Form Games**
知道完整的历史信息。每个点是一个独立的选择。所有点的选择的集合就是策略，纯策略数量就是($2^{选择点数量}$)。
一颗子树是一个Subgame。Subgame均衡的纳什均衡才可信(与Subgame不均衡的相比往往是在其他走不到的子树上有区别)。据此可以从叶节点倒推出均衡状况。
**Imerfect information Extensive-Form Games**
相比来说有了等价结点的概念，Player只能知道目前在某一类等价节点，无法区分具体位置

##Repeated Games
近乎无限多次的博弈。
这个时候求收益方法 1.求均值的极限 2.求带(0,1)内指数加权和的极限
后者可以看作是早期的博弈比后期的博弈重要，也可以看作是博弈每轮都有个概率p在这轮结束。
虽然彻底的均衡也是一次游戏的纳什均衡，不过如果是通过加权和算的收益而且权p大于某个阈值，可以通过协商，制定惩罚方法，先合作用对双方来说都有更高收益的非均衡策略（权p太小，会导致单次偏离的收益比后面所有加起来的均衡收益极限都高）。
惩罚1 grim trigger strategies：一旦对方偏离一次，自己就永远偏离，回到纳什均衡。
惩罚2 tit for tat：对方偏离一次，下回合自己偏离一次，然后继续合作
**Folk's Theorm**
不小于至少可以取得的(往往单次均衡中的)收益的收益值都enforceable。对各个Action施以概率分布，加起来可以取得的收益都是feasible。既是enforceable又是feasible就是某个纳什均衡中的值啦。

##Bayesian Games
同一个Action，Player有不同的收益，这里有一个变化概率的情况。可以看作每个Player在他的Game集中分布，或Player在他的类型集中分布。
如果只是一次游戏，本质和Mixed Strategy差不多，都是计算期望

##Coalition Games
Player组队有组队的收益。
有两种推荐的所有玩家(不是某个组内)的收益分配方案
1. Shapley Value，考虑所有组队顺序情况下单个人的贡献。即全部组队排列下这个人的边缘贡献和/全排列数。
2. Core Value，合作收益分到每个子集，都不低于子集本身能取得的收益的分配方案(对于要么有收益要么没有的simple game，就是关键的不可或缺的Player分收益(不一定平分)，其他Player收益为0)

***

下面是 Game Theory 2 的内容
##Basis and Voting(Social Choice)
最好以“投票”这个场景来理解下面内容
**Linear Order**: 下面提到这个词是指完备的、可传递的（即每个人对所有候选人都有完整的偏好顺序）
**Social Choice Function**: Linear Order集（即所有人的偏好）映射出outcome集（某（几）个候选）
**Social Welfare Function**: Linear Order集映射出Linear Order（偏好映射出全序）

几个属性
Condorcet Consistency: 孔多塞胜者(两两对决)一定是最终胜者
【相对于Social Welfare Funcition】
**Pareto Efficiency**: 全部人都一样的偏好对作为输入，最后结果也一定和输入一样
**Independent of Irrelevant Alternatives**: 最后结果的偏好对，只取决于输入的中这两个人之间的偏好对（即维持AB之间偏好所有输入不变，结果不变）
【相对于Social Choice Function】
**Weak Pareto Efficienct**: 全部人都更偏好于一对的某个，另一个一定不会被选
**Monotonicity**: 保持对支持获胜者的所有偏好对输入，结果一定维持不变

**Arrow's Theorem**: 三个以上候选人，同时满足PE和IIA的机制，一定有Dictator(他怎么选、怎么改，最终结果一定按照他的来，虽然他自身不一定知道)
**Muller-Satterthwaite theorem**:WPE和Monotonicity的SCF必定dictatorial

顺带提到几种投票方式：Plurality(一人一票), Cumulative rating(一人有限多选), Approval voting(一人无限多选), Plurality with elimination(末尾淘汰选多轮), Borda Rule(带权重选票), Successive Elimination(两两对决累计)

##Mechanism Design

Mechanism: Action到Outcome的映射方式。
Utility function: 每个agent的收益。"private"的话，和其他agent的$u(\theta)$无关。可以拆分输入outcome为choice和payment两部分(Tranferable  Mechanism)。前一部分也叫"Valuation function"。而有了payment，机制受害者就可以从获益者那里得到补偿。

属性：
**Truthful Mechanism**: agent的preference是怎样，他表达出来就怎样，说真话是dominant strategy(常见反例是borda rule中，最喜欢的选不上，为了次喜欢的而不是最讨厌的被选上，昧着心思投次喜欢的。可以观察单个agent能否操纵什么来判断)
**Direct Mechanism**: 一轮结束，一次声明，没有秘密(一定知道agent类型)
**Pareto-efficient Mechanism**: 所有Valuation function相加最大(注意没payment)
**Budged-balanced Mechanism**: 所有payment相加为0。松弛为*weak*，则大于等于0。
**Individual-Rational Mechanism**: 参与机制的收益期望大于等于0(ex-interim) / 一定大于0(ex-post)
**Revenue Maximization/Minimization**: payment总额最大 / 最小化(大于等于0的情况下)
**Maxmin Fairness**: 让收益最低的情况的收益额尽可能高。
**Price of Anarchy Minimization**:  Price of Anarchy指最坏情况下，最优均衡下的Social Welfware与最坏均衡下的比率。最小化它来尽可能接近Efficient (PoA=1)的状况。

理论：
**Revelation Principle**: 所有social choice function都可以得到一个truthful, direct的机制实现（核心思想是这个机制本身就帮agent去cheat，最大化agent利益。注意将非T/D的机制转化为T/D的机制不一定能保留所有均衡态）。
**Gibbard-Satterthwaite's Theorem**: 如果Truthful对所有人所有情况都是dominant，机制必定Dictatorial（松弛Dominant为Bayesian-Nash均衡，或者用有结构的Preference就好了）

##Vickery-Clarke-Groves Mechanism

**Groves Mechanism**：选让utility总和最大的选项，i的payment是 其他人{没有i时的选项的函数-有i后总utility}，即 $h_i(\hat{v}_{-i})-\Sigma _{j\ne i}\hat{v_j}(x(\hat{v}))$
**VCG Mechanism**：跟上面一样，选让utility总和最大的选项。payment是 其他人的{没有i时的总utility-有i后总utility}。即上面$h_i(\hat{v}_{-i})=max_x \\{\Sigma _{j\ne i}\hat{v_j}(x)\\}$。一般VCG收益大于零。
**Green-Laffont Theorem**：所有人都可以有任意preference顺序的话，只有Groves Mechanism既effcient，又truthful。

**VCG与ex-post individual rationality**：要满足choice-set monotonicity(去掉任意agent不会增加新的选项)和No negative externalities(不考虑i做的选项不会让i的uitility变负)
**VCG与weakly budget balance**：要满足no single agent effect(去掉i后不会必定导致总utility下降)

**Myerson--Satterthwaite's Theorem**: buyer-seller问题上，存在一种buyer-seller分布，使得没有机制同时efficient, weakly budget balance和interim individual rationality

##Auctions
感觉就是讨论了一下Auction类的机制
Auction有很多种，包括常见的Bidder自己喊价格的English，Auctioneer抬价格的Japanese，Auctioneer降价格的Ducth，秘密出价(seal-bid)的First-price(付最高出价)，Second-price(付第二高出价)，All-pay(所有人付自己出价)。
对于bidder：其中，Second-price实质上是VCG，truth-telling是(weakly)dominant。用下面的理论，Japanese和English也类似，是dominant；first-price和Ducth不是，可以考虑参加拍卖的人数而相应降低出价，做赢的概率和出价的trade-off。value在正态独立分布下，合理的出价是$\frac{n-1}{n}v_i$
对于seller：上面revenue全部一样，见下面理论

**Revenue Equivalence Theorem**：bidder都是risk-neutral（愿意通过期望考虑问题），value同分布时：如果两个机制 均衡时分配结果一样，且value=0的人期望收益为0，这两个机制必定有同样的收入期望，每个agent的期望支出相同。

**Optimal Auction**：最大化卖家收入的拍卖。卖家可以通过牺牲efficiency(有出价不卖出去或者不卖给最高出价的人)，设reserve price来实现(前提是individual rational/risk-neutral和分布已知)。
**Virtual Valuation**: $\Phi_i(v_i)=v_i-\frac{1-F_i(v_i)}{f_i(v_i)}$，上面是累积分布函数，下面是概率密度函数。如果他是单调增长的， 最好的reserve price就是V.V.=0的时候。（注意即使R.P.是分布下界，对可能出现的只有一个人的拍卖也有效）
**Myerson Theorem**：Single-good下，direct机制里，Optimal Auction即把东西卖给V.V.最大的人，且V.V.最大的人支付第二高V.V.。

***

##后记

结果最后写起来更像是笔记而不是一个完整的故事哈哈*^_^*下次再努力吧。
这个公开课和我专业的知识有些偏差，不过回想起来呐，以前总是纠结为什么囚徒困境的均衡结果会是大家都要受轻刑，一个not efficient的，次差的结果。是不是人性的自私最终总会导致一个不太好的结局，引领社会走向黑暗？后来再学到Repeated Games，看到怎么建立协商的机制，来达到最终总体的最佳结果，茅塞顿开了呢。所谓的道德伦理，也是先贤们考虑到人性的自私，而建立起来的一种约束机制，引领我们的社会在Repeatted Games中走向更好的均衡吧。想想还是很感慨呐。

Course 2本来是因为在百度做的内容比较偏广告竞价机制的设计，所以去看了一下的。不过机制这一块果然好大，Course 2本身也不是很有系统性，偏优秀机制的举例更多？并不是很有心思完整地梳理了，他日用到再补充吧:D
