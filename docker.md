## docker部署openclaw
- 先在隔离文件夹(建议用users/xx/下的文件夹)下拉取源码
- 使用git checkout v2026.3.13-1切换到固定版本
- 构建镜像：docker build -t openclaw:local -f Dockerfile . 
    - docker build → 告诉 Docker 开始构建镜像。
    - -t openclaw:local → 给镜像打上名字和标签（tag），这里名字是 openclaw，标签是 local。
    - -f Dockerfile → 指定要用的 Dockerfile 文件（可以不写，如果文件名正好是 Dockerfile）。
    - . → 上下文目录，Docker 会读取这个目录下的文件来构建镜像。
- 用 Docker Compose 运行一次性任务：docker compose run --rm openclaw-cli onboard
    - docker compose run → 启动一个容器并运行指定服务。
    - --rm → 任务完成后自动删除容器，不留临时容器。
    - openclaw-cli → Docker Compose 配置文件里定义的服务名
    - onboard → 传给容器的命令，这里是 OpenClaw 的初始化或注册操作。
- 启动 OpenClaw 的网关服务，并在后台运行：docker compose up -d openclaw-gateway
    - docker compose up → 根据 docker-compose.yml 启动服务。
    - -d → 后台运行（detached mode），终端不会被占用。
    - openclaw-gateway → 要启动的服务名，可以只启动这个服务，不启动 Compose 文件里的其他服务。

## 常用命令
- 查看当前镜像：docker images
- 停止并移除(不建议使用)：docker compose down（改了.env环境变量要先移除再启动）
- 启动网关：docker compose up -d (--force-recreate) openclaw-gateway;--force-recreate强制删除旧容器并创建一个新容器
- 停止网关：docker compose stop openclaw-gateway
- 重启网关：docker compose restart openclaw-gateway
- 查看前状态：docker ps
- 查看当前docker存储占用情况：docker system df
- 删除打包产生的缓存：docker builder prune


## 需要修改
-  docker-compose.yaml
      HTTP_PROXY: ${OPENCLAW_HTTP_PROXY:-}
      HTTPS_PROXY: ${OPENCLAW_HTTPS_PROXY:-}
      ALL_PROXY: ${OPENCLAW_ALL_PROXY:-}
      http_proxy: ${OPENCLAW_HTTP_PROXY:-}
      https_proxy: ${OPENCLAW_HTTPS_PROXY:-}
      all_proxy: ${OPENCLAW_ALL_PROXY:-}
      NO_PROXY: ${OPENCLAW_NO_PROXY:-localhost,127.0.0.1}
      no_proxy: ${OPENCLAW_NO_PROXY:-localhost,127.0.0.1}
- 添加.env文件
    OPENCLAW_IMAGE=openclaw:local
    OPENCLAW_CONFIG_DIR=/Users/yuhongyang/clawWorkspace/config
    OPENCLAW_WORKSPACE_DIR=/Users/yuhongyang/clawWorkspace/workspace
    OPENCLAW_GATEWAY_PORT=18789
    OPENCLAW_BRIDGE_PORT=18790
    HTTP_PROXY: ${OPENCLAW_HTTP_PROXY:-}
    HTTPS_PROXY: ${OPENCLAW_HTTPS_PROXY:-}
    ALL_PROXY: ${OPENCLAW_ALL_PROXY:-}
    http_proxy: ${OPENCLAW_HTTP_PROXY:-}
    https_proxy: ${OPENCLAW_HTTPS_PROXY:-}
    all_proxy: ${OPENCLAW_ALL_PROXY:-}
    NO_PROXY: ${OPENCLAW_NO_PROXY:-localhost,127.0.0.1}
    no_proxy: ${OPENCLAW_NO_PROXY:-localhost,127.0.0.1}

## 首次会遇到
- 列出待批准配对的设备：docker compose run --rm openclaw-cli devices list
- 批准某台设备：docker compose run --rm openclaw-cli devices approve <requestId>