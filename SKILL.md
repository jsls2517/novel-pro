---
name: novel-pro
version: 1.6.3
summary: 轻主控小说协作 skill。先判断工作流，再按需调用子角色。
---

# novel-pro

## 1. 先分流，再执行
收到任务后，先判断属于哪一种场景；只读取对应 workflow，不要先把全部说明和 agents 一次性装入上下文。

1. 新小说启动
   读取：`workflows/01-new-novel.md`
   说明：先判断用户是否已有创作思路，再进入启动八问与项目初始化
2. 存量小说接管
   读取：`workflows/02-takeover.md`
3. 继续写下一章
   读取：`workflows/03-continue-next-chapter.md`
4. 单章审计 / 修订
   读取：`workflows/04-audit-revise.md`

## 2. 全局铁律
- 不跳章，不预读，不伪造“已同步”。
- 事实优先于意图；正文优先于摘要；最新正文优先于旧快照。
- 先写总账，再刷新快照；快照只保留当前值，不保留长流水历史。
- 任何当前结论都应能追溯到 `fact_id` 或明确章号。
- 能按需读局部，就不要整包加载全部真相文件或全部 reference。

## 3. workflow 的职责边界
- workflow 负责告诉 AI：什么时候进入、至少读什么、项目结构长什么样、需要初始化哪些文件、执行顺序和门禁是什么。
- 新书启动 workflow 还必须先判断用户是否已有创作思路，再决定是“按现有思路建项目”还是“进入引导式立项”。
- 启动问题应尽量结构化，优先给用户明确可选答案，而不是只抛开放题。
- agent 负责执行某一步，不负责重新定义整个项目骨架。
- 模板、目录结构、状态门禁等硬信息，优先写在 workflow，而不是散落在对话里等待 AI 自己猜。

## 4. 子角色入口
只在当前 workflow 明确需要时再读取对应 agent 文档。

- `agents/planner.md`：产出章节意图
- `agents/composer.md`：压缩上下文包
- `agents/writer.md`：生成正文
- `agents/observer.md`：抽取本章事实
- `agents/settler.md`：写总账并刷新快照
- `agents/auditor.md`：审计正文
- `agents/reviser.md`：定点修订

## 5. 最小加载原则
- 先读 workflow，再决定是否需要 agent。
- 先读当前任务直接相关文件，再读补充 reference。
- 若一个 agent 文档已经够用，不再顺手展开其他 agent。
- 若用户只是问规则或让你优化 skill，优先改文档本身，不进入小说正文流程。
