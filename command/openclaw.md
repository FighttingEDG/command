## openclaw 部署
- 目前macmini是docker部署的，并且是github拉的最新代码build的镜像
- 真实代码路径：/Users/yuhongyang/clawWorkspace
- 配置文件：代码目录config，.env文件，还有docker-compose.yml
## docker相关openclaw命令
- 修改配置重启：docker restart openclaw-openclaw-gateway-1
- 改了.env后应该充分重启：config % cd /Users/yuhongyang/clawWorkspace/openclaw；docker compose down;docker compose up -d
## 更新版本
- git pull拉取最新版本
- 还需要把.env和docker-compose.yml的镜像改成本地的
- 强制重新构建：docker compose build --no-cache
- 启动：docker compose up -d