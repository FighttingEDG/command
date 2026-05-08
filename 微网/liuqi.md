## 本地启动
- 纯服务部署开发非docker：
    - redis：redis-cli -a 12345678
    - nacos：cd /Users/jevonsmac/Desktop/project/infrastructure/nacos/bin；sh startup.sh -m standalone
    - 可选Sentinel：java -Dserver.port=8718 -jar sentinel-dashboard-1.8.6.jar
- 
## 启动顺序
1. MySQL
2. Redis
3. Nacos
4. ruoyi-auth
5. ruoyi-modules/ruoyi-system
6. ruoyi-gateway
## 当前修改
- ruoyi-gateway-dev.yml注释了 key-resolver: "#{@pathKeyResolver}" # 使用 SpEL 表达式按名称引用 bean