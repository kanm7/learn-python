## Hello Agent

#### 三种模型范式：

| 范式           | 核心流程        | 适合任务                                       |
| -------------- | --------------- | ---------------------------------------------- |
| ReAct          | 思考→ 行动→观察 | 查天气、搜索、调用API等实时性强的任务          |
| Plan-and-Solve | 规划→执行→汇总  | 数学题、学习计划、方案设计等操作路径明确的任务 |
| Reflection     | 生成→反思→优化  | 代码优化、文章修改等旨在提升解决方案质量的任务 |

#### 目前项目能力已经有

```
1. LLMClient：封装大模型调用
2. ToolExecutor：统一注册和执行工具
3. ReActAgent：调用工具解决动态任务
4. PlanAndSolveAgent：先规划再执行
5. PlanAndSolveToolAgent：规划 + 工具调用
6. ReflectionAgent：生成、反思、优化
7. ReActReflectionAgent：工具执行 + 答案自检
```

#### Memory

分为两类：

- 短期记忆，对应本轮任务里的上下文
- 长期记忆，跨多轮、跨任务保存的信息
