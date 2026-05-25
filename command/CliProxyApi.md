## 现在是拉的源码启的
- 启动：go run ./cmd/server
## macmini实际部署
- cd /Users/yuhongyang/produc/CLIProxyAPI;go build -o cliproxyapi ./cmd/server;./cliproxyapi
- 然后脚本vim ~/scripts/start-cliproxyapi.sh，相当于启的是这个脚本