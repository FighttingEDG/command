## openclaw和hermes 部署
- 目前macmini是docker部署的，并且是github拉的最新代码build的镜像
- 真实代码路径：/Users/yuhongyang/AiWorkspace
- 配置文件：代码目录config，.env文件，还有docker-compose.yml
- dockerfile里面是插件配置文件，特别是hermes的，很重要
## docker相关命令
- 大多数重启：docker compose down && docker compose up -d
- 修改了dockerfile只能强制重新构建再重启：
    - 
    ```
        docker compose build --no-cache --pull \
            --build-arg HTTP_PROXY=http://host.docker.internal:10808 \
            --build-arg HTTPS_PROXY=http://host.docker.internal:10808
    ```
## 更新版本
- git pull拉取最新版本
- 还需要把.env和docker-compose.yml，dockerfile还有config的镜像改成本地的
- 强制重新构建
- 启动


## Hermes相关
## 关键信息
## 发送消息应该约定
- 放一个视频：/Users/yuhongyang/AiWorkspace/shared-workspace/video/inbox/demo.mp4
- 请用 Hermes 把 /workspace/video/inbox/demo.mp4 的 00:00:10 到 00:00:30 剪出来，输出到 /workspace/video/output/demo_cut.mp4，并返回执行命令和结果路径。