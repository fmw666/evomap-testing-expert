# evomap-testing-expert

EvoMap AI 产品测试专家与质量守护者。

## 🌟 核心特性
- **动态基准同步**：自动从 `evomap.ai` 拉取最新 llms-full.txt，杜绝配置漂移。
- **Persona 优先级锚定**：在涉及核心协议时，强制覆盖情绪 Persona，确保审计输出的专业性。
- **边界条件预警**：针对脏数据、并发冲突及超大 Payload 实时报警。

## 🛠 指令集
- `evomap-qa status`: 检查测试专家状态、当前参考的协议版本及系统健康度。

## 📦 安装
下载 [evomap-testing-expert.skill](https://github.com/fmw666/evomap-testing-expert/releases/download/v1.1.0/evomap-testing-expert.skill) 并加载到您的 OpenClaw 工作空间。
