## brew命令
- 已管理服务:emqx,mysql
- 启动 EMQX:brew services start emqx;停止stop;重启restart
- 查看状态:brew services list | grep emqx
- 后台启动:emqx start;停止stop;服务状态status
- 前台运行(日志):emqx foreground

## 系统级别管理服务
- 自启：sudo launchctl load -w /Library/LaunchDaemons/com.frpc.plist
- 退出：sudo launchctl bootout system/com.crmeb.swoole 2>/dev/null || true
- 启动：sudo launchctl bootstrap system /Library/LaunchDaemons/com.crmeb.swoole.plist
- 重启：sudo launchctl kickstart -k system/com.crmeb.swoole
- 查看状态：sudo launchctl list | grep minio

## ngix重启
- sudo nginx -t && sudo nginx -s reload

## 


## crmeb问题
- 长连接：cd /Users/yuhongyang/produc/crmeb/crmeb && sudo rm -f runtime/workerman.pid；sudo launchctl kickstart -k system/com.crmeb.swoole
- 查看日志：log show --predicate 'eventMessage CONTAINS "com.crmeb.swoole"' --last 1h