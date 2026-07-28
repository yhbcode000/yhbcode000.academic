---
layout: single
title: "Geometric Visual Illusions as Inductive Biases for Vision Models"
date: 2025-04-20 11:08:34
author_profile: true
---

Research notes on leveraging geometric visual illusions as perceptual inductive biases for vision models — the foundational exploration behind the InDL dataset and related publications.

1. 如果我们投递neuralps dataset and benchmark track, evaluate cost on the illusion dataset is a good idea which provide a new insight into the machine learning models, how well they can react to human illusion and give valuable insights from the result with evaluation results and with the evaluation we can make modification to ml models and make them working more smoothly.
2. besides if we get into human side, illusion is where human bad at, therefore this illusion dataset would be the one give AI an idea that human may suffer from this and do collaboration working with human may not a good idea. but this illusion might be the source of creativity, but to be honest, creativity is the most difficult thing to evaluate by human, and by certain metrics.
3. therefore in this case what is the contribution of our method? besides cost, we can also get into the latent space to evaluate if an attention machnism has similar idea as human and generate illusion effect in a high dimension, and to remove such illusion, we have to provide tools for it to better understand the world instead of percept with bare eye or attention. We have to admit that, it is impossible for human to measure something with bare eye, so does doing math, we need thinking tools to help us do math etc.
4. 所以按照两篇论文去写，一篇是数据集的论文，按照榜单，分析，利用的思路去做。另一篇是从错觉诞生的过程中获得insight，优化attention甚至是multi-head attention的效果（因为已经有人分析说diffusion model存在和人类似的错觉了，但diffusion model更多是色彩上的，而不是特征层面的，所以讨论attention优化需要更抽象更小心些）这篇文章就不需要使用视错觉数据集了，但可以在视错觉数据集上进行测试和验证，看是否有一个很好的排名，毕竟是是错觉剔除后的模型。
5. 第二篇论文要用vit或者支持transformer架构的模型来做，而且是使用最基础的vit架构去做。（但是另一方面，如果我们在讨论频率和attention带来的错觉，那么我们需要好好思考使用的场景，是否需要是next token prediction的场景）但另一方面来讲，错觉是与过往经验的错误匹配导致的，像是打乱顺序的文字依然可以正常阅读，这在attention中如何剔除，是我们需要考虑的。

---

The Art of Deception: Color Visual Illusions and Diffusion Models:
这篇论文的讨论是有问题的，他在利用AI模型存在的视错觉，实现视错觉的produce。


---

视觉错觉是否是因为attention 的存在频率导致的


ChatGPT said:
这个问题非常有意思！“视觉错觉是否是因为 attention 的存在频率导致的”，可以从神经科学和人工智能两个角度来看。

从 神经科学 角度：
人类大脑的视觉处理系统并不是完全客观地“记录”视觉场景，而是通过一系列预测和注意机制（attention）来高效处理信息：

视觉注意（visual attention） 是我们感知系统中的关键组成部分，它决定我们在哪些信息上“分配资源”。

很多视觉错觉正是因为我们 大脑在处理信息时做了某些“默认假设”，而这些假设不总是准确的。例如：

赫尔曼栅格错觉：我们认为交叉点更亮，是因为我们对边缘的注意方式影响了光强的感知。

米勒-赖尔错觉：线段看起来不同长，是因为我们对“空间深度”的注意习惯产生了偏差。

这与“注意的存在频率”确实有一定关系——我们会优先关注我们习惯性注意的区域或特征，从而导致错觉。

从 人工智能（Transformer & Attention） 的角度：
在机器学习中，Attention机制（尤其是在Transformer模型里）是为了模拟“在处理输入时关注更相关的部分”。

如果你想类比错觉，可以考虑这样一个思路：

如果一个模型的 attention 机制 长期偏向某些 token 或图像区域，可能会在生成、识别过程中产生偏差。

比如在视觉Transformer（ViT）中，如果模型训练过程中总是将注意力分布在某些区域，它可能会“忽略”其他信息，最终形成类似“错觉”的判断错误。

回到你的提问：
视觉错觉是否是因为 attention 的存在频率导致的？

可以这样理解：

✅ 是的，部分视觉错觉确实是因为我们大脑在注意力分配上的频率性偏好或默认策略，导致我们在视觉信息处理上产生了偏差。

你可以把它理解为：注意力是一个“资源分配器”，而错觉是我们资源分配不均或错误预测的副作用。

如果你是从 AI 模型的角度在思考这个问题，也可以继续往 attention 的分布、热图、偏差学习等方向深入探讨。你是在哪个背景下想到这个问题的？研究还是日常观察？我可以帮你挖得更深一点。




---


You said:
有相关AI领域的论文讨论这个事情吗


ChatGPT said:
是的，​在人工智能领域，确实有研究探讨了视觉错觉与注意力机制之间的关系。以下是一些相关的研究成果：​

🧠 1. 预测编码与错觉感知
一项研究中，研究人员在卷积神经网络中引入了预测编码反馈机制，使其能够感知类似人类的错觉轮廓（如 Kanizsa 方块）。这表明，​通过引入反馈机制，神经网络可以更接近人类的视觉感知方式，​并在处理视觉信息时产生类似的错觉感知。​
arXiv

🎨 2. 生成对抗网络与视觉错觉
另一项研究利用生成对抗网络（GAN）生成新的视觉错觉图像。​研究人员设计了一个模型，其中生成器负责创建潜在的错觉图像，而判别器则评估这些图像是否能引发人类的错觉感知。​该模型成功生成了多种类型的错觉图像，​并通过心理物理实验验证了其有效性。​

🌈 3. 扩散模型中的错觉编码
最近的研究发现，扩散模型在其潜在空间中能够编码类似人类的亮度和颜色错觉。这表明，​即使在没有明确设计用于模拟错觉的情况下，​这些模型也能在处理视觉信息时自然地表现出类似人类的错觉感知。​
arXiv

🧬 4. 神经动态模型与错觉再现
还有研究利用 Wilson–Cowan 类型的神经动态模型，成功再现了多种视觉错觉现象。这些模型通过模拟神经元之间的相互作用，揭示了错觉产生的神经机制，并强调了注意力在其中的关键作用。​

🔍 5. 深度神经网络对错觉的响应
研究人员还发现，经过 ImageNet 训练的深度神经网络（如 VGG-19）在处理某些视觉错觉图像（如闪烁网格）时，会表现出与人类类似的非线性响应模式。这表明，这些网络在处理视觉信息时，可能会自然地表现出类似人类的错觉感知。​

这些研究表明，人工神经网络在处理视觉信息时，可能会自然地表现出类似人类的错觉感知，而注意力机制在其中起到了关键作用。这为我们理解人类视觉系统的工作原理提供了新的视角，也为改进人工视觉系统提供了启示。​

如果您对某一特定方向（如 Transformer 模型中的注意力机制与错觉的关系）感兴趣，我可以为您提供更深入的资料和分析。



源


---



You said:

那是否有讨论attention受到过往经验的影响进行了错误的匹配呢


ChatGPT said:
​是的，人工智能领域确实有研究探讨了注意力机制如何受到过往经验的影响，导致错误的匹配和感知偏差。以下是一些相关的研究成果：​

🧠 1. 先验期望对感知的影响
研究表明，​人类大脑会根据过往经验形成先验期望，这些期望会影响感知过程。例如，​一项研究发现，​先验期望可以改变视觉皮层中刺激的表示方式，​即使在早期的感官处理阶段也是如此。这表明，​注意力机制可能会根据过往经验对感知进行偏差处理，从而导致错误的匹配和感知偏差。 ​

🧠 2. 确认偏误与注意力的选择性部署
另一项研究提出，​我们的注意力倾向于选择性地关注与先前决策一致的感官证据。​这种选择性部署可能导致我们忽视与先前经验不一致的信息，从而加剧确认偏误。这表明，​注意力机制可能会受到过往经验的影响，导致错误的匹配和感知偏差。 ​
科学直通车

🤖 3. 神经网络中的认知偏差框架
在人工智能领域，​研究人员提出了一个神经网络框架来解释认知偏差，​其中包括注意力机制如何受到过往经验的影响。​该框架指出，​神经网络在处理信息时，会根据过往经验形成偏好，​从而导致注意力的偏差部署和感知错误。 ​
PMC

🧠 4. 偏向竞争理论
偏向竞争理论认为，​视觉系统中的对象在处理过程中会相互竞争，而这种竞争可以被过往经验所偏向。例如，​我们更容易注意到与先前经验相关的对象，而忽视其他信息。这表明，​注意力机制可能会受到过往经验的影响，导致错误的匹配和感知偏差。 ​
Wikipedia

🧠 5. 愿望性思维与注意力偏差
愿望性思维（wishful thinking）研究表明，​我们的注意力可能会偏向于符合我们期望的感官信息，​从而导致感知偏差。例如，​我们可能更容易注意到与我们期望一致的信息，而忽视与期望不一致的信息。这表明，​注意力机制可能会受到过往经验的影响，导致错误的匹配和感知偏差。 ​
Wikipedia

这些研究表明，​无论是在生物视觉系统还是人工神经网络中，​注意力机制都可能受到过往经验的影响，​从而导致错误的匹配和感知偏差。​这为我们理解感知过程中的偏差提供了新的视角，​也为改进人工智能系统提供了启示。​

如果您对某一特定方向（如 Transformer 模型中的注意力机制与错觉的关系）感兴趣，我可以为您提供更深入的资料和分析。

---

Let's analyze the weight design in this training step carefully.

### Weight Assignment Logic:
The weights are assigned based on the correctness of both target and illusion class predictions:
1. **Both correct (target & illusion)**: weight = 0.25
2. **Correct target only**: weight = 0.5
3. **Correct illusion only**: weight = 0.75
4. **Both incorrect**: weight = 1.0

### Intended Purpose:
This appears to be a form of "importance weighting" where:
- The model gets the smallest penalty (0.25) when it's completely right
- Medium penalty when partially right (0.5 or 0.75)
- Full penalty when completely wrong (1.0)

### Potential Issues:

1. **Inverse Relationship to Importance**:
   - Normally in importance weighting, higher weights are given to more important/more difficult cases
   - Here the weights are inversely related to correctness (better predictions get lower weights)
   - This means the loss function will pay *less* attention to samples it's getting right

2. **Potential Negative Effects**:
   - The model might learn to ignore easy cases and focus too much on hard cases
   - Could lead to instability as correctly classified samples get progressively less attention
   - May cause the model to "forget" previously learned patterns

3. **Weight Magnitude Concerns**:
   - The weight differences are quite large (4x difference between best and worst cases)
   - This might make training unstable

### Suggested Improvements:

If the goal is to focus more on difficult cases, a better approach might be:
1. Use higher weights for incorrect predictions rather than lower weights for correct ones
2. Consider a smoother weighting scheme (e.g., based on prediction confidence)
3. Alternative approaches:
   ```python
   # Example alternative - focusing more on errors:
   weights = torch.ones_like(outputs[:, 0])
   weights[correct_target & correct_illusion] = 1.0    # Both correct - normal weight
   weights[correct_target & ~correct_illusion] = 1.5   # Partial error - higher weight
   weights[~correct_target & correct_illusion] = 2.0   # Partial error - even higher
   weights[~correct_target & ~correct_illusion] = 3.0  # Both wrong - highest weight
   ```

### Conclusion:
The current weight design is mathematically valid but may not be pedagogically optimal for learning. The inverse relationship between correctness and weight magnitude could lead to unintended training dynamics. A more conventional approach would be to give higher weights to cases the model is getting wrong rather than lower weights to cases it's getting right.

---

the reason why the training cannot get best result might be the ratio between the task samples and the synthetic data samples. take the illusion strength filter as example, which filter out 10% of data and the peak performance is great.

---

对比完全噪声的图像

---


<!-- bug: 不是所有的illusion都有数据，未能成功normalization -->

<!-- ![1745911541245.png](https://image.yhbcode000.tech/1745911541245.png)


![1745910623689.png](https://image.yhbcode000.tech/1745910623689.png)


![1745911135875.png](https://image.yhbcode000.tech/1745911135875.png) -->


---

现在我们按照experiment最好的实验结果和配置，然后discussion讨论各个可能的变量带来的影响并实验证明或者推翻。

---

好的！基于你以上详细的讲述，我为你整理出这份完整、结构清晰、逻辑连贯的**论文写作大纲**：

---

# 论文写作大纲

## 1. Abstract
- 总结全文亮点，突出两大反直觉现象：
  - 多任务（Multitask）学习中，辅助任务**提升**了主任务性能（反直觉）。
  - 将人类认知（如几何视错觉）引入人工智能数学模型后，性能出现**提升**（反直觉）。
- 强调首次系统性引入人类感知错觉到机器学习。
- 突出本工作对人工智能可解释性、建模的新视角。
- 引出本文提出的新数据集名称（待定，如 *IllusioNet*）。

---

## 2. Introduction
- 研究动机：
  - 许多AI中的核心概念（如 attention）来源于人类感知机制。
  - 探索能否将人类感知领域的成果（特别是错觉现象）系统性引入到人工智能领域。
- 问题定位：
  - 当前AI模型普遍忽视人类认知机制中的错觉现象。
- 本文贡献概述。

---

## 3. Related Works
- 人工智能中的感知建模工作（如 attention机制、感知学习等）。
- 多任务学习（Multitask Learning）中任务干扰和提升的文献综述。
- 人类错觉研究及其在心理学、认知科学中的基础工作。

---

## 4. Dataset Specification
- **数据集构建**：
  - 选取了五种经典几何视错觉，作为**几何视错觉**完整子集合（具有系统性和理论依据）。
  - 每种错觉的实例生成方法和原理概述。
- **数据集特点**：
  - 每个样本的生成细节（图像尺寸、错觉强度变化等）。
  - 说明该子集合覆盖了全部主流的几何错觉类型。
- **与现有数据集的区别**。

---

## 5. Experiments
- 实验设置：
  - 真实任务：ImageNet分类。
  - 在主任务训练中引入错觉数据集，考察其对主任务准确率的影响。
- 实验结果：
  - 引入错觉数据集后，ImageNet分类准确率上升。
- 实验细节：
  - baseline、控制组设置。
  - 训练细节（batch size，学习率，训练时长等）。

---

## 6. Discussion
### 6.1错觉有效性分析
- 通过不同程度的错觉强度引入实验，分析错觉程度与模型准确率的关系。
- 探讨是否存在最佳错觉强度区间。

### 6.2图像大小的影响
- 小尺寸（如32×32）下错觉现象弱化，导致效果下降。
- 寻找图像尺寸的最佳 sweet spot。

### 6.3错觉数据集的独特贡献验证
- 引入一个新的对照数据集（ImageNet的其他类别）。
- 替换后观察性能变化，验证错觉数据集的独特性和有效性。

---

## 7. Conclusion
- 总结研究成果：
  - 首次将人类感知错觉系统性引入到人工智能数据集中。
  - 展现了反直觉的提升现象，为未来感知与智能结合提供新思路。
- 未来展望：
  - 作为理解与解释人工智能模型行为的新工具。
  - 促进认知科学与机器学习的交叉研究。

---

## 8. Supplementary Material
- 额外实验结果：
  - 不同 batch size 对性能的影响。
  - 不同错觉种类、不同参数配置的探索实验。
- 更多关于错觉程度、数据增强、训练细节的深入分析。

---

# 总结

这个大纲清晰反映了你的论文结构、逻辑重点和每一部分的主旨，特别是围绕“两大反直觉现象”和“几何错觉完整性”的核心卖点进行了布局。  
后续可以基于这个大纲，逐步展开各章节的详细写作。

---

要不要我顺便也帮你**想一些更正式的论文标题和数据集名字**，方便你投稿 NeurIPS Dataset & Benchmark Track？  
（比如可以再专业一点地起名，不止是 "IllusioNet"，还能有别的风格备选。）要的话告诉我！✨


![1745976759044.png](https://image.yhbcode000.tech/1745976759044.png)


![1745976779761.png](https://image.yhbcode000.tech/1745976779761.png)


### 🔵 **ResNet Models**
- **Base mean accuracy**: 0.8511
- **102**: +0.000013 → *Virtually identical* to base.
- **102_v2**: −0.000094 → *Slightly lower*, negligible.
- **103**: +0.000098 → *Slightly higher*, negligible.

📌 **Interpretation**: All tasks perform almost identically to the base task, with differences less than ±0.01%. No meaningful performance shift across tasks for ResNet.

---

### 🟣 **ViT Models**
- **Base mean accuracy**: 0.8718
- **102**: +0.0020 → *Slight improvement* (~0.2%)
- **102_v2**: +0.0034 → *Moderate improvement* (~0.34%)
- **103**: +0.0051 → *Notable improvement* (~0.51%)

📌 **Interpretation**: ViT models show consistent and increasingly better accuracy from 102 → 102_v2 → 103. ViT benefits more from advanced task versions than ResNet.

---


![1745990470308.png](https://image.yhbcode000.tech/1745990470308.png)


![1745990482271.png](https://image.yhbcode000.tech/1745990482271.png)

一个几何特征，一个challenging task

---


Thanks for the clarification. I'll generate several NeurIPS-style titles that emphasize the broader implications of your work for AI and human perception, while reflecting the novelty of using illusions as a source of inductive bias. I'll get back to you shortly with a set of well-aligned options.


# NeurIPS-Style Paper Title Ideas

Below is a range of proposed paper titles that capture the core idea: using **human geometric visual illusions** as **inductive biases** to train vision models, thereby improving generalization in image classification. These titles vary in style from concise and abstract to more descriptive and precise, while maintaining a tone that is technically rigorous, succinct, and idea-driven (as is typical for NeurIPS papers).

## Concise and Abstract Titles

* **Geometric Visual Illusions as Inductive Biases for Deep Vision Models**
* **Inductive Biases from Perceptual Illusions for Improved Image Classification**
* **Illusion-Informed Inductive Biases Enhance Generalization in Neural Vision Models**
* **Human-Like Perception via Illusory Inductive Biases in Image Classification**

## Descriptive and Precise Titles

* **Learning from Illusions: Non-Veridical Cues Improve Vision Model Generalization**
* **Synthetic Illusions as Inductive Biases: Bridging Human Perception and Machine Vision**
* **From Human Illusions to Model Generalization: Perceptual Cues as Inductive Biases**
* **When Perception Deceives, Networks Learn: Geometric Illusions as Inductive Priors**
* **Perceptual Science for Machine Vision: Visual Illusions as Inductive Biases**
* **Non-Veridical Perception as an Inductive Bias: Illusory Cues Boost Neural Network Generalization**

---

Based on the current structure, focus, and findings of your paper, it is more **suitable for the main NeurIPS track**, rather than the dataset & benchmark track. Here's a breakdown of why:

---

### ✅ **Why it fits the NeurIPS Main Track:**

#### 1. **Conceptual Contribution > Dataset Engineering**

While you introduce a new dataset, your **central contribution is not the dataset itself**, but the **insight that human visual illusions can act as inductive biases** that improve general-purpose vision models. This addresses a **core question in machine learning and perception**, not just data curation.

> *“We treat visual illusions not as artifacts to discard, but as principled supervision signals.”*

#### 2. **Model Behavior & Inductive Bias**

The paper deeply investigates **how vision models respond to non-veridical inputs**, opening a bridge between perceptual science and AI. This is squarely in line with **core NeurIPS themes**, such as:

* Representation learning
* Generalization theory
* Biological inspiration
* Human-AI alignment

#### 3. **Rigorous Methodology & Evaluation**

You provide:

* A multi-source learning framework
* Comparisons across architectures (ResNet, ViT)
* Ablations on illusion strength and resolution
* Insightful qualitative analysis

These go **well beyond what’s expected** in a dataset-only paper.

---

### 🚫 Why it likely does **not** fit the Dataset & Benchmark Track:

The dataset is synthetic and used **internally** as part of the experimental design, rather than being proposed as:

* A standardized benchmark for the community
* A long-term reusable testbed with broad utility
* A carefully annotated or crowdsourced resource

> Dataset track papers are typically about enabling community-wide evaluation, with a clear protocol and leaderboard potential. Your work is about using the dataset to test a *theory*.

---

### 🧠 Suggested Framing for Main Track Submission:

If you’re submitting to the main track, keep emphasizing:

* **Theoretical motivation**: using illusions as cognitive priors.
* **Empirical insight**: inductive bias improves classification.
* **Generalization perspective**: illusions improve hard-case structure recovery.

You might slightly de-emphasize the dataset details and instead frame them as tools for probing an important ML hypothesis.

---

Would you like a paragraph or sentence that clearly justifies your submission to the main track in the NeurIPS submission form?


---

geometric illusion
inductive bias




> **🌸唠嗑QQ群**：[兔叽の魔术工房](https://jq.qq.com/?_wv=1027&k=EaGddTQg) (942848525)
> **⭐B站账号**：[白拾ShiroX](https://space.bilibili.com/98639326)（活跃于知识区和动画区）
> **✨GitHub主页**：[yhbcode000](https://github.com/yhbcode000)（工程文件）
> **⛳Discord社区**：[AierLab](https://discord.g/nn5NDXMgae)（人工智能社区）