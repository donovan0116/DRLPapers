1. 自动化所，解决大规模baseLLM的agent的决策制定，其中agent的数目不固定。为了解决合作问题。使用AC框架，中心化critic，分布式actor
2. natural language-based reinforcement learning，引入task language概念，将nl翻译为agent能够理解的tl，然后执行，并且具备tl生成的模块
3. 腾讯AIlab，训练新的联盟学习玩星际，使得智能体有目的性的挖掘自身联盟的弱点（在星际中，不完全或不完美信息可以被侦察出来，与麻将不同），并激励智能体更倾向于侦察，通过更少的资源训练更好的AI。
4. ICML2021，COPA算法，教练带球员，1)对教练和球员都采用注意机制;2)提出一个变分目标来规范学习;3)设计一种自适应的沟通方式，让教练决定何时与球员沟通。motivation：协调成员动态变化的队伍。
5. 腾讯AI Lab，训练以人为本的智能体和人类组成的多智能体系统。（**或许可以结合偏好强化学习**）motivation：以自己为中心的智能体只能和人类一起走向胜利，但不能以人类为中心。例如都是打王者胜利，但ai抢人类人头会让人类玩家不爽。这里加上了“以人类为中心”的增强。方法：首先人类根据自己的目标创建表现，称为“baseline”；训练value网络来评估人类玩家达到目标得到的return。其次训练gain网络评估agent以人为本为人类带来的积极gain，最后根据agent产生的积极性gain对agent微调。
6. 新加坡NUS，FRL框架。motivation：rl面临训练样本量不足且没法分享的问题，frl可以使得rl智能体相互分享轨迹，增强学习成功的可能性。该文章提出的框架解决了FRL收敛性分析和系统容错率（容错率包括agent随机故障和可能的攻击）问题。
7. Deepmind，RLHF。motivation：在没有程序化奖励模型的基础上训练agent。由人类的偏好指导agent的训练方向。方法：基于模仿学习baseline，通过人类偏好训练建立reward model

> 目前为止，认为HAC&MARL可以分为两类：
>
> 1. 由人类参与指导，如偏好强化学习、RLHF、AI lab的以人类为中心。旨在训练中就引入人类的部分
> 2. 不由人类指导，完全AI内部自行博弈，如魔改架构（COPA），相互博弈等。
> 3. 人类在训练过程不参与指导，但是在执行过程AI需要理解人类的指令。该过程可以与LLM相结合

8. 人大高瓴，LLM-based HAC，motivation：提出一种基于LLM的与人类进行协作的智能体，并且该智能体能够判断什么时候该让人类介入。人类把握大方向，agent实现子领域。
8. 清华，zero-shot cooperation assume human bias。motivation：已有的zero-shot不需要人类数据就能训练出MARL的agent，但是这种训练只是根据环境reward建模，人类的偏好和环境的reward model不一致。本文借助人类偏见（bias），生成一个有效的策略池。（之前为了防止self-play进入过拟合，多个智能体一起训练形成一个策略池，然后智能体针对策略池自适应调整，预防进入次优）方法：在第一阶段构造策略池时就将隐藏的人类回报放入。
8. US Army，测量MARL系统中多智能体协作的质量。方法：提出一种指标CCM，将智能体的一段行为视为时间序列，然后embedding。embedding之间的影响就是多智能体协作质量的指标。
8. MIT，motivation：研发一个框架，将人类和ai的行为对齐，有助于生成式ai的发展。方法：放弃使用传统的state和action，而是使用更高级的task、行为流形behavioral manifold。通过完成task、比较人机行为来对齐。本质上还是训练期就人机交互。
8. 弗吉尼亚大学，开发对MARL的解释性框架，让人类理解MARL系统的策略。方法：将策略罗列出来；根据人类的自然语言问询来过滤出人类想查询的具体策略，并给出。
8. 微软研究院与滑铁卢大学，motivation：以人类为中心的AI在合作时接受人类的自然语言指示，AI根据这些问题理解、提问澄清和执行。

open speil google football