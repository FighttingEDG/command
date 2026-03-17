## openclaw 部署

### 一键部署
- 执行：`curl -fsSL https://openclaw.ai/install.sh | bash`

### 配置
- gateway 端口：18789
- token：508593b26f0225e75d5c4aa43405eda80a26ee4e5046b4c8（需放在 `OPENCLAW_GATEWAY_TOKEN` 环境变量中）
- OpenRouter Key：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

### 命令
- 查看 gateway 状态：openclaw gateway status
- 启动：openclaw gateway start
- 关闭：pkill openclaw
- 自动修复：openclaw doctor --fix(不使用)
- 启动并显示日志：openclaw gateway run
- 临时强制启动(忽略警告)：openclaw gateway run --allow-unconfigured
- 指定新的key：openclaw auth add openrouter:default --api-key "你的新KEY"
- 设置新的token：openclaw config set gateway.auth.token "Jevon1659782099"
- 查看当前skills：openclaw skills list
- 使用npx从clawhub下载技能：npx clawhub install video-frames
- 停掉守护进程：launchctl stop ai.openclaw.gateway
- 移除自启：launchctl remove ai.openclaw.gateway