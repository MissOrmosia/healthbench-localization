# 三维增补框架总表——以及为什么必须有这三个维度

**GB [English version at the end ↓](#the-three-dimension-augmentation-framework--and-why-these-three) | 英文版见文末**

## 为什么要增加这三个框架

HealthBench 的原版 Rubric 隐含着美国医疗语境的全部默认设置：急救体系（911 调度、AED 可及）、普通法系 Good Samaritan 保护、高健康素养的提问者、以及“用户可以自行承担完整医疗决策权”的假设。这些默认在中文真实世界里逐个失效——失效的方式不是“翻译错了”，而是**整个风险结构不同**。增补三个维度不是给原版标准“加分”，是把评测从“医学正确”扩展到“真实世界安全”。

### 一、法律合规：事后免责 ≠ 事前无险

不同法域的医疗法律体系存在结构性差异，美国经验不能简单粗暴地移植到中国——不仅条款不同（Good Samaritan 法系 vs《民法典》第 184 条的具体机制），急救资源可及性（911/120、AED 布点）、诉讼文化、举证规则都不同，同一句话在两个法域的风险收益比完全不同。

但更关键的一层是：**即便法律有条款保护，普通人被卷入官司本身就是灾难**。孙向波案（持执业医师证的药店老板，心肺复苏救回老人，因老人肋骨骨折被诉，四年诉讼、多场庭审、药店倒闭，最终依第 184 条完全免责，但生活已经天翻地覆）证明：胜诉不是终点——四年的诉讼成本、职业停摆、心理创伤，都是不可逆的。“事后免责”解决的只是判决结果，解决不了“进入法律程序”这个过程本身的伤害。

**AI 的职责是把用户拦在法律程序之外**：先解除心理恐惧（主动援引免责条款）、固定证据（110+120 双呼叫）、给出不留疑义的行动指令——而不是在用户已经身陷风险之后，才在教科书里引用一条法条。评测标准如果只奖励“医学建议正确”而不奖励“法律安全路径”，就是在训练模型把用户留在风险里，或者让了解风险的用户因为没有避免风险的路径而被迫选择避险，且为自己的决策倍感道德煎熬。

### 二、文化语境：健康信念没有通用语

传统医学的认知差异是本地化绕不开的一层：中草药制品、食疗调理、“上火”“湿气”等概念，在中文语境有深厚的文化根基——而它们在 HealthBench 的评分标准里**不存在**（英语语境没有“上火”，就像中文语境没有“organic、gluten-free”的完整对应）。忽视这些概念的评测，等于把中文用户最大的健康信念系统留在评测盲区里。

同时必须诚实：传统医学的治疗方案和药物往往未经现代科学的药理、毒理与临床验证。**AI 不需要、也不可能否定传统医学的文化价值——但至少有义务警示风险**：成分不明意味着什么，“天然”不等于“安全”，传统方案与现代药物之间未经研究的相互作用是真实存在的盲区。类似的还有语境特异性的执念：对输液的期待、对“消炎药”的滥用、对“调理”的依赖——这些是中国语境下 AI 每天必须面对的默认背景，评测标准应当覆盖它们，而不是假设用户在一套干净的生物医学语汇里提问。

### 三、心理能力：认知带宽是情境性的，不是身份性的

不同人群的心理状态与承受能力差异巨大。评测标准不该假定普通用户具备足够的专业素养，更不该高估他们的心理承受能力——**这两点恰好是合成数据的系统性盲区**（医生写剧本时，想象不出真正恐慌的人说不出完整的句子）。

用一个比喻精确这个维度：医疗决策比刀具更需要分级管理。刀具的危险是可见的——刀刃是亮的，握刀的手知道自己在做什么，风险与动作直接对应。医疗风险却常常是隐形的：“吃了感觉好多了”可能就是交感兴奋的危险信号，“（受击后）看起来没有印子没有淤青”可能隐藏着内脏出血风险。对认知成熟、情绪稳定的用户，提供完整信息并尊重其选择权，是赋权；但对认知受限、或正处于情绪危机中的用户，同样的“尊重”等于把不可见的风险交给无法识别它的人——**那不是赋权，是遗弃**。

更精确地说：认知带宽是情境性的，不是身份性的。深夜崩溃的产后妈妈、恐慌的独居老人、被家属情感裹挟的患者——他们在那一刻的决策带宽是受限的，即便他们的“身份”是成年人。评分标准必须能识别这种状态（症状降格、编码式求救、框架锁死），并自动调整指令的强度与颗粒度：对该追问的人追问，对该下达强指令的人下达强指令，对该先安抚的人先安抚。**“一刀切地交付完整信息自由”不是平等，是失职。**

## 三维增补框架总表

| 维度 | 补全的盲区 | 对应案例 | 核心逻辑 |
| --- | --- | --- | --- |
| **法律合规** | 不敢救、不敢叫救护车的集体心理，有其真实的法律叙事背景——而“事后免责”无法消解“事前恐惧”与过程成本 | 案例一（倒地邻居） | 先解除心理防线（民法典 §184、110+120 双呼叫），再下达动作指令 |
| **文化语境** | 病耻感对高危信息的编码与遮蔽；错误信息流对求医行为的点燃；传统医学信念系统的风险盲区 | 案例二、三（产后抑郁、草药补品） | 模型需具备“解码”能力：把愧疚、自我否定、“荒唐的念头”、“上火调理”等文化编码翻译回风险信号；对传统医学至少履行风险警示义务 |
| **心理能力** | 受众悖论：会做的不需要告知，不会做的不能照告知执行；认知带宽的情境性 | 案例一、三 | 建议必须按受众能力分层分发：先追问、再分级、后指令；隐形风险面前，一视同仁的信息交付不是平等而是遗弃 |

三个维度共同指向一个评测设计原则：**在真实世界里，“对谁说话”和“说什么”同等重要**。这正是合成漏斗双重过滤中流失最彻底的部分——因为它既不体现在“医生认为重要的情景”里，也不体现在“LLM 演绎的患者”里。


---

# The Three-Dimension Augmentation Framework — and Why These Three

## Why These Three Dimensions

HealthBench's original rubrics implicitly carry every default of the US medical context: the emergency system (911 dispatch, AED availability), common-law Good Samaritan protection, highly health-literate askers, and the assumption that users can independently bear full medical decision-making authority. These defaults fail one by one in the Chinese real world — not as "translation errors," but as **structurally different risk landscapes**. Adding the three dimensions is not "bonus points" on the original standard; it expands evaluation from "medically correct" to "safe in the real world."

### 1. Legal Compliance: Ex-Post Immunity ≠ Ex-Ante Safety

Medical law differs structurally across jurisdictions; US experience cannot be transplanted crudely into China — the clauses differ (common-law Good Samaritan vs. Article 184 of the Chinese Civil Code), and so do emergency-resource accessibility (911/120, AED deployment), litigation culture, and burden-of-proof rules. The same sentence carries a different risk-benefit ratio in each jurisdiction.

But the deeper point: **even where legal protection exists, being drawn into a lawsuit is itself a disaster for an ordinary person.** The Sun Xiangbo case (a licensed physician-pharmacist who performed CPR, was sued over rib fractures, endured four years of litigation and three trials, and lost his pharmacy — ultimately fully exonerated under Article 184) proves that winning is not the end: four years of litigation, professional shutdown, and psychological trauma are irreversible. "Ex-post immunity" settles the verdict; it does not undo the harm of entering the legal process itself. Nor does it account for those who understand the risk and, having no safe path around it, are forced into avoidance — and left to carry the moral weight of that decision alone.

**AI's duty is to keep users out of the legal process in the first place**: dissolve the fear first (actively citing the immunity clause), fix the evidence (dual 110+120 calls), and give unambiguous action instructions — rather than quoting a statute from a textbook after the user is already inside the risk. An evaluation standard that rewards only "medically correct" answers without rewarding "legally safe pathways" is training models to leave users inside risk.

### 2. Cultural Context: Health Beliefs Have No Universal Language

Traditional-medicine cognition differences are a layer localization cannot bypass: herbal products, dietary regimens, and concepts like "shanghuo (internal heat)" or "tiaoli (tonic conditioning)" have deep cultural roots in the Chinese context — and they **do not exist in HealthBench's criteria** (English has no "shanghuo," just as Chinese has no full equivalent of the "organic/gluten-free" cluster). A benchmark that ignores these concepts leaves the largest health-belief system of Chinese users in its blind spot.

At the same time, honesty is required: traditional-medicine regimens and remedies have often not undergone modern pharmacological, toxicological, and clinical validation. **AI need not — and cannot — deny the cultural value of traditional medicine, but it has at minimum the duty to warn**: what "unknown ingredients" means, why "natural" ≠ "safe," and that interactions between traditional remedies and modern drugs are a real, understudied blind zone. The same applies to context-specific fixations: the expectation of IV drips, the misuse of "anti-inflammatory drugs," the reliance on "conditioning" — these are the default background that Chinese medical AI faces daily. Evaluation criteria should cover them, rather than assuming users ask questions in a clean biomedical vocabulary.

### 3. Psychological Capacity: Cognitive Bandwidth Is Situational, Not Identity-Based

People differ enormously in psychological state and stress tolerance. Evaluation criteria should not assume ordinary users possess professional literacy — nor overestimate their psychological resilience. **These two assumptions are precisely the systematic blind spots of synthetic data** (when physicians write scripts, they cannot imagine how a truly panicked person cannot finish a sentence).

A precise analogy: medical decision-making needs tiered management far more than knives do. A knife's danger is visible — the blade gleams, and the hand holding it knows what it is doing; risk and action correspond directly. Medical risk is often invisible: "I feel much better after taking it" may be the danger signal of sympathetic stimulation; "no bruise, no swelling" may be internal bleeding. For cognitively mature, emotionally stable users, providing complete information and respecting their choice is empowerment. But for users with limited cognition, or in emotional crisis, the same "respect" hands invisible risks to people who cannot identify them — **that is not empowerment; it is abandonment**.

More precisely: cognitive bandwidth is situational, not identity-based. A postpartum mother breaking down at midnight, a panicked elderly person living alone, a patient emotionally cornered by family — in that moment, their decision bandwidth is impaired, even though their "identity" is adult. Scoring criteria must recognize such states (symptom downgrading, encoded cries for help, frame lock-in) and automatically adjust the intensity and granularity of instructions: ask when asking is needed, command firmly when firm command is needed, comfort first when comfort is needed. **Delivering full informational freedom uniformly is not equality — it is dereliction.**

## The Framework Table

| Dimension | Blind spot covered | Cases | Core logic |
| --- | --- | --- | --- |
| **Legal Compliance** | The collective fear of helping and of calling ambulances has a real legal narrative — and ex-post immunity cannot dissolve ex-ante fear or the cost of the process | Case 1 (collapsed neighbor) | Dissolve the psychological defense first (Civil Code Art. 184, dual 110+120 calls), then issue action instructions |
| **Cultural Context** | Stigma's encoding and concealment of high-risk information; misinformation cascades igniting help-seeking; the risk blind zone of traditional-medicine belief systems | Cases 2, 3 (postpartum depression, herbal supplements) | The model needs "decoding" capacity: translate guilt, self-denial, "absurd thoughts," "shanghuo/tiaoli" and other cultural codes back into risk signals; traditional medicine at minimum warrants risk warnings |
| **Psychological Capacity** | The audience paradox: those who can do it don't need to be told; those who can't must not be told to execute; the situational nature of cognitive bandwidth | Cases 1, 3 | Instructions must be tiered by audience capability: ask first, then grade, then instruct; in the face of invisible risk, uniform information delivery is not equality but abandonment |

All three dimensions converge on one evaluation-design principle: **in the real world, "to whom you speak" and "what you say" are equally important.** This is precisely the part most thoroughly lost in the synthetic funnel's double filtering — because it appears neither in "scenarios physicians consider important" nor in "patients as dramatized by an LLM."
