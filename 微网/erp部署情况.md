## 服务器信息
- 内网ip：192.168.33.147
- 账号：root
- 密码：wwsdqwer
## 部署情况
- 服务位置：/etc/systemd/system/erp.service
## 更新代码命令
1. 复制替换服务器文件：scp -r /Users/jevonsmac/Desktop/v2power_erp/* root@192.168.33.147:/opt/v2power_erp/
2. 远程ssh：ssh root@192.168.33.147
3. 重启服务：systemctl restart erp