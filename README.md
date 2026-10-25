# agenthub-models — AgentHub 官方模型服务注册表

AgentHub「官方模型」内置入口的数据源：服务端点与模型清单写在这里，应用按需拉取（ETag 缓存，改清单不用发应用版本）。

## index.json 字段

| 字段 | 说明 |
|---|---|
| `service` | 服务显示名 |
| `endpoint` | OpenAI 兼容端点。**必须 https**——写 `http://` 的清单会被应用整表拒收 |
| `models[].id` | OpenAI 兼容 model id（一键生成 Agent 时预置的 modelId） |
| `models[].name` / `models[].desc` | 界面展示名与一句话描述 |
| `models[].contextWindow` | 上下文窗口（token 数，正整数），界面提示用 |
| `updatedNote` | 本次更新说明，界面可展示 |

## 当前清单

| id | 用途 |
|---|---|
| `auto` | 三路智能路由：生图 → FLUX；代码/推理 → Qwen3.8-27B；日常 → Qwen3.5-9B |
| `qwen3.5-9b` | 日常对话，64K 上下文 |
| `qwen3.8-27b` | 代码与深度推理，32K 上下文 |

服务由提供方个人主机经 Cloudflare Tunnel 对外提供，凭 API Key 访问；key 由服务提供方私下分发，与本仓库无关（仓库里永远不出现 key）。
