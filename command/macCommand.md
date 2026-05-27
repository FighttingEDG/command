## 环境
- nacos：/Users/jevonsmac/Desktop/project/infrastructure/nacos
- pyenv管理python版本，python3.11.9,pyenv是brew安装的
- 现在的mac的nacos的配置文件是写死的nacos数据库的
- nginx是brew安装的
- mysql是brew安装的

## brew命令
- 已管理服务:emqx,mysql
- 启动 EMQX:brew services start emqx;停止stop;重启restart
- 查看状态:brew services list | grep emqx
- 后台启动:emqx start;停止stop;服务状态status

## 系统级别管理服务
- 自启：sudo launchctl load -w /Library/LaunchDaemons/com.frpc.plist
- 退出：sudo launchctl bootout system/com.crmeb.swoole 2>/dev/null || true
- 启动：sudo launchctl bootstrap system /Library/LaunchDaemons/com.crmeb.swoole.plist
- 重启：sudo launchctl kickstart -k system/com.crmeb.swoole
- 查看状态：sudo launchctl list | grep minio

## ngix重启
- sudo nginx -t && sudo nginx -s reload
- ubuntu:sudo systemctl restart nginx

## 远程
- 远程mac命令：ssh -p 10001 yuhongyang@120.55.112.67

## 临时修改ip
- 固定ip：sudo ifconfig en0 192.168.2.222 netmask 255.255.255.0
- 删除多余的ip：sudo ifconfig en0 -alias 192.168.2.222
- 自动获取ip：sudo ipconfig set en0 DHCP

# 安全性
## 去掉“隔离标签（quarantine attribute）”，让系统不再认为它来自“危险来源”
- sudo xattr -rd com.apple.quarantine /Applications/xxxx.app
## 启用睡眠
- sudo pmset -a disablesleep 0

## crmeb问题
- 长连接：cd /Users/yuhongyang/produc/crmeb/crmeb && sudo rm -f runtime/workerman.pid；sudo launchctl kickstart -k system/com.crmeb.swoole
- 查看日志：log show --predicate 'eventMessage CONTAINS "com.crmeb.swoole"' --last 1h