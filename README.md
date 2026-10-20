# AI 产品拆解 · ai-product-teardown

一个面向 AI 产品经理、研究者和设计者的 Codex Skill。以真实场景和可追溯证据，从产品体验还原五层架构，输出有依据的产品拆解报告。

## 分析什么

- 用户需求场景：给谁用，在什么场景解决什么问题。
- 用户层：入口、输入、过程、输出、交付，以及异常恢复。
- 技术层：人机分工、工具、确认点与 Workflow / Agent 架构判断。
- 模型层：模型能力、档位、收费、积分与运行成本的区别。
- 基础层：数据、上下文、业务接口、专业积累及壁垒。

支持网页产品、手机 App、桌面客户端、插件等形态。网页优先浏览器操作截图；App 优先研究公开演示、官方截图和帮助资料，缺失部分再集中补充。报告区分实际体验、公开材料重建与实现假设。

## 工作流程

确定范围 → 产品与市场定位 → 场景测试设计 → 用户旅程取证 → 人机与技术拆解 → 模型和商业机制 → 基础能力与壁垒 → 二次验证 → 架构汇总与交付。

每条关键结论使用两个维度：

|维度|取值|
|---|---|
|确认状态|已经明确确认 / 待确认核实|
|结论性质|页面事实 / 合理推断 / 尚未确认|

待核实项进入统一验证清单；技术推导不冒充真实内部实现。默认输出 Markdown，也支持 HTML 或飞书文档。飞书需要所在环境有相应写入能力；HTML 风格可另行指定。缺少实测条件时明确限制，不编造操作结果或评分。

## 安装到 Codex

可以直接告诉 Codex：

> 安装这个 GitHub 仓库中的 Skill：https://github.com/Caishuang-ma/ai-product-teardown

也可手动安装到个人技能目录（目标目录已存在时先检查，避免覆盖自己的修改）：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/Caishuang-ma/ai-product-teardown.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/ai-product-teardown"
```

安装后在下一轮对话中调用。

## 使用示例

```text
$ai-product-teardown 帮我拆解蚂蚁阿福，输出 Markdown 报告。
```

```text
$ai-product-teardown 拆解这个 AI 网站，沿一个真实任务操作并截图，
重点分析人机确认点和失败恢复，输出 HTML 报告。
```

```text
$ai-product-teardown 根据这些 App 截图和录屏拆解产品。
请把待核实信息单独列出；Agent 的实现推导另行标注。
```

## 文件结构

```text
SKILL.md                         执行入口与标准流程
agents/openai.yaml               Codex 界面信息
references/evidence.md           证据规范与二次验证
references/report-template.md    报告模板及格式适配
references/agent-deep-dive.md    Agent 深入分析与实现假设边界
```

核心方法以用户确认的“五层五问”为基础。方法来源说明见报告模板文末。仓库只包含技能与说明；实际拆解报告、产品素材和个人资料需在使用时另行提供。
