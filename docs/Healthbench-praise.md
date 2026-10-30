# HealthBench 做对了什么

**🇬🇧 English version at the end ↓｜英文版见文末**

在批评之前，先把成绩说清楚。HealthBench 的四个设计值得肯定：

- **对话而非选择题**：5000 条多轮健康对话，任务是给用户的最后一条消息做出最佳回应，贴近真实使用形态；
- **Rubric 计分而非单点打分**：每条对话配医生撰写的评分细则，含加分项与负分项（如“建议给无反应者喂食喂水，-9”），可解释、可归因；
- **大规模医师参与**：262 名来自 60 个国家、26 个专科的医生参与构建；
- **开源与自我审视**：数据与评测套件公开，论文坦承局限（85% 对话为英语、约 87% 的 rubric 条目由单一作者撰写未经共识校验）。

“本土化改写”也已有学术先例：日本学界发表了将 HealthBench 系统移植到日本医疗语境的研究，证明 localization 是被认可的方法论方向。本项目的增量在于：中国语境除语言转换外，还必须补全三个连日本研究也未覆盖的维度（详见Framework（三维论述+总表））。

总结一下：HealthBench的意义在于，首先，这是全球第一个拥有一定体量且由头部大模型公司主导的医疗训练数据集，它可以作为一个标杆。物理世界的运动与静止需要参照系，人类的学习和进步需要标杆，LLM的训练数据集也是如此。从0到1，然后从1到100，跨出质变性的第一步是困难的，也是可敬的。其次，它由专业人士参与编写，尽管有“医生假装病人”的问题在，但比起纯粹的互联网采集医疗信息并逆向生成数据，它的方法论更科学、更有效也更能促进模型在相对真实的世界里进步。

本项目正是在HealthBench的基础上展开，正如牛顿所言，他站在巨人的肩膀上，而万幸的是，我们可以因此而触到更高。

---


---

## What HealthBench Got Right

Before any criticism, credit where due. HealthBench's four design decisions deserve genuine acknowledgment:

- **Conversations, not multiple choice**: 5,000 multi-turn health conversations, with the task of giving the best response to the user's final message — close to real usage patterns;
- **Rubric scoring, not single scores**: each conversation pairs with physician-written criteria, including negative items (e.g., "advising to give food or drink to an unresponsive person, −9") — explainable and attributable;
- **Large-scale physician involvement**: 262 physicians from 60 countries across 26 specialties;
- **Openness and self-scrutiny**: the data and evaluation suite are public, and the paper openly admits limits (85% of conversations in English; ~87% of rubric items written by a single author without consensus validation).

"Localization" also has academic precedent: Japanese researchers have published a systematic adaptation of HealthBench to the Japanese medical context, proving that localization is a recognized methodological direction. This project's increment lies in: beyond language translation, the Chinese context requires three additional dimensions not covered even by the Japanese work (see Framework for the full argument and summary table).

**In summary**: HealthBench's significance operates on two levels.

First, it marks the moment when a frontier lab formally set a benchmark for the entire industry — the first large-scale, top-lab-anchored medical training-data standard with global influence. Its importance is comparable to what ImageNet meant for computer vision: whether or not you agree with it, the entire field now has a physical reference frame. Everyone training medical models must now ask: how far am I from HealthBench?

Second, it is the first medical dataset of this scale built with substantial physician involvement — a methodological commitment that deserves real respect. The alternative, pure internet-scraping followed by reverse-generation, is the well-known path taken by far too many.

Newton said he stood on the shoulders of giants. Critique of HealthBench should proceed from the same posture. And fortunately — because these giants exist, the rest of us may reach higher.
