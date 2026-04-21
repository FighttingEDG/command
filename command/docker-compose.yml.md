# Docker Compose 最简模板（通用版）
> 这是一个“纯 Docker 入门级最小结构”，不依赖任何框架（Node/Python/AI 都没有）。
---

# 1. docker-compose.yml

```yaml id="compose-basic"
# Docker Compose的规范版本
version: "3.9"

services:

  # =========================
  # 🧪 示例服务（最基础容器）
  # =========================
  app:
    ## image是已经打包好的镜像，所以docker-compose.yml只是申明运行规则，Dockerfile才定义如何构建image
    image: hello-world:latest   # 使用官方最轻量测试镜像，image 是否与本地有关，取决于是否使用：build，volumes，外部依赖注入

    # 容器启动后执行的命令（hello-world 会自动退出）
    command: ""

    # 是否重启（避免退出后自动重启）
    restart: "no"
```