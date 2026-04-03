## Anaconda
- 查看所有环境：conda env list
- 创建conda环境，指定python版本：conda create -n name python=3.11
- 激活环境：conda activate odoo18
- 删除对应版本：conda env remove --name odoo18
- 退出当前环境：conda deactivate

## linux
- 过滤：grep
- 排除xxx相关的信息：grep -v xxx
- 查看一定时间内的日志：grep -e '10:3[0-5]'
- 查看29和30分这两个时间日志：grep -E '10:2[9]|10:30'
- 把二进制信息强制当成文本解析：grep -a "error" xxx.log
- 流式查看：tail
- 流式查看日志：tail -f /opt/log/xxx.log
- 查看最进20行日志：tail -n 20 /opt/log/xxx.log
- 先看20行再实时追踪：tail -n 20 -f /opt/log/xxx.log
- 查看文件：ca
- 查看文件内容：ca /xx/xx/xx.log
- 看进程状态：ps
- 显示所有用户进程：ps aux
- 查看所有关于java的进程：ps -ef | grep java
- 直接变成超级用户(前提有sudo权限)：sudo -i
- curl
- 访问接口：curl http://localhost:9999/api/xre/sys/refresh/233
- 开启历史记录：set -o history
- 关闭历史记录：set +o history
- 详细格式列出目录：ll
- 查看特定时间之前的日志：ls wxapi.log.*.log | awk -F'[._]' '{ if ($3$4$5 < 20251220) print $0 }'
- 查看再删除特定时间之前的日志：ls wxapi.log.*.log | awk -F'[._]' '{ if ($3$4$5 < 20251220) print $0 }' | xargs -r rm -f
- 启动服务：sudo systemctl start odoo-ce
- 杀掉进程：sudo kill 4715
- 开机自启：sudo systemctl enable odoo-ce
- 激活python环境：source /usr/local/odoo-ce/odoo18-venv/bin/activate
- 递归修改用户组：sudo chown -R odoo:114 /usr/local/odoo-ce
- 除activate等外赋予权限：`find /usr/local/odoo-ce/odoo18-venv/bin -type f ! -name "activate" ! -name "activate.csh" ! -name "activate.fish" ! -name "Activate.ps1" -exec chmod 755 {} \;`
- 递归赋予目录权限：chmod -R 755 /usr/local/odoo-ce/odoo18-venv/lib
- 编辑网络配置文件：sudo nano /etc/network/interfaces
- 重启网络服务：sudo systemctl restart networking
- 静态IP配置示例（interfaces）：
  ```
  auto ens33
  iface ens33 inet static
      address 192.168.3.215
      netmask 255.255.255.0
      gateway 192.168.3.1
      dns-nameservers 8.8.8.8 8.8.4.4
  ```

## PostgreSQL / psql
- 登录：psql -U postgres
- 连接数据库：psql -U 用户名 -d 数据库名 -W
- 指定主机连接：psql -h 127.0.0.1 -U 用户名 -d 数据库名
- 创建用户：`CREATE USER "odoo-ce" WITH PASSWORD '12345678';`
- 给权限：`ALTER USER "odoo-ce" CREATEDB;`
- 查看所有用户：\du
- 查看数据库列表：\l
- 切换数据库：\c 数据库名
- 查看当前数据库：SELECT current_database();
- 查看所有表：\dt
- 退出：\q

## python
- 安装依赖：pip install -r requirements.txt

## 网络检查
- 检查网址是否在线：curl -I http://13313777163.kmdns.net:8019
- 检查服务器是否响应：ping 13313777163.kmdns.net
- 检查端口是否开放：telnet 13313777163.kmdns.net 8019

## 数据库
- 切换数据库：web/database/manager，密码：system

## Redis (Windows)
- 注册服务：redis-server.exe --service-install redis.windows.conf
- 启动服务：redis-server.exe --service-start
- 开机自启：sc config Redis start= auto
- 停止服务：redis-server.exe --service-stop
- 卸载服务：redis-server.exe --service-uninstall

## minio
- 启动：`minio server D:\minio-data --address :9900 --console-address :9901`
- 设置别名：`mc alias set local http://localhost:9900 minioadmin minioadmin`（mc.exe 放 minio.exe 同目录，Mac 需加执行权限：chmod +x mc）
- 设置桶可公开下载：mc anonymous set download local/memo-user-avatar
- 设置桶公开策略：mc policy set public local/memo-user-avatar

## git
- 回退到指定版本：git reset --hard f75c6a83
- 放弃之前修改：git reset --hard
- 切换分支：git checkout v2026.3.13-1
## npm清缓存
- npm cache clean --force

## 代理 (环境变量)
- 设置 http/https 代理：`export http_proxy=http://127.0.0.1:10808`、`export https_proxy=http://127.0.0.1:10808`
- 设置全协议代理：`export all_proxy=socks5://127.0.0.1:10808`
- 大写变量（部分工具用）：`export HTTP_PROXY`、`export HTTPS_PROXY`、`export ALL_PROXY`