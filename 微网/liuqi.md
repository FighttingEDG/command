## 本地启动
- 纯服务部署开发非docker：
    - redis：redis-cli -a 12345678
    - nacos：cd /Users/jevonsmac/Desktop/project/infrastructure/nacos/bin；sh startup.sh -m standalone
    - 可选Sentinel：cd /Users/jevonsmac/Desktop/project/infrastructure；java -Dserver.port=8718 -jar sentinel-dashboard-1.8.6.jar
- 
## 启动顺序
1. MySQL
2. Redis
3. Nacos
4. ruoyi-auth
5. ruoyi-modules/ruoyi-system
6. ruoyi-gateway
7. sp-base
8. sp-event
9. sp-statement
10. sp-fcast
## 部署流程
1. html打包文件要放在/opt/scales-power-data/docker/nginx/html/dist，会复制到/home/ruoyi/projects/ruoyi-ui的
1. 打包jar包：cd /Users/jevonsmac/Desktop/project/wwProject/wuqi/scales-power-cloud；mvn clean package -DskipTests
2. cpoyjar包：cd /Users/jevonsmac/Desktop/project/wwProject/wuqi/scales-power-cloud/docker；sh copy.sh
3. 服务器cd到docker一键构建：docker compose build
4. 一键启动：docker compose up -d
5. 重新打包重启所有服务：  docker compose build;docker compose up -d；docker compose ps