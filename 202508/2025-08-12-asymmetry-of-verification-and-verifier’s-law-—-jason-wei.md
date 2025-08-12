# Asymmetry of verification and verifier’s law — Jason Wei
- URL: https://www.jasonwei.net/blog/asymmetry-of-verification-and-verifiers-law
- Added At: 2025-08-12 05:55:09
- [Link To Text](2025-08-12-asymmetry-of-verification-and-verifier’s-law-—-jason-wei_raw.md)

## TL;DR
验证不对称性指AI中验证答案比求解更容易的现象，分为验证远易、对称、更难三类。关键通过优化验证效率适应强化学习，核心是验证者法则：要求目标明确、高速批量验证等五项属性。满足这些的任务将被AI攻克，推动数字世界加速进化。总结自强化学习背景下的验证问题分析。

## Summary
验证不对称性指某些任务验证答案比求解答案更容易的现象，随着强化学习（RL）的广泛应用，这已成为AI领域关键概念。

### 一、验证不对称性的类型
1. **验证远易**  
   - **典型实例**：数独/填字游戏（求解需尝试多种组合，验证只需检查约束）、开发Instagram级应用（开发耗时数年，验证功能只需用户简单操作）、[BrowseComp问题](https://openai.com/index/browsecomp/)（求解需浏览数百网页，验证可直接搜索确认答案）
   - **本质特征**：问题约束明确，验证逻辑简单
2. **验证对称**  
   - 如900位数加法：验证耗时≈求解耗时
   - 数据处理代码审查：理解他人代码耗时≈自写代码
3. **验证更难**（符合Brandolini定律）  
   - 事实核查论文（验证时间 >> 撰写时间）
   - 科学假说验证（提出"仅吃野牛西兰花饮食"简单，验证健康效果需数年）

### 二、优化验证效率的方法
通过前置研究增强验证不对称性：
- **标准答案辅助**：如竞赛数学题用答案密钥秒验
- **测试用例覆盖**：LeetCode等平台用全面测试集自动化验证代码
- **局部优化**：如"列举荷兰球星"任务借助名单库，但验证仍需人工核对

### 三、验证者法则的核心
**定律**：AI解决任务的训练难度 ∝ 任务可验证性。满足五项属性的可解任务终将被AI攻克：
1. **目标明确**：优劣解标准共识化
2. **高速验证**：单解验证≤秒级
3. **批量验证**：支持并行化验证
4. **低噪声**：验证结果与解质量强相关
5. **连续奖励**：能对多解进行质量排序  
*注：主流AI基准（如图像分类）均满足1-4项，第5项可通过平均二元奖励实现。*

### 四、典型案例：AlphaEvolve
- Google开发的[AlphaEvolve](https://deepmind.google/discover/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/)通过"猜测-验证"循环优化目标
- 示范问题：*"容纳11个单位六边形的最小外接六边形"*（完美满足验证者法则5属性）
- **创新逻辑**：科研场景中单一问题突破价值极高（train=test），无需传统ML的泛化能力

### 五、未来影响
可验证任务将形成AI智能的"锯齿边缘"——凡可精确测量的领域终被攻克，推动数字世界远超物理世界的进化速度。**延伸阅读**：[Alperen Keles对可验证性的探讨](https://alperenkeles.com/posts/verifiability-is-the-limit/)
