## 问问题方式案例
- 请真实执行：/workspace/video/tools/video_task plan 人物叙述.mp4，返回命令输出，不要总结历史结果。@小软

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
    ```
        docker compose build \
            --build-arg http_proxy= \
            --build-arg https_proxy= \
            --build-arg HTTP_PROXY= \
            --build-arg HTTPS_PROXY= \
            --build-arg all_proxy= \
            --build-arg ALL_PROXY= \
        openclaw-gateway
    ```
- 查看实时日志：docker logs --tail 100 -f openclaw-gateway
- 查看实时日志：docker logs --tail 100 -f openclaw-gateway
## 更新版本
- git pull拉取最新版本
- 还需要把.env和docker-compose.yml，dockerfile还有config的镜像改成本地的
- 强制重新构建
- 启动
## 更新openclaw技能
- skill在repo的skill文件夹下更新
- 更新网必须重新build再down，再up

## Hermes相关
## 关键信息
## 发送消息应该约定
- 放一个视频：/Users/yuhongyang/AiWorkspace/shared-workspace/video/inbox/demo.mp4
- 请用 Hermes 把 /workspace/video/inbox/demo.mp4 的 00:00:10 到 00:00:30 剪出来，输出到 /workspace/video/output/demo_cut.mp4，并返回执行命令和结果路径。

## 调试步骤
- 删除旧产物：
rm -f /Users/yuhongyang/AiWorkspace/shared-workspace/video/tmp/人物叙述.transcript.srt
rm -f /Users/yuhongyang/AiWorkspace/shared-workspace/video/tmp/人物叙述.edit_plan.json
rm -f /Users/yuhongyang/AiWorkspace/shared-workspace/video/output/人物叙述_auto.mp4
- 直接hermes执行任务：docker exec hermes /workspace/video/tools/video_task auto-cut 人物叙述.mp4
- 查看产物：ls -lah /Users/yuhongyang/AiWorkspace/shared-workspace/video/tmp
ls -lah /Users/yuhongyang/AiWorkspace/shared-workspace/video/output
- 查看当前视频信息
yuhongyang@Mac ~ % docker exec hermes ffprobe -v error -show_entries format=duration,size -of default=nw=1 /workspace/video/output/人物叙述_auto.mp4
duration=61.658000
size=10766713

## 当前增加以及修改过的东西
- ！！！后续需要整理一次
