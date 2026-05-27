## mysql常用命令
- mac下brew安装启动：mysql.server start
- 打包数据库sql：mysqldump -u root -p --databases scales_power --result-file=E:/note_db.sql
- 导入数据库sql：mysql -u root -p scales_power < /Users/jevonsmac/Desktop/project/wwProject/李亮工作对接资料/4期/scales_power.sql