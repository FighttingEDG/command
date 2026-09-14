## 服务器密码
- wwsdqwer
## 部署情况
- 服务位置：/etc/systemd/system/erp2.service
## 更新代码命令
1. 在公司（连 Wwsd-1505，密码 Wwsd11233.）
- scp -r /Users/name/Desktop/v2power_erp/* root@192.168.33.147:/opt/v2power_erp_v2/
- ssh root@192.168.33.147 " systemctl restart erp2"
2. 在家（ssh -p 22022 root@113.98.254.74）
- scp -r -P 22022 /Users/jevonsmac/Desktop/v2power_erp/* root@113.98.254.74:/opt/v2power_erp_v2/
- ssh -p 22022 root@113.98.254.74 "systemctl restart erp2"