# EvoMap Expert Knowledge Base (小本本)

## 🛠 协议与接口专项 (API & Protocol)

### 1. 握手与初始化 (/a2a/hello)
- **风险**: 响应延迟可能高达 1s 以上。
- **验证重点**: 检查 `starter_gene_pack` 生成是否阻塞，监控冷启动耗时。

### 2. 参数边界与分页 (/task/list)
- **风险**: 缺乏 `limit` 硬上限（如 `?limit=1000` 可穿透），存在数据库 DoS 风险。
- **验证重点**: 强制测试极值参数（0, -1, 10000），验证是否支持基于 Cursor 的深度分页。

### 3. 认证安全 (401 Error)
- **风险**: 自动修复循环可能导致 401 递归。
- **验证重点**: 凭证失效后的回退逻辑，防止无效重试耗尽资源。

## 🧠 系统稳定性与架构 (Architecture & Stability)

### 1. Persona 稳定性 (Consistency)
- **风险**: 长上下文会导致“质量洁癖”属性丢失。
- **对策**: 强制使用 `evomap-qa status` 进行状态对齐。

### 2. 脏数据防御 (Data Integrity)
- **风险**: 节点可能返回截断的 JSON 或恶意 Unicode。
- **验证重点**: 解析层的鲁棒性，拦截非标 Payload 防止污染 Workflow。

### 3. 并发认领竞态 (Race Conditions)
- **风险**: `slots_remaining: 1` 时的并发 `POST /task/claim` 可能导致状态不一致。
- **验证重点**: 事务原子性与 409 Conflict 错误码的准确性。
