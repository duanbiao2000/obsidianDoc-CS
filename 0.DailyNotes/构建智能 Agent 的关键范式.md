[[构建智能 Agent 的关键范式]]这篇笔记详细阐述了除了[[ReAct]]框架之外，多种用于增强[[大型语言模型]]（[[LLM]]）推理、规划和执行能力的[[智能 Agent]]构建策略。这些范式可以单独应用，也可组合使用以解决更[[复杂任务]]。

以下是笔记中提及的[[核心范式]]及其要点：

1.  **[[链式思考]] (Chain of Thought, [[CoT]])**
    *   **核心思想**：[[LLM]]在给出最终答案前，生成一系列中间[[推理步骤]]，展现“思考过程”。
    *   **特性**：提高复杂推理能力（如算术、符号推理），提供决策过程的[[可解释性]]，纯粹依赖[[LLM]]自身能力，无需外部工具。
    *   **与 ReAct 关系**：CoT是ReAct中“Thought”部分的基础，ReAct将CoT的推理步骤与外部“Action”相结合。

2.  **[[自我反思]] / [[自我修正]] (Self-Reflection / Self-Correction)**
    *   **核心思想**：Agent执行任务后评估自身输出或行动，识别错误并基于[[反思]]进行修正或改进。
    *   **特性**：实现错误检测与修正，需要明确的评估机制，支持[[迭代优化]]。
    *   **与 ReAct 关系**：ReAct的“Observation”步骤为自我反思提供数据，Agent可根据观察结果反思其[[Thought-Action链]]的有效性。

3.  **[[思想树]] (Tree of Thought, [[ToT]])**
    *   **核心思想**：扩展CoT，允许[[LLM]]在思考过程中探索多个不同的[[推理路径]]（[[树状结构]]），进行前瞻性思考、回溯和全局评估。
    *   **特性**：支持多路径探索，具备回溯能力，适用于复杂搜索或多步规划任务。
    *   **与 ReAct 关系**：ToT可在ReAct的“Thought”阶段内部应用，使[[LLM]]思考过程更丰富、更有策略。

4.  **[[模块化推理、知识和语言]] (MRKL - Modular Reasoning, Knowledge and Language)**
    *   **核心思想**：将[[LLM]]作为路由层，决定将请求转发给哪个“[[专家模块]]”（如知识库、计算器、API等工具），或直接由[[LLM]]回答。
    *   **特性**：强调模块化、路由能力，仅在需要时调用特定模块以提高效率。
    *   **与 ReAct 关系**：MRKL是工具使用的早期概念，ReAct更进一步，在工具使用后进行深度推理和迭代。

5.  **[[生成式 Agent]] (Generative Agents)**
    *   **核心思想**：模拟人类行为和[[认知过程]]，通过[[记忆流]]、[[反思]]和[[规划]]构建可信的虚拟人物。
    *   **特性**：具备长期记忆和反思能力，能进行动态规划，支持社会互动，展现更复杂、类似人类的行为模式。
    *   **与 ReAct 关系**：生成式Agent可能在其内部的规划和执行循环中采用ReAct模式来与环境或内部工具交互。

6.  **[[自主 Agent]] (Autonomous Agents - 如 AutoGPT / BabyAGI)**
    *   **核心思想**：围绕一个高层次目标，自主进行任务分解、子任务执行、结果评估和迭代，直至目标达成，通常无需人类频繁干预。
    *   **特性**：目标驱动，自主循环（思考 -> 行动 -> 观察 -> 评估 -> 调整），具备任务分解与管理能力，通常利用外部存储实现持久性。
    *   **与 ReAct 关系**：ReAct是许多自主Agent内部微观执行循环的关键，自主Agent负责宏观规划和任务管理，ReAct负责细粒度推理和工具调用。

7.  **[[思想图谱]] (Graph of Thoughts, [[GoT]])**
    *   **核心思想**：将CoT和ToT进一步泛化，允许[[LLM]]的思想状态以任意[[图结构]]演化，而非仅限于线性或树状，支持更复杂的非线性思考。
    *   **特性**：提供更灵活的思考结构，支持多源信息融合，解决高度非线性复杂问题。
    *   **与 ReAct 关系**：GoT可作为ReAct中“Thought”阶段更高级、更复杂的实现方式。

**总结**：
这些范式各有侧重：CoT关注内部推理的[[透明性]]，ReAct结合[[推理]]和[[外部行动]]，自我反思强调[[自我修正]]，ToT引入[[多路径探索]]和[[回溯]]，MRKL是模块化工具使用的探索，而[[生成式 Agent]]和[[自主 Agent]]将[[LLM]]提升到更宏观的[[自主规划]]和[[行为]]层面，GoT则提供更灵活的思考结构。在实践中，构建[[智能 Agent]]通常会混合和匹配这些范式以达到最佳效果。